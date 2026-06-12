---
title: "[SOLVED] How do i use marcomedia flash and java?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Brookeorama on 2008-01-30
Can anyone help me? I admit it, I've only used linux for all of a few hrs now, so I'm not too familiar with how it works.

So here's the situation. I'm trying to install a flash player so that I can watch all the flash videos on the net; I'm a real big multimedia person.

I went to the Adobe Flash Player download center, and I downloaded the linux version of Macromedia flash player. I now have a file called install_flash_player_7_linux.tar.gz. A little while ago I tried to extract it to the tmp folder and then install it from there, but that didn't work. What do I need to do? and how do i do it...


Do they mean run the line "./flashplayer-installer" in terminal?

Anyone know what I should do? Any help would be appreciated.
I needa step by step process...
this is killing me!!

i think i got the java working but fire fox still says that i need to turn it on or somehting?
WHAT!?!??!:(:confused::(

---

### Post by FuturePilot on 2008-01-30
Yes run ```
./flashplayer-installer
``` in a terminal. Just make sure you're in the directory where you extracted it to. You can navigate to it in the terminal with the "cd" command
```
cd path/to/directory/
```
For Java run this in a terminal
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```
If you see a License Agreement hit Tab to highlight OK then hit Enter.

---

### Post by jaytek13 on 2008-01-30
Well, the easiest way to install flash is to type

```

sudo apt-get install flash-nonfree

```

into a terminal

and for java

```

sudo apt-get install sun-java6-plugin

```

---

### Post by Paqman on 2008-01-30
The package ubuntu-restricted-extras contains both flash and Java, plus a lot of other useful bits and pieces. It's one of the first things I install on a new setup.

---

### Post by oedha on 2008-01-30
after you download the file....extract it
by using file manager ...just point to the extracted folder and open it
find the file : flashplayer-installer  <-- double click it
you will be asked.....click with run in terminal
then follow the direction

addition : go to applications - add/remove
search for gstreamer on all available applications
mark on 6 gstreamer packages......
you will enjoy almost all multimedia files......

regards;
~E~

---

### Post by Brookeorama on 2008-01-30
Download the Flash Player .tar.gz for Linux
OR
Download the Flash Player .rpm for Linux
OR
Download the YUM repository definition for Flash Player


WHICH OF THESE DO I DOWNLOAD?

Thanks you guys for the all the replies!!:confused:

---

### Post by FuturePilot on 2008-01-30
The .tar.gz one

---

### Post by Brookeorama on 2008-01-30
BTW i installed all the gstreamers...
i dont know if that makes a diff, as I am a total n00b when it comes to ubuntu!!


:P

---

### Post by jaytek13 on 2008-01-30
> **Brookeorama said:**
> Download the Flash Player .tar.gz for Linux
OR
Download the Flash Player .rpm for Linux
OR
Download the YUM repository definition for Flash Player


WHICH OF THESE DO I DOWNLOAD?

Thanks you guys for the all the replies!!:confused:

Out of those you would go with the tar.gz file. That is simply a compressed source file which you would compile on your own.

.rpm references the "redhat package manager." Typically redhat and opensuse use this.

YUM is redhats version of "apt." Both yum and apt are used to ease the installation of .rpm and .deb packages, respectively. 

Being that Ubuntu is debian based, if there is a .deb option you would go for that. Otherwise, tar.gz files are fine, too, but require a bit more effort on your end to install.

---

### Post by Brookeorama on 2008-01-30
It saved it to the archive manager, is that good?

---

### Post by DMK62 on 2008-01-30
There is currently a bug in the installer for flashplugin-nonfree. If you install it via synatpic or add/remove it will say that it was installed but it actually fails to install.

For a more detailed explanation and a method for installation please go here

[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

Dale

---

### Post by Brookeorama on 2008-01-30
Spo fire fox saved it to the archive manager, and i went and put teh code from one of the 1st post into the termianl and this is what i got.. (sorry again guys!)

bear with me!! 

lol

[username and compute]~$ sudo apt-get install flash-nonfree
[sudo] password for brooke:****************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flash-nonfree



WHAT?

---

### Post by jaytek13 on 2008-01-30
> **Brookeorama said:**
> Spo fire fox saved it to the archive manager, and i went and put teh code from one of the 1st post into the termianl and this is what i got.. (sorry again guys!)

bear with me!! 

lol

[username and compute]~$ sudo apt-get install flash-nonfree
[sudo] password for brooke:****************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flash-nonfree



WHAT?


Sorry, my fault

It's actually

sudo apt-get install flashplugin-nonfree

---

### Post by Kilz on 2008-01-30
> **Brookeorama said:**
> Spo fire fox saved it to the archive manager, and i went and put teh code from one of the 1st post into the termianl and this is what i got.. (sorry again guys!)

bear with me!! 

lol

[username and compute]~$ sudo apt-get install flash-nonfree
[sudo] password for brooke:****************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flash-nonfree



WHAT?

The correct name of the package is flashplugin-nonfree

---

### Post by wolfen69 on 2008-01-30
dont install via apt-get or synaptic
here's an easy way for flash.
[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

---

### Post by DMK62 on 2008-01-30
Please go to the link in my above post. The instructions on the first page will tell you how to install it as well as gives you a link to download the .deb file ( its the install file ). It's just a matter of double clicking on the deb file and running the install.

Dale

Or even easier just click on the link given by wolfen69 and double click on the file. Ubuntu does the rest for you.

---

### Post by Brookeorama on 2008-01-30
WOW!! Its working! 
Thank you Thank you Thank you Thank you Thank you Thank you!!!!

---

### Post by einherier on 2008-01-30
when i try downloading it it says wrong architecture...

---

### Post by einherier on 2008-01-30
duh....nevermind....

---

### Post by einherier on 2008-01-30
****...im still having trouble....everytime i try to watch a flash video i get a damn grey screen...and i did reinstall the java for firefox.

I have tried opera....epip and got the same results...

i tried wine iexplore...and man...iexplore was ALL jacked up....half the text was missing and  pages werent displaying correctly

---

