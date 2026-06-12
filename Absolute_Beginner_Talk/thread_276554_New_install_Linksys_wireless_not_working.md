---
title: "New install: Linksys wireless not working"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Oyjord on 2006-10-13
Hi all,

First off, I'm TOTALLY new to Linux, I just installed Ubuntu on an empty partition alongside Windows.

The install worked great, didn't have to do a thing.

But my Internet isn't working.  I have a Linksys WRT54GS router and corresponding wireless network card, which work fine when booting into Windows.  Apparently the network didn't auto-configure when I installed Ubuntu.

Is there a walkthrough which would hold this newbies hand in getting my wireless internet back?  

I "Activate" the eth1, set the properties with the correct SSID and WEP password, and though it activates after a while, I get no net traffic.

I can't hook it up by wires, first, for the comp is way downstairs and I don't have the cable.  Again, the Windows install connects to the router just fine.

Any tips would be greatly appreciated. I'm already loving being away from Windows, if I can just get my internet back.

Thanks a bunch,
Oyjord.

---

### Post by wieman01 on 2006-10-13
What wireless card are you using? Linksys wusb54g by chance? If so, which version?

---

### Post by Oyjord on 2006-10-13
Honestly, I'm not sure which card I'm using.

I poked around some instructions from here and found a command lspci and found this out about it:

bcm4306
14e4:4320

Seems to be a pretty standard card, if I recall correctly.

Hope that helps a bit. I'm still going nuts over this.

Thanks again,
Oyjord.

---

### Post by wieman01 on 2006-10-13
Don't worry. You probably need to install "ndiswrapper". This is the right direction: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Let us know if that is a no-go. We can help.

_**EDIT:**_
Just some background information: "ndiswrapper" is a shell/container for the native Windows driver. Yes, you can use the same driver as in Windows and "ndiswrapper" is the tool that helps you deploy it. :-)

---

### Post by minhkhoi on 2006-10-13
> **wieman01 said:**
> Just some background information: "ndiswrapper" is a shell/container for the native Windows driver. Yes, you can use the same driver as in Windows and "ndiswrapper" is the tool that helps you deploy it. :-)

But It convert only window driver to Ubunto driver. I mean it can't convert to any other Linux?

---

### Post by wieman01 on 2006-10-13
It won't really convert anything at all. I simply deploys or uses - whatever you call it - the Windows driver and wraps it so it will work with Linux. Linux, yes, not Ubuntu... It not only a Ubuntu thingy but it a Linux open-source tool. So you might use it in conjunction with other distros.

---

### Post by minhkhoi on 2006-10-13
> **wieman01 said:**
> It won't really convert anything at all. I simply deploys or uses - whatever you call it - the Windows driver and wraps it so it will work with Linux. Linux, yes, not Ubuntu... It not only a Ubuntu thingy but it a Linux open-source tool. So you might use it in conjunction with other distros.

Thanks you very much. Wonderfull!!!!!
I'am find driver for puppy linux, but I just find no thing.

I ask you one more question: "ndiswrapper" is used to "conver" (easy to write :rolleyes:  ) only wifi driver or any driver?

---

### Post by Oyjord on 2006-10-13
Thanks for helping, all!

Ok, so I followed those instructions in that link very closely.

I got down to step 2.5.2.3 and did a 

  tail /var/log/messages

but had errors.

They read

"VFS: busy inodes on changed media"
and there are a bunch of them, about 9 or 10 of them.

I used ndisgtk and loaded the driver lsbcmnds.inf which I downloaded from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) and burned on a cd on my laptop (which I'm using here).

Arrgh, this is frustrating.  Fun, but frustrating.

Any other tips?

When I do an ifconfig I see an eth0 (my unused ethernet port) and lo.

When I do an iwconfig I see an eth1 with my wireless setting and ssid listed, and a sit0.

No wlans listed at all.

Again, thanks a bunch!
Oyjord.

---

### Post by wieman01 on 2006-10-13
> **minhkhoi said:**
> Thanks you very much. Wonderfull!!!!!
I'am find driver for puppy linux, but I just find no thing.

I ask you one more question: "ndiswrapper" is used to "conver" (easy to write :rolleyes:  ) only wifi driver or any driver?
Wireless only...

---

### Post by wieman01 on 2006-10-13
Ok, try this:
> iwlist scan
Let's see if you need "ndiswrapper" at all. Then also:
> iwlist eth1 scan
> iwconfig
All from a terminal window.

---

### Post by Oyjord on 2006-10-13
iwlist scan gives:

lo interface doesn't support scanning

eth0 interface doesn't support scanning

eth1 No scan results
sit0 interface doesn't support scanning


iwlist eth1 scan gives:

eth1 No scan results


and iwconfig gives:

lo no wireless extensions
eth0 no wireless extensions
eth1 IEE 802.11b/g ESSID:"arsenal1" nickname "broadcom 4306" than a lot of stuff all reading 0 or off

sit0 no wireless extensions

That's it.

Thanks a million for helping me with this!!

Oyjord.

---

### Post by wieman01 on 2006-10-13
Ok, it seems your card hasn't installed. Can you get hold of all the driver files and put them in one single directory in you home-folder? Were you able to get them off the CD? If not, try a USB memory device, that should do. 

The driver files are the starting point...

---

### Post by wieman01 on 2006-10-13
One more question: Have you turned on your wireless AP? I mean the router.

---

