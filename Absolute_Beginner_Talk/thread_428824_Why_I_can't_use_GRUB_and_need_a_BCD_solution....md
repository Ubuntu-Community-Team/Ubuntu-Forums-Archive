---
title: "Why I can't use GRUB and need a BCD solution..."
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-04-30
I have recently really taken to Ubuntu, so I decided to drop the LiveCD act and just dualboot Vista and Ubuntu. I initially tried to do this with GRUB. However, something was amiss.

Vista, if not the BOOT partition, will not hibernate. As soon as I change the flags to make my Vista partition the boot one, everything works great. Thing is, I use hibernate a LOT, so I really need a way to do this.

I tried EasyBCD, but when I choose Ubuntu, I get a File missing: /NST/mst_grub.mbr everytime, even though GRUB is installed to my Ubuntu partition header. nothing works, and all links to an EasyBCD patcher that include this file are down.

/NST/mst_grub.mbr is all I need.  Can this be found *anywhere*?

Any ideas guys? I am at my wits end...

---

### Post by GrueTamer on 2007-04-30
Try installing Grub to a floppy, there are instructions [here]("http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html").  That way, vista can overwrite the mbr all it wants and ubuntu is fine.  Another option that may work is the [super grub disk]("http://supergrub.forjamari.linex.org/").  I hope you get your problem worked out! :)

Sorry I couldn't help with what you specifically asked for, but I couldn't find it myself, so I just offered a slightly different solution.

---

### Post by gohanssjn on 2007-04-30
That would work...but unfortunately, no floppy drive on the laptop :(

Anyone else?

---

### Post by GrueTamer on 2007-04-30
> **gohanssjn said:**
> That would work...but unfortunately, no floppy drive on the laptop :(

Anyone else?The super grub disk is for cd.  It took me awhile to find it, but I managed to do it eventually.  EDIT: this was because I couldn't boot into linux at the time, but the same thing might apply to you, thanks to vista, so I'm looking for the cd I got as of now, will post back when I get it.

---

### Post by gohanssjn on 2007-04-30
Well, I have it installed burned, but thats a lot to go through each time I boot.

---

### Post by GrueTamer on 2007-04-30
> **gohanssjn said:**
> Well, I have it installed burned, but thats a lot to go through each time I boot.

Well, you're right about that.  Perhaps if you have another hard drive, or a usb flash drive, you could put grub on that, with your menu.lst file and everything.  There's a lot of things you could try, but not having a floppy drive takes away the suggestion I would normally recommend the most.

---

### Post by gohanssjn on 2007-04-30
Guess I give up.  There is no way I can find to make the Vista Bootloader see GRUB, or for Vista to Hibernate without a 'BOOT' flag on the partition.  Noone here or on Vista forums seems to know. 

 I can't believe noone else has experienced this issue though.  Just can't believe it :(

---

### Post by GrueTamer on 2007-04-30
> **gohanssjn said:**
> Guess I give up.  There is no way I can find to make the Vista Bootloader see GRUB, or for Vista to Hibernate without a 'BOOT' flag on the partition.  Noone here or on Vista forums seems to know. 

 I can't believe noone else has experienced this issue though.  Just can't believe it :(I hope you're not giving up on ubuntu altogether because of this.  Going through that grub disk process every time you boot is well worth it, especially since you can leave your computer on longer than in windows :)

I'm still looking for a solution, actually, so don't give up hope just yet!

---

### Post by gohanssjn on 2007-04-30
I'm not giving up on Ubuntu yet, but I'll have too when school starts if I can't hibernate Vista, I have to pull up the computer quickly for classes and such.  

Thanks for the help!

---

### Post by gohanssjn on 2007-04-30
Interesting.  If I remove the 'BOOT' flag in GParted, all of a sudden the Vista partition is unreadable by GParted.  Replace the flag, and it sees it again.  Weird Vista partition, very weird.

---

### Post by Computer Guru on 2007-05-09
gohanssjn, try out [EasyBCD 1.6]("http://neosmart.net/dl.php?id=1"), it should fix your problem.
First, delete all pre-existing Linux entries in EasyBCD from Vista, then proceed to add the Ubuntu partition from there with version 1.6.

---

