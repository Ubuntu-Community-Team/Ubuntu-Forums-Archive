---
title: "An update on Airport Extreme Driver Progress..."
date: 2005-03-21
forum: Apple PPC Users
---

### Post by spaceballl on 2005-03-21
Hey guys, so i did some searching. This post was just a few days ago over at sourceforge in regard to the development of broadcom 802.11 drivers... I'll copy/past the relevant text...

"
Hi, 
  
 Although I've been working on this project now for a few years, I haven't yet posted here. I am one of the main developers working to reverse engineer the driver. I thought I'd stop by and allay some fears. 
  
 The project is not dead, as is often asked, and we are still making progress reverse engineering it. For those of you who want a status update, the current percentages are: 
  
 wlc_phy : 12003 of 20303 instructions translated (59.12% complete). 
 wlc_led : 0 of 890 instructions translated (0.00% complete). 
 wlc_security : 0 of 234 instructions translated (0.00% complete). 
 wl_linux : 2654 of 2654 instructions translated (100.00% complete). 
 wlc_rate : 248 of 760 instructions translated (32.63% complete). 
 wlc_tkhash : 0 of 370 instructions translated (0.00% complete). 
 wlc_cmn_ioctl : 0 of 1601 instructions translated (0.00% complete). 
 wlc : 18169 of 42807 instructions translated (42.44% complete). 
 Total : 33074 of 69619 instructions translated (47.51% complete). 
  
 I generally don't frequent this forum, but if anyone would like to help, you can send an email to me or Andrew (amiklas). I will try to post new percentages every so often, when significant progress is made.
"

That looks like decent news. I'm going to go join that forum in order to hopefully provide better support and see if I can't help the development process along. I think we owe it to all iBook/Powerbook users to do the same!!!

-Kevin

---

### Post by chascon on 2005-04-27
Great News!
Anything to keep that alive.  Considering the below.

