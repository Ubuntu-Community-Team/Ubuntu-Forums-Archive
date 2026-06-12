---
title: "Can I install Ubuntu this way??"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by gotnoidea on 2008-02-17
I really want to learn Linux. This will be my second attempt; my first was an utter disaster. I was trying to load another version of Linux to a HDD via USB port and almost lost my main HDD OS. 2 very long days later I got my system back, so I went to the book store and bought all 4 books on Ubuntu and the desktop CD.  This is what I want to do.  Can I install Ubuntu onto a HDD on another computer, take that HDD and put it into my external HDD case and load via USB. Furthermore, will this version work with my system- using Ubuntu 6.06 LTS desktop CD I have a quad core AMD CPU, 2 gig RAM, and 200 gig SATA HDD with a LCD monitor, and a cheep GeForce8400 GS video card. I know I am putting a lot of information here but if this will work I am sure someone will let me know of extra drivers I may need. By the way, I know I will probably have to load this drive through bios since I will not be loading on this system, if it will work at all

---

### Post by sandysandy on 2008-02-17
a better option may be to connect ur second hdd to ur computer (and not another computer), disconnect ur first hdd, and load ubuntu on the secod hdd. that way u can be sure that grub loads on the ubuntu hdd and ur first hdd is not touched. 

i have loaded ubuntu countless times on one hdd with another OS co-existing with no problem. Now that u have a CD u may like to try this also.

---

### Post by Shazaam on 2008-02-17
This is what I did to get Linux on an old laptop with no cd/rom drive.
Bought a usb hard drive enclosure and put the laptop hard drive in it. Disconnected ALL hard drives in the main pc. Connected enclosure to main pc. Started main pc with livecd in drive, when booted to livecd desktop installed linux to said usb drive.
BTW, what was the original installation problem?

---

### Post by gotnoidea on 2008-02-17
""
a better option may be to connect ur second hdd to ur computer (and not another computer), disconnect ur first hdd, and load ubuntu on the secod hdd. that way u can be sure that grub loads on the ubuntu hdd and ur first hdd is not touched. ""




I understand your reasoning for this, however I cannot install on this computer without buying another HDD as it is all SATA and I have several ATA drives just lying around, not to mention this system is still under warranty and I haven&#8217;t finished my CompTIA A+ certification so if I open it I void it. I have a few systems I put together I can use for the install I am just scared to death of trying to install this through the USB again. But I am here because I need someone that knows what they are talking about and that surely isn&#8217;t me&#8230;

---

### Post by Presto123 on 2008-02-17
> **gotnoidea said:**
> I really want to learn Linux. This will be my second attempt; my first was an utter disaster. I was trying to load another version of Linux to a HDD via USB port and almost lost my main HDD OS. 2 very long days later I got my system back, so I went to the book store and bought all 4 books on Ubuntu and the desktop CD.  This is what I want to do.  Can I install Ubuntu onto a HDD on another computer, take that HDD and put it into my external HDD case and load via USB. Furthermore, will this version work with my system- using Ubuntu 6.06 LTS desktop CD I have a quad core AMD CPU, 2 gig RAM, and 200 gig SATA HDD with a LCD monitor, and a cheep GeForce8400 GS video card. I know I am putting a lot of information here but if this will work I am sure someone will let me know of extra drivers I may need. By the way, I know I will probably have to load this drive through bios since I will not be loading on this system, if it will work at all

There are ways to get Linux onto USB flash drives. :) 

I actually would suggest trying Puppy Linux on USB flash drive since it is small and an interesting intro to Linux. You can also get Ubu on one as well, but you will need a bigger flash drive for it.

FYI: this is only a suggestion.

---

### Post by Presto123 on 2008-02-17
You can also utilize a Gparted disk and partition part of your USB HD, say 20 gigs and go at it that way. But, remember, you REALLY need to back everything up BEFORE.

---

