---
title: "installation interrupted-help!"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by tugh on 2007-05-22
I was upgrading from 6.10 to 7.04 and suddenly power went off. It was going through some Firefox updates when this happened, I guess towards the end of the installation. When I restart it, it can't load, saying "/bin/sh: can't access tty: job control turned off(initranfs)" ](*,)

I guess, I can start installing again, but then it asks me for partitioning etc. My question is: Is there a way to fix this without losing the files on my harddrive?

Thank you. :(

---

### Post by n8bounds on 2007-05-22
ouch

you can back up the files on your harddrive to somewhere else (usb disk?) from the live cd, you just have to mount your old partition first, open a terminal and say

sudo fdisk -l

whatever device it lists as your old drive (like, say, /dev/sdb1 or whatever) keep that in mind as you tailor the following steps

sudo mkdir /media/olddrive

sudo mount /dev/sdb1 /media/olddrive

sudo chmod 777 /media/olddrive -R

then you should be able to browse your old drive with nautilus and copy them to somewhere else

good luck (and consider a UPS battery)

---

### Post by tugh on 2007-05-22
Hi,

Thanks a lot for the suggestion. I don't know much about unix and the file structures yet, though. Where can I locate my external hard drive once I get to the terminal and run those commands?

Thank you, again.:D

---

### Post by n8bounds on 2007-05-22
there may be some gui for this, but I dont know

sudo fdisk -l

will list all the block devices (disks, jump drives, whatnot) the kernel is aware of, mounted or no

df -HT 

will show you everything you have mounted (possibly less than the above command) and some interresting things about them

mount

that command with no args shows everything that is mounted also, but a little uglier

if your fdisk command said you have, say, a usb drive called /dev/sdb1 but it doesnt show as mounted when you run a df, you can do something like this

sudo mkdir /media/myawesomeusbDrive

sudo mount /dev/sdb1  /media/myawesomeusbDrive

assuming its not ntfs, you should be good

you might need to 

sudo chmod 777 /media/myawesomeusbDrive -R

to give your regular user proper privelages to write/read to your drive

or maybe instead of that say

sudo chown tugh:tugh  /media/myawesomeusbDrive -R

...or whatever your linux username (tugh) is

have fun, *nix rocks

---

### Post by tugh on 2007-05-23
It worked!!! :D Awesome, man you're a life saver. I could never do that by myself.

Thanks a lot!!!

---

### Post by n8bounds on 2007-05-24
:) You are most welcome, glad I could help.  We all knew nothing about this at one point; if you keep using linux, you will learn so much so quickly you'll wonder what you've been doing with your computer all those years before you started..

If I can help with anything else, feel free to PM/IM me any time.

---

