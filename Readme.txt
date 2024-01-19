
	VLC_CTK 1.2 release notes:  

Updates:  

1.	Updated Ctoolkit.pdf manual.

2.	The CToolkit.rcd sample, now uses the +LONG_PAD method 
	to ensure 4 bytes values.  LONG_PAD is defined as 0L. 
	This is a preferred method because the resulting value 
	is always 4 bytes,  regardless on how the actual value is defined. 

3.	Adds a default definition for COMPANYNAME  and LEGALCOPYRIGHT.  
	These 2 keys are supposed to be defined in version.h.	
	If your compiler complains about them being defined twice,  
	check View/Resource Includes  on  <module_name>.rc.  
	Globcom.h should not be among the included files.  




	VLC_CTK 1.1 release notes:  


New featrures:  

1.	Support for INtime 2.0 

2.	Support for both MS Visual C++ 6.0 and 5.0

3.	The installation path is no longer hard-coded to \INtime. 
	It now is an install time option.  
	By default it is suggested to Vlc\Development.  

4.	Better version information.  
	Version tab on <module_name>.rt3/Properties.  

5.	The C Runtime debugger is now a separate product called VLC_CDB.

6.	Uninstall.



Fixed bugs:  

1.	Process hung up when functions from the C Standard Runtime library 
	are called.  C Modules created with CTK 1.0 and used with VLC 4.1 
	are affected.  These modules need to be re-built with CTK 1.1.  



How to port a project from CTK 1.0 to CTK 1.1:

The CToolkit project installed by CTK 1.1 shows how a good project should 
look like.  
The following is a list of CToolkit settings that have changed from 1.0 
to the 1.1 sample.

To build the project under CTK 1.1 please check for the following settings: 

	Project/Settings/Runtime/All Configurations
		C/C++/Preprocessor
			Additional include directories:
				".\inc;..\..\inc;..\..\intime\inc"
			Ignore standard include paths:	
				Checked
			
		Link	
			Additional library path:			
				"..\..\lib;..\..\intime\lib"


If the C module defines very large static data (over 64K), 
please check for the following settings: 

	Project/Settings/Runtime/All Configurations
		Link	
			Project Options:			
				/heap:0x100000,0x4000 


To bring in version information to a <module_name>.rt3 file 
created with VLC_CTK 1.0:  

1.	Copy CToolkit\Runtime\version.rc to <module_name>\Runtime

2.	Add it to the MSVC <module_name>\Runtime project. 

3.	Edit <module_name>\inc\version.h to follow the 
	CToolkit\inc\version.h sample



