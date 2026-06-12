---
title: "How do I install Java for Firefox?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by suomalainen on 2008-03-26
Hello Ubunteros!

I have a web site with Godaddy.com and can't FTP files to the account cause my FireFox v.2.0.00.12 browser is apparently missing a plug in of some kind.

How do I install THAT which I don't know is missing and what am I suppose to do?

Thank you

---

### Post by jan quark on 2008-03-26
to install java run this in terminal
```

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by billgoldberg on 2008-03-26
Why don't you try a real ftp client?

Searching for "ftp" in add/remove will give you a number of clients.

---

### Post by suomalainen on 2008-03-26
I ran the command in terminal as instructed and received the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
paavo@paavo-desktop:~$ 

So what do I do know?

---

### Post by kpkeerthi on 2008-03-26
> **suomalainen said:**
> I ran the command in terminal as instructed and received the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
paavo@paavo-desktop:~$ 

So what do I do know?

Enable Universe and Multiverse repositories under System -> Admin -> Software Sources and install again

---

### Post by suomalainen on 2008-03-26
It appears this has already been done!

What do I do now?

---

### Post by DJ_Peng on 2008-03-26
There are some known issues with Ubuntu and the Firefox Java plugin. I remember seeing a post about fixing it in the last day or two but I don't remember where it was now. You can probably turn it up in a search of the forums though.

---

### Post by monkspeed on 2008-03-28
> **jan quark said:**
> to install java run this in terminal
```

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

i have been struggling since yesterday morning trying to get java to work.

Thanks this did the trick!!

---

### Post by sidewalkcynic on 2008-03-28
I've been having difficulties too, this thread has taken me a bit further. But, now, I ahve encountered the following:
[QUOTE=TERMINAL]sidewalkcynic@circuit-circus:~$ apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
sidewalkcynic@circuit-circus:~$ sudo su
root@circuit-circus:/home/sidewalkcynic# apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@circuit-circus:/home/sidewalkcynic# 
[/QUOTE]

---

### Post by Perfect Storm on 2008-03-28
> apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin

It's  **sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin**


> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

sudo dpkg --configure -a

---

### Post by sidewalkcynic on 2008-03-28
I came up with this> sidewalkcynic@circuit-circus:~$ sudo dpkg --configure -a
Password:
Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

sidewalkcynic@circuit-circus:~$ 
 Then I...> sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-pluginAnd, I get a licensing agreement, that I can't do anything with. There's like an <ok> button, and a scroll bar, but I can't activate them: Is it in a configuration mode, that takes awhile?

---

### Post by Perfect Storm on 2008-03-28
Use the arrow keys, scroll down with the keys and right left to get at "OK"

---

### Post by sidewalkcynic on 2008-03-28
Okay, I did that, and I wind up with a licensing agreement, that freezes.

I then get an updates message from the Package Manager for two Java packages.

I do the install clicks, and I get a warning message

> E:dpkg was interupted, you must manually run 'dpkg --configure -' to correct problem.
E:_casche->open()failed,please report.

---

### Post by Perfect Storm on 2008-03-28
ok, run the sudo dpkg --configure - stuff again.
Then try install the packages via synaptic package Manager instead.

---

### Post by sidewalkcynic on 2008-03-28
Okay, I did the scrolling, and that seems to be working...

---

### Post by suomalainen on 2008-04-01
Hello everyone!

I still haven't been able to resolve my issue. I.e. ability to FTP via godaddy.com account. 


I have however made a change. I'm running 64 bit version of Ubuntu 7.10 so I made change and now run the following:

java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)


but still some plugin is missing cause the website to FTP doesn't load.

What can I do???

THANK YOU!!!!

---

### Post by taavikko on 2008-04-01
No prkl.

enter the commandline and issue
> sudo update-alternatives --config java
change to use icedtea.

Also have you installed java-plugin?

---

### Post by suomalainen on 2008-04-01
Icedtea is already selected.

BUT how do I install plugins for 64 bit?

Terve

---

### Post by taavikko on 2008-04-01
> **suomalainen said:**
> Icedtea is already selected.

BUT how do I install plugins for 64 bit?

Terve

```
sudo apt-get install icedtea-java7-plugin
```

Edit: Terve vaan ;)

---

### Post by suomalainen on 2008-04-01
Mita nyt?

paavo@paavo-desktop:~$ sudo apt-get install icedtea-java7-plugin
[sudo] password for paavo:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
icedtea-java7-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
paavo@paavo-desktop:~$

---

### Post by SyberKowboy on 2008-04-01
> **taavikko said:**
> ```
sudo apt-get install icedtea-java7-plugin
```

Edit: Terve vaan ;)


So I'm still having trouble. I've tried all the suggestions on this thread and have both the newest version of icetea and java on my 64bit gusty install and the firefox plugins still will not load...PLEASE HELP

:confused::confused::confused:

---

### Post by suomalainen on 2008-04-01
Yea I too still have problems . What can be done?

---

### Post by xbalanque on 2008-04-01
I have the same problem, since sun-java6-plugin disappeared, and icedtea-java7-plugin came around, applets stopped working ...

any ideas ? 

any way to revert back to sun-java6-plugin ? -- it seems no longer available on the standard repositories (universe, multiverse, etc.)

cheers, and thanks in advance!

---

### Post by suomalainen on 2008-04-01
The answer xbalanque may be on page 2 of this thread. Check it out.

---

