The FATES parameter file
--------------------------------------

The FATES parameter file is a text file, and uses the JSON format convention.  JSON is similar to XML in that it relies on key and object pairs, and allows nesting of key and object pairs.  Instead of describing the format here, we recommend reading the standard itself: https://www.json.org/json-en.html .

Or, users may find it is somewhat self explanatory by following how it was built for fates.  A "default" version of this file is maintained in the FATES version control, see here:

https://github.com/NGEET/fates/blob/main/parameter_files/fates_params_default.cdl

Accessing a modified parameter file
"""""""""""""""""""""""""""""""""""
Unlike previous versions of the FATES parameter file, the JSON format is read directly by the FATES model. In the past, the text version of the file (i.e. the "cdl") needed to be converted to a binary format (i.e. the "nc") prior to use. FATES also relied on external code to perform the reading, which resulted in a complicated API and made testing more difficult.

Now, users modify the file to their liking (such as changing parameter values), and simply provide the path to the newly modified parameter file in the namelist during run setup. The namelist variable is "fates_paramfile" and is provided a string with the filepath. Two types of paths are acceptable, a path relative to the land-model's source folder or the absolute file path.

Example: The user creates a set of parameters at their site in Barro Colorado Island, they put it in the FATES parameter folder and call it "fates_params_bci.json", they could either provide the full path to this file, or the following relative paths:

1. For CTSM:

fates_paramfile = 'src/fates/parameter_files/fates_params_bci.json'

2. For E3SM (As of API 43):

fates_paramfile = 'src/external_models/fates/parameter_files/fates_params_bci.json'


Modifying the FATES parameter file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Users may choose to modify the FATES parameter file through various methods, which include:
1. Via a text editor
2. Using python scripting tools provided in https://github.com/NGEET/fates/blob/main/tools/
3. Using their own scripts

Here is a brief description of the tools that are provided:

1. `modify_fates_paramfile.py`_: Python script that allows a command-line style modification of parameters. It can query details about specific parameters. It can modify specific array indices of parameters. It also provides the option of over-writing the input file, or creating a new file. This script can also be used as a "linter" when in its inquire mode, as it will fail gracefully if the user provided an input file that does not conform to the JSON standard.

   

.. _modify_fates_paramfile.py: https://github.com/NGEET/fates/tools/modify_fates_paramfile.py

https://github.com/NGEET/fates/tools/modify_fates_paramfile.py

https://github.com/NGEET/fates/tools/batch_patch_params.py

https://github.com/NGEET/fates/tools/cdl_to_xml.py

https://github.com/NGEET/fates/tools/pft_index_swapper.py

https://github.com/NGEET/fates/tools/sort_parameters.py