### Post by kmir on 2008-02-17
Do you want to install or load through USB? If I understood you correctly, you want to install Ubuntu onto a HDD (IDE?), normally connected to some computer and then take that HDD out, connect it to your main computer via USB and then boot? If this is what you want to do, I have done it before and it worked fine (installed using an eMachines computer and booted on a Dell laptop).

---

### Post by gotnoidea on 2008-02-17
> **kmir said:**
> Do you want to install or load through USB? If I understood you correctly, you want to install Ubuntu onto a HDD (IDE?), normally connected to some computer and then take that HDD out, connect it to your main computer via USB and then boot? If this is what you want to do, I have done it before and it worked fine (installed using an eMachines computer and booted on a Dell laptop).

Correct a 120gig ATA drive in drive case via USB

---

### Post by kmir on 2008-02-17
Well, if that drive that you want to install it on does not contain any important data, it should be pretty easy. If it is connected via the IDE port, all you need to do is boot from the CD, choose to install, follow the guide and select something like "entire section" when you are asked where you want to install. I once tried to install Ubuntu on a part of a hard drive with important stuff in other areas and - I did not do so well (that might be because of my lack of expertise, though). But if you want to do it as described, it should be pretty straightforward. When I booted from USB, it just simply worked with the first attempt. Good luck!

---

### Post by sandysandy on 2008-02-17
here's a nice link to dual booting. 

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

---

### Post by gotnoidea on 2008-02-17
> **kmir said:**
>  I did not do so well (that might be because of my lack of expertise, though). But if you want to do it as described, it should be pretty straightforward. When I booted from USB, it just simply worked with the first attempt. Good luck!

That is the situation I am trying to avoid again. Last time was a complete mess. Thank you I will post if it works. Loading it to the other HDD now in another computer. I just hope I can find all the drivers when I bring it to this computer.

---

### Post by Presto123 on 2008-02-17
> **gotnoidea said:**
> That is the situation I am trying to avoid again. Last time was a complete mess. Thank you I will post if it works. Loading it to the other HDD now in another computer. I just hope I can find all the drivers when I bring it to this computer.

I wish you luck on this, but I'm afraid you will run into some hardware issues as with any OS I know, it loads the drivers necessary for THAT computer. Then again, I did change a lot of hardware on my computer and it recognized it quite easily.

---

### Post by gotnoidea on 2008-02-17
you give me hope...

---

### Post by Presto123 on 2008-02-17
Sorry...I just don't want you to go into this blindly.

---

### Post by gotnoidea on 2008-02-17
haha don't be nothing could be worse whan what has already happened

---

### Post by jpates20 on 2008-02-17
my I suggest ,buying some old computer off ebay,that way if you mess up something ,no big deal!
I bought a dell power edge raid server for $60 and install 6.06 LTS desktop everything works great! I'm also new to this............John

---

### Post by kmir on 2008-02-18
And, did it work?

I agree with the other user, btw. It is a good idea to buy a separate computer whose technology is not the very newest. The more straightforward and "normal/mainstream" your system and what you want to do with it is, the more likely is it that things are going to work. Any complexities (64 bit, wireless, etc.) are going to make the learning curve steeper in the beginning.

---

### Post by louieb on 2008-02-18
Its just a little different install method to  put Linux on an external drive.

1st thing you need to make sure your PC can boot to an external drive. If it  can - its time for the install. So plug the external in and boot the install CD.

2nd thing you need to know is what Linux has named your external drive. Windows name partitions / drives:  c:, d:, e: ... Linux uses names like sda, sdb ... for hard-drives. And names like sda1, sda2 for partitions on the drive. On the Live install CD you can go to System>Administration>Partition Editor to get this information. 

There are 2 places you need the drive name. The 1st is in the partition step hopefully the external drive will be listed as an install to option - use it.
The 2nd is to tell it where to put GRUB. Just before the install begins you will see an **Advanced** button. Click it and tell it to install GRUB in the external drive in your case it will probably be /dev/sdb. 

After the install you should be able to use BIOS to boot whatever on the internal drive or Ubuntu on the external. Good Luck.

---

