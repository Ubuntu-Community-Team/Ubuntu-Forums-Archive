---
title: "Considering Ubuntu from XP MCE, Many questions, Please inform?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by nintennuendo on 2007-02-22
Okay, First off, I know no one has to help, but any will be appreciated.  I read all of the beginner threads and stuff, but I did not see any for my questions. 

1.  I have wireless Internet from Time Warner Cable, RoadRunner, going to My laptop, where I want Ubuntu.  I tried the LiveCD, but I did not get any Net-ness.  Also, In XP, I had to enter a WPA key to Log in, because the net is secure.  Can I do that in Ubuntu?

2.  After a bit, the two bars at the top and bottom froze with the calender open(which rocks, btw).  A program(correct term for it?), Bug Buddy, opened and asked me to save the txt and send it to someone.  Does it still crash regularly in 6.06?  And How could I fix it?

3.  Are there any p2p programs, preferrably BitTorrent?  I know, copyrighted Material, I do not.  But there are other things that are not copyrighted.  

4.  I could no find a complete list of software available, but I did see a mighty nice list within Ubuntu that had quite a few.  Is a complete list available?

5.  Would any computer games, i.e. Grand Theft Auto:  San Andreas or the like work on Ubuntu?  Is there some kind of Virtual PC available?

6.  Is there a way to get a higher resoultion than 1024?  I like 1280x960 on my laptop, can I use that with this?

---

### Post by tgalati4 on 2007-02-22
You'll get better response with fewer questions per post.
1.  Wireless will take some work.  There are lots of tutorials.  You should try a wired connection first and that is more reliable using the live CD.  Wireless requires knowing the exact chipset for the wireless card and if it is detected properly, you need to set up the network parameters.  WEP works well, though not as secure.  WPA is buggy with some cards.  Seach the forums and you will quickly know what works for others.

2.  Calendar is pretty solid in 6.06.  The live CD does not have the lastest updates.  I counted 107 updates from installing 6.06.1 recently.  Perhaps there was a bug, but more likely some hardware problem.  The Live CD is a serving suggestion.  Just as you wouldn't eat the picture on the cereal box, you wouldn't do serious work with the live CD.  The live CD is helpful to determine how well your hardware will work with Ubuntu "out of the box".  Laptops have strange hardware so they require more tweaks to get them to function.  Without the model of your laptop there is nothing I can recommend.

3.  There are several p2p programs.  It's funny, these programs run better under Linux than windows.

4.  There are 18,800 packages for Ubuntu.  You need to enable all of the repositories under synaptic to see them.  The add/remove button is for grandma.

5.  Gaming is a weak point in Linux, for several reasons.  Do a seach in the forums for a specific game and you will hints on how to set it up.

6.  You need to edit xorg.conf file and add the 1280 x 960 resolution or do a reconfigure xorg and reboot.  Search xorg for how to do this.  This works for an installed Ubuntu.  The Live disk uses a "safe" resolution of 1024 by 768 because it works on most laptops.  Most laptops have strange resolutions.  They can be made to work, but not with the Live CD because the config files are generic.  

Welcome to the Ubuntu community

---

### Post by nintennuendo on 2007-02-22
2.  On the my my comp, it says W34OUA and N-10, under Model numbers.  Are those what you mean?

1.  My laptop came with wireless in it already.  I do not know how to get the wireless card info.

I think all the other questions were answered.

---

### Post by tgalati4 on 2007-02-22
Perhaps your machine looks like the following?

The eMachines N-10 laptop computer bundle delivers the perfect balance of productivity, multimedia and security features ideal for any student. Take up less space in the dorm or at your desk with a reliable AMD-powered notebook with a compact 14.1" widescreen ultrabright display. Feature-loaded laptop lets you easily complete school projects, watch DVDs and work in multiple applications.

Then bring your computer anywhere with the included Targus notebook backpack. Protect your investment with a 2-year service plan from Computrace with the LoJack for Laptops theft recovery service and a 2-year parts and labor warranty from eMachines.

Operating System: Microsoft Windows XP Media Center Edition 2005
Processor: AMD Sempron 3200+, Operating at 1.6GHz 512KB L2 Cache HyperTransport technology @ up to 1600MHz
Memory: 512MB DDR2 (1 x 512MB); Expandable to 2GB; Total: 2 DDR2 Slots Available: 1 DDR2 Slot
Hard Drive: 60GB (4200 RPM)
Optical Device: DVD+/-RW Multi-Format Double Layer (up to 8.5GB)
Display: 14.1" Ultrabright Widescreen XGA TFT
Video: NVIDIA GeForce Go 6100 Integrated Graphics; Up to 128MB Shared Video Memory
Audio: AC'97 2.3 Compliant Audio; Built-in Speakers
Network: Integrated 10/100 Mbps Ethernet LAN; Integrated 802.11g Wireless LAN
Power: 6-Cell Lithium ion Battery
External ports: 3 -USB 2.0 Ports; 1 -VGA External Connector; 1 -RJ11 (modem); 1 -RJ45 (Ethernet LAN); 1-Microphone; 1 -Headphone / Audio Out
Measurements: 1.41"(H) x 13"(W) x 9.45"(D)
Weight: 5.28 lbs
Software: Productivity Software: Microsoft Works 8.5, MicrosoftOffice 2003 Student Teacher Edition Trial (includes 60-day complimentary trial period), MicrosoftMoney 2006, AdobeReader

Do a search in the forums on your nvidia geforce graphics card to see what problems folks are having.  Ubuntu should fly on this machine, but it will take some tweaking to get everything working.
 
