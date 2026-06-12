---
title: "Question about using ndiswrapper"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by t341 on 2007-02-13
I have only been using Ubuntu for a couple of days, so I am sorry if
this is a dumb question.  I found a tutorial for setting up a Broadcom 
bcm4310 windows wireless adapter driver using ndiswrapper.
Using my other(WinXP)computer I downloaded ndiswrapper1.37.tar.gz
and Windows driver sp34512.exe.  (The tutorial advises to obtain
the newest version of ndiswrapper) 
Before starting the steps in the tutorial, where exactly do I place the
files listed above so that the Ubuntu installation will find them?

---

### Post by Fahuadai on 2007-02-13
I found these two guides helpful: 

[http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm43]("http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm43")

[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom]("http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom")

Hope this helps.

Unfortunately Broadcom provide pretty much zero linux support and so is a pain to get working. I still not able to get it working with WPA. 

Also something that i noticed on my laptop that having Wireless Assistant manager, or any other netowrk manager for some reason stops it working.

I for one will not be purchasing any Broadcom hardware any more. 

hope the above links prove useful. As for where to put the files, it doesn't matter. the guides usually use the desktop or your /home folder.   but you can place anywhere you want, as lnog as you remember the location and use the correct one when entering the commands.

---

### Post by t341 on 2007-02-13
Thanks for the reply.  I didn't think WPA would work with this 
method so I might try these steps after setting up ndiswrapper  [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
although it seems hardware-unspecific, or maybe this older method if it works with 6.06
[http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136).


I might just end up getting rid of the bcm4310. I have an old Buffalo USB adapter
with a ralink rt2570 chipset lying around that may work.

---

### Post by Fahuadai on 2007-02-14
If your wireless card is external, and you can afford it, then by all means use another chipset.

There should be lists, both on google and somewhere on the ubuntu website with capable cards. Sorry but I don't have time at the moment to research them for you, but try using these keywords:

"wireless,  supported, ubuntu, chipset".  

Also the FOSS website has lists of reccomended. So if purchasing, please support the companies that support linux. 

Hope this helps.

---

### Post by t341 on 2007-02-14
Thanks for the help.  I chose an adapter with the Ralink chipset because even
though they didn't release any Linux drivers, they at least released the source
so that others could.  I will be using the driver from serialmonkey.com.

---

