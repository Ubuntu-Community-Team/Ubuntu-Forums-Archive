---
title: "I have a fix for the wireless internet!!"
date: 2007-08-16
forum: Apple PPC Users
---

### Post by makinasvp on 2007-08-16
Anybody who is on an iBook G4 or has an airport built-in and cannot connect to the internet wireless, you're in the right thread.
All you have to do is download this:

[http://www.speedyshare.com/214793933.html](http://www.speedyshare.com/214793933.html)

Save it and install it. Then simply restart your computer and you are good to go!!
Don't forget to left click your network computer icon on the top right side and choose your connection.
Yes!! It's that easy!!!

---

### Post by pxwpxw on 2007-08-16
Yes, good one. Just installed on PowerMac G5, in debian etch. Now uising wirelees with it.

---

### Post by makinasvp on 2007-08-16
> **pxwpxw said:**
> Yes, good one. Just installed on PowerMac G5, in debian etch. Now uising wirelees with it.

You are SOOOOOOOOOOOOOO welcome my friend!! :)
By the way, this is the first time I have ever fixed something on linux and we are celebrating!!
Cheers guys! Enjoy it.

---

### Post by makinasvp on 2007-08-19
bump for whoever needs it :)

---

### Post by dombleu on 2007-08-19
Thanks man. Not working any better than a manual install of the firmware files but much easier!

---

### Post by brad_c6 on 2007-08-19
I absolutly LOVE the deb package!:lol:

---

### Post by Ripfox on 2007-08-20
DEB:

SpeedyShare doesn't know the type of this file. It may be practically everything, compressed archive, video, picture, or something else. Make sure to check the file for viruses, because computer viruses are very dangerous. If you don't have any antivirus program, consider buying one.

:lolflag:

BTW did you put together this fix or did you find it (out of curiosity)

---

### Post by makinasvp on 2007-08-20
my friend who is a linux guru came up with it. When I told him the problem about my wireless internet, he told me to install it. When I did, it worked. I was very happy so I asked his permission to post it here in the forums and he said it was ok.

No viruses by the way, if you were able to "read" the posts above yours, you can see that it worked for others as well. :):):)

---

### Post by pxwpxw on 2007-08-20
It should be posted on the powerpc sticky, since that currently bombs.
IMO.

---

### Post by Zaelore on 2007-08-20
Maybe you should put this in the wiki so it can be there for whoever needs it. The FAQ might be a good place for it. [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by Ripfox on 2007-08-20
> **makinasvp said:**
> No viruses by the way, if you were able to "read" the posts above yours, you can see that it worked for others as well. :):):)

Um, yea dude i know...i was just reposting what is posted on the site where you download the deb...I just thought it was funny how they described the .deb file type with that little rant. (notice the lol flag?)

---

