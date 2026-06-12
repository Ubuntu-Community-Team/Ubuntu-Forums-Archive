---
title: "2 physical hard drives"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Rory from the Rock on 2006-08-05
Hello Everyone,

I received my Ubuntu cd's in the mail last week and I have been reading through wiki and about a million searches through the forums and I think that I am going to try installing Ubuntu on Monday,Aug 7.

My system is a P3 800mhz, 512ram, 40 gig hard drive and a 80 gig hard drive.

I have windows 98 on a 40 gig hard drive, and currently red hat on a 80 gig( someone else installed ).
With the research that I have done and with booting up the live cd I do not think that Ubuntu will auto install drivers for my HSP56 V92 micromodem(I don't have the chipset yet...), or for my Canon s820 printer.

Will the 40 gig hard drive be safe if I just try the install on the 80 gig disk?

Thanks.

---

### Post by Blondie on 2006-08-05
Yes.

---

### Post by confused57 on 2006-08-05
Since you have 2 hard drives and you're worried about your Windows install, you might want to read this thread for an option:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

If you installed Ubuntu, using the Live CD, onto the slave drive(hdb); grub would automatically be installed onto your Windows mbr on the master drive(hda).

---

### Post by suicidalsam on 2006-08-05
ya ....just dont reformat the other drives when installin ubuntu

u will be just fine

---

### Post by Rory from the Rock on 2006-08-05
Thanks confused57,

I currently have the boot sequence set up for to boot off cd rom first, then the 40 gig(windows) hd, then the 80 gig(red hat)hd.

I was just going to install ubuntu on the 80gig, and just change the boot sequence in bios as needed.  

Now I will not be doing that thanks to your advice.
I like the idea of having different OS options listed during boot a lot better than having to mess with bios every time I want to switch.

Rory.

---

