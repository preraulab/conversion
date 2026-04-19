# conversion

Type, format, and representation conversions — numbers to strings, structs to name-value cells, tables ↔ CSV.

Part of the Prerau Lab [`utils`](https://github.com/preraulab/utils) meta-repository. Can also be used standalone.

## When to use which

| Task | Use |
|---|---|
| Format double as an exponential string (for axis labels) | `double2estr`, `double2expstr` |
| Format double as a fraction | `double2fracstr` |
| Format double as a multiple of π | `double2pifracstr` |
| Generic value → string | `value2str` |
| Convert a numeric array to a cell of strings | `num2cellstr` |
| Struct → `{'k1', v1, ...}` cell (ready for `varargin`) | `struct2nvp` |
| Struct → `'k1', v1, ...` string (for code) | `struct2nvpstr` |
| Struct → literal MATLAB code text | `struct2codestr` |
| MATLAB table ↔ CSV | `table2csv`, `csv2table` |

## Examples

```matlab
% Struct -> name-value pairs for varargin
opts = struct('Fs', 200, 'thresh', 3.5, 'verbose', true);
nvp  = struct2nvp(opts);
my_fn(data, nvp{:});   % same as: my_fn(data, 'Fs', 200, 'thresh', 3.5, 'verbose', true)

% pi-fraction axis labels
xticklabels(arrayfun(@double2pifracstr, xticks, 'UniformOutput', false));
% e.g. -> 'pi/4', 'pi/2', '3pi/4', 'pi'

% CSV round-trip
T = csv2table('input.csv');
table2csv(T, 'output.csv');
```

## Function list

`csv2table`, `double2estr`, `double2expstr`, `double2fracstr`, `double2pifracstr`, `num2cellstr`, `struct2codestr`, `struct2nvp`, `struct2nvpstr`, `table2csv`, `value2str`

See `help <function>` at the MATLAB prompt for the full docstring of each.

## Install

```matlab
addpath('/path/to/conversion');
```

## Dependencies

MATLAB R2020a+. No required toolboxes.

## License

BSD 3-Clause. See [`LICENSE`](LICENSE).
