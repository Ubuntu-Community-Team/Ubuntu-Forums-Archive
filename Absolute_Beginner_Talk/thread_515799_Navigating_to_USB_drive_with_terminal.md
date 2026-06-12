---
title: "Navigating to USB drive with terminal ?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by WIREHEAD on 2007-08-02
Go ahead and call me an idiot .

I can navigate on my internal drive ( using cd ) just fine .

ls shows my USB drive, I can access the USB and it's files fine with the GUI .

I need to figure out how to switch my current directory in terminal to my USB drive to run terminal commands in specific directories on the USB drive .

Using cd won't take me anywhere except my internal drive ?

I hope I have explained this properly .

Thank you in advance !

I am running Dapper if that makes a difference .

Feel free to point out the obvious , and explain things in more detail than normally required ... 

THANKS !

---

### Post by undertakingyou on 2007-08-02
You need to know where the usb drive is mounted.  Lets say it is /media/usbdrive.  You then do ```
cd /media/usbdrive
``` and then you are in the usb drive.  You can then use CD as you would normally.

---

### Post by Hospadar on 2007-08-02
It's probably going to be mounted in /media
so try
```
cd /media
ls
```
This should show which drives are mounted there, if it's a usb flash drive 
it will probably mounted to one of the sda# folder, so check them and see which it's in, then you can cd into and do whatever.

Alternatively, if you can get at it through the GUI, look at the adress bar at the top of the window that shows you where you are, and cd to that location in a terminal.

Hope this helps.

---

### Post by asmoore82 on 2007-08-02
^^ sound advice ^^

:backstory:

it is a LAW of UNIX system that no files may exsist outside of the root filesystem tree thatbegins  with a single '/' even if the files are physically located on other partitions/media.
so, UNIX systems have the ability to **mount** or attach other filesystems to directories
*anywhere* within the root '/' filesystem.

Just to simplify life a little bit it is commonplace to mount all removable media (CD/floppy/USB/DVD)
in one location which is in ...

/media/ on modern desktop Linux systems.
/mnt/ on classic Linux systems
/Volumes/ on Mac OS X (it's UNIX too)

---

### Post by LaRoza on 2007-08-02
Also, remember it is case sensitive.

---

### Post by WIREHEAD on 2007-08-02
The short story:
drwx------ 6 tbf  tbf  4096 1969-12-31 17:00 RUTH'S\ 1G
tbf@SPOTCOMP5:/media$ cd /media/RUTH'S\ 1G
>

This is where the problems start the ">" won't go away , 

I have tried typing, and cut and paste both with the same result , either it's this or " no such file or directory .

A verbose description :
gnome-terminal --working-directory /media/ ........................opens a new window

Scenario #1:
tbf@SPOTCOMP5:/media$ ls
cdrom  cdrom0  DRV4_VOL1  RUTH'S 1G
tbf@SPOTCOMP5:/media$ cd RUTH'S 1G
>
I'm stuck ?

Thanks again !

---

### Post by Raineer on 2007-08-02
No problems...
The carat is showing up because of characters you are typing during the command, just ctrl-c to get out of it.  It doesn't like the apostrophe in the mount name.

```
cd "/media/RUTH'S 1G"
```
will save the day.  Adding the quotes will do it for you. 

Also, you could type cd/media/RU[TAB KEY]  and watch what happens, you'll be impressed :D


Take care.

---

### Post by asmoore82 on 2007-08-02
:KS the TAB key is our **bestest** friend :KS

---

### Post by WIREHEAD on 2007-08-19
THANK YOU !

Very much ...

Again.

---

