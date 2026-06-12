---
title: "Urgent !!! Lost My File  !!???"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by sebdj on 2007-04-11
URGENT!!!!

I have install (well trying) Ubuntu (My first time trying something else then windows).
But now I have fear I have erase all my file but I'm not sure.

I have put the cd at the boot of my computer

Then I have choose Start Install Ubuntu

After it go alone by showing the Ubuntu logo with a orange load timeline.

After the desktop appear. I have play a little with it a little with ubuntu.

LOOK HERE :

[http://fosswire.com/2007/01/12/givin...t-time-part-3/](http://fosswire.com/2007/01/12/givin...t-time-part-3/)

(I MAKE EXACTLY WHAT THIS GUY DID (BEGIN AT THE UBUNTU START INSTALL)

But now I try to boot my computer nothing happen...
I have look in the bios if the Boot order was correct (it's correct the hard disk boot first)

Now what do I do???
Did I lost my file???

:confused:   PLEASE HELP!!!!

---

### Post by Razorback on 2007-04-11
Did ubuntu ever boot up?

---

### Post by sebdj on 2007-04-11
Not without the cd... No

---

### Post by arron on 2007-04-11
What does it do with no cd?  Does it hang?  Does it come up with a error message?  Is the BIOS set to the proper HD?  Some can specify HD 0,1,2,3 etc.  Is the HD plugged in and everything (were u in the box?)  Did you say it was ok to install the boot loader or cancel it?

---

### Post by sebdj on 2007-04-11
The bios setup is ok     The first to boot is Hard Drive after cd-rom  that it 

I did like the link I send you in the first post. 

look like it never happen to nobody before ...lol 

Thank you for helping me!
do you know what should I do :confused: 

now I really just want to have my file back... 
I know they are still there because my hard drive is 160 GIG and  when I click on install (on the desktop) they give me 2 choice 

1. Erase All (to install after) 

2. Create a new partition. 

I have click on 2.  and the disk show only 149 is free (not 160 gig )   So my old file are still there. 

I have trying to reinstall windows but no success (they said I got to format to install...

---

### Post by arron on 2007-04-11
When you try to boot from the hard drive (take out the CD) what does it say or do?

---

### Post by sebdj on 2007-04-11
lol.  Already try that 

it only make a flicker appear (like when you write a text) 

no text at all and I click on every button but it still do nothing

---

### Post by jpeddicord on 2007-04-11
[http://fosswire.com/2007/01/12/giving-linux-for-a-spin-the-first-time-part-3/](http://fosswire.com/2007/01/12/giving-linux-for-a-spin-the-first-time-part-3/) (Fixed the link for those wondering about the 404)

Where exactly in the tutorial did you start having problems?
Did it get to the progress meter where you just wait for it to install?
Did it crash earlier on?

Windows should still be installed, even if you cannot boot it. Try using the Windows disk in repair mode when you try to install it. (It should ask you about pressing a certain key to "fix a broken MBR.")

If that does not work, post back here again and we'll try to get Ubuntu completely installed so you can still boot Windows alongside it without any ill side-effects.

(On a sidenote: While I did not write that article, I do write for FOSSwire. :-D)

---

### Post by arron on 2007-04-11
While booted with the CD if you run

```

sudo fdisk -l

```

This will print out the partition table on the disk.  Did the install complete fully?  Before the blank screen is there a ubuntu logo loading?  Is there any text on the screen when it stops, or just before it, if so what is it?  For example from the BIOS text straight to a black screen? Or BIOS to a Loading Linux......" then black screen?

---

### Post by sebdj on 2007-04-11
Thx for your help 


My computer crash when I boot and nothing appear... 
Just the initial loaqding of when my computer start (access the bios, boot menu, etc...)

and then just a flicker. 

What I did is put the cd on at the start Clcik install ubuntu (exactly as the guy did on the link I post. ) 

But then I can't boot at all without the cd. 

I try to recover my file with the Windows xp boot disk 
they ask me to insert a flopy disk.       Another problem .... My floppy disk is plugged correctly but stop to work since 3 month...

---

### Post by arron on 2007-04-11
> **sebdj said:**
> 
My computer crash when I boot and nothing appear... 
Just the initial loaqding of when my computer start (access the bios, boot menu, etc...)


What boot menu?  a Grub Boot menu?  Or some kind of windows boot menu?  Or some sort of BIOS boot menu?

---

### Post by sebdj on 2007-04-11
just the boot of the computer... 

When you have to type  DEL to acces the bios  or Type F12 To acces the boot menu 

or F8 to acces the network menu 


It's just the initial boot of the computer nothing else...

---

### Post by pxwpxw on 2007-04-12
**sebdj **

You need Super Grub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If your floppy drive is broken you will need to download the CDROM version and 
burn a CD (on another computer). Then boot from it.

It can restore your MBR for Windows as well as booting your Linux.

Also disconnect the broken floppy and make sure it is not in the bios bootup list.

I assume you have only one hard drive.

---

### Post by thefoolisme on 2007-04-12
What version of Windows are you trying to fix?  If it's XP, then it shouldn't be asking you for a floppy disk (unless you need special drivers).  Simply boot to the Windows CD, let it go through it's loading process (drivers, etc.), and you will come to a menu that asks if you want to install or REPAIR using recovery console.  Select REPAIR, and it will go into Recovery Console.  It will ask you which installation of Windows you want to fix.  Input the number of the installation (most likely 1), enter password (if there is one).  Once you get to the C prompt, type FIXMBR   It will ask you if you're sure you want to do this, enter yes, and it will fix the MBR.  Exit out of Recovery Console, take out Windows CD, and reboot, and it should boot your Windows.  

SuperGrub may do it for you as well, but if you don't have it, try what I said above first.  I haven't had to use SuperGrub, although I think I need to have a copy of it on hand for the future. Once your MBR is fixed for Windows, you can go back and try to install Ubuntu properly, since it sounds like an aborted installation last time.  

Good luck!

---

### Post by aberry5555 on 2007-04-12
you can recover your files using the live CD, I think that would be the best idea, then you won't accidentally delete them whilst trying to fix it.

Unfortunately, though, it sounds like you might have already deleted that drive as the "149GB" free bit does not mean anything, every single hard-drive is quoted as being one size but is usually different, for instance my disk at home is supposed to be 120GB, but it only ever reads at 111GB.

Firstly run the Live CD, then open a console window and type in

```
sudo fdisk -l
```

and post what is says back on this forum, then we can try and go from there.

<--EDIT--> 

Also, as the people above are saying, the FIXMBR option on the windows disk might work but **DON'T** try it before using the live cd because, in my experience, it *really* doesn't like Linux partition tables, so it could just make it worse.

---

### Post by pxwpxw on 2007-04-12
Agreed 
```

sudo fdisk -l

```

would be very useful to show what partitions are there.

---

### Post by sebdj on 2007-04-12
Thx for all your reply... 

I have try SuperGrup cd but still don't work... 

I did the number 2 : 

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows)

I also try to boot windows cd and type FIXMBR But still not work. 

I have access to Ubuntu by the cd boot. I should try to configure something by there but I'm new to Ubuntu... 

Where do I write the code you give me?

---

### Post by sebdj on 2007-04-12
HOw do I open a console so I can type : sudo fdisk -l    ??

---

### Post by sebdj on 2007-04-12
I just try to boot by the ubuntu cd and in the 4 choice in the begin like this link : 

[http://fosswire.com/2007/01/12/giving-linux-for-a-spin-the-first-time-part-3/](http://fosswire.com/2007/01/12/giving-linux-for-a-spin-the-first-time-part-3/) 

I choose boot from the hard disk 

and it tell me linux code error

---

### Post by sebdj on 2007-04-12
SO what should I do ??? 

I can access Ubuntu if I have the cd... 

SO what should I do on Ubuntu to find my file??? 

:confused:

---

### Post by sebdj on 2007-04-12
don't stop reply please I need your help!

---

### Post by confused57 on 2007-04-12
Boot into your installed Ubuntu(using the live cd), open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

this was suggested in an earlier reply, but might help

Also post the output of:
```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list

Added:  You also might want to boot up the live cd & try to reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by devnulljp on 2007-04-12
This is all overkill - the mbr is just hosed.
I suspect the original poster didn't understand the recovery console fixmbr method, but that's the best shot here. The poster doesn't know enough linux to get to a console, I doubt there's much point trying to explain loading kernel modules to allow mounting ntfs drives in rw, then copying files around.
The best solution to fix this is as posted by thefoolisme
Here's a google search as a starting point for the original poster: [http://www.google.ca/search?hl=en&q=fixmbr+recovery+console&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=fixmbr+recovery+console&btnG=Search&meta=)
This one looks like a good walkthrough: [http://www.simplyguides.net/guides/recovery_console/recovery_console.shtml](http://www.simplyguides.net/guides/recovery_console/recovery_console.shtml)

Really, this sounds like the problem and the best solution.

Insert your  windows cd and reboot
Hit R for repair once the blue screen loads
Choose the main drive & type "fixmbr" without the quotes
That will rewrite the boot sector, and you should be able to reboot back into windows.


this will re write your boot record and get rid of grub

---

### Post by pxwpxw on 2007-04-13
> **sebdj said:**
> I just try to boot by the ubuntu cd and in the 4 choice in the begin like this link : 

[http://fosswire.com/2007/01/12/giving-linux-for-a-spin-the-first-time-part-3/](http://fosswire.com/2007/01/12/giving-linux-for-a-spin-the-first-time-part-3/) 

I choose boot from the hard disk 

and it tell me linux code error


You are in the installer, you have gone too far.

I am posting this from the xubuntu Destop CD, running from the CD, not installed.

Start again.
If you have an internet connection for the computer, connect it now.

You have the Desktop CD. 
Start the comouter from the Desktop CD

From the first screen - Select start or install

After about 4 minutes the Ubuntu Desktop appears.

It has Menu Bar across top, and icons on screen for  - Examples,  Install
Do not install.

Stop right there and look at the applications you can find on the desktop, menu bars and drop down panels.

Find terminal, editor, filemanager. firefox browser.

If you have an internet connection you can log into Ubuntu forum from there using Firefox browser. That is what I am doing now. You dont have to install anything,

Take your time, enjoy, no hurry.
Report back when ready.

Then we will be able to  get the information we need. :)

---

