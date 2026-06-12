---
title: "Desperate"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by oeasler on 2007-11-05
Windows Vista has convinced me, along with the outrageous prices of their OS and the way they spy on their customers, that it is time to switch to Linux.  I have been able to install linux on a second hard drive I purchased but can get no further.  I cannot even get Ubuntu to recognize and install RealPlayer.  As a matter of fact, I can't get it to install anything.  I have read the instructions, but folks, you are going to have to remove the geeky gobledegook for us new guys to understand it.  I know its simply to you, but to those of us who are new, the words you use have no referent or meaning.

I don't understand why drives don't have a designation such as C:/ or D:/ and so forth.  I don't know what to put in the search bar to find what I am looking for.  I can't find the folder in GNOME that has all the programs in it.  I thought if I could find that folder and put the RealPlayer executable file in it, I could then install it???

Why can't Ubuntu have programs that you can install by simply clicking on them like you do in Windows?  It would certaily help in the popularity of this OS.  Some programs you have to put in a string of code - thats definately out for the beginning.  By the way,  I like to never have found the terminal.

The next difficulty is getting on the internet.  I have not even come close.  I don't understand NdisWrapper.  Why can't you just have a straight forward list of the WIFI and Graphics cards, etc. that work in Ubuntu.  I'm sure you have it somewhere, but it is buried in goobledegook.  

Quite frankly, I am about to throw up my hands and quit.  I hate to be stuck with Windows for the rest of my life but what can I do?  I love the look and layout of Ubuntu and love the Ubuntu philosophy.  I believe that it is the wave of the future.

**I have tried, I have really tried**.  I have put hours and hours into trying to make this work for the past three weeks.  I don't know what to do or where to turn.  **_CAN SOMEONE PLEASE HELP ME_**.  I want to make this work.  I want to send an email to [email]support@microsoft.com[/email] so that I can give Bill Gates a rousing goodby!

HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  My email is [email]oleasler@carolina.rr.com[/email]

---

### Post by wieman01 on 2007-11-05
This is your first post... you should have come here earlier. :-) Should we fix your internet connection first? What sort of wireless adapter have you got?

Also, do you mind doing a bit of command line? It's really simple and we can guide you through it.

---

### Post by Dr Small on 2007-11-05
First off, calm down. Ubuntu is **NOT** Windows. There are differences, and not everything is the same. There is a learning curve, and with time and patients, you can overcome this curve and learn Linux.

First, let's address each problem at a time.

1.) Your drives are not labled C:/ and D:/, but as /dev/sda1 and /dev/sda2 as the device, and mounted at different mount points. Your default root directory would be /

2.) There is no real folder where every application gets installed to, like Windows. There is /usr/bin/, /usr/share/, /bin/, /opt/, etc. But you really don't need to worry about that, because you can access most applications via the menu.

3.) The terminal can be found at Applications > Accessories > Terminal.
You can input apt-get commands into here, that other users or tutorials instruct you, to install software. You can also "click" on debian file packages to install them, if you have some downloaded.

4.) For network, have you tried going to System > Administration > Network and setting up your network from there ?

Dr Small

---

### Post by oilchangeguy on 2007-11-05
> **oeasler said:**
> Windows Vista has convinced me, along with the outrageous prices of their OS and the way they spy on their customers, that it is time to switch to Linux.  I have been able to install linux on a second hard drive I purchased but can get no further.  I cannot even get Ubuntu to recognize and install RealPlayer.  As a matter of fact, I can't get it to install anything.  I have read the instructions, but folks, you are going to have to remove the geeky gobledegook for us new guys to understand it.  I know its simply to you, but to those of us who are new, the words you use have no referent or meaning.

I don't understand why drives don't have a designation such as C:/ or D:/ and so forth.  I don't know what to put in the search bar to find what I am looking for.  I can't find the folder in GNOME that has all the programs in it.  I thought if I could find that folder and put the RealPlayer executable file in it, I could then install it???

Why can't Ubuntu have programs that you can install by simply clicking on them like you do in Windows?  It would certaily help in the popularity of this OS.  Some programs you have to put in a string of code - thats definately out for the beginning.  By the way,  I like to never have found the terminal.

