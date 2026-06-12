---
title: "Another Nubie With Questions"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by dime2007 on 2007-05-20
OK, first ever day with Ubuntu and second day with Linux.

Yesterday I dug out an old Dell Inspiron 8100 and found that one of the last things I did with it over 2 years ago was install Mepis. After playing with is for about 20 mins I had managed, without reference to the internet, connected it to my BT HomeHub with a Linksys WPC54G card. I then had a look around for Wine as the only thing I need XP for is Football Manager 2007. I found Wine and downloaded it and then tried to install/unpack/make work (not sureof the exact term in Linux) but I think it told me my version of Mepis was to old for the version I downloaded. I then downloaded Mepis32 but for reasons I can' t explain that did not intsall in anyway. So I cast around and found that Ubuntu is a popular version of Linux and I decided to try that at it worked.

However, as I actually wish to use this laptop in real life I need a few of pointers.

1. I need to be able to use the wrieless card. No matter what setting I use it wont connect - any ideas? Why work in old Mempis but not new Ubuntu?
2. I need to be able to use a USB stick. I tried just pluugging the stick in and then leaving the stick in during start up. Neither worked. Is this becuase the usb port is USB 1.1 and the stick USB 2?
3. I need the fans to work more on the laptop - is there a setting to change somewhere.

If I can get these three things going then I am going to ditch M$ asap.

If you can answer these questions remember I am on day two of my Linus adventure then I would be grateful.

D.

---

### Post by locke.dragon on 2007-05-20
with ubuntu, as long as it installs properly, those features should work correctly right out of the box.  have you already installed ubuntu?  and if so, which version?

---

### Post by dime2007 on 2007-05-20
The iso I downloaded and burnt was ubuntu-7.04-desktop-i386 which I got from the ubuntu homepage today.

I have also found that my BTHomeHub, connected to the laptop sees it but the laptop is not seeing the internet.

I tried sudo ifconfig - a on the terminal thing and this came up:

eth0 Link encap:Ethernet    etc

lo Link encap:Local Loopback  etc

Thanks  

D.

---

### Post by dime2007 on 2007-05-20
How does one tell if the installation has been done correctly?

Thanks

---

### Post by locke.dragon on 2007-05-20
sadly, i'm not exactly qualified to answer all your questions, but i'll do my best.  

1. i didn't have a SINGLE problem with my wireless on my laptop so i can't help you there.  do some searches on this forum though, i've seen a lot of threads regarding the topic.  
2. i'm not sure about the usb stick.  but a google search brought up this.  maybe that'll help.  [http://www.everythingusb.com/usb2/faq.htm](http://www.everythingusb.com/usb2/faq.htm)
3. [http://ubuntuforums.org/showthread.php?t=432180](http://ubuntuforums.org/showthread.php?t=432180) that may help with the fans.  once again, i've never had any problems with mine.  

even if this post doesn't help much, at least it'll bump this thread to the top.  :P  maybe then someone more experienced can help you.  cheers!

---

### Post by tyres on 2007-05-20
What USB adapter is it? If you do a search in the Ubuntu forums on your Linksys WPC54G card you should be able to find out if it is supported.

---

### Post by scrooge_74 on 2007-05-20
For your wireless this should help

[http://www.ubuntuforums.org/showthread.php?t=269438&highlight=wireless+network](http://www.ubuntuforums.org/showthread.php?t=269438&highlight=wireless+network)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Try configuring the wifi using the network-manager which comes default with Feisty.

The USB port should just work, even if it is an older type. Plug something in Gnome should put an icon on the desktop.  If not open a terminal window and type dmesg and see the entry at the end which should tell about the USB device.

The fans should work out of the box as dragon said.  In some cases you may need to configure a few things or get a few modules to work so the fans work p&#341;operly, but again with Feisty they should just work ok.

Keep posting if on doubt

---

