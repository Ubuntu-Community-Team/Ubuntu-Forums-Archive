---
title: "Dial-up modem - best choice(s)?"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by Bartender on 2005-11-13
Good day -
I want to put together a dedicated Linux computer rather than asking the M$ machine to share some space on C: drive.
No broadband available on our road, so it's dial-up or satellite and I ain't payin' for the eye in the sky.
I poked around for a list of dial-up modems that work with Linux but some of the websites are ancient and some of the devices don't appear to even exist anymore.  Anybody got a few current models to recommend? 
I'm willing to pay the extra bucks for a hardware modem if that's the best solution.  
What I don't want to do is buy the wrong modem and freak out trying to make it function.  It's pretty clear from reading these forums that I'm gonna be severely taxing the few remaining brain cells trying to learn Linux even under the best of conditions.

---

### Post by Bartender on 2005-11-13
Here I am, talking to myself already - here's the link to a "hardware-based" Intel modem at Directron.  Would this one work?

[http://www.directron.com/intelhwmodem.html](http://www.directron.com/intelhwmodem.html)

Thanks in advance for anyone who has the time to help me out!!

---

### Post by Mustard on 2005-11-13
[QUOTE=Bartender]Here I am, talking to myself already - here's the link to a "hardware-based" Intel modem at Directron.  Would this one work?

[http://www.directron.com/intelhwmodem.html](http://www.directron.com/intelhwmodem.html)

Thanks in advance for anyone who has the time to help me out!![/QUOTE]

That looks suspiciously like a winmodem, which will put you in modem hell when you try it in linux.  What you should be looking into is an external modem that connects through your serial port, rather than the many cheap winmodems that use the pci slot, and require you to have windows to function properly.  They are cheap because they have taken shortcuts with the hardware, by using parts of the windows operating system, rather than having it built in with hardware. 

I'm half asleep while typing this, so I hope it makes sense.

Anyway, despite what the blurb on the page says, this one line in the specs has me worried.

> System requirement: Win98/ME/2000/XP; 

---

### Post by Kapre on 2005-11-13
Bartender - I second what Mustard stated above. Any external modem would be best so you wouldn't have problem installing it (software side). I would suggest US Robotics 56K.

K

---

### Post by autocrosser on 2005-11-13
I use a older Zoom Fax/Modem--2986L USB external--bought it off eBay for $10+shipping--I have heard that the older Supra Express (SUP 2780 & earlier) work ok---Take a look at-- [http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/)  for more info--covers all kinds of USB equipment.......:smile:

---

### Post by Bartender on 2005-11-14
Thanks, guys -
I don't know if you realize how encouraging it is to come back a day later and find several people took the time to help out.
I was a little leery about the price for that Intel modem.  Too good to be true?
If I want to be sure about avoiding headaches, it sounds like an external is the way to go.  
As of this morning (who knows what I'll be thinking by mid-day) I'm leaning towards a different first project.  Well, after installing Ubuntu that is, but  the install should go O.K.  I think a little networking project between the existing M$ machine and the soon-to-be Linux box might make more sense for this noob.
The Pentium III I have picked out for the Linux install comes with a 3Com fast etherlink card - "3C905B-TXNM" appears to be the model number.  I've never networked anything before, but it seems like networking is a fundamental part of Linux so it makes sense to me to pick a first project with good odds...
Then it'd be fun to see if Ubuntu can connect to the net via the networked M$.  I'll be scrounging around for networking pointers.  It looks like there are some generic guides right on this forum or thru the Wiki (?)  I'm not very familiar with Wiki yet.
O.K., I'm rambling now.  Thanks again!

---

### Post by zerhacke on 2005-11-14
Try to stay away from External USB modems.  Most won't work on Linux.  I have yet to find one that does, but there's bound to be something that does.  Still, it's your best bet to not use USB modems.  Get a serial line one as already outlined.

---

### Post by psyguy92 on 2005-11-14
Personally, it would annoy me to have an external modem.  What I did for my desktop was to find a REAL hardware modem on eBay (PCI).  You can look for modems for sale and compare them against this database:
[http://www.devidal.tv/~chris/winmodems/]("http://www.devidal.tv/~chris/winmodems/")

If that site doesn't respond, go to [http://start.at/modem]("http://start.at/modem")

I don't know of any new models that are real hardware modems, though they probably exist.  I would be careful about buying a modem that states it's a hardware modem without checking it's data exactly against the above referenced database.  I've bought a modem before that was supposedly hardware, but when it came, it was not.  Check the list first.

linuxant.com drivers are available for purchase (closed source and not gratis/free) for some/most? conexant winmodems.  That's what I chose to do for my laptop's modem. :/

---

### Post by blastus on 2005-11-14
I lucked out when about 5 or 6 years ago I got fed up with the incompatibility of modems between various versions of Windows. I was not even using Linux at the time. So I spent $100 and bought an internal Zoom/Lucent PCI modem. It listed on the box compatibility with several versions of Windows and even Linux. 

Fortunately for me, when I switched to Linux a couple of months ago, I was able to get this modem to work on it. I bought this modem many years ago back when full-blown "winmodems" were not mainstream. Unfortunately, I don't know if you can buy a real PCI modem anymore. In short, if the box says the modem is "host-based", "HCF", "HSP", "HSF", "controllerless", "host-controlled", "soft modem" or "designed for Microsoft Windows" then I would be leery about buying it. Another thing you may want to look out for is the price of the modem--if the price is very cheap, chances are it is not a real modem. One more thing, most USB modems are like PCI modems--they are not real modems either. The only modem that is guaranteed to be a real modem is an external serial (RS-232) modem.

As mentioned, you may be able to find a PCI modem that is compatible with Linux but you may have to buy the drivers for it (i.e. modems with Conexant chipsets.) However, Linuxant will not supply you with the source code--they will only give you the binary kernel modules. The issue with that is that if you want to install a new kernel, or upgrade to a new kernel, or upgrade from one distribution of Ubuntu to another, the modules that they gave you may not work. However, if you have the source code for the kernel modules for your modem (which I do) you can simply recompile the code and reinstall the modules. Finally, I will never buy a modem based on a Conexant chipset again because I had one before and that modem, which was exclusively designed for Microsoft Windows, was so damn flaky on Microsoft Windows that it was useless.

---

### Post by psyguy92 on 2005-11-14
[QUOTE=blastus]
<snip>

As mentioned, you may be able to find a PCI modem that is compatible with Linux but you may have to buy the drivers for it (i.e. modems with Conexant chipsets.) However, Linuxant will not supply you with the source code--they will only give you the binary kernel modules. The issue with that is that if you want to install a new kernel, or upgrade to a new kernel, or upgrade from one distribution of Ubuntu to another, the modules that they gave you may not work.

<snip>
[/QUOTE]

Clarifications.
If you buy a real hardware modem, you don't need a driver at all - linuxant or otherwise.  If you need a linuxant driver, the fee is per modem. If you upgrade / rebuild kernel / etc., you do not loose your driver, but must reinstall the driver.  It checks the MAC address of the modem itself, and the driver is good for that modem only.

Also, ndsiwrapper may work for you with winmodems.  It uses the windows driver for the modem.  It can be a pain though.

---

### Post by Bartender on 2005-11-14
Man, I'm gonna have to print all the above so I can keep track of all this good info.

O.K., guys, here's a link to the USR website, where they advertise one internal controller-based PCI modem.  Does this one look like the real deal?  I scrolled thru the "Modems 101" tutorial on the right-hand side of the page - kinda neat overview of different kinds of modems, and seems to confirm that the 5610b is a controller-based modem.  Um, the tutorial didn't work in Firefox.  I had to go back to IE to run it.

[http://www.usr.com/products/home/home-product.asp?sku=USR5610B](http://www.usr.com/products/home/home-product.asp?sku=USR5610B)

---

### Post by psyguy92 on 2005-11-15
[QUOTE=Bartender]Man, I'm gonna have to print all the above so I can keep track of all this good info.

O.K., guys, here's a link to the USR website, where they advertise one internal controller-based PCI modem.  Does this one look like the real deal?  I scrolled thru the "Modems 101" tutorial on the right-hand side of the page - kinda neat overview of different kinds of modems, and seems to confirm that the 5610b is a controller-based modem.  Um, the tutorial didn't work in Firefox.  I had to go back to IE to run it.

[http://www.usr.com/products/home/home-product.asp?sku=USR5610B](http://www.usr.com/products/home/home-product.asp?sku=USR5610B)[/QUOTE]

[http://www.devidal.tv/~chris/winmodems/ti/ti_700.html](http://www.devidal.tv/~chris/winmodems/ti/ti_700.html)

This is a full hardware modem, Texas Instruments manufactured for U.S. Robotics.

US Robotics 56K Performance Pro (V.92), Model 0778 (USR325610B), 56K/14.4K d/f modem (PCI\VEN_12B9&DEV_1008&SUBSYS_00D312B9&REV_01)


It's a bit pricy and eBay would be cheaper, though this modem would probably work nicely.  

Good luck!

---

### Post by Bartender on 2005-11-16
Hi, psyguy92 -
Thanks for the neat link.  Printed it out and will keep for reference.
I see what you mean about ebay - lotsa 5610A's and B's all over the place.  I've always been nervous about ebay but maybe this would be a good opportunity to try it...

---

### Post by blastus on 2005-11-16
[QUOTE=Bartender]Man, I'm gonna have to print all the above so I can keep track of all this good info.

O.K., guys, here's a link to the USR website, where they advertise one internal controller-based PCI modem.  Does this one look like the real deal?  I scrolled thru the "Modems 101" tutorial on the right-hand side of the page - kinda neat overview of different kinds of modems, and seems to confirm that the 5610b is a controller-based modem.  Um, the tutorial didn't work in Firefox.  I had to go back to IE to run it.

[http://www.usr.com/products/home/home-product.asp?sku=USR5610B](http://www.usr.com/products/home/home-product.asp?sku=USR5610B)[/QUOTE]

It looks like a good modem to me. They explicitly state that it is a controller-based modem and that it is compatible with Linux. So the modem will work on Linux--if it will actually work on Ubuntu and how to get it to work on Ubuntu is another question. I'd do a search first and find out if anyone else is using this modem (Model USR5610B) on Linux and what their experience is with it. If I was going to buy a PCI modem it would probably be that one.

You could always get an external serial modem instead, but I've heard that some PCs do not have RS-232 ports. As far as I know, USB has or is phasing out RS-232. The issue with USB is that the interface is fast enough that the modem does not have to have a DSP and other essential hardware. Consequently, most USB modems are soft modems. On the other hand, the RS-232 interface is too slow so all serial modems have to be hard modems.

---

### Post by bob_knab on 2006-04-18
bob_knab here _____________________________

i am new to UBUNTU and this is my first post-
just installed ubunti 5.10 
and encountered 3 problems

1-- the floppy drive would not mount.

2--my USB 5610B would not auto inatall;
it intresting to note that i ran this modem
on Fedora-1 and on a linux 2.4 in anouther
distro and it worked very well-

3--when i ran scanModem from the desk top 
installed from the cdrom as stated ,to detect 
the modem chip set i get -NO SUCH FILE

I am reluctant to pass 5.10 out with this kind of problem
why will 5610B work in 2.4 and not in 2.6 and there is
no reason that the floppy drive will not auto mount -
modems are a problem but i think this can be worked out
and simplified please send any support info you have
i am also scaning this site for information - i want to get 
fine distro working - Thanks bob knab

---

### Post by htinn on 2006-04-18
Huh? Auto mounting floppies? Is that even possible? (Outside of Amigas and Macs of course.)

---

### Post by Badut on 2006-04-18
[QUOTE=Bartender]Good day -
I want to put together a dedicated Linux computer rather than asking the M$ machine to share some space on C: drive.
No broadband available on our road, so it's dial-up or satellite and I ain't payin' for the eye in the sky.
I poked around for a list of dial-up modems that work with Linux but some of the websites are ancient and some of the devices don't appear to even exist anymore.  Anybody got a few current models to recommend? 
I'm willing to pay the extra bucks for a hardware modem if that's the best solution.  
What I don't want to do is buy the wrong modem and freak out trying to make it function.  It's pretty clear from reading these forums that I'm gonna be severely taxing the few remaining brain cells trying to learn Linux even under the best of conditions.[/QUOTE]

Hi Bartender,

Here's an avenue you might not have considered. With so many people changing to broadband these days, there's bound to be someone you know who doesn't need their dial-up modem anymore. Ask around and you can probably score a modem for free ;) I did. Even if you end up with a modem that doesn't play well on Linux, you didn't have to pay for it. Worth a shot I think.

As for a modem that works with Linux. I have a Pragmatic external 56k (can't remember the exact model#). Works like a champ. No tinkering/tweaking required.

From what I've heard, most external modems should be ok.

---

