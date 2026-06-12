---
title: "Urgent Help Needed!!!! Boot Problem"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by sebdj on 2007-04-12
Hi!

Yesterday, for the first time I have installed Ubuntu. I had at the same time windows XP

I put the cd on at the startup Choose install Ubuntu after it load by itself. 

Then I click on install on the desktop and I select to not Format but second choice 

I did exactly at this tutorial : 

[http://fosswire.com/2007/01/12/giving-linux-for-a-spin-the-first-time-part-3/](http://fosswire.com/2007/01/12/giving-linux-for-a-spin-the-first-time-part-3/)

(Begin to the install of Ubuntu not before) 

Then I was suposed to see Windows and Ubuntu logo so I can choose one of them. 

But now my computer just don't boot at all. (It just boot the initial boot with the click DEL to acces the bios, click F12 to have the Boot Menu , clcik F8 for the Network Menu. )

I have post help on this forum but people seem to stop answered and none have help. 

Here my first post : 

[http://ubuntuforums.org/showthread.php?t=407147](http://ubuntuforums.org/showthread.php?t=407147) 

1. I have try Super Grub 

2. I have try to boot by the Windows XP Boot Cd and the recovery file and the FIXMBR

3. I have try to reinstall XP (but they don't let me the choose (I'm obligated to format) 

Now I just really need my files back... 

Please help this is very urgent!

---

### Post by seshomaru samma on 2007-04-13
First , if you have files that needs to be saved , download [Knoppix ]("http://www.knoppix.org/") (If it appears in German ,click on the UK/USA flag) this is a live CD which is very easy to use. You will able to copy any files to a USB stick or burn them onto a CD.
If you just need to restore your system then it seems like you have several problems:
There is a problem with the Ubuntu installation
There is a problem with reinstalling Windows

In order to solve Ubuntu's problem, you need to boot from the live CD.
If you don't understand any of the terms I'm using , ask!
When the live CD boots, choose the first option (start or install)
You will a screen with two icons (example and install)
On the top panel you will see "Applications" click on it , choose accessories and then terminal
A black screen will come up
in it you have to paste the following command:
```
sudo fdisk -l
```
then post a reply here with the outcome
paste this command as well:
```
cat /boot/grub/menu.list
```
post the output here.
We will be better able to help you solve your problem with this output

To solve Windows' problem
What kind of computer are using?
Do you have a Windows XP cd? or some sort of recovery CD?

---

### Post by sebdj on 2007-04-13
Thank this seem to be really useful.

About KNOPPIX wich one I download?? It look like this software is 600MB and more is that normal? 

Can I have the link from a server with the right file ?

There a lot's of choose of download... 

thank you

---

### Post by sebdj on 2007-04-13
I just make the code 

I have just make a screenshot of it : 

[http://suprfile.com/get.php?id=6rm7mm4](http://suprfile.com/get.php?id=6rm7mm4)

Is everything normal? 

Look like a partition problem.

---

### Post by daniel of sarnia on 2007-04-13
this is the latest stable cd [http://www.kernel.org/pub/dist/knoppix/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso]("http://www.kernel.org/pub/dist/knoppix/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso")

---

### Post by sebdj on 2007-04-13
I have try 

sudo fdisk -l 

But it don't seem to do nothing... 

I have a error message now when my computer boot it's : 

NTLDR is Missing
Press any key to restart


What should I do now?

---

### Post by seshomaru samma on 2007-04-13
To download Knoppix - choose a mirror site that is close to you from[ here]("http://www.knoppix.org/")
then you will see a directory with a bunch of files ,choose this:
KNOPPIX_V5.1.1CD-2007-01-04-EN.iso  
Knoppix is a little like the Ubuntu live CD except it's faster and easier to use.
It will automatically see your Windows partition and Linux partition and will allow you to pull data files out of there to a USB or CD


NTLDR is missing is a WIndows problem
It means your computer is looking for some Windows file to boot but can't find them

Basically - it looks like your Linux installation didn't finish
If it had you would get a menu called grub ,when you boot your computer 
A grub menu looks like [this]("http://yekubuntu.free.fr/hoary/i-dualboot.php") (see the image at the bottom of the page)

Also it appears your partition table is corrupt or something - there is definately a problem.
I would suggest this - download Knoppix and rescue your files.
Wipe the harddisc clean
Reinstall Windows
Reinstall Linux

Before you do that make sure you have a proper Windows XP CD , not a recovery disc that comes with some systems.


EDIT- actually , you might have a more serious problem than I initially thought ,because Ubuntu not recognising your partitions is a bad sign. If Knoppix wont recognise them as well , it will be difficult to rescue your data.

If you have very important data on Windows (which you should have backed up ...) the first step you might want to take is using the XP disc to rescue Windows , here is a good guide : [http://www.windowsforum.org/forums/index.php?showtopic=10455](http://www.windowsforum.org/forums/index.php?showtopic=10455)
If not - just wipe the whole disc clean and reinstall both (Windows first).

A side note - when you post try to include more details , it will make it easier to help you.

Good Luck

---

### Post by Sef on 2007-04-13
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk"), it can recover lost parititions.

A couple of questions for you:

1) Did you md5sum the download?  Md5sum checks to make sure the download is good.

2) Did you burn the iso at 4x or less?  Burning at more than 4x may create a bad cd.

---

