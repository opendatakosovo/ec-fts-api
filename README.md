# ec-fts-api
An API to access data used by the European Commission's Financial Transparency System (FTS)

# POST /api/ec/fts

A query filter is sent as a POST request JSON message body.

## Sample JSON query filter:
```json
{
	'years': [2015, 2016],
	'territories: ['Albania', 'Bosnia and Herzegovina', 'Croatia', 'Kosovo', 'Macedonia', 'Montenegro', and 'Serbia'],
	'beneficiaries': ['AB AMBER GRID', 'LITGRID AB*'],
	'expenseTypes': ['Operational', 'Administrative'],
	'responsibleDeptartments': ['Innovation and Networks Executive Agency'],
	'budgetLines': ['Sustainable energy'],
	'actionTypes': ['Cohesion Fund (CF)', 'Food and Feed'],
	'fundingTypes': ['Grants', 'Provisional commitment followed by payment'],
	'amount': {
		gte: 50000,
		lte: 100000
	},
	sortBy: ['year', 'territory'],
	order: 'asc'
}
```

## Sample Response JSON (not reflective of actual data)
```json
{
	'count': 2,
	'amount': {
		'total': 120000,
		'min': 40000,
		'max': 80000,
		'avg': 
	},
	results: [
		{
			'years': 2015,
			'territory: 'Croatia',
			'beneficiary': 'AB AMBER GRID',
			'expenseType': 'Operational',
			'responsibleDeptartment': 'Innovation and Networks Executive Agency',
			'budgetLine': 'Sustainable energy',
			'actionTypes': 'Cohesion Fund (CF)',
			'fundingTypes': 'Grants',
			'amount': 40000
		},{
			'years': 2016,
			'territory: 'Kosovo',
			'beneficiary': 'LITGRID AB*',
			'expenseType': 'Operational',
			'responsibleDeptartment': 'Innovation and Networks Executive Agency',
			'budgetLine': 'Sustainable energy',
			'actionTypes': 'Cohesion Fund (CF)',
			'fundingTypes': 'Grants',
			'amount': 80000
		}
	]
}
```


# TODO:
Allow for filter parameter that defines grouping of results, e.g. group by budget line.
