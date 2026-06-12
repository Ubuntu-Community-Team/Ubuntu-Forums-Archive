---
title: "Wow!!! Go Gutsy!!! (wireless!!)"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by totalnub on 2007-10-11
I know the title is childish, but just as a heads up, the restricted driver manager in gutsy gave me an option to install the "dreaded" broadcom 4306 drivers. I was thinking.....yea right, this is only a beta, just wishful thinking. But i rebooted and POOF!! IT WORKS!! WOW is all i can say. Great job devs for fixing what has been a hassle for so many of us :).

(btw i installed the beta on a 4GB flash drive. lol)

---

### Post by Lord Illidan on 2007-10-11
Hmm, got it to try it on an old laptop we've got hanging around somewhere.

But does it need access to the internet to d/l those files for the broadcom? Or does it install them from the cd?

---

### Post by stchman on 2007-10-11
> **Lord Illidan said:**
> Hmm, got it to try it on an old laptop we've got hanging around somewhere.

But does it need access to the internet to d/l those files for the broadcom? Or does it install them from the cd?

When I put Feisty on my laptop the Atheros HAL was enabled by default.  I would imagine the Broadcom stuff is enabled by default.

---

### Post by crimesaucer on 2007-10-11
When I fresh installed/tested xubuntu 7.10 tribe5 and immediately did the next upgrades, I also was given the "restricted Driver" option, and since I already had my wl_apsta.o saved on a disk, all I had to do was let it install the fwcutter, and then give it the proper path to where I had my wl_apsta.o


