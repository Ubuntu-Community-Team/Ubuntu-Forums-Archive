---
title: "Problems Installing OSS"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Ravorion on 2008-04-04
First off... Sorry if this has been discussed before, but I could not find anything that helped me out so I decided to post this. :(

I have been trying to get my Creative X-Fi Xtreme Gamer (not using 64 bit pc) soundcard to work under Ubuntu. Seen the many posts about it, but nothing concrete about it actually working or not. Ended up going to [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi) and downloading the DEB package (which is the one you need for Ubuntu right?). I right clicked the package and had the option to use GDebi Package Installer so I did. At first everything seem to install correctly. No warnings, but when I tried to use the ossinfo command at the terminal I got an error: 

```
No /dev/mixer device available in your system.
Perhaps Open Sound System is not installed or running.

```

So I used the installer again to reinstall the package with the details visible and indeed... errors !
Can't seem to copy paste that, but the lines that struck me as odd were:

sh: Can't open install.sh
Starting Open Sound System
Then 2 lines about "No such file or directory"
and then No /usr/lib/oss/etc/installed_drivers - cannot continue

I am a total Linux noob so all these commands are unfamiliar to me. I've tried using the terminal to install the package (how its explained in the OSS Installer pdf) instead of using that GDebi package installer, but no matter what I did I always got:

```
No packages found matching oss-linux_v4.0-1015_i386.deb.

```

In my previous attempts at Linux installing packages was also my biggest problem so I have no idea what im suppose to do here. :oops:

If someone could help me out either by explaining what im doing wrong or giving a link where it was discussed before id be a happy boy! If you guys can confirm the fact that my soundcard won't work no matter what I try then thats ok too. Atleast I know then that I should look for another solution. :)

EDIT: Forgot to mention that I am using the 8.04 beta Ubuntu, but installing OSS seems like a basic function so I don't think my problem would have anything to do with an unstable beta ?

---

### Post by mikeyphi on 2008-04-04
Sorry!!! Hardy is still being developed so there's no way to know if anything will work correctly!

However, normally a .deb will install with a double click.
If using a terminal remember to navigate to where the package is (Desktop?) BEFORE using the install command!!

---

### Post by Ravorion on 2008-04-04
Ah okay. Had some other small issues and started to wonder myself if it was me, my pc or the fact that it was a beta that was giving the issues. Suppose I will install the stable version instead to be sure... AFTER I am done messing around with Compiz Fusion that is. Those desktop effects are so damn awesome ! :D

Oh btw I did do the terminal thing wrong at first, but found out how to go to desktop in terminal and it still didn't work so I'll give up for now till I have the stable Ubuntu running. Thanks for the input :)

---

