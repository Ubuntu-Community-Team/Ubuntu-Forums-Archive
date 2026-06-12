---
title: "usb with weird files"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by esva on 2008-01-12
I just plugged my usb stick and I'm seeing tons of weird files that I never saw before like autorun.exe, autirun.bin.inf, whatever.vir, etc etc
can i delete all this junk or there are like some files that are important and would cause the stick not to work?

---

### Post by lluisanunez on 2008-01-12
Those are windows files

---

### Post by esva on 2008-01-12
should I delete them?

---

### Post by Het Irv on 2008-01-12
Does your Jump drive have a program that starts when you plug in the jump drive?  If so these are probably the files for that program.  It is up to you to delete them or not.  If you do delete them you might want to make a copy of them just in case.

---

### Post by lluisanunez on 2008-01-12
It depends, what do you use your usb stick for, and with what OSs? You don't need them to use the drive with linux, though

---

### Post by DarkN00b on 2008-01-12
I have a Sandisk Cruzer U3 Micro that does this. It actually has two internal memory areas. Windows XP and Ubuntu can't see one of them -- Windows 2000 sees a 2GB flash drive and a CDdrive on the same device.

Plug your device into a windows machine and you'll get an interface of some kind to interact with it. 

You can delete the files in Linux, but they'll be back the next time you plug this thing into a Windows machine.

---

### Post by esva on 2008-01-12
is that i suspected they might be viruses or something since sometimes in windows it did weird things happen, but here nothing happened, I asume cause it's linux.
The usb thingie did came with a  cd but when i plug it in things no program interface opens, it's just liek a diskette or something.
thanks , i think I will erase them >:]

---

### Post by DarkN00b on 2008-01-12
That won't hurt a thing. Just keep in mind that they _will_ reappear the next time you stick it in a Windows machine. Think of them as being on a hidden and undeletable partition. Windows will see them and run them when you plug it in. The files will be copied back onto the main "partition" at that time.

---

### Post by eolson on 2008-01-12
You might want to keep the .inf files just in case you might want one of the drivers handy in the future.

---

### Post by DarkN00b on 2008-03-23
Here's a late update: You can get a Windows program provided by sandisk to remove the hidden partition and the files it contains [here]("http://www.sandisk.com/Retail/Default.aspx?CatID=1415"). I have used the removal tool and can verify that it works.

---

