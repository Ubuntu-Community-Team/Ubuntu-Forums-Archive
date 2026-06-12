---
title: "how to access drives in terminal?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-04-19
I have a couple of questions about the command line.
1 - How do I change drives like in DOS I just entered D: & it would take me to my D drive or A: to get to my floppy. 

2 - What kind of prompt will I get to let me know where I am? 
 I think I got to my floppy drive but when I entered "pwd" it still showed i was in my home directory.
I did notice a "#" instead of a "$" at the end of the prompt but I didn't know what it meant.
" ls" also showed my home directory.

3 - This may be a question for a separate post but I'm trying to make a boot floppy so I can read all my drives in an emergency situation. Can anyone post a good link for that. I've found one for grub but that's really not what I'm looking for.

---

### Post by Iceni on 2007-04-19
There is probably a way cooler way to do this but I figured out that standard cd'ing to /media/floppy/ works:)

ohabu@ohabu:~$ cd ..
ohabu@ohabu:/home$ cd ..
ohabu@ohabu:/$ cd media
ohabu@ohabu:/media$ cd Graendal
ohabu@ohabu:/media/Graendal$ 

(just as an example, in case you have even less terminal experience than me:) )

---

### Post by garyed on 2007-04-19
> **Iceni said:**
> There is probably a way cooler way to do this but I figured out that standard cd'ing to /media/floppy/ works:)
...


Don't I feel stupid. 
I still can't figure out what the "#" sign means instead of the "$".  I can't get it back now either.

---

### Post by aysiu on 2007-04-19
```
df -h
``` will tell you what's mounted, where each is mounted, and how much space is on each drive.

Once you see what's mounted and where, you can just *cd* directly to the mount point: ```
cd /media/usbdisk
``` for example.

**username@ubuntu:~$**
*username* is your username.
*@* says at
*ubuntu* is the name of the computer *username* is logged in at
*:* is just the separator between the computer name and your active directory
*~* means /home/username is your current directory
*$* is the prompt where you type commands.

---

### Post by Panzor on 2007-04-19
Well, there are plenty of sites to figure out how to navigate around your HD. You're confusing Ubuntu with windows. In windows, there are harddrive names. In ubuntu there is "/". "/" is probably what the aquivalent of the C: drive is. I'm sorry that I can't help you with multiple harddrives, I don't feel like I should guide you since I've never had two in an ubuntu machine.

You want to boot from floppy? Well, that's not really an OS thing. You want to hit the SETUP button as your computer is booting up. Usually the buttons are F1-4, F8, or delete. It should display which one it is. Many of the interfaces vary, so I'm just going to let you find something that says "startup", "boot sequence", or "boot order." Set the order that you would like the computer to boot from. If you want it to check the floppy driver first, I would recommend to put that first; however, You should not need to worry about doing this now since you can access this if your HD ever fails on you. You're looking at an ON-Board OS that all motherboards have. If you ever have a problem and need to boot from floppy, I suggest that you set it when you need it. You don't want to be booting unless you have a problem, right?

---

### Post by garyed on 2007-04-19
> **Panzor said:**
> ................
You want to boot from floppy? Well, that's not really an OS thing. You want to hit the SETUP button as your computer is booting up. Usually the buttons are F1-4, F8, or delete.............. I

I probably didn't make myself clear about booting from a floppy. 
I only want to make a boot floppy for emergencies, not for everyday boot up. For instance if I do something from the command line by mistake that causes my system not to boot I would like to have a boot floppy that I could use to get into my system & edit whatever I need to fix the problem.
In windows they call it a system disk & you can make one very easily with a "format/s" command.

---

### Post by aysiu on 2007-04-19
Do you have a Ubuntu Desktop CD? If you have one of those, you won't need the boot floppy for emergencies.

Unless... do you need the floppy in order to boot from CD-ROM?

---

### Post by garyed on 2007-04-19
> **aysiu said:**
> Do you have a Ubuntu Desktop CD? If you have one of those, you won't need the boot floppy for emergencies.

Unless... do you need the floppy in order to boot from CD-ROM?

I do have the CD that made from the iso file to install edgy.
That will obviously boot my computer but I didn't think I could use it to access my drives.
If so then that should solve that problem but I still would like to know how to make a boot floppy.
I'm just used to floppies for emergencies.

---

### Post by aysiu on 2007-04-19
If it's the Desktop CD (the one that has a live session), then, yes, you can use that to access your drives.

If it's the Alternate CD (goes straight to installation without a live session), then, no, you can't.

---

### Post by garyed on 2007-04-19
> **aysiu said:**
> If it's the Desktop CD (the one that has a live session), then, yes, you can use that to access your drives.

If it's the Alternate CD (goes straight to installation without a live session), then, no, you can't.

I just have the installation CD.
I'm really surprised if there isn't a simple command line to make a system floppy to boot into Ubuntu.

---

### Post by aysiu on 2007-04-19
> **garyed said:**
> I just have the installation CD.
I'm really surprised if there isn't a simple command line to make a system floppy to boot into Ubuntu.
There probably is, but it's not well-publicized since most people just use CDs for recovery.

---

