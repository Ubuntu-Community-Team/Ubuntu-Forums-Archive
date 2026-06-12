---
title: "Installation issues (installer doesn't run)"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-07-15
Sorry if this is a really dumb question but I've looked through the various help files and resources and haven't found a solution to this issue.  

I downloaded Ubuntu desktop, wrote the .iso file to a CD, and restarted.  The installer didn't run.  What did I do wrong?

Again, sorry if I this is a really dumb question, I'm a newbie. :confused:

---

### Post by catlett on 2006-07-15
It's not a dumb question. There are a couple of things it could be.
First did you "burn" the iso to a disc with nero or a 3rd party application. You do not want to "write" the files to disk with XP's cd writer. There is a difference.
If you burned the iso correctly, then your computer's startup option might not have "boot to the cd drive" ahead of "boot to the hard drive". The boot order is configured in the computers bios. The bios is the software that runs the motherboard. It is seperate from the operating system. You access bios before XP starts up. Usually a screen is displayed quickly before XP starts with your computer makers logo on it.
If you are lucky there will be instructions for how to access the bios. All systems are different but makers usually use the same command for all there brands.
For example my IBM uses F1. My Asus motherboard uses the Delete key. My Dell used Delete twice. If it isn't therr you can do a google search or go to support at your makers web site.
Once you get into bios it will be a text menu. You use the arrow keys to navigate and the enter key to access sub-menus. You want to get to "Boot" options. Usually there will be a boot order of 4 entries. Most of the time it is Floppy, CD Rom, Hard drive and Removable devices. Sometimes the last one is hard drive 2. It doesn't matter.
What does matter is that the cd rom (or cd drive, however it is listed) is ahead of the hard drive. If the hard drive is ahead of the cd then the cd will not start because the hard drive will start up first.

Check those 2 things and try again.

---

### Post by Rhizome21 on 2006-07-15
I'm having the same problems. However, Im on Ubuntu 5.10 right now and i want to install the new dapper in a complete install. I burned the .iso file w/o using NERO or some other program, i just used the "CD/DVD creator" default that comes with ubuntu. or do i have to burn it with gnome baker?

Do i have push a keyboard button to get the installation disk to run when starting the computer? what do i do :confused:

---

### Post by catlett on 2006-07-15
> **Rhizome21 said:**
> I'm having the same problems. However, Im on Ubuntu 5.10 right now and i want to install the new dapper in a complete install. I burned the .iso file w/o using NERO or some other program, i just used the "CD/DVD creator" default that comes with ubuntu. or do i have to burn it with gnome baker?

Do i have push a keyboard button to get the installation disk to run when starting the computer? what do i do :confused:

Use gnomebaker to burn the iso. It's simple, select "burn cd image". Your bios might be incorrect as well. Look for the splash page of your computer maker, that's when you get in.
You also may have a computer that doesn't automatically boot into a cd even when the menu entry is correct. Some computers will ask you to "select any key to enter cd". I had an old lapto that I had to keep pressing C to start it.
The easiest way to find out is google "can't get in bios dell" or whatever brand you have and look for a thread with an answer.

---

### Post by fatsheep on 2006-07-15
Ah, I didn't know that the XP CD writer was an invalid tool for the job.  I'm burning another CD with CDBurnerXP Pro 3, I'll post back here and let you know the results.  

Thanks for the help,

-sheep

---

### Post by fatsheep on 2006-07-15
Hmmm still doesn't work. :confused: 

What's really strange is in the properties for the disk it says it contains 0 kb used space and 0 kb free space. :-k 

I burned it as a bootable class 1 iso and closed the disk so as not to allow any further writing.

What did I do wrong? :-# 

-sheep

---

### Post by catlett on 2006-07-15
You didn't uncompress the files did you? You just want to download the file. And then "burn" that file to the disk. You don't want to make it a botable disk, it is a bootable image already.
Aysiu's guide gives a graphical layout. [http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by fatsheep on 2006-07-15
Thanks for the guide, I will try, yet another time. :)

---

### Post by Rhizome21 on 2006-07-16
Okay, i used my laptop to burn the iso image on the cd (i used NTI program). Now my desktop has successfully booted on the cd. However, when the installation is about to start and error comes up: "Error on reading from boot CD". Is my CD defective? :(

the cd-rw had information on it before and i guess it didn't delete everything : \.

Maybe i should just wait for the installation cd to arrive on the mail. I ordered it a few weeks back.

---

### Post by fatsheep on 2006-07-16
I'm typing this message from Ubuntu so it's been party successful but now I'm having problems with installation.  I selected the first option (which, in the guide, they said was good for dual boot which is what I want) but it freezes when I click the button.  The installer is still running (doing nothing) and I can't get it to exit. :confused:

---

### Post by catlett on 2006-07-16
> **Rhizome21 said:**
> Okay, i used my laptop to burn the iso image on the cd (i used NTI program). Now my desktop has successfully booted on the cd. However, when the installation is about to start and error comes up: "Error on reading from boot CD". Is my CD defective? :(

the cd-rw had information on it before and i guess it didn't delete everything : \.

Maybe i should just wait for the installation cd to arrive on the mail. I ordered it a few weeks back.

Put the installation disk back in and start up. When it comes to the first screen, it will give you a menu. Choose the option "check CD for defects". This will let you know if the cd is defective.
There is another slight possibility that actually happened to me before. Your cd drive could be on it's way out. I had errors on 5 different installs with 3 different distros until someone recommened trying a different cd drive. I happened to have 2 and the cd's worked.

---

### Post by catlett on 2006-07-16
> **fatsheep said:**
> I'm typing this message from Ubuntu so it's been party successful but now I'm having problems with installation.  I selected the first option (which, in the guide, they said was good for dual boot which is what I want) but it freezes when I click the button.  The installer is still running (doing nothing) and I can't get it to exit. :confused:

It appears your cd is fine but a "chech cd for defects" couldn't hurt.
The other thing that comes to mind is your computers resourtces.
What system do you have? The live cd installer is resource inte4nsive. Your computer has to run a full x window system from the cd drive as well as partiton, format and write an operating system to your hard drive. If ypu have under 256mb of ram and les then a P4 this may be the issue. In that caes (I know the last thing you want to do is download and burn another iso) you can download and use the Alternate Install CD. It is a text based installlation that doesn't put the burden of a live session on your system.
Here is a great guide for the alternate cd [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