Since you have a built-in, wired, ethernet, use that for network connection during testing and installation.  Not sure what your wireless chip is, that will require searching google or "device manager" (system-->admin-->device manager) and then search the forum for setting up wireless for that specific wireless chip.  This is difficult to do with the Live CD since you need to save the configuration files.  It can be done by setting up a small partition for these files, but you won't get the full benefit of Ubuntu without doing a proper installation.

If you do get everything working, please post back here and let us know how well Ubunutu works compared to Windows XP media edition.

---

### Post by nintennuendo on 2007-02-22
That is my computer, indeedy.  In windows, Ctrl Panel > System > Hardware > Device Manager, network adapters, I see Realtek RTL8185 54M Wireless LAN Network Adapter, Is that it?

---

### Post by nintennuendo on 2007-02-22
and, I downloaded both the cd and Dvd Isos, which is better to install with?

---

### Post by igknighted on 2007-02-22
> **nintennuendo said:**
> and, I downloaded both the cd and Dvd Isos, which is better to install with?

I would recommend the CD install... it results in a more trim system free of bloat, and since you have high speed internet anything on the DVD you want is an easy install from the net.

---

### Post by tgalati4 on 2007-02-22
Search Realtek in the forums to find clues as to the best way to set up your wireless.  Give the DVD to someone who has dial-up.

Burn another CD and give it away as well.  Share the love.

---

### Post by nintennuendo on 2007-02-22
Oh totally, I am definitely going to give it around after I try it out.

---

### Post by punx45 on 2007-02-22
sometimes some manufacturers switch chipsets on various revisions of the same hardware model.   next time you are in live CD, go to the command line and type 'lspci' and then skim through the output for a refrence to wireless.   usually that will be the specific chipset information, and armed with that you can find out alot more about your wireless compatability.  

an excellent example of this is one of Linksys' wireless PCI cards which has a model name of W-something-54G , but some versions have a Broadcom chipset, such as the dreaded 4306!

---

### Post by nintennuendo on 2007-02-22
I did that, but cannot copy/paste it into a document and save it to my USB drive.  But it says it recognizes it.  Eh.  It says:

Ethernet controller:  Realtek Semiconductor Co., Ltd. Unknown device 8185(rev 20)

Didnt see any wireless anywhere.

I would really like to use Ubuntu, but I am skeptical aso to if internet will work on it, and if I need the WPA key I needed in Windows, since I do not have it anymore and cannot copy from the box where it is.


Also, assuming I get the internet to work, could I still watch videos online?  Like in .flv format?  And, some websites like the Adult Swim Fix have their videos from Windows Media Player, is there something available so I could still see Wmvs, rm, or quicktime files online?

---

### Post by tgalati4 on 2007-02-22
To copy and paste in Linux, highlight the text with your mouse cursor.  Go to the application where you want to paste and press the middle button.  On a laptop, press both trackpad buttons at once.  Some apps use control-c and control-v to cut and paste.  Just like that other operating system.

I'm not sure what the .flv format is, but Linux can support just about anything although it will require that you download some "restricted" codecs.  Ubuntu only ships with open source software.  Windows Media Player requires a fee to license which everyone in the Linux community happily pays.

---

### Post by nintennuendo on 2007-02-22
I managed to get it all into OpenOffices word program, Txt Editor and something else, but it would not save to my USB pen. 

But, I found someone that I think would work:  It is the Linux Drivers for my wireless card(as of now, i think that and getting my wpa key are the only holdups), but once I install Ubuntu, I would need to get Ndiswrapper, but I do not know how without Net access, or is it on the cd/dvd installer?  Then, what would I do with that to get te drivers working?  Then, I think I can find out how to get it set up and enter my key.  

Would that work?  barring any unforeseen complications?

---

### Post by jml on 2007-02-22
I would not recommend installing Ubuntu without reliable Internet access.  Can you at least temporarily connect to your Internet connection with an Ethernet Cable?  Once you have Ubuntu installed and configured, you can then download everything else you will need from software repositories, including ndiswrapper and all the other things you may want/need.  

WPA encryption is more of a challenge.  It took me months to get it to work, but things are getting better.  I would recommend doing a standard install with a wired connection to the Internet and then search and post questions on the networking/wireless sub-forum here to get connected wirelessly.

Joe

---

### Post by tgalati4 on 2007-02-22
Regarding the USB pen drive:

You should be able to save the text file.

In Nautilus (file manager) drag the file into the icon on your desktop.  The one labeled "My Cheesy USB Pen Drive".

Double click on the USB desktop icon to make sure the file is in there.  Right Click eject before removing.

---

### Post by 3rdalbum on 2007-02-22
Ndiswrapper is included on the Desktop CD (the one you have), so you don't need an existing internet connection in order to install it.

---

### Post by nintennuendo on 2007-02-24
How do I get to it?  I looked everywhere and could not see it.  Once I get it going, how would i install the drivers to make sure my net could work with it?  Or do I have to install to get that working?

---

### Post by nintennuendo on 2007-02-25
bump..

---

### Post by Blario on 2007-02-26
> **nintennuendo said:**
> bump..

You should take the advice above andget yourself setup over a wired connection.  You're going to need internet far more times later on than you think, far before you get the WPA up.

to install ndiswrapper from the cd, put in the cd and open synaptic from the 'system' menu on the top left of your desktop.  Go to administration and 'synaptic' should be in there.  When you open it, it should scan apps from the cd that are available to install.  you can search for 'ndiswrapper', check the box, then apply changes in order to install it.

---

### Post by Blario on 2007-02-26
for further help with ndiswrapper, the wiki is the best place to go, in my opinion.  

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

---

