# OCI Compute Capacity Checker OCI Python SDK

These scripts run against your tenancy and check for availability and available count for the OCI Compute shapes you specify. 
The "GetComputeShapes.py" script will provide you with a list of compute shapes, their specifications and proper naming conventions to use in "GetComputeCapacity.py".

## Prerequisites
Before you run this script, make sure you have authentication to your tenancy via OCI CLI with proper priveleges, as well as being whitelisted to view compute capacity. 
Contact your OCI Sales Representative and Cloud Engineer to verify you can be whitelisted. 

## Setup
### Optional
1. Add your tenancy OCID/Compartment ID in GetComputeShapes.py
2. Run GetComputeShapes.py to get a .CSV and terminal output of available OCI Compute Shapes and their names to use later. 
```
python3 ./GetComputeShapes.py
```

### Required
1. Add your tenancy OCID/Compartment ID in GetComputeCapacity.py
2. Add your regions you wish to query - Ex: "us-ashburn-1", "us-phoenix-1" etc etc. 
3. Add your desired OCI Compute shape type and sizing - Ex: "{"shape": "VM.Standard.E5.Flex", "ocpus": 1, "memory_in_gbs": 16}" 
NOTE - The amount of OCPU and Memory you specify will determine how many "counts" you will see in the output, or available amount of machines you can provision. 
4. Run GetComputeCapacity.py
```
python3 ./GetComputeCapacity.py
```

NOTE - The script will output in both terminal and a timestamped JSON file to parse from if you're integrating with other scripts. 

### Output
GetComputeCapacity.py will take all the shapes you described and begin to loop through every region described. 
Within each region, the script will run through all availability-domains in that region, as well as each fault domain - then provide you with capacity results. 
Exmaple
```
Shape=VM.Standard3.Flex (OCPUs=1.0, Mem=8.0GB), FD=FAULT-DOMAIN-1 -> Status=AVAILABLE, Count=xxxxxxxx
```


## Updates
Added optional JSON output, creating a timestamped JSON file container all of the compute capacity information. 
