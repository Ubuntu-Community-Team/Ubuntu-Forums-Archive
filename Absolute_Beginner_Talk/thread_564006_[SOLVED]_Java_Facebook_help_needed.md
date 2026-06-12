---
title: "[SOLVED] Java Facebook help needed"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by juantastico on 2007-09-30
hello,
I need to install java for to upload photos to create new albums. When i do so firefox says that i need to do a manual installation. When i click on manual install in takes my to the java site then it asks me to download one of the following:
I tried the 2nd one and when i click one the icon on my desktop i get this message:Could not open the file /home/jean/Desktop/jre-6u2-linux-i586.bin. 
				
	Linux RPM (self-extracting file) filesize: 17.73 MB 	
	Linux (self-extracting file) filesize: 18.22 MB 	
	Linux x64 * filesize: 17.23 MB 	
	Linux x64 RPM * filesize: 16.82 MB

Can someone please explain me hot to install the jave application on ubuntu 

many thanks:)

---

### Post by juantastico on 2007-09-30
I find a solution 
Installing the Java Runtime Environment

First you need to check multiverse repository enabled or not after that open a terminal window. Since you are going to be installing the JRE and the web browser plug-in, you’ll be using the following command from a terminal

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

Once it downloads the packages and begins the installation, you’ll get a screen that contains the Sun Operating System Distributor License for Java and hit Enter to continue. You’ll see a dialog that asks you if you agree with the DLJ license terms. Select Yes, and hit Enter; the JRE will finish installing.

Testing Java Runtime Environment

You’ll want to confirm that your system is configured properly for Sun’s JRE. This is a two-step process.

First, check that the JRE is properly installed by running the following command from a terminal.

java -version

You should get similar output

java version “1.6.0&#8243;
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
Testing Java Plugin for Firefox

open Firefox and typing about:plugins in the address bar and check for java plugin


:guitar:

---

### Post by juniah on 2007-10-31
I followed your solution and it doesn't work for me.  when I entered

java -version

it didnt come up with the testing firefox plugins.  any ideas as to a further solution?

---

