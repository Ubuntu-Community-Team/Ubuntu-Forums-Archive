---
title: "Can't mount Windows XP hard drive with Ubuntu live CD"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by norair on 2005-11-18
so the drive is showing up, but when i added: 
"/dev/sda1       /media/xpdata   ntfs nls=utf8,umask=0222 0 0"
to the fstab it did not mount, how can i mount it without needing to add it to the fstab file??

the drive is not a scsi drive, it is an SATA drive running on a controller that is not built into the motherboard

---

### Post by darth_vector on 2005-11-18
do it manualy. open up a terminal and type:

sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

---

### Post by Decon1 on 2005-11-18
darth Vector, sorry man that just flat don't work!  I wasted an entire evening trying that...........

norair do this:

First..Open the Terminal - Apps, Accessories, Terminal and type in: sudo mkdir /media/windows

Then:
1. Select System, then Administrator, then Disks.

2. One of the disks on the left side will show that it has some amount of file size. Mine is 69.25. No matter. Select that disk.

3. Click on the Partitions Tab. In access Path type: /media/windows and click on change.

4. 2 lines down, Status, the Enable button will be highlighted. Click it. It will change the Status from inaccessible to accessible.

5. Click on "Browse", wait a few seconds and you have access to your HDD

NOTE** The HDD can only be accessed this way.  Not sure why.  I am sure there is a command like darth_vector and samba etc uses.

---

### Post by Chayak on 2005-11-18
odd that won't work
I had a similar issue with having to get data off of two xp drives so I could format them for linux.
```
sudo mkdir /media/winxp
sudo mount /dev/sda1 /media/winxp -t ntfs
```
is exactly what I did, even for my sata drives.  Darth_vector pretty much posted the same.  That's how it's done.  Are there any errors? What does it say when you try to mount?

---

### Post by Decon1 on 2005-11-18
Note to some of you power users!!

Ubuntu is cool but the inability to mount the HDD on boot is running us noobs off!!!  The only reason I'm here is because Ubuntu was so very easy to print from where as the others were No Go!  I knew from playing with the other LiveCD's that sooner or later I'd figure out how to get to the HDD.

Will I someday put this on?  Yup I will, but not on my gamer.  Too much there to even chance a dual boot.  You have too good of a program here to not have easy "On-Boot" access to the HDDs.  Maybe SATA is the problem but hey IDE is old tech.

Hope someones listening, there are 3 diffferent posts on this problem on the front page.  Think how many others are doing Knoppix or Slax.

Decon

---

### Post by cluelessnoob on 2005-11-18
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

Use the NTFS on boot-up

Oops! sorry wasn't reading your using a SATA drive on a live cd install... 

hmmm this might help

