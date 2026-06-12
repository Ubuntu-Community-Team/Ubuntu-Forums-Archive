---
title: "My floppy doesn't work!"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2006-03-24
I wanted to save a document from OpenOffice Writer to floppy, but no option to save there came up. Under System > Admin > Disks, the floppy's on the storage list but nothing happens when i click on it. But it formatted 2 disks for me! My computer isnt online and my cd's read-only, so the floppy's my only way to get files out. It formats... so how can i make it work?

---

### Post by gr0kzer0 on 2006-03-24
Oh, if it's of any use: in Rythmbox i just selected Import Folder and it showed the floppy drive as a possible source. So i clicked on Floppy Drive and got "Unable to mount the selected volume. Error: given UDI is not a mountable volume". This is the same msg i got when i put a CD-RW in my CD-ROM drive. But i just formatted these floppies using this drive so they must be compatible!

---

### Post by IYY on 2006-03-24
Try typing this in the terminal:

> mount /dev/fd0

What does it say?

---

### Post by gr0kzer0 on 2006-03-24
Hi IYY. When i type  "mount /dev/fd0" it replies "I could not determine the filesystem type, and none was specified". I also saw the reply to the other post, referring to a HOWTO. But that involves internet access. I'd have to go to the library, download to cd on a windows box, and then dl from the cd. Could s'one explain how? what file to dl, how to transfer it from cd, etc? (i'm a helpless n00b)

---

### Post by gr0kzer0 on 2006-03-24
Well... I typed in "sudo modprobe floppy" like ferri said at the end of the HOWTO thread (which is linked to in the other thread in this forum about floppies). Then i ejected a disk, put it back in, typed "mount /dev/fd0" - and crunch, clack, its mounted! Kewl!  So thanks, everyone!

---

### Post by gr0kzer0 on 2006-03-24
Aagh!! Spoke too soon! The floppy may be physically mounted but i cant write to it (not with the gui anyway - i dont know the command, is it "cp file /dev/fd0/file"?) so i still need help. Anyone?

---

### Post by ace2005 on 2006-03-24
Can you post your /etc/fstab please, it contains information on all the drives on your system that have so far been recognised

There should be a line similar to this:

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

So if the device is already mounted all you have to do is go to  /media/floppy0 and save there, and unmount (i think you have to unmount before any changes are made to the disk, thats what happens to my usb stick)

---

### Post by IYY on 2006-03-24
[QUOTE=gr0kzer0]Aagh!! Spoke too soon! The floppy may be physically mounted but i cant write to it (not with the gui anyway - i dont know the command, is it "cp file /dev/fd0/file"?) so i still need help. Anyone?[/QUOTE]

Close, but not quite. **/dev/fd0** is the device, not the location where it is mounted. The actual location is usually /media/floppy. If you want to check the exact location on your system:

**cat /etc/fstab | grep /dev/fd0**

You could also try opening /media/floppy in the file manager and transfer the file  through the GUI.

---

### Post by gr0kzer0 on 2006-03-25
Thanks IYY! I found it, /media/floppy0. I can also save by dragging files from the home directory to the floppy icon on the desktop. It doesnt automount, and i cant save direct to floppy from Open Office, but at least i can use it. Thanks again!

---

### Post by OBnascar on 2006-03-25
[QUOTE=gr0kzer0]I wanted to save a document from OpenOffice Writer to floppy[/QUOTE]

In Breezy 5.10, there always has been a bug using the floppy drive. Dapper has the bug fixed. There are several work-arounds, but look at this one below over, I guess it does work. I do not have a floppy drive anymore, I use mini flash drives, I would never go back to a floppy after using them.

[**[COLOR="DarkOrange"]Here Is The How-To[/COLOR]**]("http://www.ubuntuforums.org/showthread.php?t=104259")

I have never tried it myself, but I have seen where people have with sucess.

---

### Post by gr0kzer0 on 2006-03-27
Thanks for the link OB. Unfortunately - if i read that right - it involves downloading a fix, and i'm having problems with that. I'm not online at home, i use a windows box at the library to download stuff, so i havent got the simplicity of apt to use... i dont think. Maybe i'm wrong, and there is a simple way to manage downloads this way. Anyway, i can wait for an auto-mounting floppy

---

### Post by Sef on 2006-03-27
> if i read that right - it involves downloading a fix

Yes, you read it right.

---

### Post by StefanoCole on 2006-03-28
Hello gr0kzer0, you can download the fix (package pmount) from here, even from a Windows box: [http://packages.ubuntu.com/breezy-backports/utils/pmount]("http://packages.ubuntu.com/breezy-backports/utils/pmount")

You can store the pmount package to a USB memory stick and copy it in your Ubuntu box at home. Then, from the folder where you have stored it you can install with: 
sudo dpkg -i pmount_0.9.6-1~breezy1_i386.deb

Stefano

---

### Post by gr0kzer0 on 2006-03-28
Thanks stefano, i'll try that tomorrow when i can go to the library and use their computers.

---

### Post by Guns90 on 2006-04-23
Now I need help.  I'm using ver. 5.10.  I've read everything I can find on floppies.  What I need is to be able to use Office.Writer, save it in Windows XP format, and save it floppy so my kids can take it into school and use it on a Windows machine.  When I woke up this morning I was able to see my floppy on the Places>Computer screen and format a floppy using App>System Tools>Floppy Formatter.  After trying all the above solutions, I am in worse shape now than I was.  The Computer &#8211; File Browser window shows the floppy as Floppy Drive: floppy0, and I no longer can format on it.  When I attempt to format now, I get an Error window saying 'Error formatting track 0'.  Would appreciate some help.

---

