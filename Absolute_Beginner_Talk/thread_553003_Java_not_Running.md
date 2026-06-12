---
title: "Java not Running"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Rosemere on 2007-09-17
I don't believe my Java is running properly so this is what I did. 
I was reading this web site ( web site below) and opened Terminal and entered the following Line:
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
**Here is the message I received. **
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I** tried to open Synaptic and this is the error message I rec'd.**
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Why I did the following is this web site I found  and I guess I misunderstood the first paragraph!!

I have just checked Firefox for plugins   typing about plugins  and when I scan the list  *I have the following:*

application/x-java-vm         Java  Yes
application/x-java-applet    Java   Yes
application/x-java-applet;version=1.1   Java    Yes
application/x-java-applet;version=1.1.1   Java  Yes
application/x-java-applet;version=1.1.2   Java   Yes
application/x-java-applet;version=1.1.3    Java    Yes
application/x-java-applet;version=1.2      Java    Yes
application/x-java-applet;version=1.2.1     Java    Yes
application/x-java-applet;version=1.2.2     Java    Yes
application/x-java-applet;version=1.3       Java    Yes
application/x-java-applet;version=1.3.1    Java   Yes
application/x-java-applet;version=1.4       Java   Yes
application/x-java-applet;version=1.4.1    Java   Yes
application/x-java-applet;version=1.4.2     Java   Yes
application/x-java-applet;jpi-version=1.4.2   Java  Yes
application/x-java-applet;jpi-version=1.4.2_01   Java   Yes
application/x-java-applet;jpi-version=1.4.2_02    Java   Yes
application/x-java-applet;jpi-version=1.4.2_03    Java    Yes
application/x-java-applet;jpi-version=1.4.2_04    Java    Yes
application/x-java-applet;jpi-version=1.4.2_05    Java    Yes
application/x-java-applet;jpi-version=1.4.2_06    Java     Yes
application/x-java-applet;jpi-version=1.4.2_07    Java     Yes
application/x-java-applet;jpi-version=1.4.2_08    Java     Yes
application/x-java-bean                                     Java     Yes
application/x-java-bean;version=1.1                   Java      Yes
application/x-java-bean;version=1.1.1               Java       Yes
application/x-java-bean;version=1.1.2                Java      Yes
application/x-java-bean;version=1.1.3                Java      Yes
application/x-java-bean;version=1.2                  Java        Yes
application/x-java-bean;version=1.2.1               Java     Yes
application/x-java-bean;version=1.2.2       Java          Yes
application/x-java-bean;version=1.3           Java         Y es
application/x-java-bean;version=1.3.1        Java         Yes
application/x-java-bean;version=1.4           Java         Yes
application/x-java-bean;version=1.4.1        Java         Yes
application/x-java-bean;version=1.4.2        Java         Yes
application/x-java-bean;jpi-version=1.4.2    Java         Yes
application/x-java-bean;jpi-version=1.4.2_01   Java     Yes
application/x-java-bean;jpi-version=1.4.2_02   Java     Yes
application/x-java-bean;jpi-version=1.4.2_03   Java     Yes
application/x-java-bean;jpi-version=1.4.2_04   Java     Yes
application/x-java-bean;jpi-version=1.4.2_05    Java    Yes
application/x-java-bean;jpi-version=1.4.2_06    Java     Yes
application/x-java-bean;jpi-version=1.4.2_07    Java   Yes  application/x-java-bean;jpi-version=1.4.2_08  Java  Yes

**When I go to System Preferences and Scan the List I notice I have **
a) Java Control Plugin  (1.4)
    Java Policy Tool (1.4)
b) Java Control Plugin )1.6)
     Java Policy Tool (1.6)[I]

Installing the Java Runtime Environment[/I]
[www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)
First you need to check multiverse repository enabled or not after that open a terminal window. Since you are going to be installing the JRE and the web browser plug-in, you’ll be using the following command from a terminal
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

This all started as I wanted to watch a mini video in a CNET class and it said Java wasn't installed. 
So maybe you can get this Newbie out of trouble by giving me the commands for Terminal/Feisty.

---

### Post by mikeyphi on 2007-09-17
Can you confirm that you opened a terminal and typed  dpkg --configure -a

---

### Post by jw5801 on 2007-09-17
Take the above command and prepend it with sudo and everything will be good and right in the world again:
```
sudo dpkg --configure -a
```
if that spits an error out at you then post the error back here and we shall help!

