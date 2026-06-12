---
title: "Setting up Wireless Card in Ubuntu"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by ScooterDMan on 2007-02-22
I just got Ubuntu up and running on my Wallstreet Powerbook. I am trying set up a Macsense Aerocard Plus, 802.11b PCMCIA card.

I have no idea what I need to do in order to get this thing working. I am running Ubuntu 5.10.

---

### Post by netkid91 on 2007-02-22
5.10?!

---

### Post by ScooterDMan on 2007-02-22
Is that bad? Should I upgrade? I used 5.10 because I was following a specific guide on the net for Old World Macs.

I'm new to this stuff.

---

### Post by netkid91 on 2007-02-22
Huh?  All of this is need to know stuff, if you are using a mac, we need to know this.  More importantly now that we know you are using one, what exactly is it?  A G4 iBook, a Bondi Blue G3 iMac, what?

---

### Post by jml on 2007-02-22
When asking for help, more information is better than less.  I just did a Google search on your laptop and found out that it is based on the G3 processor.  Does 5.10 run well on your computer?  Or does it seem rather sluggish?  The reason I ask is that Xubuntu, if its available for the G3 architecture is less resource intensive and will run faster on more modest, (ie older,) hardware.  The other point is that Xubuntu/Ubuntu 6.10 recognizes more hardware, and seems to do wireless better than older versions.

I also found out that your wireless card is based on the Realtech chipset.  If a newer version of Ububtu does not recognize the card out of the box, then you may need to utilize the Windows drivers that ship with the card and utilize an application called ndiswrapper.  Searching the wireless sub forum will point you in the right direction.  If you no longer have those drivers, you may be able to download them from this site.

[http://www.macsense.com/support/driver_pc.html](http://www.macsense.com/support/driver_pc.html)

Good luck

Joe

---

### Post by ScooterDMan on 2007-02-22
Thank for the help guys. And not for nothing, but I specified the machine I was using in my first post (Wallstreet Powerbook).

5.10 is running rather sluggish. I've been trying to install Xubuntu, but have had little success on this old machine. For some reason, 5.10 is the only distro that seems to work for me.

Can I upgrade from 5.10 to 6.10 from within Ubuntu? If so, how?

---

### Post by netkid91 on 2007-02-22
Sorry about the machine, didn't read the post fully, but your processor is usually very helpful info in the mac world, along with RAM on old world machines.

---

### Post by IronMac on 2007-02-23
> **ScooterDMan said:**
> Can I upgrade from 5.10 to 6.10 from within Ubuntu? If so, how?

No, you have to go from 5.10 to 6.06 and then 6.10.

---

### Post by Debaser on 2007-02-23
> **netkid91 said:**
> Sorry about the machine, didn't read the post fully, but your processor is usually very helpful info in the mac world, along with RAM on old world machines.


The Wallstreet Powerbook - is a G3 equiped 'book. Usually 233 -266 mhz, there were a few diff. models released. Ram is usually 64-128 MB but can be expanded.

---

### Post by netkid91 on 2007-02-23
Sounds like he wants Xubuntu then, a normal Ubuntu install won't run well on anything under ~192MB of RAM.  Xubuntu can handle 64 nicely.

---

### Post by ScooterDMan on 2007-02-24
My problem is I can't seem to install Xubuntu. I have burned no less than 6 various versions of Ubuntu and Xubuntu, including different version #s (5.10, 6,10, etc) and alternate CDs as well.

No dice. Is there another distro that would work well on this old machine? Again, I just want it to run FIrefox so I can browse the web, and recognize my wireless card (Macsense Aerocard 802.11b)

---

### Post by netkid91 on 2007-02-26
Why won't XUbuntu install?  If anything else you might want to try Debian, which has better support for old-world macs if you read the guides.  Just make sure to use XFCE or another light-weight window manager.

---

### Post by doobit on 2007-02-26
Did you follow the advice in this thread?

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

