zynamics MSDN Crawler has moved to Google Code
==============================================

This repository has moved to Google Code:
http://code.google.com/p/zynamics/source/checkout?repo=msdn-crawler



zynamics msdn-crawler - Copyright 2010
For updates please check http://github.com/zynamics/msdn-crawler

Using the zynamics MSDN crawler script you can extract Windows API
documentation from compiled MSDN help files. The MSDN crawler parses
the help files and generates an XML file that contains all important
information about Windows API functions.

1. Usage

To run the MSDN crawler you have to do the following:

- Install a local copy of the MSDN documentation (I use the Windows Software
  Development Kit (SDK) for Windows 7 and .NET Framework 3.5 Service Pack 1)
- Get a copy of hxcomp.exe which is the help file decompiler. I got mine from
  the Visual Studio 2005 SDK.
- Decompile all HxS files in your MSDN documentation "help" directory. This
  should give you a lot of subdirectories like "ad", "adam", "adschema", ...
- Run he MSDN crawler like this:

	python msdn-crawler.py C:\Program Files\Microsoft SDKs\Windows\v7.0\Help\1033
	
  Change the path to reflect the location of your decompiled help files.
  
You should see the MSDN crawler running now. When it's done you can find an XML
file called msdn.xml in the directory from which you started the crawler. The
XML file contains information about 33984 functions and has the following
structure:

<?xml version="1.0" encoding="ISO-8859-1"?><msdn>
<functions>
	<function>
		<name>ADsPropCheckIfWritable</name>
		<dll>dsprop.dll</dll>
		<description>The ADsPropCheckIfWritable function determines if an attribute can be written.</description>
		<arguments>
			<argument>
				<name>pwzAttr</name>
				<description>Pointer to a NULL-terminated WCHAR buffer that contains the name of the attribute.</description>
			</argument>
			<argument>
				<name>pWritableAttrs</name>
				<description>Pointer to the array of ADS_ATTR_INFO structures returned by ADsPropGetInitInfo.</description>
			</argument>
		</arguments>
		<returns> Returns non-zero if the attribute is found in the writable-attribute list or zero otherwise. Also returns zero if pWritableAttrs is NULL.</returns>
	</function>
	...
	
2. License

The MSDN crawler is licensed under the GPL 2.0 license. Please see gpl.txt for
more information.