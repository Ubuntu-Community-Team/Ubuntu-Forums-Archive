---
title: "Urgent  - How to copy file from a floppy to ubuntu desktop"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by agarwaldvk on 2006-02-22
Hi Everybody

I have downloaded the scanmodem tool and have to copy it from the floppy to the ubuntu desktop.

How do I do that? How do I specify the filepath for the floppy drive in ubuntu terminal command.


Best regards


Deepak Agarwal

---

### Post by nalmeth on 2006-02-22
are you in gnome? if so, on the top panel just go PLACES --> COMPUTER and you should see your floppy drive

edit:
if you want the terminal, your drives should all be in /media  
nano /etc/fstab 
for details on your mount details

I don't even have a floppy...

---

### Post by agarwaldvk on 2006-02-22
Guys

I went to terminal and typed the command :-

sudo mcopy a:scanModem.gz .

which it did not like.

I then typed the following command :-

sudo cp a:scanModem.gz scanModem.gz

Says no such directory or file.

I have changed directory to /Desktop and am in it and have typed the command from there.

Why cannot it not see the file. The file sits on a floppy drive.


Best regards


Deepak Agarwal

---

### Post by agarwaldvk on 2006-02-22
Guys

Tried mount /media/floppy0

The floppy had 2 files viz scanModem.gz and unloading.gz

It complained saying cannot determine the filesystem and none was specified.

What do I need to do to see these files so that I can copy them on to my Desktop in Ubuntu?


Best regards



Deepak Agarwal

---

### Post by abhaysahai on 2006-02-22
long answer -- try this first
man mount

short answer 
looks like you floppy is formatted for FAT

mount -t fat /media/...

---

### Post by agarwaldvk on 2006-02-22
Guys

Nothing works!

What next - forget Ubuntu, do I?

Apparently it is not for me if I can't get it to see the damn floppy disk, is it??????????????????????????/


Best regards


Deepak Agarwal

---

### Post by agarwaldvk on 2006-02-22
Guys

I need more help on this please!

I have a floppy on which I have downloaded the scanModel.gz and unloading.gz files in the context of getting my winmodem configured with Ubuntu.

I had been trying to copy the file from this floppy disk on to the Desktop on Ubuntu but couldn't.

Can somebody please help me how to copy this file on the Ubuntu Desktop so that I can proceed further?


Best regards



Deepak Agarwal

---

### Post by SavageBeginner on 2006-02-22
First, stop using sudo unless you know what your doing.  Sudo lets you make system wide changes that could break your system.  Be careful with it.

Have you tried clicking on Places -> Computer?  It should show you all of your drives in there.  

If not post what this gives you:  ```
cat /etc/fstab
```

---

### Post by Brunellus on 2006-02-22
1) find out where your floppy mounts.  in all probability, you want to do something like

sudo mount /dev/fd0 /media/floppy

then 

cp /media/floppy/rest/of/path/to/file /path/to/destination

remember that all the DOS and Windows drive names are irrelevant to Linux, which uses a totally different filesystem.

---

### Post by agarwaldvk on 2006-02-22
Thanks Guys for your help!

SavageBeginner
I did see 3 entries on the Places -> Computer :-
Floppy
CDRom
FileSystem

With a CD inserted, it did bring up the directory contents of the CDRom when I clicked on the 'Browse' button.

Nothing happened when I clicked on the 'Browse' button when either of the other 2 entries selected. The floppy disk was already in with the 2 files on it. This is for your information only!

I will do as you have suggested when I get home tonight and report back.


Brunellus
I will do that as well once I get home tonight. For my information what does the bold bit do in your statement below (that was something that I wan't doing).

> sudo mount **/dev/fd0** /media/floppy


Thanks once again for bearing with my ignorance and for your continued assistance. The same is greatly appreciated and highly valued.


Best regards


Deepak Agarwal

---

### Post by agarwaldvk on 2006-02-23
SavageBeginner/Brunellus

This is the feedback after I tried to do what you all had suggested.

On running cat /etc/fstab, the output was like so :-

proc            /proc            proc       defaults                                 0      0
/dev/hdb1    /                  ext3       defaults, error =remount ro        0      1
/dev/hdb5    none             swap      sw                                        0      0
/dev/hdd     /media/cdrom  udf, iso9660 ro, user no auto                  0      1
/dev/fd0     /floppy0          auto, rw user no auto                            0      1


On running sudo mount /dev/fd0 /media/floppy, it asked for the filesystem and I did not know what to specify for the filesystem.

I hope this helps. I couldn't print or save the output from the terminal to the disk - for I do not yet know how to do so.

Can anyone of you help further, please?


Best regards



Deepak Agarwal

---

### Post by dvarsam on 2006-02-23
Try this:

sudo -i

Type your password &

mount -t vfat /dev/fd0 /media/floppy0

Go in the directory /media/floppy0 to access your floppy or it might appear on the desktop.

OR:

go visit: [http://www.linux.org/lessons/beginner/l13/lesson13c.html](http://www.linux.org/lessons/beginner/l13/lesson13c.html)

Hope I helped

---

### Post by agarwaldvk on 2006-02-23
Dear dvarsam

Thank you very much for your help!

I shall try that at home tonight and see how I go.

Further, very grateful for pointing me to the linux file system link - I am sure it will do me a whole lot of good.


Best regards


Deepak Agarwal

---

### Post by agarwaldvk on 2006-02-23
dvarsam

what does sudo -i do? Just for information - can't wait to get home to test for myself!


Best regards


Deepak Agarwal

---

