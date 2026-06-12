---
title: "So... where IS the hard drive?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by infrarad on 2007-04-19
Hi there,

I installed Ubuntu about a month ago with the help of someone tech-savvy. This is my first post, and Ubuntu experience has been my first foray into trying to understand how my computer works, rather than just crossing my fingers and double-clicking on things.

I bought an external hard drive with a USB cable. Once I plugged it in, I realized that since it doesn't automatically mount (and why would it, really?) I have no understanding of what exactly the hard drive IS, really. Is it a directory hidden in one of the directories immediately inside the root? Is it a "device" or a "media"? Is it something else entirely?

I understand that "everything in Linux is a file," but knowing next to nothing about computers to begin with, the nuances of just what that implies are lost on me. I'm very interested in learning about the command line, but my awareness of how to use cd, ls, and rm are currently insufficient to find the drive and, like, do whatever it is that you do to a new hard drive =)

Advice or pointers to advice would be very much appreciated.

---

### Post by igknighted on 2007-04-19
use "sudo fdisk -l" to list all attached hardrives.  My money is on /dev/sda or /dev/sdb, but who knows.  I have to admit, when I read the title of this thread I thought, "One would guess in the computer "... although clearly I was wrong in this case :)

---

### Post by aktiwers on 2007-04-19
Often when you buy a new harddrive you have to format it first. Because they often (atleast in all cases I have seen) comes without any filesystem and filled with empty data.

Therefore I think you might need to format it. You can do that with the program gparted.
If its not already installed, you can install it by typing this into the Terminal:
```
sudo apt-get install gparted
```

And run the program by typing:
```
gparted
```

Then inside gparted you need to look for "unpartitioned space" and create a filesystem.
You can pick Ext3 from the drop down menu, as thats a good Filesystem for linux.

---

### Post by infrarad on 2007-04-19
Hey neat, there it is! 

I imagine the next step is formatting--is there anything else that one does? I note that the way my file system is currently set up, it's for some reason transparent that I have two internal hard drives, but I didn't quite understand the explanation my geek gave me on why this is so.

---

### Post by igknighted on 2007-04-19
> **infrarad said:**
> Hey neat, there it is! 

I imagine the next step is formatting--is there anything else that one does? I note that the way my file system is currently set up, it's for some reason transparent that I have two internal hard drives, but I didn't quite understand the explanation my geek gave me on why this is so.

Depends what you are using it for.  If it is only for linux, use ext3 as the file format.  If it will only be read by your windows pc and linux pcs, still use ext3 (and install the windows driver for ext2/3).  If you might want to attach it to someone else's windows PC, use ntfs (might have to format from windows) and install ntfs-3g on your ubuntu install

---

### Post by infrarad on 2007-04-19
Linux only. I have fully defenestrated my desktop, and the only other computer using it is going to be an Ubuntu laptop (once I do the install, that is... learning how an install works is going to be my major way of figuring out the linux ins and outs).

I'm currently partitioning the drive with ext3 using gparted. About how long should that take for a 320 gig drive? It's been saying "0 of 1 operations completed" for about 10 minutes now.

---

### Post by aktiwers on 2007-04-19
It can take some time..  but not much more than 10-20 mins I think. Dont know know really though. My biggest harddrve is 250gb and its years since I last formated it.

But I really think you are going to get disappointed when you install Ubuntu on your Laptop. Because you wont really learn much, as its very very easy.  :)

Good luck with the partitioning and let us know how it went :)

---

### Post by Jarn on 2007-04-19
> **infrarad said:**
> I have fully defenestrated my desktopdefenestrate - v. to throw out a window

Sounds like a waste of a good desktop!

---

### Post by infrarad on 2007-04-20
It seemed an appropriate word for having thrown out Windows. =)

Now that the partitioning program has finished, when I open the terminal and do

```
sudo fdisk -l
```

again, it (1) doesn't list the new hard drive, and (2) the terminal doesn't accept any further commands--i.e., if I hit up-arrow to try and do that command again, I just get "^[[A", and I have to reopen the terminal to do a new command. That can't be good....

---

### Post by infrarad on 2007-04-20
Um... is

```
Unable to open /dev/sda - unrecognised disk label.
```

a bad thing to see when you run gparted?

---

