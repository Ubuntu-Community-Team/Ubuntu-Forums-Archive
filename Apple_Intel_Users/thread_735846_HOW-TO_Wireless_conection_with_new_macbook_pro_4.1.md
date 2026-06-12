---
title: "HOW-TO: Wireless conection with new macbook pro 4.1 (penryn)"
date: 2008-03-26
forum: Apple Intel Users
---

### Post by amonsul on 2008-03-26
Hi!

This is for Macbbok Pro (penryn) with Hardy Heron 32 BIT!!

1) Take the broadcom drivers from the MAC installation DVD (in "bootcamp/drivers")

2) > unrar x broadcomxpinstaller.exe

3) Install wireless driver by this command.

> sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper

4)  Then set ndiswrapper to auto load at boot time. Type:
> sudo gedit /etc/modules 
add "> ndiswrapper" to the last line and then save the file

5) Create file /etc/init.d/ndiswrapper
>  sudo gedit /etc/init.d/ndiswrapper

Add the text below, save and close
>       #! /bin/sh
      ### BEGIN INIT INFO
      # Provides: ndiswrapper
      # Required-Start:
      # Required-Stop:
      # Default-Start: S
      # Default-Stop:
      # Short-Description: enable to load ndiswrapper
      # Description: enable to load ndiswrapper
      ### END INIT INFO
      rmmod ohci_hcd
      rmmod ssb
      rmmod ndiswrapper
      modprobe ndiswrapper
      modprobe ssb
      modprobe ohci_hcd

6)  Set file access permissions
> sudo chmod 755 /etc/init.d/ndiswrapper

7) Finally, create a symbolic link call S99ndiswrapper in the folder /etc/rc2.d, from /etc/init.d/ndiswrapper
> sudo ln -s /etc/init.d/ndiswrapper /etc/rc2.d/S99ndiswrapper


Thank you all!
Andrea
[www.helios.bz](www.helios.bz)

---

### Post by DrAma999 on 2008-03-26
Tryed with Hardy beta 64 on new MBP Penryn, WPA encrypted lan and doesn't work :(
Anyway, THX

---

### Post by amonsul on 2008-03-26
Im using 32bit hardy! If you use 64 you have to "unrar" the 64bit drivers!

Try it...

---

### Post by AussieHolden on 2008-03-26
Being a newbie to Ubuntu could you make the instructions alot more clearier I have no idea what to be opening etc to get the airport working in Ubuntu ???

---

### Post by DrAma999 on 2008-03-26
> **amonsul said:**
> Im using 32bit hardy! If you use 64 you have to "unrar" the 64bit drivers!

Try it...

If you mean the broadcominstaller64.exe, is better that you know that unfortunately the bcmlw6 driver inside it doesn't work...i think that is for something else because, it can't make you recognize the card. With the bcmlw5 it recognises and make you scan all the APs but doesn't connect if the AP is encrypted, i had also tryed a lot of tutorial for setting up wpa supplicant.
:mad::mad::mad::mad:

---

### Post by cyberdork33 on 2008-03-26
> **AussieHolden said:**
> Being a newbie to Ubuntu could you make the instructions alot more clearier I have no idea what to be opening etc to get the airport working in Ubuntu ???There is a network applet in the system tray by the clock that is used to select the AP you want. BTW, "Airport" is just Apple's term for WiFi or "wireless networking". Try using the standard terminology and more people will understand what you are talking about (non-Apple people).

