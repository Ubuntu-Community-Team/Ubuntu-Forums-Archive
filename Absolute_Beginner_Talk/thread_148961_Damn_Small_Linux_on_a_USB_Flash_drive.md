---
title: "Damn Small Linux on a USB Flash drive"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by daacosta on 2006-03-23
Hello,

How do identify the port at which a USB flash drive is connected in Ubuntu?  I am not talking about /media/usb but /dev/tty0 or something like that...

My goal is to install DSL on a flash drive using my Ubuntu at home...

Or, if it is possible to install Ubuntu on a flash drive (2 GB) I would also go for that.  I am very scared of experimenting so before I ruin my nice Ubuntu box I would appreciate step by step instructions...

Thanks!


-D-

---

### Post by LinuxKid on 2006-03-23
you'll need damn small running to get it on your usb drive

currently there is no version of ubuntu that supports usb booting

I have the usb-hdd version of damn small on my thumbdrive, I'll put all the files up (except the main distro file, too big) and you can try to work from there (maybe copying the knoppix file from the iso image into it and it may work) 

tell me if you'd like to go through it

---

### Post by white_tiger_daniel on 2006-03-23
Umm, where can I get Damn Small linux? I want to do some experinmenting.

---

### Post by GreyFox503 on 2006-03-23
Usually, USB flash drives show up as /dev/sda, sdb, etc.  If you have no SATA hard drives, then sda is probably the location of your flash drive.  Also try running:

```
dmesg
``` 

After inserting your flash drive for more info.

The easiest way to get it installed it to burn DSL to a CD and boot into it.  Once you are there, look for the menu options for installing to a flash drive.  It is not too difficult.  There are two kinds of installs, usb-hdd, and usb-zip.  You might have to try both to find one that works.  usb-zip works for me.


As for where to get DSL?  C'mon, you gotta at least try.   :)

[Click here.]("http://www.google.com/search?hl=en&q=Damn+Small+Linux&btnG=Google+Search")

---

### Post by Eklöf on 2006-03-23
I did a server-install to an USB-stick from the flight5 install CD. Worked perfect.

---

### Post by LinuxKid on 2006-03-24
here are the files, if you would like to do some experimenting
[http://download.filegig.com/?filename=../fg_files/8p/DSL.zip](http://download.filegig.com/?filename=../fg_files/8p/DSL.zip)

remeber to unzip and only put the files inside it on the usb drive, plus remember to check inside the "KNOPPIX" folder for a read me file

have fun experimenting!

---