[http://www.willmer.com/kb/2005/02/installing-ubuntu-hoary-from-livecd/](http://www.willmer.com/kb/2005/02/installing-ubuntu-hoary-from-livecd/)

---

### Post by Chayak on 2005-11-18
[QUOTE=Chayak]odd that won't work
I had a similar issue with having to get data off of two xp drives so I could format them for linux.
```
sudo mkdir /media/winxp
sudo mount /dev/sda1 /media/winxp -t ntfs
```
is exactly what I did, even for my sata drives.  Darth_vector pretty much posted the same.  That's how it's done.  Are there any errors? What does it say when you try to mount?[/QUOTE]
EDIT: Note that this will mount the drive as read-only with root ownership.  So you must choose 'browse drive' from within the drive manager or APPLICATIONS>>System Tools>>Run as another user     
then a file browser to be able to copy files
Hrm, why did it quote this when I clicked edit?!? lol

---

### Post by Decon1 on 2005-11-18
Chayak!  Ok yours worked!  However you still can not click on the desktop Icon or at least I can't.  It says:  "You do not have the permissions necessary to view the contents of "winxp"."  I end up in the Administrator dropdown anyway??

Thanks though!  Any idea how I get the proper permission??

Decon

OBTW  Was an EM1(SS) USS Jallao SS 368 and the Eathan Allen SSBN 608. In 68-74 <salute>

---

### Post by darth_vector on 2005-11-18
sudo chown <username> /media/winxp

---

### Post by Decon1 on 2005-11-18
Ok but what do I put in under Run: in the "Run as Different User"?  user defaults as root correct?

Decon

---

### Post by BLTicklemonster on 2005-11-19
[QUOTE=darth_vector]sudo chown <username> /media/winxp[/QUOTE]
That did not work. I have an icon on my desktop now that I can't use. I imagine that this is the windows hard drive?

(any chance I can edit something somewhere in ubuntu so that I can dual boot now?)

*edit:

oddity: the icon on my desktop works now.
Interersting tidbit: I can drag files from there to linux, but they are locked. What I have to do to manipulate them is to rt click, go to scripts, root-nautilus-here, and it brings the directory the file is in up, and if I want to delete file, I can now delete it.

---

### Post by aysiu on 2005-11-19
[QUOTE=Decon1]Note to some of you power users!!

Ubuntu is cool but the inability to mount the HDD on boot is running us noobs off!!!  The only reason I'm here is because Ubuntu was so very easy to print from where as the others were No Go!  I knew from playing with the other LiveCD's that sooner or later I'd figure out how to get to the HDD.

Will I someday put this on?  Yup I will, but not on my gamer.  Too much there to even chance a dual boot.  You have too good of a program here to not have easy "On-Boot" access to the HDDs.  Maybe SATA is the problem but hey IDE is old tech.

Hope someones listening, there are 3 diffferent posts on this problem on the front page.  Think how many others are doing Knoppix or Slax.

Decon[/QUOTE] Ubuntu is not a live CD distro. Ubuntu is an installer distro that *has* a live CD to try out.

Knoppix is a live CD distro that *has* the ability to be installed.

The priorities are different. *Can* you mount Windows partitions in a Ubuntu live session? Yes, you should be able to. Why you're having trouble I don't know. But it is not Ubuntu's priority to make the live CD automount Windows partitions.

By the way, these instructions given earlier ```
sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
``` has worked for me every time I *have* used the Ubuntu live CD.

[QUOTE=norair]so the drive is showing up, but when i added: 
"/dev/sda1       /media/xpdata   ntfs nls=utf8,umask=0222 0 0"
to the fstab it did not mount, how can i mount it without needing to add it to the fstab file??[/quote] By the way, if you add that line to your /etc/fstab, it won't actually mount to /media/xpdata until you type in this command after saving /etc/fstab: ```
sudo mount -a
```

---

### Post by Decon1 on 2005-11-19
aysiu,

Thanks for your kind reply.  Being new I guess I assumed that all the various distros are in a competition of sorts.  It is most irritating to a noob to have the windows HDD mount automagically in MOST distros.  Yet here it doesn't?  Just how much would that take to do?  If a noob downloads and tries something that doesn't work he will most probably push on to one of the others.  Again, I am now staying with Ubuntu and kept trying because the printer setup is a no-brainer.  Again, strange that effort would be made to print easily as the others don't, yet HDD mounting is errr...was such a chore!

Now then for some odd reason it finally worked but not without pasting it in twice the first time didn't take.  the second it said the media/windows couldn't be made because it already existed.  Entered the mount statement and waaalaaah! Done and good.

Thanks again!  To all!
Decon/Dennis

---

### Post by aysiu on 2005-11-19
So it finally worked?

As for the different distros--no, not all of them are in competition with one another. Linux is generally a friendly place. Would Novell prefer to get contracts over Linspire or Red Hat? Sure. Does the maker of Damn Small Linux care if you use Damn Small or Slackware? Probably not.

Different distros serve different purposes. For example, Mepis mainly targets ex-Windows users who are used to point-and-click. Slackware targets people who are a bit more used to the command-line and who are definitely not computer novices.

If easy printer setup is the only reason you're using Ubuntu, I'd suggest using another distro, honestly. Ubuntu does not do most things automatically or in a point-and-click way (at least for installation and configuring). I'd suggest Mepis or Blag.

If you do decide to stick with Ubuntu, you'll be rewarded, but it'll take some time and a lot of learning.

---

