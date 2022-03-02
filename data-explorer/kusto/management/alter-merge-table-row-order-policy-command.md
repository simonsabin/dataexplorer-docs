---
title: ".alter-merge table row order policy command- Azure Data Explorer"
description: "This article describes the .alter-merge table row order policy command in Azure Data Explorer."
services: data-explorer
author: orspod
ms.author: orspodek
ms.reviewer: yonil
ms.service: data-explorer
ms.topic: reference
ms.date: 01/13/2022
---
# .alter-merge table row order policy

Change a table's [row order policy](roworderpolicy.md). The row order policy is an optional table policy that defines the row order in a data shard. This policy can improve performance for queries that relate to a small set of values that can be ordered.

## Syntax

`.alter-merge` `table` *TableName* `policy` `roworder` [*column1* [asc|desc], *column2* [asc|desc],...]

## Arguments

- *TableName* - Specify the name of the table.  
- *column* - specify order of columns and whether columns are ascending (`asc`) or descending (`desc`).

### Examples

Set the row order policy for one table:

```kusto
.alter-merge table events policy roworder (TenantId asc, Timestamp desc)
```

Set the row order policy for several tables:

```kusto
.alter-merge tables (events1, events2, events3) policy roworder (TenantId asc, Timestamp desc)
```