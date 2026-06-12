---
title: "internet problems"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by steve0961 on 2008-03-28
I am having trouble understanding how to connect my laptop that I just installed ubuntu 7.10 on. Using this page ([https://help.ubuntu.com/7.10/internet/C/wireless-connecting.html](https://help.ubuntu.com/7.10/internet/C/wireless-connecting.html)) as a reference, I went to the network manager and didnt see my wireless network in the list, so I followed the link that says "If there is no Wireless Connection shown see Troubleshooting (the section called &#8220;Troubleshooting&#8221;)" This is where im TOTALLY baffled. The first direction says to open the device manager under (System &#8594; Administration &#8594; Device Manager). I go to system, then administration, then... nothing. There isnt anything named device manager in the administration drop down menu. So I decided to skip that part and went on to the next direction. I did the search for a driver, and I see a bunch of information come up including the name of the wireless card in my laptop and it has a number for the version of the driver installed, so i figure one is installed. I went to the next direction which is: 

Check device is on
1. Many wireless network devices can be turned on or off. Check to see if the device is turned on by opening a Terminal (Applications &#8594; Accessories &#8594; Terminal) and type the command: sudo lshw -C network.
2. If it is turned on then see the section called &#8220;Check for a connection to the router&#8221;.

In the information it shows me, the only thing that has anything to do with it saying on or off is in the first line which says *-network DISABLED. Im assuming that means my device is off. The documentation says nothing about how to turn it on. I have limited to no knowledge of linux (first time trying it) so you might need to dumb down any help for my sake :P Thanks.

*EDIT* sry about the I thing, i kinda hit post on accident :P

---

### Post by kool_kat_os on 2008-03-28
hmmm.... "I", thats a tricky question....:confused:

---

### Post by Joeb454 on 2008-03-28
Can you give more details than "Internet Problems I" ;)

What exactly is the problem you're having?

---

### Post by steve0961 on 2008-03-28
I edited the first post, sorry about that :P

---

### Post by Joeb454 on 2008-03-28
No worries, I'll give it a read through now :)

---

### Post by steve0961 on 2008-03-28
I think I have narrowed down my problem to the firmware for my wireless card ( Broadcom BCM4401-B0 100Base-TX version 02). When I open up the Restricted drivers page, it has "Firmware for Broadcom 43xx chipset family" in the list. From what the text in the restricted drivers page says, it makes it seem like it will never work. Is this true?

---

### Post by Joeb454 on 2008-03-29
Try using the driver in the restricted driver manager :) It might work :) Support for Broadcom 43xx chipsets has increased a load in the last year or 2 :)

---

### Post by steve0961 on 2008-03-29
> **Joeb454 said:**
> Try using the driver in the restricted driver manager :) It might work :) Support for Broadcom 43xx chipsets has increased a load in the last year or 2 :)

Tried that, a popup comes up and says "The software source for the package "bcm43xx-fwcutter" is not enabled" what does this mean?

---

### Post by dsauxier on 2008-03-29
You'll need to use a hardwired connection just long enough to download the fwcutter package.  When it installs, it will ask if you want to download the drivers (the answer is yes).  After that, you should be able to go through the wireless configuration like you tried in your first post.

---

### Post by steve0961 on 2008-03-29
Where would I find the fwcutter package and how would i install it?

---

### Post by dsauxier on 2008-03-30
> **steve0961 said:**
> Where would I find the fwcutter package and how would i install it?

Within the restricted drivers manager, if you check the box to enable the "Firmware for Broadcom 43xx chipset family" then it should install the package as long as you have an internet connection.
(that's why you need to plug into the hardwired LAN for this)

If it says it's not available, then you probably need to enable the Universe repository.

Go into Synaptic : System -> Administration -> Synaptic Package Manager
Click Settings -> Repositories
Now check the "community maintained" box 
Close the Repositories window, and click "Reload" within Synaptic.
Close Synaptic. 

Now back in the Restrictive Drivers Manager you should be able to install it successfully this time.
(note that if Synaptic is still open, you'll get an error about unable to get a lock on the apt archive or something like that)

---

