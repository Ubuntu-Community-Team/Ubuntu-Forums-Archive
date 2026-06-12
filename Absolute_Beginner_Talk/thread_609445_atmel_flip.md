---
title: "atmel flip"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by embed_bread on 2007-11-11
I doubt that anyone else in this forum has used this software, but hopefully someone can still help me.

I'm using Atmel flip to program a microcontroller (8051) for school.  I want to use linux to give myself a free way of writing code and programming (sdcc, eclipse, and flip).  
However, I can't seem to get flip installed and Atmel's documentation is not very good for a beginner at Linux.

**MY PROBLEM**
Besides not really knowing where to start, I can't seem to figure out this ldconfig thing.
The installation instruction read as follows:
"Flip partly relies on Tcl/Tk libraries; your Linux release may contain

outdated versions of these libraries. In this package, we provide

the Tcl/Tk libraries on which Flip has been built.



In order to load the Tcl/Tk libraries provided by Atmel (libtcl8.3.so and 

libtk8.3.so) you should edit (as root) the "/etc/ld.so.conf" file and add 

the full path of these libraries. Execute the "ldconfig" command afterwards."

I'd like to point out that there is an executable file "flip" in the folder that I can't seem to get to run.

--Remember I'm a beginner at Linux so try to dumb down any device you give me.

---

### Post by embed_bread on 2007-11-11
looks like i just got it to work
turns out you have to copy the .so files to /usr/lib
something along the lines of this:
 $ sudo cp -df Desktop/libtk8.3.so* /usr/lib/

After that I ran the executable in the terminal as ./flip to get the program to execute
I'm still confused on getting an easily accessible way to run the program.  I don't want to have to run ./flip every time.

Any suggestions?

---

### Post by PointyWombat on 2007-11-11
Do you know the location of the provided lib files libtcl8.3.so and libtk8.3.so ?

If you know where they are, note the path to them then,

Create a file in /etc/ld.so.conf.d/ called amtel.libs or something and in this file, put the path noted above in this file, such as:

/usr/local/amtel/lib

Run the 'ldconfig' command. This will rebuild where the system looks for libs.

Finally, run 'ldconfig -p' and see if the new libs are noted.

(Use sudo where necessary.)

Then try to run your app

PointyWombat

---

### Post by PointyWombat on 2007-11-11
...or you can just copy the amtel libs to /usr/lib. Not the best way, but will still work.

Where did you install the app? Where is the flip binary?

you can add it to the applications bar. right-click on the Applications button, and select "edit menu" then add your flip application.

---

### Post by embed_bread on 2007-11-11
> **PointyWombat said:**
> 
you can add it to the applications bar. right-click on the Applications button, and select "edit menu" then add your flip application.
awesome  
that worked great
now i just need to get sdcc working with eclipse which hopefully won't be hard

---

### Post by BennBuntu on 2008-02-15
I was using last year, but I think it has changed over to java. I can't get it to run.

> Running Instruction:
-------------------------
FLIP needs java runtime environments version 1.5 or sooner.

To run flip without trouble the following variable must be set in the
Following order:

setenv  JAVA_HOME `your java home location`
  java version are usually found in /usr/java directory

setenv FLIP_PATH `you flip installation path`
  this is the flip path with bin directory.

Running flip:
  Once those variable has been defined, you can run flip.sh or batchisp3.sh
  Located in you flip installation path.
  
  
If you don't when to use those batch file, you have to set more variable:
setenv  LD_LIBRARY_PATH `your flip installation Path`:$LD_LIBRARY_PATH:$JAVA_HOME/lib/i386/client
  you must set this variable in order to access flip dynamic library and java
  dynamic library.

setenv PATH `your flip installation path`:$PATH

Then you can run batchisp3.
To run flip, you have to lunch thanks to the java command :
  java -jar $FLIP_PATH/flip.jar

anyone familiar with this setenv stuff?
if I run flip.sh I get > :~/flip.3.2.1/bin$ ./flip.sh 
FLIP_HOME is not defined, please use setenv to set flip home
e.g :
setenv FLIP_HOME /home/flip.3.2.1/bin


---

### Post by Riddl3r on 2008-04-08
My guess is you wanna use it with the T89C51AC2 microcontroller, right? hehe :D
Well anyway anyhow the following command should help you to set the FLIP_HOME
```
export FLIP_HOME=/the dir your flip resides/flip.3.2.1/bin
```
and after this is done it will prompt you to enter the Java directory, mine was
```
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03 
```
maybe your java dir is different so you might have to search a bit, that you can do
with locate as follows:
```
sudo locate -u
locate java-?-sun* 
```
after all this is done it should work :) just type:
./flip.sh
just in case i am right and you wanna use it with that microcontroller verison, you should be able to download your hex files with flip using the T89C51RD2 from the devices list because the AC2 is missing :P

---

