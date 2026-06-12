---
title: "Installing on Windows 98"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Supavillain on 2006-08-17
Im not sure if you can or not but it seems to not be working for me..I start up my computer with the disk in and it automaticlly goes to my desktop..any ideas?
thanks

---

### Post by Greycloak on 2006-08-17
Check your BIOS options and make sure that the boot order has CD-ROM listed before the hard drive.

---

### Post by Supavillain on 2006-08-17
and how do I do that? lol

---

### Post by goatmale on 2006-08-17
To check your BIOS settings try jamming on the f1-f12 (except f8 cause that goes to safe mode) keys while your computer is booting up.
Your computer might not be able to boot off a cd.

---

### Post by goatflyer on 2006-08-17
Check your boot order in the bios.  You want CD-ROM, then C: then A:

If your machine does not have the option to boot from CD, but does have a floppy drive, you can download SmartBootManager and create a floppy with it on it.

(homepage is here if you want to read up on it first)
[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

--- EDIT ---

You didn;t say how big your machine was, but if its an old Win98 machine, you might want Xubuntu instead.  Use the alternate cd (not the desktop cd).

---

### Post by Supavillain on 2006-08-17
Im in it, what do I do in it? I have "Main" "Advanced" etc what do I change ?

---

### Post by Supavillain on 2006-08-17
wait kay im where I think I have to be..what do I change first boot device to?

---

### Post by Supavillain on 2006-08-17
alright I dont have anything that sais "C drive" I have something that sais "1st IDE-HDD" is that it?

---

### Post by goatflyer on 2006-08-17
1st IDE sounds like your C drive.  You want to try some other device, keep drive C last.  Look for a parameter called Boot Order.

---

### Post by Supavillain on 2006-08-17
ok so I have it "CD rom" "1st IDE-HDD" and then "floppy"

is that how its supposed to be?

---

### Post by Supavillain on 2006-08-17
nevermind I just tried it and it works

thanks for the help

---

### Post by goatflyer on 2006-08-17
If you want to one day boot from floppy, I'd pick CDROM, floppy, then drive C.  But then your machine will always make a floppy noise (checking for disk) everytime you boot.  Its your choice.

btw - This machine -- how much ram? what speed?

---

### Post by crane on 2006-08-17
> **Supavillain said:**
> ok so I have it "CD rom" "1st IDE-HDD" and then "floppy"

is that how its supposed to be?

That should work. If ou can try to make it CD, Floppy, then Hard drive.
That way if you ever need to boot from floppy. you can.

---

