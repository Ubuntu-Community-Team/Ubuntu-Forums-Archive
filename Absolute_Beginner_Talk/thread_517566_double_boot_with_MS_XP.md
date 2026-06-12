---
title: "double boot with MS XP"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by m10sang10 on 2007-08-04
Hi:
I have my ubuntu in double boot with MS XP Professional (the letters in bold indicate how the boot is disposed) in a hard drive -“0”- this works perfectly. But I wanted to add another hard drive-“1”- which contained Microsoft XP home, which I added to the grub of disk 0 (described below in red font) Problem is, when I started the grub, seemingly all the OS worked ok. But when I selected XP Home, XP Professional starts up. It is obvious I have made a mistake, so I would ask for your advise on this matter.

 
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

  (this one is the aggregated) 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title                  Microsoft Windows XP Home
root                  (hd1,0)
savedefault
makeactive
chainloader     +1 

thanks in advance

---

### Post by belikralj on 2007-08-04
Are you sure it's slave on channel one and on first partition?

---

### Post by m10sang10 on 2007-08-04
Thanks for  repond;   the HDs are corrects in the Bios (slave(black) and Master(slot red))
I think that this one is the problem,

# on /dev/sda1
but I dont know that  do.

---

### Post by TBerben on 2007-08-04
I think it should be ```
/dev/sdb1
```

At least if that's the name of your second harddrive

---

### Post by m10sang10 on 2007-08-04
I forget said that HDs are Sata 350Gb each

---

### Post by m10sang10 on 2007-08-04
Thanks to every one , I am going to try it.

---

### Post by m10sang10 on 2007-08-04
Nope, the problem continuous , some suggestion ?

---

### Post by belikralj on 2007-08-04
I can see that you have two Windows XP Professional partition entries and one Home one. Are you sure you installed the home edition? Because if the parameters were wrong grub would give you an error. Is there some way you can check what partition your windows is starting on and then see whether you installed the right one? Also changing the /dev/sdb1 in my opinion shouldn't fix anything because that line is commented and does nothing but inform you that the letters hd(0,0) stand for /dev/sda1 (hd(hard disk number, partition number)) in grub and since you just copy-pasted the entry from above those lines don't matter. It seems to me that you did it right and it should be starting the right windows but I may be wrong. Could you check where the Windows that starts under Home in grub is located when started?

---

### Post by belikralj on 2007-08-04
Sorry it's 3am and I'm starting to get a bit rude and cryptic, and I appologise. What I mean is that if you put the wrong numbers nothing would start and grub would tell you that there is nothing there to start. So since it is starting something is there and that something is XP Professional so I just wanted to ask if you were sure you installed the Home Edition on that partition or some other one because on that partition is obviously XP Professional? What happens when you boot the other XP's? And could you have installed XP Professional by mistake instead of the Home Edition?

---

### Post by m10sang10 on 2007-08-04
Oky doky,before I was play each HD separately and they worked very well, now I am going to prove to them.

---

### Post by m10sang10 on 2007-08-04
Each HD (with OS respective) worked very well , now that I join them is the problem.

---

### Post by m10sang10 on 2007-08-04
Now I am writing to you of XP home ,all OK. Some suggestion ?

---

### Post by m10sang10 on 2007-08-04
IF you see two XP pro its because in my HD 0  I have in addition to Ubuntu, 3 partitions more ,1 active, 1 Imagen(backup) ,1for files.

---

### Post by m10sang10 on 2007-08-04
Perhaps , I am not  explaining  well, the problems continue , xp home;ok, xp pro + ubuntu;ok, all for separate, but them joins in the grub, xp home  doesn't  boot.

---

### Post by belikralj on 2007-08-04
And this hard disk with XP Home is the slave on the first SATA Channel and Windows XP Home is on the first partition? If that is the case I really don't know what's going on. I never had multiple Windows installations. But these links may help

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-grub-terminology.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-grub-terminology.html)
[http://en.opensuse.org/SDB:Booting_Multiple_Windows_Installations_from_One_Hard_Disk](http://en.opensuse.org/SDB:Booting_Multiple_Windows_Installations_from_One_Hard_Disk)

I don't know how else to help, sorry...

---

### Post by belikralj on 2007-08-04
Wait I think I may have found an even better explanation try this:

[http://en.opensuse.org/SDB:Booting_Windows_from_the_Second_HD](http://en.opensuse.org/SDB:Booting_Windows_from_the_Second_HD)

hope it works

---

### Post by m10sang10 on 2007-08-04
Yes,apparently all is ok, thanks a lot . the important thing   its the intention. last ask , how can i find this question for example tomorrow?

---

### Post by m10sang10 on 2007-08-04
Excellent!! I am  going to try it (in the morning ) thanks  ,I will write my experience.

---

