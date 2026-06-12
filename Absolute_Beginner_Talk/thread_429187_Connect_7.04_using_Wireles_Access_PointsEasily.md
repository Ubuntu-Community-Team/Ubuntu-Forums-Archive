---
title: "Connect 7.04 using Wireles Access Points?Easily?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by pellesnusuit on 2007-05-01
Can one connect easily using a wireless access point like (Asus wl330, Trendnet 54, Netgear Linux capable) running a live CD of Feisty 7.04 ?  I am asking because I cannot get my Dell b130 laptop to go online with any Ubuntu distro's wired or wireless.  Therefore no diswrapper or NDisgtk drivers downloadable to ubuntu o/s.  My wireless card is a BRCM 4318 Airforce one,1370.  Will any earlier versions like Featherlite-Dapper work better? Any insight would be greatly appreciated. I want this badly Thank you , Pelle

---

### Post by nanotube on 2007-05-01
give it a try... but generally hw compatibility improves between releases, so maybe feisty livecd will do it for you.
wireless is really very hardware-specific, so no guarantees...

---

### Post by pellesnusuit on 2007-05-01
Thank You for your reply. If I try a wireless access point and it works I'll post it. I Appreciate the response Pelle

---

### Post by teddybairs1 on 2007-05-01
I'm also running a Dell B130 with the exact same card that you have. Your problem is the card itself. It requires the firmware. Feisty already has the correct driver, bcm43xx, but for legal reasons they can't include the firmware on the disk. You have to locate the firmware. Someone posted a link on the forums, I can't remember where, but do a search for Broadcom 4318 firmware on the forum and you're likely to turn it up. 

This card is notorious for being nearly devilish in trying to get it to work. Under edgy, I had to use the ndiswrapper and the windows drivers. Under Feisty, the Ubuntu drivers work perfectly. You can get the windows drivers from the Dell website. They are marked as bcmwl5.sys and bcmwl5.inf and come in the driver download package. the .sys is the firmware. You can use a program called bcm43xx-fwcutter, found in the repos, to extract the firmware but I would recommend locating the .deb package here on the forum, it's a lot easier.

Search the forum, and you will find in depth guides to dealing with this little nasty of a card. You will get it working, just be patient and read everything you can. As I said, I've got one too, and I'm using it right now to write this.

---

### Post by pellesnusuit on 2007-05-01
TeddyBairs1, good info. I am getting what you are saying firmware vs. drivers. Could I ask you since we have same computer, your dell went online with edgy and feisty with a wired connection? I guess that is how you did Ndiswrapper.  I can't achieve that so far.  Maybe I can open the cd drive somehow and install firmware while live cd is going or load it on with usb? Thank you it makes a bit more sense Pelle

---

### Post by teddybairs1 on 2007-05-01
I'm not sure how to do it with the livecd. I just took the plunge and installed it on my laptop's hard drive.

You won't be able to download and install any new packages through the livecd that I know of because you can't make any changes to the iso image, which is what is loaded into your system with the livecd.

Yes, I used the wired connection to get everything running. It's a pain having a leash, but if you take the time to use it to set up the wifi, it's not too bad.

In order to get your laptop card running you have to install to the hard drive. There's no way around it. That's the only way you're going to be able to install new packages, and thus install the firmware, ndiswrapper, etc.

It's not really Ubuntu's fault. Broadcom is stingy with their drivers and firmware. The developers and people here on the forum have bent over backwards to get this card running. Broadcom could make it easier, but they won't.

---

### Post by pellesnusuit on 2007-05-02
Teddybairs1, I think I will follow suit and put on hardrive too. I'll start some of the hard work and learn abit more first. Might even buy an extra hardive. Not always as fun as just trying it but cutting corners the way I have has not worked yet.  Thank you for your ideas , Pelle

---

### Post by teddybairs1 on 2007-05-02
The Livecd is good, but limiting. The OS was meant to be installed on a hard disk.

---

