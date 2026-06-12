---
title: "Internet Problems"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2006-10-01
So my Ubuntu box has, for a while, worked fine on the internet, no problem. All of a sudden one day, it stopped working, unannounced. I didn't change any settings or anything like that, it just...stopped. I will note that a) I am able to connect to my router, b) the other computers (all Windows) on my network, connected to the same router, are able to get online, and c) in the upper right hand corner of GNOME, there's an icon telling me that I have no internet connection, and when I click on it I just get a dropdown box that tells me that "No network devices have been found." Somehow, it must have lost these devices, because it used to work just fine.

---

### Post by uk_sphinx on 2006-10-01
try installing your ethernet adapter driver.
thats if thats what type of network card you have.
give that ago.
also i used to have a program called broadband medic for windows.
see if you can find it for linux or somthing similer.

---

### Post by chimerical_brio on 2006-10-01
As it happens, I don't really know what my ethernet card is. That is, until, I looked it up in the device manager, and here's what I got: SiS900 PCI Fast Ethernet. I'm not entirely sure what that means, and I'm not sure how to proceed, but I'll poke around the internet and see what I can find. Which isn't to say I don't need help anymore.

---

### Post by uk_sphinx on 2006-10-01
that is the make or type of card you got.
every piece of hardware on a system needs software to "drive" it and tell it how to respond with other hardware etc.
im just guessing you need to download a linux one.
coz u said the o.s said yours aint been found.
can u do a hardware search in linux???
im new myself.
is there a device manager in linux??

---

### Post by chimerical_brio on 2006-10-01
Alright, so I found a .tar.gz file with, evidently, everything I need to install the driver for my card. Here's what the readme that was in the driver file (which also contains "sis900.c" and "sis900.h") says:

""make modules" fails on Redhat 8.0.It is kernel 2.4.18-14 , and it need driver 1.08.06.
You can individually compile the sis900.o with below procedures: 
a.Symbolic Links "asm" and "linux" to "/usr/src/linux-2.4.18-14/include/." 
a.1.Go to /usr/include directory 
a.2.mv asm asm_ ( or rm asm) 
a.3.mv linux linux_ (or rm linux) 
a.4.ln -s /usr/src/linux-2.4.18-14/include/asm asm 
a.5.ln -s /usr/src/linux-2.4.18-14/include/linux linux 
b.Create new directory and copy sis900.c and sis900.o into them. 
b.1 mkdir tmp 
b.2 cp -f sis900.c /tmp/sis900.c 
b.3 cp -f sis900.h /tmp/sis900.h 
b.4 cd /tmp 
b.5 gcc -DMODULE -D__KERNEL__ -Wall -Wstrict-prototypes -o6 -c -sis900.c 
c.Copy and replace sis900.o into "/lib/modules/2.4.18-14/kernel/drivers/net/." 
c.1 cp -f sis900.o /lib/modules/2.4.18-14/kernel/drivers/net/sis900.o"

What does this mean? Should i just follow these instructions in the terminal? Do you think that this driver will even work?

---

### Post by guysmiley25 on 2006-10-07
If I where you I would try booting to a live CD and see if it works before installing any drivers. Like you said it was working before. I't might have been a upgrade or a config? Does you router have DHCP. Maybe your not getting the right IP. Can you ping other host by ip. It could be your dns settings.

---

### Post by chimerical_brio on 2006-10-07
Unfortuanetly, I can't use a Live CD on the computer with Ubuntu on it (I'm not sure why, but using it was the first thing that I thought of). The DNS servers are the same in Ubuntu as on my Windows computer that successfully accesses the internet. I'm purposely using static IPs with my router so that I can use BitTorrent. And still no connectivity...

---

### Post by chimerical_brio on 2006-10-07
Alright, so I had a breakthrough. I changed the default gateway device (or something like that) to "eth0", and restarted. And there in the upper-right hand corner, next to the connections boxes that still told me that there was no connection, was the "Updates are Ready to be Downloaded" icon. And when I told it to update, it downloaded all the updates, then restarted, and all of a sudden the internet worked. But the icon still says there's "No network connectivity," any ideas what that's all about?

---

