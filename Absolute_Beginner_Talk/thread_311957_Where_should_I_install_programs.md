---
title: "Where should I install programs?"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Vasant56 on 2006-12-03
Hi, I recently installed ubuntu, and am about to install Java. I downloaded it to my desktop, and I was following the instructions online, but I am not sure where I should install the program so that everyone will have access to it. Will it be done automatically (I'm scared it will be installed onto the desktop)? Also, is there any popular locations of where I should install programs (ie how there is a C:/Program Files in windows)

Thanks

---

### Post by rbprogrammer on 2006-12-03
well, what i do is i have a separate partition for my [/home] directory, and when i have to manually install something i install it to something like [/home/ProgramFiles/].  i like this method because if something should happen to my system, i can reinstall ubuntu, and then just mount the [/home] directory to that partition and i dont have to reinstall everything all over.

as for your java install, move the compressed folder the the folder where you want it installed.

---

### Post by bollix47 on 2006-12-03
You can install java system-wide by using synaptic.

See [_here_]("https://help.ubuntu.com/community/Java") for instructions.

---

### Post by IYY on 2006-12-03
Just follow the instructions on the Ubuntu Guide, and everything will be installed in the correct location, where all users have access to it:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

The link goes to the JRE and firefox plugin (used to *run* Java programs). That same page also has similar instructions for JDK, if you want to develop Java programs.

---

### Post by wpshooter on 2006-12-03
> **rbprogrammer said:**
> well, what i do is i have a separate partition for my [/home] directory, and when i have to manually install something i install it to something like [/home/ProgramFiles/].  i like this method because if something should happen to my system, i can reinstall ubuntu, and then just mount the [/home] directory to that partition and i dont have to reinstall everything all over.

as for your java install, move the compressed folder the the folder where you want it installed.

rbprogrammer:

Would installing the applications in a sub of the home directory cause problems if there were users on the system other than the user that did the installation of the application ?  Would the other users have ready access to the applications if installed this way ?  I don't know, I am just asking.

Thanks.

---

### Post by The Mekon on 2006-12-03
When you install programs using specially packaged software such as deb packages these normally end up in /usr/bin/.

A very convenient way to install normal software is by using the Synaptic Package Manger which takes care of the installation for you and add the new software to the Applications Menu.

You can also use [Automatix]("http://www.getautomatix.com/") for the restricted packages not included in the Ubuntu distribution.  This also provides the Java packages for Open Office and Firefox.  Again it sorts out where to put things and updates the Applications menu as required.

Brian

---

### Post by rbprogrammer on 2006-12-05
> **wpshooter said:**
> rbprogrammer:

Would installing the applications in a sub of the home directory cause problems if there were users on the system other than the user that did the installation of the application ?  Would the other users have ready access to the applications if installed this way ?  I don't know, I am just asking.

Thanks.

on my system, i have the folder [/home/ProgramFiles] owned by root, group is admin, and the permissions are 775.  so as long as a person is in the group admin, they have read, write, executable permissions. and everything in the folder has the same permissions.

---

### Post by nickburns on 2006-12-05
Back to your original question to get java go to a terminal (Application >> Accessories) and type:

apt-get install sun-java5-jre 

for the jre, and if you want the jdk type:

apt-get install sun-java5-jdk

---

### Post by sebastiansantoso on 2006-12-05
If i have to do the installation process manualy, what command should I type? From where? Is it just run terminal from the program folder kept in the removable media? and where do i have to install it? With what option?
I just put it this way: what is the Xubuntu command line, which similar to windows where i should go to the program folder and run the setup?
Thx.

---

### Post by nickburns on 2006-12-05
To get to a terminal, go to Applications >> Accessories >> Terminal

and follow the instructions that I posted earlier, the command line will download the installation files and install the Java jre/jdk and add the install to the classpath and everything for you.

---

### Post by Buck2348 on 2006-12-05
How can I see a list of all the users and groups in my system please?

---

### Post by nickburns on 2006-12-05
System >> Administration >> User and Groups

(PS, with all kindness, please please start a new thread if you have other questions, it is easier to work on one problem at a time)

---

### Post by mitchbones on 2006-12-05
> **nickburns said:**
> Back to your original question to get java go to a terminal (Application >> Accessories) and type:

apt-get install sun-java5-jre 

for the jre, and if you want the jdk type:

apt-get install sun-java5-jdk

Forgot to put sudo :P
sudo apt-get install sun-java5-jre
sudo apt-get install sun-java5-jdk

---

### Post by nickburns on 2006-12-05
oops :) how could I forget my favorite word.

---

### Post by sebastiansantoso on 2006-12-05
> **nickburns said:**
> To get to a terminal, go to Applications >> Accessories >> Terminal

and follow the instructions that I posted earlier, the command line will download the installation files and install the Java jre/jdk and add the install to the classpath and everything for you.

What if I don't have any internet connection...

---

### Post by nickburns on 2006-12-06
You will need to download this deb file and get it to the computer somehow (CD or thumb drive)

[java deb]("http://http.us.debian.org/debian/pool/non-free/s/sun-java5/sun-java5-jdk_1.5.0-08-1.1_i386.deb")

then you need to copy it to the desktop of the other computer.

and open a terminal and type

cd Desktop
sudo dpkg --install *.deb

---

