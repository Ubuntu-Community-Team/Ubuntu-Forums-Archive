---
title: "Grub Doesn't Recognize Windows XP"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by Maci_01 on 2006-05-02
Hi, my name is Joe. I have installed other linux distros before but never really used them much. I hope to use Ubuntu full time with my desktop. Anyway --

When I boot my computer and hit esc to go to the OS choice menu in grub, windows does not appear. Only Ubuntu, Ubuntu Recovery, and Ubuntu memory test appear. I run ubuntu on one partition and Windows XP on the other. I am using Ubuntu 5.10.

Can anyone provide some help with this?

Hope to hear from someone soon. ;)

---

### Post by BoneKracker on 2006-05-02
IF you already had Windows XP installed when you installed Ubuntu, the installer should have taken care of this for you.

However, since it did not, for whatever reason, you probably need to set up GRUB to present you with boot alternatives when you start up, and to add an entry for Windows.

The file you need to edit is /boot/grub/menu.lst.  The menu.lst file that comes with Ubuntu (provided by Debian, I think) is well-commented and pretty easy to configure.  It provides an example for adding Windows to your menu alternatives that you can simply un-comment and change a couple of settings.  Also, in the comments at the top of the file, it refers you to other sources of documentation about GRUB.

Essentially, you will need an entry in /boot/grub/menu.lst that looks something like this:
```

title              Microshaft Windoze XP
root		  (hd0,0)
makeactive
chainloader	+1

```

