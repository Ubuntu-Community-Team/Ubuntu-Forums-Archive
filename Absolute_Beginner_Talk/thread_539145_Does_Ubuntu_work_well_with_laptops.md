---
title: "Does Ubuntu work well with laptops?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Parkinsons on 2007-08-30
I have been using Ubuntu on my desktop for about a month now and I love it! I would love to completely switch over to Ubuntu, including my lenovo R60e thinkpad. I was curious if Ubuntu was laptop ready? Does it have power management, wifi, and Fn key support without having to speed a long time figuring it out?

---

### Post by oilchangeguy on 2007-08-30
> **Parkinsons said:**
> I have been using Ubuntu on my desktop for about a month now and I love it! I would love to completely switch over to Ubuntu, including my lenovo R60e thinkpad. I was curious if Ubuntu was laptop ready? Does it have power management, wifi, and Fn key support without having to speed a long time figuring it out?

your best bet is to boot from the live cd and have a look for yourself. everything should be fine, except the fn keys. those are usually part of each computer makers setup (restore cd).

---

### Post by raja on 2007-08-30
Generally speaking - yes. 
Power management, wifi support, suspend and hibernate are all mature.
However, the amount of work you may need to put to have everything work on your laptop will depend on the hardware on it.
Ubuntu and ArchLinux both run perfectly on my Thinkpad X40. You can have a look at [this site]("http://www.linux-laptop.net/") to see how Linux might behave on your laptop.

---

### Post by ericmitz on 2007-08-30
I've been using Ubuntu on laptops (HP, Toshiba, Dell, Alienware, etc), since 2004 (Warty Warthog). The only really consistent issue i've run into is getting wireless networking going, but its never taken me more than a few hours to get it going.

---

### Post by linux noooob on 2007-08-30
I have been running ubuntu on my acer aspire 3610 for a year now and i could not be happier there is nothing i love more than my ubuntu. There is a bit of issues with wireless but i fixed that with a software called wicd go to: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)  also you may want to install wine  it is in the add remove programs tab and it is awesome! It lets you run windows apps on linux!! Last if you are a video game freak like me you might want to download the java console in the add/remove tab it makes installing it allot easier . Anyway ubuntu is the best open source linux out there!!  
p.s. Oh and if your comp is slow like mine off the live cd use safe graphics mode!!

---

### Post by FuturePilot on 2007-08-30
I have an old Dell laptop that works just about perfectly with Ubuntu. The only thing that doesn't really work is Suspend, but I really haven't fooled around with that too much to get it working. And I also have a new HP laptop. It took a little more work than I expected, but it's working great now.

---

### Post by funrider on 2007-08-30
check if your laptop model is fully support in the forum first!!
i have a cheap acer laptop which loaded fiesty happily except for the wifi part, end up getting a cheap external wireless card but i can live with it

Fn key, track pad are both working well for me.

---

### Post by ragrim on 2007-08-30
Im running Ubuntu 7.10 Gutsy 64 bit on my Acer Travelmate 4234 and its working perfectly, Wireless worked straight away, sound video the lot. havnt had any problems yet.

1 thing i havnt tested is my webcam but i know it was detected.

---

### Post by ts51 on 2007-08-30
If it works on the PS3, Apple Computers, and Virtually every computer made in the last 10 years, it will work on your laptop.

---

### Post by JeSTeR7 on 2007-08-30
Works perfectly on my Inspiron 5150.  Fn key support for volume and brightness right out of the box.  As was said above, the only thing I had to fight with was wifi, but after a few hours it works perfectly too.

---

### Post by Parkinsons on 2007-08-30
Thanks, I'm a little worried about the wifi but I will give it a go.

---

### Post by crispy_420 on 2007-08-30
I have it three laptops of various hardware:

Dell Inspiron 2500 (700MHz Celeron - 320MB ram)

Averatec 5400 series (Athlon XP Mobile 1800 - 512MB ram)

Acer 5060(?) (Intel Core 2 1.6MHz - 1024MB ram)

