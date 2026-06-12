---
title: "Can't run an application which I've downloaded (CmapTools)"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by alarichall on 2006-11-25
I'm well new to Ubuntu (and Linux generally). I've downloaded an application called cmaptools (from [http://cmap.ihmc.us/)](http://cmap.ihmc.us/)). It arrived on my desktop as a .bin file and I was able to use posts on this forum to find out how to install it. The installation seems to have gone fine, and I now have a folder in my home folder called "IHMC_CmapTools". This folder contains a 'link to shell script' called "CmapTools", which looks like the right thing to click on to make the application run. When I click on it, I'm asked whether I 'want to run "CmapTools", or display its contents'. If I click on 'run', nothing happens. If I click on 'display' a tab saying 'opening CmapTools' appears at the bottom of my screen, but disappears again after a few seconds with no further result. If i click on 'run in terminal', a terminal flashes into life and then instantly disappears again. I'm at a loss as to what to try next. Any ideas gratefully received.

---

### Post by lamego on 2006-11-25
Hello,
open a terminal and try to run it from there, it should give a more detailed error message.

---

### Post by alarichall on 2006-11-25
Thanks Lamego. Er, how do I do that? I've had a look around trying to find instructions for running an application from a terminal, but so far I can only find pages telling me how to list files and move them around and things.

---

### Post by lamego on 2006-11-25
You will need to learn the linux commands basics:
[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html)

Then to run the script just change to the program dir and runt it with:
```
./script
```

---

### Post by alarichall on 2006-11-25
Thanks. I'm not sure I've followed your instructions right: when I try './script' the terminal says 'No such file or directory'. The attached screenshot shows my terminal window, along the directory which I'm trying to work with in File Browser, incase that makes it clearer what I've done/am trying to do. Any further ideas appreciated. [ATTACH]19979[/ATTACH]

---

### Post by lioncoeur on 2006-11-27
Hi!

OK, first off this is a Java application, which just means it runs in Java, so you need to install Java first before you get it to work. To see if you have Java installed or not, you can search in Synaptic Package Manager (if it has a tick next to it it's installed) or a faster way is to go to Applications > Accessories > Terminal (which will open your missing Terminal) and then type:

```
sudo apt-get install sun-java-jre
```

This will either tell you Java is already installed and is the latest version or will install it for you. If it's not installing, for some reason, that probably means you don't have Multiverse and Universe repositories enabled. In any case, you really should go through the [Ubuntu Desktop Guide]("https://help.ubuntu.com/ubuntu/desktopguide/C/index.html") which is the first thing you need to work your way through after you install Ubuntu. Especially look at Section 1 and 2, which will answer all your questions about the basics and about setting up your package manager (Synaptic or apt-get) correctly.

(The reason why  you're going through all these hoops to get Java on your system is because it wasn't open source when you got that CD off me. But since Sun is giving everyone a Christmas present by open sourcing Java, the next Ubuntu CD should already come with it installed :P)

After you've sorted out your (possibly) missing repositories, and installed Java 1.5, installing CMAP is quite straightforward, even though there are no instructions available on the CMAP site (they must assume all Linux users know what they're doing).

Download their .bin file (binary executable), probably goes straight to your desktop if you're using Firefox default behaviour.

You go to a terminal and type these things:

```
cd Desktop/
./LinuxCmapTools_v4.07_10-10-06.bin
```

It should then unpack from archives and load a splash screen, eventually a bunch of install options which you can just click through or change however you want.

When you've done all that, you'll have some new files in your /home/alarichall directory, namely CmapTools, CmapTools_-_Check_for_Updates and Examples (you might not have the second one, that's something I selected in the setup).

To run your program you either double-click it and select 'run', just as you did before. Or you can simplify it in a far better way. Since I assume you're going to be using this a lot, you should make an icon on your top toolbar next to all your others. To do this:

Right-click next to your other icons.
Select 'add to panel'.
Select 'Custom application launcher'.
Name: whatever you want.
Command: /home/alarichall/IHMC_CmapTools/bin/CmapTools
Comment: whatever you want.
Click on the 'no icon' button.
Click on 'browse' and go to /home/alarichall/IHMC_CmapTools/help/images.
Click ok and you should have a bunch of icons to choose from.
Pick one you like and click ok.

Now you should have an icon on your top toolbar, which saves you typing things in a terminal to start it up.

I bet their Windows version automates all of this and puts annoying things in your startbar in inconvenient locations ;-)

Also, since you've got Java installed, take a look at [Freemind]("http://freemind.sourceforge.net/wiki/index.php/Main_Page"). It seems to be virtually the same program, or similar, but with the advantage of being open source. Of course, if you're using CMAP because you're required to, then tough luck :P

Also, very glad to see you decided to liberate yourself from M$ and install Ubuntu :D

---

### Post by alarichall on 2006-11-27
Blimey, thanks Lioncoer! That's REALLY helpful, and admirably clear. I haven't ried it yet, but I'll let you know either way how is goes. Thanks for the headsup on FreeMind too--I'll check it out.

---

### Post by alarichall on 2006-11-28
Ah, right. Universe and multiverse repositories are on. I had installed Java 1.5 using Automatix. But when I type 'sudo apt-get install sun-java-jre' into my terminal, it says 

> alarichall@audr:~$ sudo apt-get install sun-java-jre
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java-jre

That doesn't look right, but I'm not sure what it means.

---

### Post by squidward_tentacels on 2006-11-28
Um, I believe that should be;

"sudo apt-get install sun-java5-jre"

:D

---

### Post by lioncoeur on 2006-11-28
> **squidward_tentacels said:**
> Um, I believe that should be;

"sudo apt-get install sun-java5-jre"

:D

Squid is completely right. I need to check my commands before I try quoting them from memory. :P

---

### Post by anaconda on 2006-11-28
Wow.. got really exited because I thought that you had found a program that can display cmap:s in linux.. but no. This is some mindmap-thing.

My experience is that Cmap is used in the navigation world. sea charts etc..

a pity..

---

### Post by alarichall on 2006-11-28
Cool, Squid's version produces the desired result:

> alarichall@audr:~$ sudo apt-get install sun-java5-jre
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java5-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have also tried adding a shortcut to my toolbar as Lioncoer suggested. So far, this has made the application work, so it looks like I may have just been clicking on the wrong file all along...

Thanks for your help, folks!

---

### Post by cub on 2007-05-31
Yay old thread resurrection!

I have installed CMAP Tools and have the same trouble when running it. I have Sun Java installed (I run Freemind for example).

When I try to run the CMAP Tools script in a terminal I get:
```

jimmy@cub:~/program/IHMC_CmapTools$ ./CmapTools 
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
rm: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

```
From what I can see I have glibc which is required, but I wouldn't bet my arm on it. Am I missing something or just doing something wrong?

---

### Post by alarichall on 2007-05-31
Just to say thanks for picking up this thread, Cub. I haven't cracked this yet--ran out of time for that project and installed on Windows instead. But if you make any progress, I'll be glad to read about it.

---

### Post by hvc123 on 2007-06-27
hi guys,

i was v. interested in Cmap and obviousley got the same errors you guys did. i.e 
irname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
rm: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

after so hunting around i found this ...... NOT MY WORK 

use the installer for cmap tools and install whereever you want. ( i installed it to /opt)

edit your CmapTools executable find the following line :
export LD_ASSUME_KERNEL

now the key here is to # out the line BUT you must delete the e from export and replace with a hash i.e

#xport LD_ASSUME_KERNEL
 
you must delete the "e" as the program looks for a certain size script and will not work if its too big. thats why you replace the character with another 

now run CmapTools and hey presto it works..


like i say not my work.

Cmaptools is the best sort of opensource mindmapping i can find i tried the others and they are ok but not as good as Cmap.


enjoy


BY THE WAY.

this works on the latest version from the Web site. i have not tried it on the repostories version

---

### Post by alarichall on 2007-06-27
Hey, thanks! I'll give that a try when I have a moment :-)

---

### Post by hvc123 on 2007-06-27
no worries. its slightley different to mind manager and i cant work out how to get rid of the headings on the line pointers. more reading required i think

---

### Post by cub on 2007-07-06
> **hvc123 said:**
> after so hunting around i found this ...... NOT MY WORK 

use the installer for cmap tools and install whereever you want. ( i installed it to /opt)

edit your CmapTools executable find the following line :
export LD_ASSUME_KERNEL

now the key here is to # out the line BUT you must delete the e from export and replace with a hash i.e

#xport LD_ASSUME_KERNEL
Worked like a charm!! :D

---

