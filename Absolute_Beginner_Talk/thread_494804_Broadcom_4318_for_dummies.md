---
title: "Broadcom 4318 for dummies"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by AJB2K3 on 2007-07-07
Im sorry but i just don't under stand any of this so i ask 
HTF do i get my broadcom 4318 to work on my acer laptop.
Included is some log file supposededly by ndis but as i know jack i haven't the foggest idea.

---

### Post by reset3x on 2007-07-07
> **AJB2K3 said:**
> Im sorry but i just don't under stand any of this so i ask 
HTF do i get my broadcom 4318 to work on my acer laptop.
Included is some log file supposededly by ndis but as i know jack i haven't the foggest idea.

Try this.... : [http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133)

---

### Post by AJB2K3 on 2007-07-07
Alredy installed but i cant seam to get much ferther then using iwlist to detect networks.

---

### Post by reset3x on 2007-07-07
The adapter may show up as eth0 and not wlan0.. At least it did in my case... Have you tried to configure via System/Administration/Network? 

EDIT:

Also, I had no luck with Network Manager... I just purged it (network-manager & network-manager-gnome) and did a manual config.... I also had to reboot after installing the deb...

---

### Post by AJB2K3 on 2007-07-07
how do i do that?

---

### Post by reset3x on 2007-07-07
> **AJB2K3 said:**
> how do i do that?

OK, After installing the bcm4318 deb... Reboot... Go into System/Administration/Network... Configure your adapter to log on to the network you wish to use.. This way you can at least see if your NIC is working...

---

### Post by reset3x on 2007-07-07
Also, have you looked at this thread? [http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318)

---

### Post by AJB2K3 on 2007-07-07
> **reset3x said:**
> OK, After installing the bcm4318 deb... Reboot... Go into System/Administration/Network... Configure your adapter to log on to the network you wish to use.. This way you can at least see if your NIC is working...
I dont understand anything thats going on with this wifi crap 
The must be a way for total mentally retarded people to get this crap working.

---

### Post by reset3x on 2007-07-07
> **AJB2K3 said:**
> I dont understand anything thats going on with this wifi crap 
The must be a way for total mentally retarded people to get this crap working.

I highly doubt that you're retarted.. Linux can be a little confusing when you first start using it.. 

Let's back up... What version of Ubuntu are you using? Also what have you tried so far? And lastly what is the output of lspci?

---

### Post by AJB2K3 on 2007-07-07
Thanks for the semi usefull encourage ment its now working, randomly installed some apps and a few restars later its all now working. thanks.
Now if only i can get the rest of the laptop working.

---

### Post by reset3x on 2007-07-07
> **AJB2K3 said:**
> Thanks for the semi usefull encourage ment its now working, randomly installed some apps and a few restars later its all now working. thanks.
Now if only i can get the rest of the laptop working.

You can dig around in these forums and probably find the answers to your problems... If you can't there are many users here to help you out... Just be patient :)

Good Luck!!!

---

### Post by forsberg on 2007-07-09
I have an acer laptop w/ broadcom 4318.  Here were my steps to get it working (I am a complete linux n00b):

1) At first when booting I get these bcm43xx_microcode.fw errors.  Don't worry about that.
2) Use a wired connection to get on the net.
3) Install bcm43xx_fwcutter.

After these steps, the wireless light on the laptop starts blinking and then I proceeded to to setup my wireless lan (entering WEP, SSID)... and it has been working ever since.

---

