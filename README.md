# Sequence Analysis

A program that compares NGS reads to a known reference seqeuence to identify mutations in the sequenced DNA.
This allows identification of mutation patterns in *S. pombe* yeast samples treated and not treated with a genotoxic agent.

## How to run
1. Open the file in google colab
2. File --> save a copy in Drive
3. Click "run all".

## Inputs and outputs
The program requires a .csv file of NGS sequencing reads, which contains the read_id, sample, group, and the read sequence for each read.
It then outputs a table showing the number of valid and invalid reads, mismatch percentage and events and top 3 positions for each sample. Then a Welch's t-test between the treated/untreated samples is conducted for the top 3 positions.

## Coding decisions
When printing the statistical analysis results for the compare_positions function, if falsy values (None, empty list/dict etc) were in the variables, a TypeError would occur in the f-string. Therefore, for variables that could be falsy, I made a one-line if/else statement: treated_mean/control_mean would be set to "0.0 %", and statistic/p_value would be set to "N/A" if they were falsy.

The helper functions made in step 4 was used to separate the summarise_samples function to split the summarise_samples function into smaller, more manageable blocks of code. Also, the helper function top_3_positions was reused in step 5 (for the compare_positions function), reducing code repetition and complexity.

## Testing
When testing compare_positions(),  One test had inputs that contained falsy values. This was to check if falsy values were properly handled. <br>
For validate_reads(), one test had an input of an empty string for sequence to check if it would correctly be identified as an invalid read. <br>
For find_mutations(), one test had the same sequence and reference, to check if the output would be empty (expected output).
