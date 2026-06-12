---
title: "edgy virgin in need of assistance"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by circa63 on 2007-02-24
i have just installed edubuntu 6.10 on to a new hdd. have had a little play and i'am more than impressed. just a couple of questions. :confused:  how do i connect to the internet using my talktalk isp? do i use set-up cd they sent. i have no idea about server's ect. sorry for sounding like a dimwit, but can someone plz help. i just have to get away from the masses![http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

---

### Post by robophred on 2007-02-24
Can you give some information about your isp?  I use a cable box connected through a network, and it worked out-of-the-box for me.  The cd they sent you probably wont function (I am assuming it is just a windows installer).
There are probably settings you need to get from your isp (ip, dns, et al), call their support line if you can, and ask about a manual setup (probably best not to mention linux, or they will be too confused to talk if they are anything like the standard customer service that seems to be out there).
I will poke around at the Ubuntu control center and see if I can find anything that might help.

---

### Post by arochester on 2007-02-24
Tell us more about your (modem) router Make? Model? I have a feeling that TalkTalk supply a USB. Hope it's not a Speedtouch...

---

### Post by slayerboy on 2007-02-24
IIRC TalkTalk requires special software to connect to it's service.  I know in PCLinuxOS they were working on a way to work around that.  You can try doing a search on the [PCLinuxOS forums]("http://www.pclinuxos.com/forum/index.php") for TalkTalk and see if it pulls anything up.

---

### Post by circa63 on 2007-02-24
i'am using an out of the box modem sent by isp and the install is for windows. i will try your advice of giving them a call ( though i don,t expect as promt a responce as yours ) i will keep a look out for anything you may be able to find for me. many thanks for your quick rely. if everybody in the community are as helpfull as youself, i,ve made the right move. thanks

---

### Post by circa63 on 2007-02-24
Yes it's a usb Speedtouch. And i,am guessing that's not good!

---

### Post by arochester on 2007-02-24
The USB Speedtouch 330, (Alcatel or Thomson) possibly can be made to work - but it can be very difficult. I was given a Speedtouch 330 by Tiscali, but after reading an article in Micromart magazine I bought a BT Voyager 205 from Ebay. It has been very easy and worked almost faultlessly,

---

### Post by slayerboy on 2007-02-24
> **circa63 said:**
> Yes it's a usb Speedtouch. And i,am guessing that's not good!


Try this [The Linux Kernel SpeedTouch Driver And Ubuntu]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")[ ]("http://www.linux-usb.org/SpeedTouch/")

---

### Post by geekgod on 2007-02-24
Off topic: the thread title could only work in this forum :)

On Topic get a 2Wire via Ethernet or wireless imho best for Linux cuz they are bsd based

---

### Post by robophred on 2007-02-24
What I found was the system->control center->Network settings, under the 'DNS' tab.  My thought was that your isp doesn't support whatever it is that lets Ubuntu automatic load that information, but if the hardware itself needs a driver, than it probably will automatically get what it needs when the driver is functional and the kernal finds the hardware.

---

### Post by circa63 on 2007-02-24
A great big thank you to all that replied to my request for help. I will try all info given. Exellent forum, big up to you all.

---

### Post by StevenHarper on 2007-06-04
I have made  a USb Modem Manger package that works with Speedtouch Modems, you can get it here

[http://www.squeezedonkey.com/svn/linux/trunk/releases/](http://www.squeezedonkey.com/svn/linux/trunk/releases/)

Read about it here 

[https://launchpad.net/usb-adsl-modem-manager](https://launchpad.net/usb-adsl-modem-manager)

and post any support Questions here

[http://ubuntuforums.org/showthread.php?t=445701](http://ubuntuforums.org/showthread.php?t=445701)

Steve

---