Then it installed perfectly, and for the FIRST time since xubuntu 6.06, the Network Settings Manager worked, and I could detect my neighbors wireless networks perfectly. (which I couldn't get to work correctly in 6.10 and 7.04, so I always had to use wifi radar and then wicd.)


I still don't know how well it actually works because I don't know the passwords to their wireless streams, so all I know is that it detects their networks, but at least I didn't have to install wifi-radar or wicd to be able to detect wireless streams which is the only way I could get it to work in Edgy and Feisty...

---

### Post by RomeReactor on 2007-10-11
> **Lord Illidan said:**
> Hmm, got it to try it on an old laptop we've got hanging around somewhere.

But does it need access to the internet to d/l those files for the broadcom? Or does it install them from the cd?

I would hazard a guess and say that since that was the Restricted Drivers Manager, then the drivers are not on the CD.

---

### Post by kevdog on 2007-10-11
Not to spoil the party, but why do you want the native bcm43xx drivers right now (maybe in the future but right now).  Max bandwidth 11 Mbs/sec vs ndiswrapper at 54 Mb/sec??  Even though ndiswrapper is a pain in the butt to get set up, Ill choose more bandwidth all the time.  The only reason at this time I would know why anyone would want the bcmr43xx drivers is if they want to use aircrack/packet injection or something similar.

---

### Post by drs305 on 2007-10-11
I just installed Gutsy via the alternate CD. Wireless (broadcom 4312) didn't work right away. Went to System, Admin, Restricted Drivers and the Broadcom driver was already listed (and unchecked). Once I checked it, gutsy automatically downloaded and installed the restricted drivers (with warnings/notes about the restricted drivers not being supported by ubuntu). Really painless.

When the laptop discovered the signal, it asked for the WEP code and connected right away.

Kudos to the gutsy crew.

---

### Post by crimesaucer on 2007-10-12
> **kevdog said:**
> Not to spoil the party, but why do you want the native bcm43xx drivers right now (maybe in the future but right now).  Max bandwidth 11 Mbs/sec vs ndiswrapper at 54 Mb/sec??  Even though ndiswrapper is a pain in the butt to get set up, Ill choose more bandwidth all the time.  The only reason at this time I would know why anyone would want the bcmr43xx drivers is if they want to use aircrack/packet injection or something similar.

Can you explain this a bit more? Thanks.

---

### Post by funrider on 2007-10-12
we need a new list of supported wifi chipset
great report!

---

### Post by crimesaucer on 2007-10-12
> **kevdog said:**
> Not to spoil the party, but why do you want the native bcm43xx drivers right now (maybe in the future but right now).  Max bandwidth 11 Mbs/sec vs ndiswrapper at 54 Mb/sec??  Even though ndiswrapper is a pain in the butt to get set up, Ill choose more bandwidth all the time.  The only reason at this time I would know why anyone would want the bcmr43xx drivers is if they want to use aircrack/packet injection or something similar.

Also, I have another question:

I have noticed that my neighbors wifi streams are detected at about 60% - 70% in the Network Settings Manager in xubuntu 7.10 tribe5 plus the newest upgrade.

And also, in my newly installed Archlinux 2007.08-2, using the newest testing  xorg-server and brand new testing xf86-video-intel... I get the same 60% -70% detection, which is 3 bars using the wireless app called Wicd.


I had used the bcm43xx driver on both of those with the fwcutter and the w_lapsta.o
 

...and then when I log into my Windows Xp partition, the same exact wifi stream is only detected at about 1 bar in the Windows Wireless program. 


So I'm wondering if my 60%-70% is a misread percentage. And I'm also wondering if I uninstall the bcm43xx driver and go through the trouble of installing ndiswrapper, if it really is worth it?


...and I have to admit, the couple weeks that I actually had to use wireless with my xubuntu (using wifi-radar and the bcm43xx with fwcutter and w_lapsta.o), the stream was always dropped and very difficult to connect to and detect. I ended up just using my Windows Xp partition.

---

### Post by Ayuthia on 2007-10-12
> **kevdog said:**
> Not to spoil the party, but why do you want the native bcm43xx drivers right now (maybe in the future but right now).  Max bandwidth 11 Mbs/sec vs ndiswrapper at 54 Mb/sec??  Even though ndiswrapper is a pain in the butt to get set up, Ill choose more bandwidth all the time.  The only reason at this time I would know why anyone would want the bcmr43xx drivers is if they want to use aircrack/packet injection or something similar.
The bandwidth that you are referring to might be only restricted to certain chipsets.  The 4311 is now able to get 54 Mb/sec using Gutsy (since Gutsy is running with a kernel > 2.6.20.6).

---

### Post by crimesaucer on 2007-10-12
> **Ayuthia said:**
> The bandwidth that you are referring to might be only restricted to certain chipsets.  The 4311 is now able to get 54 Mb/sec using Gutsy (since Gutsy is running with a kernel > 2.6.20.6).

How about the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


...and is there a command that I can use to find out info on bandwidth amounts?

---

### Post by Lambert on 2007-10-12
> **crimesaucer said:**
> How about the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


...and is there a command that I can use to find out info on bandwidth amounts?

Run [COLOR="Sienna"]iwconfig[/COLOR] from command line, it will tell you quality of connection.

Look for this.

Bit Rate-36 Mb/s

---

### Post by Joeb454 on 2007-10-12
I'm pleased. Bought a new Laptop earlier, and I'm going to dual boot it between Ubuntu & Vista (compatibilty with Uni App's main reason for keeping Vista).

Got a WPA secured wireless network at home, so I figured I'd pop the Live CD in to give it a try, and try out the 64-Bit version at the same time, given that the Proc is a Core 2 Duo.

Asked for the passkey, and away I went, surfing the net to my hearts content, so much better than Fiesty

---

### Post by guillepb on 2007-10-12
Hmmm, I only get 24 Mb/s with my 4311 (on the latest Gutsy, all updates installed). Is there anything I'm doing wrong?

---

### Post by crimesaucer on 2007-10-12
> **Lambert said:**
> Run [COLOR="Sienna"]iwconfig[/COLOR] from command line, it will tell you quality of connection.

Look for this.

Bit Rate-36 Mb/s

Thank you, it's funny, I had just figured out that I could check it with iwconfig when I ran that command to check my ESSID info....but since I don't have a wifi network that I can connect to, I am still unable to find out what rate of bandwidth my 4318 rev2 is capable of getting.


EDITED: I edited my new question because I realized my mistake.

---

