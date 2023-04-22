# Deepmind Mathematics Datasæt

Dette er en dansk version af Deepmind's matematikdatasæt, originalen på engelsk er: https://github.com/deepmind/mathematics_dataset

Koden genererer matematiske spørgsmål-svar-par, med en sværhedsgrad der cirka svarer til folkeskole- eller gymnasiumniveau.

Original artikel: [Analysing Mathematical
Reasoning Abilities of Neural Models](https://openreview.net/pdf?id=H1gR5iR5FX)
(Saxton, Grefenstette, Hill, Kohli).

## Eksempler

```
Spørgsmål: Løs 2408*j - 45066 - 24954 = -2260*j for j.
Svar: 15

Spørgsmål: Lad w være (2/((-20)/(-6)))/(3/30). Lad g være 6*2/w + 24. Lad m = 28 - g. Løs r + m*r = -9 for r.
Svar: -3

Spørgsmål: Læg 3 og 0.08872144616 sammen.
Svar: 3.08872144616

Spørgsmål: Hvad er værdien af (9810/(-5450))/((-93)/(-5))?
Svar: -3/31

Spørgsmål: Sorter 1, 4, 26, 0, -3, 2, 5, 883, 20 i aftagende rækkefølge.
Svar: 883, 26, 20, 5, 4, 2, 1, 0, -3

Spørgsmål: Fem bogstaver bliver udtaget tilfældigt uden tilbagelægning fra jjbejjkeejjjeej. Giv sandsynligheden for sekvensen ejeje.
Svar: 4/429
```

### Version 1.0

This is the version released with the original paper. It contains 2 million
(question, answer) pairs per module, with questions limited to 160 characters in
length, and answers to 30 characters in length. Note the training data for each
question type is split into "train-easy", "train-medium", and "train-hard". This
allows training models via a curriculum. The data can also be mixed together
uniformly from these training datasets to obtain the results reported in the
paper. Categories:

* **algebra** (linear equations, polynomial roots, sequences)
* **arithmetic** (pairwise operations and mixed expressions, surds)
* **calculus** (differentiation)
* **comparison** (closest numbers, pairwise comparisons, sorting)
* **measurement** (conversion, working with time)
* **numbers** (base conversion, remainders, common divisors and multiples,
  primality, place value, rounding numbers)
* **polynomials** (addition, simplification, composition, evaluating, expansion)
* **probability** (sampling without replacement)

## Getting the source

### From GitHub

You can get the source by cloning the mathematics_dataset
repository:

```shell
$ git clone https://github.com/rlrs/mathematics_dataset
$ pip install --upgrade mathematics_dataset/
```

## Generating examples

Generated examples can be printed to stdout via the `generate` script. For
example:

```shell
python -m mathematics_dataset.generate --filter=linear_1d
```

will generate example (question, answer) pairs for solving linear equations in
one variable.

We've also included `generate_to_file.py` as an example of how to write the
generated examples to text files. You can use this directly, or adapt it for
your generation and training needs.