### Post by Ripfox on 2007-08-20
> **Zaelore said:**
> Maybe you should put this in the wiki so it can be there for whoever needs it. The FAQ might be a good place for it. [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Isn't this just a deb package for this instruction already on the wiki?

"In Feisty the Airport Extreme support is built in, but you must fetch the firmware. Simply open a terminal and type:

sudo aptitude update

followed by:

sudo aptitude install bcm43xx-fwcutter

and reboot. Your Airport Extreme will now work."

Or is this different?

---

### Post by BS&amp;SIR on 2007-09-20
Thank you, and thank whomever wrote this fix!!!. I spent sooo much time and effort trying to get this Airport card working on  my PowerBook G4, and thanks to someone who knew what he was doing, I was up and running in less than 5 minutes. Great Stuff!.

---

### Post by ivelasco on 2007-09-21
> Isn't this just a deb package for this instruction already on the wiki?

"In Feisty the Airport Extreme support is built in, but you must fetch the firmware. Simply open a terminal and type:

sudo aptitude update

followed by:

sudo aptitude install bcm43xx-fwcutter

and reboot. Your Airport Extreme will now work."

Or is this different?

That´s OK

I can't believe my eyes.The airport extreme works on ubuntu 1 or 2 years ago (at least)

---

### Post by aantn on 2007-09-22
I'm going to try this in a few minutes. Do you think it'll work with wpa?

---

### Post by guidop on 2007-09-24
So far, I've had NO luck getting WPA to work with Kubuntu 7.04 ppc on my Powerbook 12" G4.
With WPA Personal (PSK) enabled on my network, the knetworkmanager applet does see my network, and identifies the encryption method, but when I try to connect, it sometimes gets to 28%, takes forever to time out and/or crashes.
With _encryption disabled_ on the same wireless router, it connects just fine.

(On the Oct 2006 MacBook Pro, knetworkmanager works perfectly with WPA, using the 2007May19 version of the madwifi driver for its atheros wireless chipset.)

I tried installing bcm43xx-fwcutter and copying the firmware from OS X, and using the linked .deb file with the firmware already installed.  Results for both methods are the same.

Besides the visual evidence that the firmware can see the router using knetworkmanager, running the following shows that the bcm43xx driver is working:

```
# EDITED WIRELESS MAC ADDRESS AND ESSID
$ sudo iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:01:02:03:04:05
                    ESSID:"WirelessNetwork"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=98/100  Signal level=-37 dBm  Noise level=-71 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 72ms ago
```

I know that KDE does many things differently, and I still haven't figured out where it hides its knetworkmanager configuration files, and whether they're in clear text or not.

I think my next step will be to start with a clean ubuntu command line install, add xfce and a few essential apps, and start working my way up various wireless configuration methods, seeing if wpa_supplicant can actually talk to the bcm43xx driver, and/or attempting to manually configure my /etc/network/interfaces and other files.  The wpasupplicant web page doesn't seem to explicitly indicate that the bcm43xx driver is supported.  I've been searching forum posts, but have not yet found direct evidence that anyone has gotten Linux ppc and the bcm43xx to actually work with WPA.  I hope one of us finds a way, if there is one.

---

### Post by guidop on 2007-09-30
Did a clean install of Xubuntu 7.04 on my Powerbook G4.
Ran apt-get update and apt-get upgrade.
wpa_supplicant and wireless-tools already installed with Xubuntu.
network-manager is NOT installed.

Used .deb from first post to install bcm43xx firmware.

Downloaded and installed wicd .deb from here:

[https://sourceforge.net/project/showfiles.php?group_id=194573]("https://sourceforge.net/project/showfiles.php?group_id=194573")

Rebooted.  Wicd available under Applications->Network menu.
Selected network, entered password:  Airport Extreme works with WPA-PSK wireless!

Using Xubuntu and WPA wireless on Apple Powerbook to type this now.

I think the problems with knetworkmanager are related to this bug in network-manager

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/101857]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/101857")

Maybe it will be fixed in gutsy?

---

### Post by lusephur on 2007-10-06
> **makinasvp said:**
> Anybody who is on an iBook G4 or has an airport built-in and cannot connect to the internet wireless, you're in the right thread.
All you have to do is download this:

[http://www.speedyshare.com/214793933.html](http://www.speedyshare.com/214793933.html)

Save it and install it. Then simply restart your computer and you are good to go!!
Don't forget to left click your network computer icon on the top right side and choose your connection.
Yes!! It's that easy!!!

oh i loved this fix, and i have it stored on a usb flash drive for when i reinstall my ibook. saves me having to go to the modem and wiring up the ibook, when i can just transfer the file from the flash drive to my desktop, and double click.
up and running in seconds.
thank you very much :o)

---

### Post by Archaeology_Student on 2007-10-27
going to try this on my powerbook G3 using a Belkin 54g PCMCIA that uses the Broadcom chipset that is the same chipset in the Airport Extreme cards ;) Will report back :)

---

### Post by bluet4rget on 2007-12-15
i love you

---

### Post by myles7701 on 2007-12-15
I have a 1.33 GHz iBook and I was going to just format it and install Ubuntu for the hell of it. I want to start using Linux, but had scrapped the whole idea until I read this thread. Thanks for posting that fix. I'll update you guys after I am using Ubuntu full time on my laptop!

---

### Post by Creepingdeadman on 2007-12-16
Danke mein freund.

---

### Post by Kopachris on 2007-12-16
I already figured all this out on my own after days of searching and posted it.
[http://ubuntuforums.org/showthread.php?t=550717](http://ubuntuforums.org/showthread.php?t=550717)

---

### Post by AlphaMack on 2007-12-17
For WPA connections you can actually get them to work through NetworkManager if you put in the hex of your WAP's password:

```
wpa_passphrase YOURWAPSSID
```

Type in your plain text network password, hit return, and you should get the hex to copy/paste into the NetworkManager dialog (be sure to correctly select WPA vs WPA2).

---

