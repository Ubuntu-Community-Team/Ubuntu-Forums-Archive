---
title: "Oh, my."
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by Culito on 2006-05-31
So the ONLY program I have that I need windows for is Arduino, a little software compiler that programs chips via USB.  I took a look at the forums for getting Arduino to work on linux...whew!  Looks like a pain in the *** for a noobie like me.
For your entertainment, here are the instructions for the install: (I can't even get step 2 to work.)

1. apt-get install subversion  
 
2. getting arduino package sources:  
download the latest version of arduino cvs with subversion:  
~/ svn checkout svn://svn.berlios.de/arduino/trunk  
we will come back to this directory later  
 
3. apt-get install gcc-avr avr-libc jikes uisp  
 
4. install jre*your version_number* (java.com) de [http://www.java.com/es/download/manual.jsp](http://www.java.com/es/download/manual.jsp) and put it into the /usr/lib directory  
 
5. install rxtx for Java:  
- - - - - - - -  
Installing RXTX  
First, obtain the RXTX binaries package with CommAPI from:  
[http://www.rxtx.org/](http://www.rxtx.org/)  
take the latest version for linux  
Decompress and Untar this package:  
~/ cp gunzip rxtx-2.1-7pre17-i686-pc-linux-gnu.tar.gz  
~/tar xf rxtx-2.1-7pre17-i686-pc-linux-gnu.tar.gz  
At this point, you'll have an rxtx-2.1-7pre17-i686-pc-linux-gnu directory. Next, you'll need to copy the shared objects into your java installation:  
~/cp rxtx-2.1-7pre17-i686-pc-linux-gnu/librxtxParallel.so /usr/lib/jre*your version_number*/lib/i386  
~/cp rxtx-2.1-7pre17-i686-pc-linux-gnu/librxtxSerial.so /usr/lib/jre*your version_number*/lib/i386  
If you are installing on an architecture other than an x86, you'll need to adjust both the /i386-pc-linux/ and the /i386/ accordingly.  
 
Next, you'll need to install the RXTXcomm.jar file:  
 
~/cp rxtx-2.1-7pre17-i686-pc-linux-gnu/RXTXcomm.jar /usr/lib/jre*your version_number*/lib/ext/  
 
At this point, the RXTX installation is complete.  
 
 
We are almost finished. We just need to create the properties file that the Comm API will use to load the drivers (.so files). To create this file, type the following command:  
 
~//bin/echo Driver=gnu.io.RXTXCommDriver > /usr/lib/jre*your version_number*/lib/javax.comm.properties  
o  
~//bin/echo Driver=gnu.io.RXTXCommDriver > /usr/lib/j2se/1.4/jre/lib/javax.comm.properties  
 
 
 
~/ln -s /dev/ttyUSB0 /dev/ttyS99  
 
If you don't have the /dev/ttyUSB0, do  
 
~/ modprobe ftdi_sio  
 
If you don't have it, then you have to give to your kernel support to usbhid and libftdi.  
 
Device Drivers ---> USB support ---> USB Serial Converter support ---> USB FTDI Single Port Serial Driver (EXPERIMENTAL)  
 
Congratulations! You have installed the Linux Comm API.  
- - - - - - -  
 
6. add the path to java/bin and rt.jar to your CLASSPATH:  
in my case this looks like:  
 
export CLASSPATH=/usr/lib/jreyour_version_number/bin:/usr/lib/jreyour_version_number/li
b/rt.jar  
 
7. you can check on this variables with the "env" command  
note that as soon as you close your xterm this settings are gone. for a tutorial on environment variables  
look at: [http://www.dynamic-apps.com/tutorials/classpath.jsp](http://www.dynamic-apps.com/tutorials/classpath.jsp)  
 
8. go back to arduino svn directory:  
 
~/ cd to trunk/build/linux  
 
9. compile it:  
 
~/ ./make.sh  
 
10. go to work directory  
 
~/ cd work  
 
11. create binaries directory  
 
~/ mkdir -p tools/avr/bin/  
 
12. create symbolic links to the programs arduino uses to compile  
 
~/ cd tools/avr/bin/  
 
~/ ln -s /usr/bin/avr-gcc avr-gcc ;  
ln -s /usr/bin/avr-objcopy avr-objcopy ;  
ln -s /usr/bin/avr-objdump avr-objdump ;  
ln -s /usr/bin/avr-size avr-size ;  
ln -s /usr/bin/uisp uisp ;  
 
13. go back to /trunk/build/linux/ folder  
 
~/ cd ../../../../  
 
Per executar arduino  
 
~/ ./run.sh  
 
14. for having the comm.api driver always properly set, change your bash configuration file:  
 
~/ vi /root/.bashrc  
 
and add  
 
/bin/echo Driver=gnu.io.RXTXCommDriver > /usr/lib/jre*your version_number*/lib/javax.comm.properties  
 
Any expert wanna give me pointer on this?

---

### Post by catlett on 2006-05-31
In my signature their are links for installing programs and apps in linux. Start there and get use to them because you are going to use them all to get that working.:-D 
Just in case there is something easier, post the link to that page and maybe someone will realise an easier way.

---

### Post by az on 2006-05-31
[QUOTE=Culito] (I can't even get step 2 to work.)
download the latest version of arduino cvs with subversion:  
~/ svn checkout svn://svn.berlios.de/arduino/trunk  
we will come back to this directory later  
 [/QUOTE]
That just means type in the command.  You need to know that the ~/ is just the command prompt.  Open a terminal and type:

svn checkout svn://svn.berlios.de/arduino/trunk

---

### Post by Culito on 2006-05-31
Sigh.  Java, I shake my fist at thee.  Java installation (and finding it after install) is one of my biggest hurdles so far in my linux experience.

---

