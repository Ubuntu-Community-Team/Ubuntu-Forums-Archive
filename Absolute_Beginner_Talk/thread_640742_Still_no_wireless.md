---
title: "Still no wireless"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by CasPol on 2007-12-14
Hi there

I have tried, and tried, but still no wireless running. I have a broadcom 802.11g card. I have donwnloaded fwcutter and my win.sys driver ready and waiting on my ubuntu desktop. Can anyone tell me in simple  terms, and please , please, please, step by step, what I should do next.

Thanks !!!

---

### Post by Cybergod on 2007-12-14
Try this guide: [http://ubuntuforums.org/showthread.php?t=201902]("http://ubuntuforums.org/showthread.php?t=201902")

---

### Post by skrribble on 2007-12-14
1.first download and install ndiswrapper-utils and ndiswrapper-common
```
sudo apt-get install ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9
```

2.then install the gui for ndiswrapper
```
sudo apt-get install ndisgtk
```

3.then access the gui for ndiswrapper from System>Administration>Windows Wireless Drivers

4.Press the "Install new Driver" button and find your driver... 

there you go.. that should do it

---

### Post by skrribble on 2007-12-14
by the way... here are the .inf and .sys files that i used for two of my broadcom cards

---

### Post by Cybergod on 2007-12-14
> **skrribble said:**
> by the way... here are the .inf and .sys files that i used for two of my broadcom cards

Yes, the drivers used are important.  I tried three different sets of drivers and none of them worked form me.  I did find drivers that worked and I'll attach them.

*EDIT:  Well it didn't attach my attachment.  How did I get it to attach?

---

### Post by siciliancasanova on 2007-12-14
There is a little paperclip next to the emoticons.

---

### Post by Cybergod on 2007-12-14
> **siciliancasanova said:**
> There is a little paperclip next to the emoticons.

That's what I clicked, it opened a new window and I uploaded the attachment.

Never mind, apparently my attachment exceeds the maximum file size and can't be attached.

---

### Post by siciliancasanova on 2007-12-14
Oh, you need 6 cups of Ubuntu before you can post attachments.

Seriously though, not sure why it's not working for you.

I'm uploading an image right now to test it. *Edit* yes it seems to work

---

### Post by Papa-san on 2007-12-14
Here are some drivers:
There are a few links in my signature line that should help...

---

### Post by anewguy on 2007-12-14
An important step:

If you are using ndiswrapper so that you can use a Broadcom chipset wireless card, you also need to add to the blacklist to stop the default driver from clobbering what you are trying to do:

sudo gedit /etc/modprobe.d/blacklist

go to the end of the file and add:

# black list default Broadcom 43xx driver
blacklist bcm43xx


the save the file and exit.  To make things simple just reboot at this point.

A brief overview of using ndiswrapper for Broadcom wireless cards:



- edit the /etc/modprobe.d/blacklist file to blacklist the default bcm43xx driver

- install ndiswrapper and the ndiswrapper_utils

- sudo ndiswrapper -l    <- see if any driver is already there - if so you need to remove it with   sudo ndiswrapper -r  xxxxxxxxx    <-- where xxxxxxxx is the driver name that showed

- sudo ndiswrapper -i xxxxxxxxxx  <--(that's a lower case "I") the driver file to install (if not in current directory be sure to specify complete path)

- sudo ndiswrapper -l  <- be sure your driver shows as loaded and available

- sudo depmod -a

- sudo modprobe ndiswrapper


(I think I covered it all).  Everytime I've needed to use ndiswrapper because of a Broadcom 4300 series wireless adapter this has worked for me.  Hopefully it will work for others as well!:)

---

### Post by CasPol on 2007-12-15
Thank you, and I really mean thanks a lot for all your advise everybody. I have tried it all but I am an sorry I now completely lost. I really have trouble working with this SUDO thing....
Also ndiswrapper is downloaded, but I cannot work out how to get the GUI to work. I have been trying all this for days on end now but not much luck. The other thing is, some people say use ndiswrapper, others say do not use it. For a total beginner in LInux this is just to confusing. I am sure all of you really want to help, so let me explain I have no experience with SUDO at all, and really do need it step by step..... 
The card in my laptop is a Broadcom. What do I need to get it working, where do I find to get what I need. How do I dwonload it, how do I get to install the required applications, and so on .....

Many thanks !!

---

### Post by jbalazs on 2007-12-15
I see you pain I have the same problem in 7.10, it should be so hard

I had no problem in 6.06 I used wifi radar that did it

---

### Post by gleble on 2007-12-15
I too am trying to install Broadcom wireless and feel pretty much as described above.
See thread [http://ubuntuforums.org/showthread.php?t=641416](http://ubuntuforums.org/showthread.php?t=641416)
Can someone please explain

---