> **DrAma999 said:**
> If you mean the broadcominstaller64.exe, is better that you know that unfortunately the bcmlw6 driver inside it doesn't work...i think that is for something else because, it can't make you recognize the card. With the bcmlw5 it recognises and make you scan all the APs but doesn't connect if the AP is encrypted, i had also tryed a lot of tutorial for setting up wpa supplicant.
:mad::mad::mad::mad:That is the Vista driver I believe and they do not work (as suggested. I believe XP driver contains both the 32 and 64 bit drivers inside. The same bcmwl5.inf file is used to install both.

There seems to be an issue with WPA / WPA2 with people running 64bit Hardy for some reason.

---

### Post by AussieHolden on 2008-03-26
> **cyberdork33 said:**
> There is a network applet in the system tray by the clock that is used to select the AP you want. BTW, "Airport" is just Apple's term for WiFi or "wireless networking". Try using the standard terminology and more people will understand what you are talking about (non-Apple people).

Well sorry but then again is this not a apple forum for people using Ubuntu so they would know what I am talking about anyway as there apple users themselves.
:lolflag:

That feature in Ubuntu is not selecable for some reason.

---

### Post by cyberdork33 on 2008-03-26
> **AussieHolden said:**
> Well sorry but then again is this not a apple forum for people using Ubuntu so they would know what I am talking about anyway as there apple users themselves. You don't have to be sorry about it. You "Airport" card is just a Braodcom WiFi card that is available to non-Apple PCs as well. People that do not have a Mac or are unfamiliar with Apple's terminology can be fully capable of helping you.

> **AussieHolden said:**
>  That feature in Ubuntu is not selecable for some reason.I don't know what you mean by "that feature". It will not offer wireless APs until you get your WiFi card working.... (because until then, your computer cannot "see" them).

---

### Post by amonsul on 2008-03-27
so now i got a problem. I cant connect me anymore. I can see the wireless networl, but now i cant connect me.

I will look for a solution.....

---

### Post by magic-neophyte on 2008-03-27
Tried it with iMac 20" aluminium iMac,Core Duo 2.0GHz, network adapter is Broadcom BCM4328 (rev 03)

My ubuntu version is Hardy Heron Beta (8.40 beta).

A note for absolute beginners: You must add ndiswrapper to your system by installing it from Synaptic. ( Use Search function and keyword ndis ) 

It works beautifully, as long as you make sure to execute the script several times from the /etc/init.d/ directory by typing sudo ./ndiswrapper 

So it DOES seem to work quite well. And indeed, ssb and ndiswrapper conflict, unless you reprogram the ndiswrapper startup script, like it is mentioned above.

Cheers to all in Open Source,

Magic Neophyte

---

### Post by dabeeeenster on 2008-03-31
I cant find the driver on my DVD's! Curious. Can I download them from anywhere?

---

### Post by amonsul on 2008-03-31
for sure you have the driver!
CD 1   Bootcamp, driver, broadcom

---

### Post by shiver on 2008-04-09
I just got my MBP 4,1 Penryn  WLAN (bcm4328 rev 05) working on Hardy 64-bit. The driver from dell.com did not work so I used the non-free unrar package to extract broadcomxpinstaller.exe on the first Apple cd and fed the driver to ndiswrapper. It even works with my wpa2 protected network! At least everything does so far. I did manually choose "TKIP" at the connection prompt since my network uses it. Don't know if it had worked with auto settings.

---

### Post by pierrelux on 2008-04-09
Just to tell you that I have the same hardware (Macbook pro 4.1 (Penryn), Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)) and I got it working using broadcomxpinstaller.exe from the first Apple DVD. I'm writing this message on a WPA PSK + TKIP network (and had some trouble with AES... the problem maybe on the router). 

I also use Hardy 8.04 64 bits.

I have not rebooted my machine since then so I can't tell yet if there will be some sort of problem to auto-connect.

---

### Post by pierrelux on 2008-04-10
Just a quick update... it does not work so well after all. I can't connect to AP with the network manager even if the signal seems good. Playing with modprobe ssb and ndiswrapper won't help much.

---

### Post by shiver on 2008-04-10
It still seems to work for me, even after I changed my AP to use the stronger AES encryption. Connecting to the encrypted wlan is quite slow, though, it usually takes about 20-30 seconds even though the signal is good. I also had to configure the ndiswrapper module to be unloaded at suspend or I would get error messages when going to suspend.

---

### Post by kzuk9237 on 2008-05-05
This is nice...however for not working for me.

unrar is not available, so I cannot even start with the first step.

Also, other posts have said that MBP (Penryn) works out of the box with video...not the case for me.

Is there anyone out there trying to get Ubuntu to work with MBP Penryn??????

---

### Post by cyberdork33 on 2008-05-05
> **kzuk9237 said:**
> unrar is not available, so I cannot even start with the first step.install it??? Really unrar is not needed. the exe file is just a zip archive. several utilities can extract the files.

> **kzuk9237 said:**
> Also, other posts have said that MBP (Penryn) works out of the box with video...not the case for me.
What do you mean by this?

Also, please post in the new Apple forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by kzuk9237 on 2008-05-07
ok....I got the driver to work that gave me 3d capabilities (desktop effects) on my Macbook Pro. After a reboot it gave me another option for an nvidia driver...and enabled it...worked.

Wireless is another matter.

I was able to unzip and all...I followed the directions at the top of this post. First off, my Leopard DVD in the bootcamp drivers has the file as broadcominstaller.exe (without the "XP" in the name). No biggie I am thinking.

When I get to the "sudo modprobe ndiswrapper" command Ubuntu freezes on the next item I click on. Example...I enter that command after the previous commands....and then click on networks (no wireless is found) but then Ubuntu freezes....had to hold down the power button to get a reboot. This happened to me 3 times in a row.

Not sure what to do next???

---

### Post by kotter71 on 2008-05-08
> **kzuk9237 said:**
> 
Wireless is another matter.

I was able to unzip and all...I followed the directions at the top of this post. First off, my Leopard DVD in the bootcamp drivers has the file as broadcominstaller.exe (without the "XP" in the name). No biggie I am thinking.


Dude.  Look again in your bootcamp directory on the DVD.  There should be a file that explicitly says "broadcomxpinstaller".  This procedure worked perfectly for me.

---

### Post by cyberdork33 on 2008-05-08
Guys, this is only here for archival purposes. Please post in the new forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by simplebeep on 2008-06-06
> **AussieHolden said:**
> Being a newbie to Ubuntu could you make the instructions alot more clearier I have no idea what to be opening etc to get the airport working in Ubuntu ???

I agree that the instructions should be alot more clearier...
(Or, rather, that they should be a lot clearer.  JK! ;))

---

