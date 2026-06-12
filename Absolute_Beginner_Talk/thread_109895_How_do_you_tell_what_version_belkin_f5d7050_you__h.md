---
title: "How do you tell what version belkin f5d7050 you  have?"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by sdwi on 2005-12-29
I have been reading the posts regarding the belkin usb wifi adapter.  I have to say I am lost:(  Everyone keeps talking about the version of his or her belkin adpater.  Where can one find this information?  I no longer have the box it came in.

I have tried to plugging in the adapter and nothing happens..  I have also run the following command.

[INDENT]**sudo ifconfig ra0 up **[/INDENT]

and i get back a nice error message of:

[INDENT]**ra0: ERROR while getting interface flags: No such device**[/INDENT]

*Note I do have the device plugged into the usb port and the device manager in ubuntu does acknowledge the device

Thanks for your time in advance.

Stephan Severson

---

### Post by d1337 on 2005-12-29
A quick forum search as well as a bit of googling(sp?) makes me think that you may have to obtain the Windows drivers for this card and use ndiswrapper to make this card function.  As far as what version of card you have, I would assume that it is documented in the firmware of the card...but you have to access the card first (I'm guessing).  There are several threads, and this one looks rather promising for you...
[http://www.ubuntuforums.org/showthread.php?t=44711&highlight=belkin+f5d7050](http://www.ubuntuforums.org/showthread.php?t=44711&highlight=belkin+f5d7050) at least for a start.  If you just do a forum search for Belkin F5D7050, there are plenty of threads.

Hope that helps,
d1337

---

### Post by sdwi on 2005-12-29
Thanks for your help with the F5D7050 setup! :)  I am up and running on Ubuntu 5.10 Breezy Badger..
I love the title of the OS release since I live in [**Wisconsin**]("http://www.wisc.edu")
Used Synaptic Package Manager from System/Administration from the top tool bar in Ubuntu 5.10 "Breezy Badger" :)
Searched for ndiswrapper
Installed 2 files -marked below in **bold**- from search in Synaptic Package Manager:
**ndisgtk** 
[INDENT]graphical frontend for ndiswrapper[/INDENT]
**ndiswrapper-utils**
[INDENT]Userspace utilities for ndiswrapper[/INDENT]

Next downloaded rt2500usb.inf to home directory on ubuntu machine from windows xp.  I downloaded the file from [Belkin]("http://www.belkin.com/support/download/downloaddetails.asp?download=1379&lang=1") and run the setup and let it install the driver.
Used **ndisgtk** and selected / installed the rt2500usb.inf

This is my second attempt at running Linux... The last time was 2000 with Suse Linux 7.3.. I had some success, but nothing like this release...AWESOME!

---

