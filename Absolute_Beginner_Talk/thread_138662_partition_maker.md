---
title: "partition maker"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by yatesDELTA on 2006-03-02
okay then i am having partition problems. i formatted my HDD and there are no longer any partitions on it and i need to get them back. Do i need to download a maker or can i do it some other way

---

### Post by Pragmatist on 2006-03-02
> i need to get them back  Back to what?  Does this drive have any OS on it, or any data at all?  If not, you should just be able to install Ubuntu using the install cd and it will help with the partitioning.

---

### Post by yatesDELTA on 2006-03-02
sorry but im completely clueless about partitioning

---

### Post by Pragmatist on 2006-03-02
To help, we need more info:

1.) Is this hard drive the only hard drive on the computer?
2.) How did you format the drive (you said you formatted it)?

---

### Post by yatesDELTA on 2006-03-02
the hardrive is not, i am using it as a linux only when its ready. the other has xp

i set it up as a slave drive and formatted it like htis in dos:

d:
format

that was the exact commands

---

### Post by Cousindaddy on 2006-03-02
I don't know much, but I do know that if I type *d: format* I will erase everything that's on the drive.  If this is what you did then you have one large single-partition drive with nothing on it.

---

### Post by yatesDELTA on 2006-03-02
then howdo i make more?

---

### Post by yatesDELTA on 2006-03-02
is it a maker like i said?
i downloaded one but its a trial and wont work since it wont let me partition as its trial

---

### Post by Cousindaddy on 2006-03-02
If you're running Windows XP, go into your disk management section.  You can do all of your partitioning from there.

---

### Post by Pragmatist on 2006-03-02
Try going into the BIOS and set the boot order to boot the slave drive before the master.  If you haven't gone into your BIOS before, it isn't hard. As the machine is booting look for a message to get into setup or BIOS or something similar. Usually you press a key like DEL or F2   When in the BIOS look through the different choices until you get to boot order. Then, set the boot order to boot first:
1.floppy
2.cdrom
3. slave drive (formatted)
4. master drive (XP)
5. whatever else you have.

As long as you set the cdrom before everything else you are ok. I put the floppy drive first, since sometimes you might need to boot a boot floppy to recover a system, or whatever.  It won't matter, it won't see anything in the floppy drive, so it will then check the cdrom drive and so on.  After changing the BIOS, put in the Ubuntu install CD and reboot.

Let us know if that works.

---

### Post by yatesDELTA on 2006-03-02
okay then, thanks. ill try it. i hope this works

---

