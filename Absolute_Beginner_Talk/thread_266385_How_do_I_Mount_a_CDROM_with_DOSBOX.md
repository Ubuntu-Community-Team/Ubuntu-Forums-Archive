---
title: "How do I Mount a CDROM with DOSBOX"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-09-27
I have Dosbox installed and it looks like a dos screen.
The drive that is shown is Drive Z:
The question is how do I access a program on the CDROM drive?

Or how do I mount the CDROM

Thanks for any Help

---

### Post by kent41 on 2006-09-27
Update *****

When I mounted cdrom 

```
mount c /dev/hdc
```

The c: dirve does not show any directories or files.

How can I access cdrom from DOSBOX ?

?

---

### Post by Neobuntu on 2006-09-27
I think you have to follow the conventions of Dosbox when in dosbox. When in Rome...

In dosbox, type "intro cdrom" and see if that gets you going. Then let me know how it went so I may help you farther.

What are you trying to run?

Good experimenting.

P.S. "sudo aptitude install dosbox" is so easy, cool and FAST!

---

### Post by kent41 on 2006-09-27
I saw the intro to cdrom earlier and tried all mount commands.

Each time I would get the error ```
Directory D:\ doesn't exist
```

I even tried to enter the cdrom label but no help.

I am trying to run a compiled Clipper 5.0 application that I wrote called LOKATE. It uses databases and other files.

If I mount cdrom with  mount d /dev/cdrom  it mounts but no files show up.

If I enter  ```
mount -cd
```   I get the following.

CDROMs found: 1
 0. /dev/cdrom

I assume that means 1 cdrom found and it is #0

---

### Post by Neobuntu on 2006-09-27
OK! I did it as follows (I can see why it's confusing.)
I'm using Kubuntu Dapper upgraded.

1) Use (mount,) your CD in (k)ubuntu as usual and make sure it works. I say...

> [COLOR="Navy"]This is a whole 'nother subtopic (but we have to mount,) and in Kubuntu with KDE, I right clicked the desktop and selected "Create new" and "Device" and picked floppy.  Then I right clicked the new desktop icon and picked floppy device as "/dev/fd0". Now, you can right click to mount and unmount.  CD's and DVD's mount after just inserting. Right click the icon in "Storage Media" to un-mount it. In other words, my floppy in Kubuntu doesn't work in the "Stoage Media" but it does on the desktop as an created device icon. Everything else works in "Storage Media." I hope the Floppy in Kubuntu is fixed soon. It's certainly been reported. 

I also have links to "/media/cdrom0" called "/cdrom" and "/media/cdrom" as well.  This way, any of them work; should they be called upon.

Note that the usual convention for linux is to use the "/mnt" folder for mount points but (K)ubuntu uses "/media" instead.  It is too bad that the "storage media" menu choice is NOT working for the floppy (in Kubuntu/KDE) as of today (for some unknown reason.)  Still, The desktop icon work-around for Floppy works very well. *Corrected*: CD's are working and pop up in "Storage Media" as they should now. [/COLOR]

Anyway, make sure the folder "cdrom0" exists in the "/media" folder as 
"/media/cdrom0" or what ever you use and **mount it in Linux first**.

You could do something like:

```
sudo mount /dev/hdc /media/cdrom0
```...in a console terminal instead; if you please.

But then, you'll have to un-mount it via sudo (root) later with:

```
sudo umount /dev/hdc
```

2) Then, don't forget to restart dosbox; to clear any other attempts.

3) **In Dosbox**
```
mount d /media/cdrom0 -t cdrom
```

4) Finaly, typing ```
d:
``` and the <ENTER> key, then ```
dir
``` (DOS commands) showed me the files on my CD (verified.)

You'll have to remember, you are in a DOS like world; with special dosbox ways to mount your linux devices, when running dosbox. Do you remember the old DOS commands? Yikes!

---

### Post by kent41 on 2006-09-27
***  UPDATE  ****

I got it ( mounted CDROM in DOS )

I found somewhere in a properties that the LINK TARGET was /media/cdrom0/

```
mount d /media/cdrom0/ -t cdrom -usecd 0 -ioctl
```

Thanks for the help

---

### Post by Neobuntu on 2006-09-27
Great.

Remember to mount your cdrom in ubuntu first.

**In dosbox** (under Kubuntu.)

Plus, one doesn't need the ```
-usecd 0
``` because 0 is the first default CDROM drive. If one wanted to use a second attached drive, one could and the ```
-usecd 1
``` instead; for example.

Those other two options (see "intro cdrom" in dosbox) may be important to you.

In dosbox:

```
mount d /media/cdrom0 -t cdrom
```

...works(when already mounted in linux)

Note: Watch out for the Windows example strings in dosbox, we're using dosbox in ubuntu. AKA "other platforms" instead.

---