The next difficulty is getting on the internet.  I have not even come close.  I don't understand NdisWrapper.  Why can't you just have a straight forward list of the WIFI and Graphics cards, etc. that work in Ubuntu.  I'm sure you have it somewhere, but it is buried in goobledegook.  

Quite frankly, I am about to throw up my hands and quit.  I hate to be stuck with Windows for the rest of my life but what can I do?  I love the look and layout of Ubuntu and love the Ubuntu philosophy.  I believe that it is the wave of the future.

**I have tried, I have really tried**.  I have put hours and hours into trying to make this work for the past three weeks.  I don't know what to do or where to turn.  **_CAN SOMEONE PLEASE HELP ME_**.  I want to make this work.  I want to send an email to [email]support@microsoft.com[/email] so that I can give Bill Gates a rousing goodby!

HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  My email is [email]oleasler@carolina.rr.com[/email]



1st paragraph. referent is not a word.
2nd paragraph. linux is not windows. so get the alphabet out of your head. and linux won't run a .exe file.
3rd paragraph. have you tried synaptic package manager?
4th paragraph. what kind of wifi card do you have?
5th paragraph. open source has been, and will be the future.

linux is not windows. if you want to do things like you do with windows, stick with it. otherwise be open to new ways of doing things.

---

### Post by lyndaj70 on 2007-11-05
I'm not a genious, but I'll do what I can...
 
Just don't panic.  It's just a machine and we'll get it working...
 
First things first:  hard drives...
 
In a sense, Linux DOES have an c:, d:, etc., on their drives, but at first the logic IS confusing....
 
hd stands for hard disk;  the letters afterward stand for the partitions after it.... therefore hda is disk one, or what Windows would probably call your C: drive unless you have some sort of recovery partition.  In that case Windows would probably hide it...  hda2 means the second partition of the first hard disk, and so forth....
 
what is confusing is that in Windows any partitions are generally hidden, and most hard disks are made into a single parition whereas Linux wants you to know exactly how your system is parceled out....
 
If you have sata drives, the drives are designated sd for sata disk... sda5 means the fifth partition on the first sata disk...
 
If you have a recovery partition your Windows partition will probably be called hda2 ... the easiest way to determine this is to go to Applications==>Accessories==>Disk usage analyzer.   It will tell you whether your disks are called sda or hda...  and as I am sure you know how large your Windows partition is, you can look for an NTFS partition of that size, and to mount, go to Places==>Computer and look there for your disk.  A lot of times they will have the actual disk name there so it may be pretty easy to spot.  For instance, when I dual-booted with Vista my Windows disk was named Presario, so it was easy to spot.
 
Just go and look, and explore a bit to get familiar with the new environment...
 
____
 
As far as programs go, IMO it is easier on Linux to install programs than windows, especially with the Debian distros....
 
Go to System==>Administration==>Synaptic Package Manager.  you will have to type in your password, but any program you could want is probably in there somewhere.  I recommend searching for "restricted packages"  just type in restricted and it should come up.  Select the one for ubuntu (or kubuntu or edubuntu depending upon what you are using), and install that first.  then look for realplayer and go from there..  it takes care of dependencies automatically, and makes uninstalling a cinch!
 
Hope this helps!
~Lynda

EDIT:  I goofed on how to find the partitions...

go to synaptic and install gparted... it will tell you about the partition information in a usable manner...  I was thinking one thing and typed another. Sorry! :(

---

### Post by frank002 on 2007-11-05
Don't despair. I am a newbie like you and there is a learning curve just like there is a le
arning curve for Windows, Apple OS Leopard, etc. Thankfully, you will find lots of friendly, helpful people ont this forum willing to help. I myself being new to Ubuntu, can only offer very limited advice but plenty of moral support. 
 As for the drives...........
 Primary master /dev/hda if EIDE or /dev/sda if SATA
 Primary slave   /dev.hdb if EIDE or /dev/sdb if SATA
 Secondary master /dev/hdc if EIDE or /dev/sdc if SATA
 Secondary slave   /dev/hdd if EIDE or /dev/sdd if SATA
 Hope that helps. Stick with it, ask questions and say goodbye to Gates & Co.

---

### Post by Dr Small on 2007-11-05
[quote=frank002]Hope that helps. Stick with it, ask questions and say goodbye to Gates & Co.[/quote]
Windows restricts your sight, and Gates keeps you locked in tight.

---