---

### Post by Rosemere on 2007-09-17
I did that  and following is the  message  in terminal. I went to the web site and could not find a[B] non-update version.
[/B]


This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

---

### Post by mikeyphi on 2007-09-17
You should be able to install java and sun java through Synaptic. If it's just the browser plugin - you should be able to get that through the browser's interface.
Which browser are you using?

---

### Post by Rosemere on 2007-09-17
I now have an error when I try to log into Synaptic:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can you give me the commands to repair this issue.

---

### Post by Ralzyoud on 2007-09-17
go to the terminal and then type dpkg configure -a then  press 5 or 4

---

### Post by Rosemere on 2007-09-17
I typed dpkg configure -a   in Terminal and below is the response  What do you mean when you say press 4 or 5??
I am using Firefox as a Browser.

pete@pete-desktop:~$ dpkg configure -a 
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
pete@pete-desktop:~$ dpkg configure -a

---

### Post by Malibu Illusion on 2007-09-17
Please **clearly** read the commands you are being asked to type:

```
sudo dpkg --configure -a
```

(Ralzyoud supplied the incorrect command.)

---

### Post by luptinpitman on 2007-09-17
Yeah, it looks like you have a broken package and you need to repair it before you are going to be able to run Synaptic or apt-get too probably.

Just follow the command listed and you should be fine.

---

### Post by Bothered on 2007-09-17
You need the sudo part of the command, i.e. **sudo** dpkg --reconfigure -a

---

### Post by Gremlinzzz on 2007-09-17
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
when time come to click OK     
 tab then enter 
tab button on your key board wil high lite  OK then click enter

---

### Post by Rosemere on 2007-09-17
Here is what I got:

pete@pete-desktop:~$ 
pete@pete-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
pete@pete-desktop:~$ 

I have already run
pete@pete-desktop:~$ sudo dpkg --reconfigure -a
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

---

### Post by Bothered on 2007-09-17
Bah, sorry my typo this time :-)

That should be:

```
sudo dpkg --configure -a
```

(no "re" on configure)

---

### Post by Rosemere on 2007-09-17
*I am back where I started. Please read where I started and where should I download the Java. I went to the Web site and unsure which one I should download for Feisty/Ubuntu.   If yopu know the steps please advise, also I still can't use Synaptic. *

pete@pete-desktop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by luptinpitman on 2007-09-17
If you still can't open Synaptic then you have bigger problems than installing java...

Try running:

sudo apt-get -f autoclean

From a terminal and see if that resolves what ever issue is jamming apt-get.  Once you resolve this you might just install Automatix and grab java from there.

---

### Post by Rosemere on 2007-09-17
[I]No it didn't  back to the same. 
Here is the message I get. How do I mnually run dpkg --configure -a
see the msg below. I am so dense and I wonder if I will ever get it. I have Automatix on the computer fyi.[/I]


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
pete@pete-desktop:~$ sudo apt-get -f autoclean
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by luptinpitman on 2007-09-17
> **Rosemere said:**
> No it didn't  back to the same. 

Does that mean you ran?

```
sudo apt-get -f autoclean
```

---

### Post by Rosemere on 2007-09-17
Yes I did see below wht I inserted in Terminal:

pete@pete-desktop:~$ sudo apt-get -f autoclean
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
pete@pete-desktop:~

---