And all work well some minor tweaking of small things.
The one thing I would even worry about is your wireless card. But just test with LiveCD to be sure.

---

### Post by FuturePilot on 2007-08-30
The Fn keys work perfectly on my Dell Inspiron 8200. I probably could get suspend to work if I fooled around with it enough.

---

### Post by marsmissionaries on 2007-08-30
The r60e uses an atheros chipset for wireless, so it should work fine. You will need to plug it into a wired network and then install madwifi.

---

### Post by cessna_89702 on 2007-08-30
Yea every thing should work but like the other person said it could take time to get things like wireless working. my hibernate doesnt work though

---

### Post by exile on 2007-08-31
I've generally found that non-cutting edge laptops (the ones that require really specialised hardware) are very well supported by Ubuntu. I have run ubuntu on 4 different laptop models in the last few years - 3 dells and a compaq. The most recent batches of Dell's (Insiprion Intel models in particular) have worked without any hitches or any special deep linux knowledge. Your mileage may vary, but live CD distros are your friend in these cases :)

---

### Post by Atomic Dog on 2007-08-31
Works very well on my centrino laptop

---

### Post by tact on 2007-08-31
I have a company supplied Dell Latitude D410.  It had winXP on it until it refused to boot one day - I booted from a Edgy liveCD and found most things worked out of the box, including wifi.   

All the Fn keys work great, even the volume up/down and mute soft-buttons work!  

About the only thing that didnt work well was suspend/hibernate.

I upgraded to Feisty when it was available.  Same experience - suspend/hibernate were not reliable still.  And eventually I discovered DVD burning was very unreliable.

Since then I followed another thread on this forum to update the standard kernel (just the kernel) to the one used in Gutsy (2.6.22-*-generic) and to my great pleasure now DVD burning AND suspend/resume work perfectly too.  Now its 100% good.  :)

---

### Post by neo_weapon on 2007-08-31
I had an old toshiba portege in which i used xubuntu and had no problems with it. Yes, it is the best bet to try it on live cd first and see if there are any problems.

---

### Post by anewguy on 2007-08-31
I have a 1 year old cheap Gateway laptop, and I thought I'd mention the specific things I had trouble with so that you might be prepared for similar things - maybe search for the answers before you start your install so you can get it done quicker.

First, do these commands:

"lspci"  will list the devices on the PCI bus so you can look through them for the name/chipset of various pieces of hardware - video, audio, wireless to name a few of the main ones,  The list can get long so you just have to scroll through it.

"sudo lshw"  will list the hardware on your system.

"sudo lshw -C network" will list only the network devices on your system.

And now the 4 things I had to get working on my laptop:

(1) Video - seems pretty common to Linux in general, and laptops are no different.  Know the video chipset and try reading the forums for any info and drivers before you install.  "lspci" usually helps with this.

(2) Wireless - again, this is a common issue.  Know the chipset being used (hint: try "lscpi" or "sudo lshw -C network").  This can seem frustrating but if you know the basic steps it is much easier.  There are more and more users that are/need to use ndiswrapper and the windows versions of the wireless drivers.  Read up on ndiswrapper ahead of time and track down your Windows drivers

(3) Sound - another common issue.  Again, from "lspci" or from "sudo lshw" you should be able to determine what you have, research it ahead of time, and be prepared for it.

(4) One that most people seem to overlook for some reason:  the touchpad.  If you have a touch pad, and if you are installing Ubuntu and not Kubuntu (I don't know the package for KDE - maybe the same one will work), you will want to do the following after installation:

- using synaptic package manager, install gsynaptics
- in the "touchpad" section of xorg.conf, add the following:
      Option   "SHMConfig"  "true"
- reboot

that will give you the "touchpad" option under system/preferences where you can do things like turn tapping off/on, set scrolling, etc..  It is MUCH easier than the post you might see where someone says add "x" to your xorg.conf, as it provides much greater configurability.
:)

Once you know those things ahead of time, you can cut down the time spent actually trying to get things working considerably, and there won't be so much frustration in the process.

