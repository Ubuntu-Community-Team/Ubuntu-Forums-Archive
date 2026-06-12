---
title: "how i can install .sh and .bin files in ubuntu 7.04?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-12
Hi
Thank you for reading my post
Can some one please let me know how i can install .sh and .bin files in Ubuntu?

I tried ./myfile.bin and also ./myfile.sh with no luck.


thanks

---

### Post by taurus on 2007-05-12
Change the permission to make them executable first and run them.

```
chmod 755 filename.bin filename.sh
./filename.bin
./filename.sh
```

---

### Post by jfinkels on 2007-05-12
Those are (probably) two different kinds of files. A *.sh file is a shell script. To run it, it needs to be made executable:
```
chmod +x myfile.sh
```
Then you can run it like this
```
./myfile.sh
```
or perhaps```
bash myfile.sh
```

You can try the same thing for the .bin file if it is meant to be a binary (executable) script.

A .bin file might be a disc image file. It doesn't 'run', it contains the image of a disc, so it contains data.

---

### Post by legolas_w on 2007-05-18
Hi
Thank you for reply.
It works for .bin file but it does not work for .sh file
when i tried both

chmod 775  myfile.sh
chmod +x myfile.sh
and then i tried 
./myfile.sh
it return an error like:

bash: ./nb6.sh: /bin/sh^M: bad interpreter: No such file or directory

but I am sure that the file is there because chmod workd and did not return an error message.

Thanks

---

### Post by bergersau on 2007-05-18
It looks like you might be missing the scriping language support for the script your running.

Open the .sh file with a text editor and in the first couple of lines you should see what type of script it is.

For example it may be  a BASH, perl, python or some other script.
Once you know what the script is you can install support with  Aptitude.  Just run aptitude and search for the language, then install the required packages.

Sorry I can't be more specific as I don't know what type of script you're trying to run.

Edit
After a quick google - It looks like you need Sun Java for this script.

---

### Post by legolas_w on 2007-05-18
Hi
Thank you for reply.

here is some content of the file, i can not understand what kind of script it is.

```

entryPoint() {		
	CURRENT_DIRECTORY=`pwd`
	LAUNCHER_NAME=`echo $0`
	parseCommandLineArguments "$@"
	initializeVariables            
	setLauncherLocale	
	if [ 1 -eq $SHOW_HELP_ONLY ] ; then
		showHelp
	fi
	
        message "$MSG_STARTING"
        createTempDirectory
	checkFreeSpace "$TOTAL_BUNDLED_FILES_SIZE" "$LAUNCHER_TEMP"	

        extractJVMData
	if [ 0 -eq $EXTRACT_ONLY ] ; then 
            searchJava
	fi

	extractBundledData
	verifyIntegrity

	if [ 0 -eq $EXTRACT_ONLY ] ; then 
	    executeMainClass
	else 
	    exitProgram $ERROR_OK
	fi
}

parseCommandLineArguments() {
	while [ $# != 0 ]
	do
		case "$1" in
		$ARG_VERBOSE)
                        USE_DEBUG_OUTPUT=1;;
		$ARG_NOSPACECHECK)
                        PERFORM_FREE_SPACE_CHECK=0;;
                $ARG_OUTPUT)
			if [ -n "$2" ] ; then
                        	OUTPUT_FILE="$2"
				if [ -f "$OUTPUT_FILE" ] ; then
					# clear output file first
					rm -f "$OUTPUT_FILE" > /dev/null 2>&1
					touch "$OUTPUT_FILE"
				fi
                        	shift
			fi
			;;
		$ARG_HELP)
			SHOW_HELP_ONLY=1
			;;
		$ARG_JAVAHOME)
			if [ -n "$2" ] ; then
				LAUNCHER_JAVA="$2"
				shift
			fi
			;;
		$ARG_TEMPDIR)
			if [ -n "$2" ] ; then
				LAUNCHER_TEMP="$2"
				shift
			fi
			;;
		$ARG_EXTRACT)
			EXTRACT_ONLY=1
			if [ -n "$2" ] ; then
				LAUNCHER_EXTRACT_DIR="$2"
				shift
			else
				LAUNCHER_EXTRACT_DIR="$CURRENT_DIRECTORY"				
			fi
			;;
		$ARG_SILENT)
			SILENT_MODE=1
			parseJvmAppArgument "$1"
			;;
		$ARG_LOCALE)
			SYSTEM_LOCALE="$2"
			LOCAL_OVERRIDDEN=1			
			parseJvmAppArgument "$1"
			;;
		$ARG_CLASSPATHP)
			if [ -n "$2" ] ; then
				if [ -z "$PREPEND_CP" ] ; then
					PREPEND_CP="$2"
				else
					PREPEND_CP="$2":"$PREPEND_CP"
				fi
				shift
			fi
			;;
		$ARG_CLASSPATHA)
			if [ -n "$2" ] ; then
				if [ -z "$APPEND_CP" ] ; then
					APPEND_CP="$2"
				else
					APPEND_CP="$APPEND_CP":"$2"
				fi
				shift
			fi
			;;

		*)
			parseJvmAppArgument "$1"
		esac
                shift
	done
}

```

---

### Post by Rui Pais on 2007-05-18
> **legolas_w said:**
> ...

bash: ./nb6.sh: /bin/sh^M: bad interpreter: No such file or directory
...

hi,
that seems to indicate that you are running a script written  on another platform (Win or Mac) that use [LF]+[CR] to terminate line, instead of [LF], symbols that are seen in Linux as ^M.

Use an editor like Scite (lighter and easier to work) or emacs (bigger and harder) to open the script and remove the ^M. 
On emacs you have to do it by hand. On Scite just go to 'Options' (on menu), check 'Line end characters' > [LF] and then on 'Options' again choose:
'Convert Line end characters'

that should solve it. :)

---

### Post by tino27 on 2007-05-18
I agree with Rui. It looks like the file is in DOS/Windows format, where the lines terminate with CRs. An easy way to convert is using tr:

```
tr -d '\r' < inputfile > outputfile
```

or sed:

```
sed -e 's/\r$//' inputfile > outputfile 
```

Substitute the script (myfile.sh) for inputfile, and a new name for the outputfile. Then make sure the new file has the right permissions (chmod), and it should work.

---

### Post by Rui Pais on 2007-05-18
thanks, tino27.
I didn't know a command line to do that. 
Your tip maybe helpful for me in the future 
(sometimes i have to exchange code with Window users... )

learning new things everyday :)

---

### Post by tr333 on 2007-05-18
The easiest way to convert text files between windows and linux formats is to install the [tofrodos](http://packages.ubuntu.com/feisty/utils/tofrodos) package.
This package will install the "todos" and "fromdos" programs which will convert text files to and from dos (windows) format.
Using this program, you don't need to remember what characters are used where.

---