### Post by luptinpitman on 2007-09-17
Have a look here:  [https://answers.launchpad.net/ubuntu/+question/5084](https://answers.launchpad.net/ubuntu/+question/5084)

Please make absolutely sure you did this:

Applications --> Accessories --> Terminal
sudo dpkg --configure -a

---

### Post by Rosemere on 2007-09-17
Yes I did as you will see by my Screen shot.   I just  read the web site you enclosed, I see some similarities **but I still don't understand enough **of this to know what to do.   I know I am missing something.

[IMG]http://img.photobucket.com/albums/v281/harbourwoods/Screenshot-1.jpg[/IMG]

---

### Post by luptinpitman on 2007-09-17
Ok, we are on the same page now.

Have you tried installing the java package available in Automatix?

[IMG]http://media.hordemilitia.com/Screenshot-Automatix2 .png[/IMG]

---

### Post by Bothered on 2007-09-18
Whoa, let's not reach for automatix just yet, that could really make a mess of the package manager.

It seems that you've install the java documentation. As a test I tried to install the java documentation package and get the same error as you did. To fix the problem try:

```
sudo apt-get remove sun-java6-doc
```

and then try installing the java runtime (and plugin):

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by Rosemere on 2007-09-18
I just tried to remove and I have that terrible command about running manually and I can't seem to figure that out.
Please note the other screen shot.
[IMG]http://img.photobucket.com/albums/v281/harbourwoods/SUNJava.jpg[/IMG]

A new day maybe more success??

---

### Post by Bothered on 2007-09-18
Ah, I think I've got it this time.

When you ran "sudo dpkg --configure -a" did you close the terminal window when it displayed the message, or did you type "no" and press return? If you closed the window then the configuration won't have completed and apt-get would then behave as you're reporting.

To fix this type in a terminal:

```
sudo dpkg --configure -a
```

then (without closing the terminal window) type "no" and press enter. Then type:

```
sudo apt-get remove sun-java6-doc
sudo apt-get install sun-java6-jre sun-java6-plugin
```

Hopefully that should fix it and the java plugin should then be working.

---

### Post by Rosemere on 2007-09-18
I will let you know Bothered you are winning. See screen shot. Since you got me this far,  can you give me the directions re the install  and where to download. That way I won't screw up.   Also just checked Synaptic works now.
[IMG]http://img.photobucket.com/albums/v281/harbourwoods/Removal.jpg[/IMG]

---

### Post by Bothered on 2007-09-18
That was my typo - I corrected it but too late :-)

The final command should be:

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

Sorry about that

---

### Post by Rosemere on 2007-09-18
I guess you won, Satisfction is wonderful.:)
Can you direct me on the install or checking or the latest of Shockwave, my as well finish it all.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  libosip2-3 libsdl-sound1.2 liblinphone1 libmediastreamer0 libortp5 libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pete@pete-desktop:~$

---

### Post by kavon89 on 2007-09-18
Sort of late but I thought I'd give it a shot, try googling Java Test. Sun has a test webpage for Java in the browser. :s

---

### Post by Rosemere on 2007-09-18
[COLOR="Red"]Oops! You don't have the recommended Java installed.[/COLOR]
Your Java version is 1.4.2. Please click the button below to get the recommended Java for your computer.  

NOTE: If you recently completed your Java software installation, you may need to restart your browser (close all browser windows and re-open) before verifying your installation.


I though I installed version 6 BUT   when I go to System Preferences I see in the List 

[COLOR="Blue"]Java Plug in control (1.4)[/COLOR]
Java Policy Tool (1.4)

**AND **

[COLOR="Red"]Sun Java 6 Plugin Control Panel[/COLOR]
Sun Java 6 Policy Tool

---

### Post by jw5801 on 2007-09-18
.

---

### Post by Bothered on 2007-09-18
That's odd ...

Have you tried to install java from any other sources? e.g. from the java website, through Automatix? The package manager won't have installed two versions. Just to be sure, could you type the following command in a terminal and post the output:

```
dpkg --get-selections | grep java
```

---

### Post by Rosemere on 2007-09-18
Awhile ago I went to Automatix and removed Sun java , see below now what version do you recommend I download for Feisty and if possbile the simple procedure.


pete@pete-desktop:~$ dpkg --get-selections | grep java
java-common                                     install
java-gcj-compat                                 install
java-gcj-compat-dev                             install
java-gcj-compat-plugin                          install
java-package                                    install
javacc                                          install
libhsqldb-java                                  install
libjaxp1.3-java                                 install
libjline-java                                   install
libservlet2.3-java                              install
libxalan2-java                                  install
libxerces2-java                                 install
openoffice.org-java-common                      install
sun-java6-bin                                   deinstall
sun-java6-demo                                  deinstall
sun-java6-fonts                                 deinstall
sun-java6-jdk                                   deinstall
sun-java6-jre                                   deinstall
pete@pete-desktop:~$

---

### Post by Bothered on 2007-09-19
I'm afraid I'm not sure how to fix this problem. You say you see two versions of java in your preferences menu? As far as I can tell you have only one installed through the package manager, which means that you have manually installed a second version (possibly via Automatix, although you say you have removed it again). Since the second (earlier) version of java has not been installed using a package manager it is now non-trivial to remove.

---

### Post by YoG%*@ on 2007-09-19
hi, 

have you tried switching the java version in use?
```

sudo update-alternatives --config java

```

if it shows two versions of java, and the 1.4.2 version is the current default, try selecting the other one.

hth,
mux

---