If you put this before your list of linux boot alternatives, it will be the default and will be booted automatically after a timeout you specify (e.g. 15 seconds).  This timeout period is set with a line that looks like this (there's an example, I think):
```
 
timeout                              15

```

Once that timeout is set, you won't need to hit <esc> any more -- you'll get a nice menu built from what's in this file.  (You can even use colors or a background image, if you want.)

The "title" can be whatever you want (as above).
The key part you need to figure out and set for your computer is the "root".  The two parts (hdX,Y) are telling it which disk drive (X) and partition (Y) Windows is on.  The counting starts from zero (so (hd0,0) refers to the first disk and first partition of it).  For example, (hd1,5) refers to your second drive, and the sixth partition on it.

That should be enough to get you started.  Make a backup of your original menu.lst file before you edit it.  Read the documentation.  There is more on the internet too.

Also, assuming you did have XP installed when you then installed Ubuntu, I'm a bit concerned that it didn't detect its presence and configure GRUB for you.  If you are not successful with what I've told you above, come back and make a new post asking for help again.

Let us know how it goes.

---

### Post by Maci_01 on 2006-05-02
The information you provided seems very usefull.

The file menu.lst can only be changed with root. How can I change it?

Thank you so much.

Edit
(Managed to login as root.)

---

### Post by rjg1021 on 2006-05-02
You have to run as "sudo" (run as root) in the terminal.
```
sudo gedit /boot/grub/menu.lst
```

edit: didn't see your edit...

Then you will be prompted for the root password (you set it during installation, may also be your user password) then read through the menu.lst until you get to the end. It should have a comments breaker that says "Other operating systems" that is where the XP entry *should* be. 

You want to add in the line:

```
title              Microsoft Windows XP
root		  (hd0,0)
makeactive
chainloader	+1
```

.If your XP was installed before Ubuntu and its on the same HDD, then you should see that already. Otherwise, it may be something more complicated that I cannot help with.

Hope this helps.

---

### Post by Nequeo on 2006-05-02
[QUOTE=Maci_01]
Edit
(Managed to login as root.)[/QUOTE]

Just wondering, did you discover 'sudo'? [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Maci_01 on 2006-05-02
When I added the lines
> 
title                   Windows XP
root                   (hd0,5)
makeactive
chainloader +1

after the linux boot choices in the menu.lst file, rebooted and tryed to load the new choice, Grub returned this message:
> 
Booting 'Windows XP'

root (hd0,5)
 Filesystem type unknown, partition type 0x82
makeactive

Error 12: Invalid device requested

Press any key to continue..._

I have also tried replacing the 'root (hd0,5)' with 'root (hd0,0)','root (hd0,1)', and 'root (hd0,2)'.

My discs look like this:
> 
 Maxtor 4k020H1
 /dev/hda
   /dev/hda1 (Ext 3, Ubuntu)
   /dev/hda6 (Memory Swap)
   /dev/hda5 (Windows NTFS, Windows XP)
 Maxtor 4R080L0 
 /dev/hdb
  /dev/hdb1 (Windows NTFS, general files)
  /dev/hdb5 (Windows NTFS, general files)


Any thoughts?

---

### Post by catlett on 2006-05-02
It says you have windows on dev/hda5. I think you might be having a 1024 problem (if that is the right number). Meaning windows has to be within a certain part of the hard drive to boot.
Was windows on the fifth partition before? If so could you boot?
Windows likes to be at the start of the drive. It should be in dev/hda1. I think that may be it. If it is you got a bit of work ahead of you.
Hopefully someone knows some commands about copying partitions to other partitions.
Also I could be wrong, wouldn't be the first time. Just thought I'd give my thoughts on it.

---

### Post by confused57 on 2006-05-02
I think I see a possible problem, but I don't have the expertise to help you correct it, I'll do a search and see if I can find something.

Windows is best installed on the 1st partition of a hd, it wants to be the only operating system.  I think there may be a way to add mapping lines  to your windows menu.lst to fool windows to think it is the only operating system.  I have 2 hd with Ubuntu master and windows slave and had to use a menu.lst similar to what's in this thread:

[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)



I agree with BoneKracker, try some simpler solutions first...before making any major changes...there's plenty of very knowledgable people here who'll help you.

---

### Post by Maci_01 on 2006-05-02
Thank you all for your expertise on this issue. I will have to look into it some more. . .

I remember reading about Windows wanting to be the first partition. . .for clearification, I had two windows operating systems running until a while back one (the first) stoped running. Then my Ubuntu CD came in the mail and I decided to give it a shot -- otherwise I'd have installed Ubuntu onto the second partition. 

I will read about "map[ing] on a single HD." If anyone can provide any further details it would be greatly appreciated.

You all have been very helpful.

---

### Post by BoneKracker on 2006-05-02
Before you head down other paths, check your syntax...

Remember what I said:
> 
The counting starts from zero (so (hd0,0) refers to the first disk and first partition of it). For example, (hd1,5) refers to your second drive, and the sixth partition on it.


Which partition is it?  
Did you subtract 1?

The fifth parition on the first drive will be (hd0,4).  Did you try that?

---

### Post by Maci_01 on 2006-05-02
I just tryed using root (hd0,4) and had no success. My eyes are begining to strain and I think I had enough for the night. Will certainly catch up tommorow.

Thanks for all your help.
Maci

---

### Post by BoneKracker on 2006-05-03
Here's the GRUB Manual:

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Try not to get frustrated.  Wading chest-deep into GRUB is a good rite of passage (partly because it's not well-documented).

Also, verify that the bootable flag is set on your Windows partition.

---

### Post by manicka on 2006-05-03
try 

```
title              Microsoft Windows XP
rootnoverify		  (hd0,0)
makeactive
chainloader	+1
```

---

### Post by Maci_01 on 2006-05-03
Adding "rootnoverify" doesn't seem to work. If I can't figure this out by tonight then I will be forced to reinstall windows and Ubuntu. I am determined to get Ubuntu working the way I want . . .

---

### Post by confused57 on 2006-05-03
Reinstalling windows then Ubuntu will probably be the only way to get your system working, but this may be a good time to experiment a little and learn something in the process since you'll be reinstalling anyway.

You may want to use your Windows CD & try to "fixmbr", then maybe use your Ubuntu Live cd to reinstall grub(to windows?):

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

Read & try some different things, if something works; post back how you did it, I'm sure many people who've had the same problem would like to know.  I haven't read of anyone having success dual-booting without windows as the 1st OS.  Just a thought, do what works best for you....Good luck.

---

### Post by BoneKracker on 2006-05-05
What confused57 said last night is exactly right -- I guess I missed it because it was late and I went straight to the "root" line looking for that common error. The best way to do a multiboot with Windows is to install it first and then add Linux. I once tried it the other way and wasn't able to make it work. If I recall correctly from my research at the time, it _can_ be done, but it's messy and I only found theoretical references (i.e., nobody does it that way). There are other bastardizations too: for example, you can use the NT bootloader and chainload Linux from it. (You can also stick a fork in your eye, but that doesn't mean you _should_.) Let us know when you're successful. :)

---

### Post by SHL on 2008-07-24
> **Maci_01 said:**
> 
title Windows XP
root (hd0,5)
makeactive
chainloader +1

According to what I found out googling around, Windows needs to believe it is accessing (hd0,0). Hence you need to trick it to believe that, by adding the following lines, e.g. under the "root" row:
```

map (hd0,0) (hd0,5)
map (hd0,5) (hd0,0)

```
And then changing the root row to be (hd0,0) rather than (hd0,5).

On my Ubuntu/WinXP box I have also a line saying "savedefault" (but I don't know what it does). So including that it could look something like:
```

title Windows XP
root (hd0,0)
map (hd0,0) (hd0,5)
map (hd0,5) (hd0,0)
savedefault
makeactive
chainloader +1

```

---