"lspci"  will list the devices on the PCI bus so you can look through them for the name/chipset of various pieces of hardware - video, audio, wireless to name a few of the main ones,  The list can get long so you just have to scroll through it.

"sudo lshw"  will list the hardware on your system.

"sudo lshw -C network" will list only the network devices on your system.

In summary, my laptop works great under Ubuntu.  I went through some headaches trying to track down the above issues after I installed, so if you are aware of them ahead of time, do the research for them and have instructions ready for them after you install, it should be a pleasant experience for you as well.:)

---

### Post by laidback on 2007-08-31
Re wifi
Check in the approved hardware list for wifi:-
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I've just finished installing Ubuntu 7.04 onto my daughter's Packard Bell laptop, I'm delighted.

I used a Netgear WG511T pcmcia card which worked out of the box.
I've also tried D-link Airplus DWLG650 which worked out of the box. 
If I bought again I think I'd go for the D-Link as it appears to pick up a signal better (stronger and further away).

Everything I wanted to install worked first time including:-

Mp3 codecs
DVD + codecs
Skype VOIP
Ekiga VOIP and landline calls via Voipstunt a/c
MSN via Gaim
K3b CD burning
Frostwire (Limewire for Linux)
Amarok music player 
.
.
etc

By Xmas I'll know how she got on with it at University, away from home.

The laptop is a Packard Bell Easynote M5255 with upgraded memory (original 256Mb + new 512Mb from Crucial) and hdd (60Gb)

---

### Post by philven on 2007-08-31
I installed Ubuntu Feisty Fawn (7.04) on an HP zv5370 Pavilion laptop with a Broadcom wireless chip built-in.  It took me 4 hours from start to Internet to complete the install.  I had to search the forums on how to get the Broadcom chip working>  WCID helped.  My biggest complaint is the touchpad.  I brush against it when I type and the cursor ends up who knows where.  I may disable the touchpad and use a mouse, except when the laptop is on my lap.

Best advice, read through the forums here.  It is the best source of info available and it has helped me alot.  Good luck.

---

### Post by swisscow on 2007-09-01
Lots of success stories here - and rightly so. Ubuntu works well. However a note of caution, some laptops aren't so happy with linux. If you are happy with things such as internal card readers, Fn keys, suspend and hibernate not working, then fine. You can try to get things working but sometimes, especially with newer models, you just can't. I speak from experience - bought a Sony Vaio on impulse, spent 3 days googling to get things working, gave up and put it on ebay!

Next time I will research a LOT MORE!

---

### Post by tact on 2007-09-02
> **philven said:**
> I installed Ubuntu Feisty Fawn (7.04) on an HP zv5370 Pavilion laptop with a Broadcom wireless chip built-in.  It took me 4 hours from start to Internet to complete the install.  I had to search the forums on how to get the Broadcom chip working>  WCID helped.  My biggest complaint is the touchpad.  I brush against it when I type and the cursor ends up who knows where.  I may disable the touchpad and use a mouse, except when the laptop is on my lap.

Best advice, read through the forums here.  It is the best source of info available and it has helped me alot.  Good luck.

Philven - try searching these forums, or googling, for the word "syndaemon".

This is a tool, its in the repos if I remember correctly, that can be set up so that your touch pad is not totally disabled.  It can be set so that it is automatically disabled while typing and only re-enabled if there has been no key pressed for say, 2 seconds. 

I find it works well for me.   Sorry I cannot be more specific about how to get and install it.  I set it up too long ago.

Some touch pads also need extra lines in the xorg.conf file so that things like scrollwheel emulation works too.  If you search here you will find info for enabling touch pad features.

PM me if you need more help and I can see what I can dig up.

---

### Post by puuma2 on 2007-09-02
I have ubuntu on a acer 2420 but not sure how to get my LCD tv connected, when I connect vga to tv on pc mode it finds nothing in windows I had an easy option of select monitor and output to vga any suggestion would complete my happiness

---

### Post by misfitpierce on 2007-09-02
Yes most laptops work fine with ubuntu

---

