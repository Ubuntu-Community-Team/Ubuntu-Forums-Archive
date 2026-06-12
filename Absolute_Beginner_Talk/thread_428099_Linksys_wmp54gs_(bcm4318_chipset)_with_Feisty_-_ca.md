---
title: "Linksys wmp54gs (bcm4318 chipset) with Feisty - can't get it to work"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by thorlin on 2007-04-30
I have struggled for the last week trying to get this damn Linksys PCI card to work in my sons' computer.  I'm new to the Linux world, and even newer to Ubuntu.  I have read at least 10 different posts in these forums trying to get the thing to work.  I've used ndiswrapper and fwcutter.  There are times where the hardware is detected and available in the network manager, and other times it is not.  With some solutions I can see the Linksys access point, and other times I cannot.  I'm lost, frustrated, and ready to give up.  Does anyone have any help for this card?  I've reinstalled Ubuntu a number of times, so doing a fresh install isn't a problem.  I'm on FF 7.04, but can go back to 6.10 if that is better.   I am running WPA security.  Below is a dump from my lspci command.  You can see the stupid Broadcom chipset there, but it currently doesn't show up in my network manager.  Please help.

```
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
00:10.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
00:11.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:12.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
00:12.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```

---

### Post by Devastator9 on 2007-04-30
Have you tried this link 
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5)

---

### Post by thorlin on 2007-04-30
I'll try that.  However, it looks very similar to what I have tried in the past.  I'll check it out when I get home.  Thanks.

---

### Post by thorlin on 2007-04-30
Ok.  I tried that walkthrough and things still aren't working.  I can see the two access points in my house.  However, I am unable to connect.  I put in the passphrase (using WPA-TKIP), the think spins for a bit and doesn't connect.  The light on the card then begins to flash green.  I'm not sure what the problem is.  I've triple checked the passphrase, and I am currently connected to the same AP through other devices, so it isn't the AP.

Any other thoughts?

---

### Post by GrueTamer on 2007-04-30
If you have the cd for your card, there may be linux drivers on there, and if there are, there are most likely instructions for installing them.  But be warned, it's probably an install that uses the command line, perhaps command line only.

---

### Post by thorlin on 2007-05-01
Good suggestion, but no joy.  No linux drivers on the cd.

---

### Post by Josey on 2007-05-01
I have this card and there is a .deb out there that that worked for me... just a second I'll find it.

edit:

install this
[http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133)
reboot
enjoy wireless.  :)

it's a shame you got the run around with ndiswrapper and such :(

---

### Post by thorlin on 2007-05-02
You are an absolute life saver.  After a week of work, this worked like a charm.  Awesome.  Thanks.

---

### Post by Josey on 2007-05-02
no problem... glad it worked for you.

---

### Post by alexef on 2007-05-03
Thank you! Worked for me on Acer 5610z laptop.

---

### Post by ZapComix on 2007-05-08
I am also having the same problem with the same card.  I had been running Feisty in a virtual machine using [[COLOR="Blue"]_VirtualBox_[/COLOR]]("http://www.virtualbox.org/") for a couple weeks and had no problem with the card or connecting to the internet.  I decided to install on a second drive and everything seems good except the wireless!

So my question is, thorlin (or anyone), did you install the .deb after you did other things like blacklist bcm43xx... or did you do a fresh install and run the .deb?

I am also a noob and have been been using various distros in virtual machines deciding on which to actually install and try.  I really like the whole open source thing and would hate for this one issue to ruin it  ;)

Thanks

**5/8/07 UPDATE:** I just reinstalled Feisty and ran the .deb that Josey provided the link for and I am now enjoying wireless!  Thanks :)

---

### Post by PartyTaco on 2007-05-12
How do I install the .deg file? Sorry I am a 2 day old ubuntu user. :]

I have tried becoming the root and using the command

"dpkg -i bcm43xx_compwiz18.1-all.deb"

But it just tells me it cannot find the file. It is installed on my desktop too. So I am lost and don't know what to do from here.

---

### Post by quinnten83 on 2007-05-12
Hi, 
I'm a two week old ubuntu user. When I downloaded the package, I immediately got an option to install the package. i didn't even have to use the command line. Try clicking the link again and see what options you get. 
This immediately solved the problem of my MSI netdancer card not working. So to the guy or girl that gave the link.
You are now my best friend!!

---

### Post by msubullyfan on 2007-06-02
Great!  It worked for me as well.  Does this work for Kubuntu, as well?  I can't figure out how to install a .deb package in Kubuntu (yes, I'm a total noob).

---

### Post by flukierdonut on 2007-06-11
Wow, I have been trying to get my damn linksys card to work for days..ive been looking for something like this forever! Great job! and thank god for google.:D

---

### Post by sandman772 on 2007-06-20
Thanks this help a lot.

---

### Post by vibe666 on 2007-07-06
same here, 2 pc's moved from windows xp to feisty and spent the last week trying to get the wireless working (along with 100 other things :D and this finally did it, so thanks a million mate, tis appreciated. :)

one thing tho, my wmp54gs is only connected at 11mbps instead of 54mbps.  does anyone have any idea how i get it connected at full speed?

thanks in advance.

---

### Post by tonaros on 2007-07-06
Awesome, thanks so much.

For anyone who has been trying and trying to get their card working, I had a bunch of messed up settings that stopped this from working right away.

First of all, make sure your bcm45xx is not blacklisted. Second, uninstall all the ndiswrapper stuff (through Synaptic). And finally, you'll need to modprobe bcm45xx.

Hopefully that works for you.

---

### Post by gembox on 2007-07-07
Thank you very much for the .deb!:D Saved me a lot of hassle!

---

### Post by jflaker on 2007-08-26
And it worked.....Nice!

Thanks\\:D/\\:D/\\:D/

---

### Post by desmondo on 2007-09-03
> **vibe666 said:**
> one thing tho, my wmp54gs is only connected at 11mbps instead of 54mbps.  does anyone have any idea how i get it connected at full speed?

I'm having much better luck with my WMP54GS using ndiswrapper. Step by step instructions are [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). With the kernel driver (detailed in this thread), I was getting sporadic connections at 11Mbps. With ndiswrapper I've got a solid connection closer to 54Mbps.

---

### Post by stacka on 2007-09-03
Many many thanks to Josey.  Clicked install, clicked reboot and wireless is up.
Buffalo Air Station WLI3-CB-G54L.

---

### Post by jbrockk13 on 2007-09-03
does anyone know if this will work with a broadcom bcm4318. same chipset just not a linksys.

---

### Post by Biznarie on 2008-01-08
> **Josey said:**
> I have this card and there is a .deb out there that that worked for me... just a second I'll find it.

edit:

install this
[http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133)
reboot
enjoy wireless.  :)

it's a shame you got the run around with ndiswrapper and such :(

Thanks! This worked very well for me with my WMP54GS (BCM4318)

---

