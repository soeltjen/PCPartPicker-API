# PcPartPicker-API

Python3 API for getting part information from [PcPartPicker](https://uk.pcpartpicker.com)

Everything is pulled directly from there, no data is stored in this package

# Documentation

To start using the API, import `PPP_API` from `PcPartPicker` (for example, `from PcPartPicker import PPP_API`)

`PPP_API` contains 2 public functions: `get_part` and `get_total_pages`:

## `get_part(part_type, single_page=False)`

This function returns a list of dictionaries, Each dictionary contains several different keys & values. To see what keys exist you can either print out the dictionary or just look up what keys there will be for your `part_type` in [_PPP_data](https://github.com/thatguywiththatname/PcPartPicker-API/blob/master/PcPartPicker/_PPP_data.py). Every dictionary will always contain the keys `name`, `price` and `ratings` (although they may not always have a value)

`part_type` is your PC part type, for example `cpu` or `cpu-cooler`. A list of these parts are in [_PPP_data](https://github.com/thatguywiththatname/PcPartPicker-API/blob/master/PcPartPicker/_PPP_data.py)

`single_page` is set to `False` by default. `False` means it will scrape all pages and gather all the info it can. If you only want to get information from, for example, page 2 of the cpu results, you would set `single_page` = `2`

## `get_total_pages(part_type)`

This function simply returns the amount of pages of results there are for a particular `part_type`

# Examples:

- Look at [test.py](https://github.com/thatguywiththatname/PcPartPicker-API/blob/master/test.py)
 
- Save all cpu data to `.json` file
	```python
	from PcPartPicker import PPP_API
	import json

	cpu_info = PPP_API.get_part("cpu")

	with open("cpu.json", "w") as outfile:
	    json.dump(cpu_info, outfile)
	```
