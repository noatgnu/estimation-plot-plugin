# Estimation Plot

**ID**: `estimation-plot`  
**Version**: 1.0.0  
**Category**: visualization  
**Author**: CauldronGO Team

## Description

Generate estimation plots with effect sizes using DABEST

## Runtime

- **Type**: `python`
- **Script**: `estimation_plot.py`

## Inputs

| Name | Label | Type | Required | Default | Visibility |
|------|-------|------|----------|---------|------------|
| `input_file` | Input Data File | file | Yes | - | Always visible |
| `annotation_file` | Sample Annotation File | file | Yes | - | Always visible |
| `index_col` | Index Column | text | Yes | - | Always visible |
| `selected_proteins` | Selected Proteins/Features | text | Yes | - | Always visible |
| `log2` | Apply Log2 Transformation | boolean | No | true | Always visible |
| `condition_order` | Condition Order | text | No | - | Always visible |

### Input Details

#### Input Data File (`input_file`)

Data file containing protein/feature intensities


#### Sample Annotation File (`annotation_file`)

Sample annotation file with conditions


#### Index Column (`index_col`)

Column name to use as feature identifier (e.g., Protein.IDs)


#### Selected Proteins/Features (`selected_proteins`)

List of proteins/features to plot (one per line or comma-separated)


#### Apply Log2 Transformation (`log2`)

Apply log2 transformation to values before plotting


#### Condition Order (`condition_order`)

Comma-separated list of conditions in desired order

- **Placeholder**: `Control,Treatment1,Treatment2`

## Outputs

| Name | File | Type | Format | Description |
|------|------|------|--------|-------------|
| `estimation_plots` | `*.svg` | image | svg | Estimation plots for each selected protein (one SVG per protein) |
| `statistics` | `*_stats.tsv` | data | tsv | Statistical test results for each protein |

## Visualizations

This plugin generates 1 plot(s):

### Estimation Plots (`estimation_plots`)

- **Type**: image-grid
- **Data Source**: `estimation_plots`
- **Image Pattern**: `*.svg`

## Requirements

- **Python**: >=3.11
- **Packages**:
  - pandas>=2.0.0
  - numpy>=1.24.0
  - dabest>=2023.2.14
  - matplotlib>=3.7.0

## Example Data

This plugin includes example data for testing:

```yaml
  index_col: Precursor.Id
  selected_proteins: AAAAAAPAGGPAAAAPSGENEAESR3,AAAAADLANR2,AAAAATVVPPMVGGPPFVGPVGFGPADR3
  log2: true
  input_file: diann/imputed.data.txt
  annotation_file: differential_analysis/annotation.txt
```

Load example data by clicking the **Load Example** button in the UI.

## Usage

### Via UI

1. Navigate to **visualization** → **Estimation Plot**
2. Fill in the required inputs
3. Click **Run Analysis**

### Via Plugin System

```typescript
const jobId = await pluginService.executePlugin('estimation-plot', {
  // Add parameters here
});
```
