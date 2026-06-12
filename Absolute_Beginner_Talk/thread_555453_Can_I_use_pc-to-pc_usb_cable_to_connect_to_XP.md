---
title: "Can I use pc-to-pc usb cable to connect to XP"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by ulatif on 2007-09-20
Hi,

On my laptop I have ubuntu installed on on one partition and some data on the other. The internet connection is not working on this computer and therefore need to connect with another laptop to backup my data to uninstall ubuntu and switch back to XP.

There are pc-to-pc USB cables available in the market but they all say that they work with Windows XP. before I buy one - I'd like to confrim whether I can use it with a Ubuntu and XP pc! Would this work? If not, is there an alternative?

---

### Post by Mr.Beast on 2007-09-20
> **ulatif said:**
> Hi,

On my laptop I have ubuntu installed on on one partition and some data on the other. The internet connection is not working on this computer and therefore need to connect with another laptop to backup my data to uninstall ubuntu and switch back to XP.

There are pc-to-pc USB cables available in the market but they all say that they work with Windows XP. before I buy one - I'd like to confrim whether I can use it with a Ubuntu and XP pc! Would this work? If not, is there an alternative?

I'm not sure if the cables work, but if you get a crossover ethernet cable, assuming both computers have an ethernet port you could transfer your data that way.

---

### Post by lisati on 2007-09-20
Hmmmm.... Interesting suggestion.

I have a USB cable which came with Windows drivers to set it up as part of a home network.....I must have a play some with it some time to see if I can get it to work with Ubuntu at one or both ends.

No promises on reporting back (I might need a reminder in a few days time)

---

### Post by ddrichardson on 2007-09-20
The problem would be with Windows, you can use the cable to send from Ubuntu by doing cat > /dev/whatever_the_usb_serial.

---

### Post by ulatif on 2007-09-21
Hi,
great... can you please check if it works. Dont want to spend money on something that might not work afterwards... will be looking for a reply from you soon hopefully

---

### Post by ddrichardson on 2007-09-21
If you don't already have the cable then frankly you should buy an ethernet crossover cable, which providing you have an ethernet port on both machines will work. Plus, having been in PC World today I noticed these USB link cables are bloody expensive by comparison.

---

### Post by w4ett on 2007-09-21
I keep an adapter in my toolkit :

[http://www.thinkgeek.com/gadgets/tools/7470/](http://www.thinkgeek.com/gadgets/tools/7470/)

---

### Post by Eric Weir on 2007-09-21
> **Mr.Beast said:**
> I'm not sure if the cables work, but if you get a crossover ethernet cable, assuming both computers have an ethernet port you could transfer your data that way.

I'm interested in transfering data from a Windows system to a new Ubuntu system. I assume it's not enough just to connect the two computers by a cable. Don't you have to have some kind of software to manage the transfers? 

If so, what would it be. Different things on the Windows and Ubuntu machines? If not, tell me more. You mean I can just go into the Windows machine from the terminal?

I have what I think is a null modem cable that I used to use to transfer files between a DOS machine and a Windows 3.1 laptop -- probably with a DOS version of Fast-Lynx. 

Could I use that?

I know my naivte is showing, but I confess, I'm learning. 

Thanks,

---

### Post by LowSky on 2007-09-21
A crossover cat5 cable would be the easiest solution if your ethernet  adapter works on the laptop and then just share your folders on the same network. You other option (and best i think for you situation) is to by a usb flash drive. A 2gig drive shouldn't cost more than $25.  I dobt your moving files bigger than that..right?

---

