# convert data to dataframe

```bash
.
├── READMD.md
├── data_struct_info # see step one
│   └── prepare_data_struct.ipynb
├── input_data # where you hold your input data
├── output_data # where you hold your output data
└── main.ipynb
```
# setup
## dependency

it's recommaned to install a new environment use [this script](https://github.com/xsthunder/linux-setting/blob/master/bash-script/conda/create-clean-data.sh)

## installation

```
git clone --recurse-submodules https://github.com/xsthunder/data2dataframe.git
```

# usage
## step one

```
`./data_struct_info/prepare_data_struct.ipynb`
`./data_struct_info/data_struct.json`
```

1. put xlsx files indicating structure in `./data_struct_info/`
2. run `./data_struct_info/prepare_data_struct.ipynb` generating dataframe structure info `./data_struct_info/data_struct.json` from xlsx files in `./data_struct_info`.

### `./data_struct_info/data_struct.json` 

#### designed in following form:

```typescript
type xlsx_files_names = 'exam_list.xlsx' | 'exam_result.xlsx'
type data_struct = {
    [key in xlsx_files_names]:{
        column2pos:{
            [key in columns]:number // indicate where to write a field
        }
        columns:columns // an array of columns in this file
    }
}
```

#### example

```json
[{
    "column2pos": {
        "note_id": 0,
        "value": 1,
        "person_id": 2,
    },
    "columns": [
        "note_id",
        "value",
        "person_id",
    ]
}]
```

## step two

put your convention code in `main.ipynb`, read from `input_data`, write to `output_data`, see example in `main.ipynb`