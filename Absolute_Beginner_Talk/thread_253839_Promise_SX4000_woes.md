---
title: "Promise SX4000 woes"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Huzudra on 2006-09-08
So, i have a promise SX4000 with 64mb of non ecc ram in it.  i want to use it for a storage array eventually but as it stands now its empty.  heres why....

when i plug a drive into it, either drive in the box, it locks at a screen showing the card info, the drives attached, the bios screen for it, normal sx4000 stuff.  then theres a pause (where i'd normally see my CMD IDE controller bios flash up and then proceded to boot to ubuntu) and i see on the screen...

PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP 0MB

with the cursor just blinking and they keyboard locked.  the system shuts right off when i press the power button.  if i unplug the drive from the card then it boots normally, but i'd like to using the sx4000 when i do get more drives for an array and because its ata133, the cmd is ata100 and onboard is ata66.  btw the system is an amd athlon 700 (slotA) 224mb of pc100/125/133, 8mb agp2x tnt card, sx4000, cmd ide 649U and a gateway jabil kadoka R5 motherboard.  

i would apreciate some help with this, i have alot of other questions since this is my first time using linux, but i can rely on a friend to answer most of those when possible.

---

### Post by Huzudra on 2006-09-09
anyone have any thoughts, ideas, or solutions (other than not using the card)?

---

### Post by Huzudra on 2006-09-11
bump?  someone said something about me needing a custom install due to something with the mbr?

---

### Post by Huzudra on 2006-09-13
now that someone claims my motherboard doesnt support add in cards, but that cant be...the CMD IDE controller works flawlessly!  he said i should make post here or look here.  i searched around but i didnt find anything like my problem so i made this thread, can anyone here help me?!?

---

### Post by Huzudra on 2006-09-13
now that someone claims my motherboard doesnt support add in cards, but that cant be...the CMD IDE controller works flawlessly!  he said i should make post here or look here.  i searched around but i didnt find anything like my problem so i made this thread, can anyone here help me?!?

---

### Post by trhermes on 2006-10-18
Did anyone get the sx4000 to work in Ubuntu?  I am waiting for a successful report before I purchase three more 250gb drives.

---

### Post by mesh on 2007-02-03
Yo man, did you ever get your sx4000 to work? I have one with 4 500gb drives in it. Currently i have windows xp and i have the operating system on a seperate 10k raptor drive. I want to install ubuntu or another linux/unix flavor being that Ubuntu is rather friendly i though i would start with that. Anyway, let me know if you got this to work successfully. Thanks.

---

### Post by myrrd on 2007-02-27
I haven't managed to get mine functional, but I did find something interesting:

there are drivers available for Red Hat, Suse, Solaris, Caldera, Turbo(?) and Novell(thought that was Suse?) but no Debian or Ubuntu specific drivers, all on the Promise support site.

To those out there reading this thread and have the ability and inclination to assist us, I should point out that as far as my Ubuntu install is concerned, the PCI slot this card is in is empty- I don't even get 'unrecognized device'.

This is in a system I just got handed to me free (yay!) but had XP on it, and this might have been why. I don't see why anyone would run XP on a dual-Xeon server, unless they wanted a really loud desktop box.

---

### Post by gianluigi.zanettini on 2007-05-14
Hi all,
same problem here. AFAIK, Promise didn't release the full driver sources, but just some parts of it. All the Linux driver for this board where relased precompiled only, for Redhat and SuSE only.

So, at least for the moment, we can't use this RAID adapter with Ubuntu at all.

---

### Post by ARhere on 2007-11-05
> **myrrd said:**
> ... I should point out that as far as my Ubuntu install is concerned, the PCI slot this card is in is empty- I don't even get 'unrecognized device'.

I am in the process of moving my file/print server from windows to Linux and I use an [SX4000]("http://www.promise.com/product/product_detail_eng.asp?segment=RAID%20HBAs&product_id=94") as well for RAID5.  I booted using a Live CD just to see how much work would be involved in the switch.  An "lspci" does list the SX4000 card but no drivers were found during the Live boot.

I am speaking out of ignorance here, but I see no reason why the [Red Hat driver]("http://www.promise.com/support/download/download2_eng.asp?productId=111&category=driver&os=3&go=GO") would not work on Ubuntu as the differences should just be file location.  I hope a more experienced Linux guy will set me straight.

I have no idea why the drivers have to be packed in a floppy image but I will unpack it and try to test them on a FC6 first, then mimic the install on my Ubuntu machine.  Wish me luck or give me advice!

Also, I saw a link either here or on ./ that was stating there were too few driver projects to keep the many Linux developers busy, maybe this is a good candidate!

---

### Post by ARhere on 2007-11-05
I am going to repost this outside of the "Absolute Beginners" section as this is an old thread and would be best served in the Networking section.:popcorn:

---

### Post by Huzudra on 2008-01-12
I had totally forgotten about this thread.  I have not put much time towards this issue, but i am getting back into linux as of late and i would like to get the card to work with my 6.06 Xubuntu install that serves files to my windows box (i ran out of room in the case for drives).  good to know someone is still working on this and that others have the same issue...well bad that others have the issue.  you know what i mean!

---

