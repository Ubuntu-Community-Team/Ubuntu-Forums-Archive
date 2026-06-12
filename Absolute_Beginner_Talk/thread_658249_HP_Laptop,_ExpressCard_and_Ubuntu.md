---
title: "HP Laptop, ExpressCard and Ubuntu"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by rhyeal on 2008-01-04
I recently bought a HP laptop, a dv6470us, and have used Vista on it for a while.  However, after running out of "free trials" of Office 2007 and a New Year's resolution to no longer pirate software, I need an alternative.  I like the feel and control that Linux gives over hardware and other computing processes and I specifically like Ubuntu because I am most familiar with it (I am reading a huge book about it).

Now, my question is thus:

I have a Broadcom-based chipset (4321AG) in my built-in wireless card, but I know that it is not supported by any Linux drivers (e.g. the bcm43xx driver).  I need a new wireless card/chipset in order to use it with Ubuntu - this is necessary because I am at a college campus with a T3 line (and how many times in life can you use a T3 line for downloading stuff?) and I need the connectivity.

The slot for a wireless card that I would like to use is the ExpressCard slot, a derivative of the PCMCIA slot but "upgraded".  But, I have not been able to find any documentation that suggests that an ExpressCard will work under Linux.  Since I do not have money to waste at this point, I want a solution that will work the first time and I would like confirmation that it would work before I spend money on a card.

As an aside, are there any open source programs like Microsoft OneNote 2007 available for Ubuntu?  I need that for note taking in class.

Thanks much guys!

---

### Post by aun on 2008-01-05
I would be willing to bet that you can get your current card to work if you are willing to go through enough pain.  I have a Compaq F560US:
 
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01069711&lc=en&cc=uk&dlc=en&product=3441659&rule=5749&lang=en]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01069711&lc=en&cc=uk&dlc=en&product=3441659&rule=5749&lang=en")

It works with ndiswrapper pretty well, if with some bugs.  Look on this page to see if you can find the right driver for your card:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/")


BTW, you can get Open Office for Windows too, while you're transitioning.  It is a one for one replacement for MS Office in almost all respects, and is free and open source.  It will open all MSOffice file formats as far as I know:

[www.openoffice.org/]("http://www.openoffice.org/")

---

### Post by rkd on 2008-01-05
I realize this might not suit your needs, but the DV6470 does have a wired ethernet port, so if an ethernet jack is available where you want to use the computer, you could connect to the network that way.  That would be much less fiddling around than getting any wireless connection working.  Of course, if there is no ethernet jack near the computer or you need to connect from various places around campus, you'll have to go with the WiFi.

---

### Post by eolson on 2008-01-05
I bought a "Belkin Wireless G USB Network Adapter."   Works fine.   CD with drivers is in the box.  Transferred the driver to my desktop, ran ndiswrapper and everything is good.  I did manage to get the onboard broadcom to work,  but the Belkin has quite a bit more range,  so use it.

---

### Post by rhyeal on 2008-01-06
Thanks guy for all your answers thus far.  I will look at the first poster's links and see what I can find for my wireless card.

I seem to have found some programs that are like OneNote for Linux.

Googling Basket for Linux and Tomboy will yield the programs that I found work just like OneNote, but with a different interface.  And Tomboy may become my new contact-keeping software.

Keep the replies coming guys :)

Thanks much!

---

### Post by coachwhip on 2008-01-06
you can or should be able to get the 4321 or 4328 depending on which OS you look at it with.

You do have to be careful on which drivers you use, I am on a 64 bit install on 7.10 and couldn't get it working at all. Then instead of just following the instructions i looked at what files were in the extracted folder. The files I had to install were     [COLOR="Blue"] netbc564.inf[/COLOR] and [COLOR="Blue"]BCMWL564.SYS[/COLOR]. When I installed then checked it comes up with bcmwl5.sys installed but it works. Took me ages to get it working though but it looks like it is something really simple once you get the right drivers. If you can't find them then i will see where I got them from. i think it was the [COLOR="Blue"]64-bit_Broadcom_54g_Drivers[/COLOR].

Good luck with it, you will get it working though, i am on the HP9646em laptop with the 4321ag wifi and am currently typing in Kubuntu.

Mike

---