"the broadcom chipset used by apple 
for the airport extreme is also used in the Linksys WAP54G wifi access point 
... which runs under linux. This of course means there is a kernel module that 
drives the chip, and thus that either Linksys or Broadcom have code some 
driver for it. It makes me angry to think they would have gone that far and 
stopped there without considering their customers who care about running linux 
on their apple hardware."
[http://lists.debian.org/debian-powerpc/2004/02/msg00445.html](http://lists.debian.org/debian-powerpc/2004/02/msg00445.html)

and 

"A few months ago, I wrote to the kernel list describing the
relationship between Linksys (now business unit of Cisco Systems),
their WRT54G 802.11g wireless home gateway, and Linux. At the time,
we had recently discovered that the WRT54G was using a great deal of
software made available under the GPL, but was not giving credit to
the authors, or providing the source as required by the GPL.

After a bit of public pressure, Linksys posted their "GPL Code Center"
[1], where they claim that "the GPL source code contained in this
product is available for free download" [2]. Shortly after the code
center was made available, a group of developers pointed out to
Linksys that their source code, particularly their Linux kernel code,
was incomplete.

Previously, it was thought that the WRT54G source releases had only
neglected to include the source code for the various kernel modules
used to run the ethernet and wireless interfaces. However, at this
time, it is clear that the kernel proper of the WRT54G itself has had
functionality added to it. This functionality is not present in the
kernel code that Linksys has provided at their "GPL Code Center".

That is to say, there is code STATICALLY LINKED with the Linux kernel
running this device that is not present in the source download. This
code seems to be shared between the Broadcom ethernet and wireless
chips. It appears to be primarily responsible for configuring the
Sonics' SiliconBackplane and handling DMA transactions for both
devices."
[http://www.ussg.iu.edu/hypermail/linux/kernel/0309.3/0904.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0309.3/0904.html)

---

### Post by Tofu on 2005-04-27
It's great news that dedicated people are devoting their time to enable Wi-Fi access from the Apple iBook.

I want to buy a G4 iBook to run Linux, but I've been holding off because of this issue. I can't see how it is in the various companies' interests (ie Broadcom, Apple) to inhibit Linux access. If I go out and buy an iBook to run Linux then Apple benefits.

I know there is a petition somewhere on the net to influence Broadcom, the maker of the Airport card. I wonder if it would be better to hammer on Apple's door, as Apple could put a lot of pressure on Broadcom to make the driver source code available.

Whenever I use Google to search for Linux PowerPC issues, most pages I find are referring to the iBook. I get the impression that the iBook is the most popular PPC machine for running Linux. Maybe Apple doesn't realize how big it is.

---

### Post by tonyB on 2005-04-28
[QUOTE=Tofu]
I want to buy a G4 iBook to run Linux, but I've been holding off because of this issue. I can't see how it is in the various companies' interests (ie Broadcom, Apple) to inhibit Linux access. If I go out and buy an iBook to run Linux then Apple benefits.
[/QUOTE]


I'll second this.  I'm a long time Mac user who has been considering buying an iBook for some time now.  I'm unlikely to do so without WiFi under Linux.  I haven't inquired yet, but I gather there is 802.11g support for intel-based portables.  Maybe that's the way to go.

---

### Post by msgyrd on 2005-05-02
I've emailed both Apple service and support and Broadcom about this matter.  Apple never responded to anything, while a conversation held with a Broadcom representative led to me stating I'd never again purchase any product that ever used their chips and would try to convince as many people as possible to do the same, and their response was "It's Apple's fault, and it's your decision where you spend your money", so basically, screw off linux users.

Broadcom are dicks about it and Apple refuses to answer.  Sourceforge is probably the only way this will ever get a working implementation, but by the time that is coded, some Super Airport Extreme (802.11n) will probably be out.

---

### Post by slux on 2005-05-02
This is getting really interesting. I checked out the linux-bcom4301 sourceforge project forums again today and someone had posted a link about [a possible GPL violation inside the *module* itself](http://lists.gpl-violations.org/pipermail/tech/2005-March/000016.html).

<edit> just adding the [follow-up](http://lists.gpl-violations.org/pipermail/tech/2005-April/000025.html) for completeness</edit>

It's nice to see the project is progressing. It would be even nicer to see Broadcom forced to release their own driver.

---

### Post by spaceballl on 2005-05-02
[http://sourceforge.net/projects/linux-bcom4301/](http://sourceforge.net/projects/linux-bcom4301/)

This is the sourceforge project page. Unfortunately, the head developer has stopped his efforts, and he's looking to pass the project off to someone else (read project webboard). Oh well I hope it ends up working out for us all...

-Kevin

---

### Post by slux on 2005-05-02
Yeah, he seems to but if you read thread I got the links from, at least two other people are still working on it so it doesn't seem so grim. On a side note it's very sad that a completely second-rate solution like Ndiswrapper has managed to bog the project down somewhat.

---

### Post by MIZREE on 2005-05-04
just wanted to add my two cents on this subject,

I installed ubuntu and everything seems to work but the wireless. Hardwired works fine, now after reading a bit I understand why. I sure wish this was posted somewhere on the umbutu downloads page for ppc users of umbutu, so I wouldn't have wasted my time installing it.
I dont really understand why airport doesnt work in linux, since  osx is built on linux and it worked fine for them. Couldn't someone smarter than me just 'borrow' the driver from osx and post it? sounds easy enough. lol

since this is a learning tool for me, I may just buy a usb wireless card to bypass the issue for now, until I can figure out how to steal my airport driver from my osx disc.

---

### Post by MIZREE on 2005-05-04
[QUOTE=MIZREE]just wanted to add my two cents on this subject,

I installed ubuntu and everything seems to work but the wireless. Hardwired works fine, now after reading a bit I understand why. I sure wish this was posted somewhere on the umbutu downloads page for ppc users of umbutu, so I wouldn't have wasted my time installing it.
I dont really understand why airport doesnt work in linux, since  osx is built on linux and it worked fine for them. Couldn't someone smarter than me just 'borrow' the driver from osx and post it? sounds easy enough. lol

since this is a learning tool for me, I may just buy a usb wireless card to bypass the issue for now, until I can figure out how to steal my airport driver from my osx disc.[/QUOTE]

oops, forgot my stats for others' reference.
I am using 12 inch ibook 800 with around 600mb ram, 40gb hard drive, and older airport internal wireless nic. I tried a netgear wgt634 router and airport AP, both with no luck to connect.
also, if someone can do the extraction of the airport driver I can provide the osx 10.1 cd by ftp or something. thanks all.

---

### Post by slux on 2005-05-04
[QUOTE=MIZREE]
I dont really understand why airport doesnt work in linux, since  osx is built on linux and it worked fine for them. Couldn't someone smarter than me just 'borrow' the driver from osx and post it? sounds easy enough. lol
[/QUOTE]

The issue we're discussing here only applies to Airport Extreme. Standard Airport (as shipped with iBook G3s) should work without problems and I've successfully used it with Ubuntu.

What do the Ubuntu network config tools say about your the airport card?

BTW, OS X is not based on Linux although *GNU/Linux* and it do share some components. They can't utilize the same drivers and the reason for AP Extreme support missing is that the Apple AP Extreme driver is proprietary.

---

### Post by MIZREE on 2005-05-04
Thanks for the info, sorry i must be in wrong thread for my wireless connectivity issue.
my network configuration says the wireless airport card is working and connected but idle. it gets 0% signal sitting next to the router.. never been able to connect to any wireless network at all since installing Umbutu on this machine. I have tried dhcp, and static ip's, have also tried two different routers at my house(netgear wgt634 -wep secured, and airport graphite -unsecured) 
I am able to connect to both routers with no problems using my winblows laptop and desktops, and had no connectivity issues with osx.
I am also able to connect to netgear one hardwired, just not wirelessly. also the system hangs on return from standby with following error about airport card:
eth1 unknown information frame received (type f202)

I did a search for that error and found other linux/ppc users had same error but they thought it had to do with a firmware upgrade(which has not been done on this router since newly installed)

---

