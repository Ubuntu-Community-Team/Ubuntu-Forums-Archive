---
title: "Live CD Doesn't Boot"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by HyperHacker on 2006-08-26
I just burned a copy of the Ubuntu live CD for 32-bit x86 on a 700MB CDRW. When I start it up the boot screen appears, but after selecting any option, it's just a blank screen with a blinking cursor in the corner and all I can do is hit Ctrl+Alt+Delete to reboot. The CD-ROM spins for a while then just stops.

My computer:
OS: Windows XP Pro SP2
CPU: AMD Sempron 2800+, Socket 754 (runs at 1.6ghz, but OCed to 1.7)
Motherboard: MSI K8T Neo-V with onboard sound/LAN
RAM: 1GB PC3200 400mhz x1
Video: 128MB Chaintech Volari V3 XGI
HDDs: 250GB 7200RPM Western Digital (from old computer), 20GB (not sure what brand or speed, but way slow, from old computer)
Optical: NEC DVDRW ND-4551A
PSU: Xeon 400 watts

I suspect my video card is to blame (it's a pile) but even Safe Graphics Mode and Check CD For Defects don't work.

---

### Post by GuitarHero on 2006-08-27
You probably burned it too fast.  Burn the iso very slowly.

---

### Post by JNowka on 2006-08-27
Whats your monitors max resolution?  If it is low, then try using the key to choose VGA thats listed on the bottom and select the appropriate resolution.

---

### Post by HyperHacker on 2006-08-27
I think up to 2048x1536. That's the highest I can select in Windows anyway. However the card also has a DVI port which I have a second monitor connected to, and that can go up to 1152x864.
I'll try burning the ISO again since I didn't realize I should have got Kubuntu instead anyway. (Not a fan of GTK.) Probably take a while to download though.

---

### Post by KGH on 2006-08-27
I had the same problem. It took 4 tries before I burned a workable CD. I slowed the speed down to 4X in order to get a good burn. 

KGH

---

### Post by Jerome36 on 2006-08-27
Yup, my first burning attempt ended in failure.  I updated the firmware on my burner and then went with a slower speed for the next burn, and it worked fine.

---

### Post by HyperHacker on 2006-08-27
I tried burning Kubuntu at the lowest speed possible and got the same result, but it ran fine on my laptop, and the Check For Defects option didn't report any problems.

---

### Post by superpctech on 2006-12-30
Same problem here. I tried almost everything, but the fix was to take out the XGI Volari and install a GF2 MX200 card. Now live works and I can install to HD. Now to figure out how to get the XGI card to work??

---

### Post by bakegoodz on 2006-12-30
Sorry, it sounds like the hardware detector is not setting up Xorg right, this confirms this if you can press crtl-alt-F1 and you get the command line. What video card do you have? If this is an option, try another video card. Though you could probably configure Xorg to work, you will need to start looking at Xorg howtos and manuals. Running "dpkg-reconfigure xserver-xorg" will be easier than editing /etc/X11/xorg directly. If you think you got Xorg configured right type "sudo /etc/init.d/gdm restart" and see if it works. Though If you got it to work on the LiveCD it would lose the settings on next reboot. The alternative install CD will install Ubuntu in a easy to use text based install.

---

### Post by HyperHacker on 2006-12-30
> **HyperHacker said:**
> Video: 128MB Chaintech Volari V3 XGI
But since this card sucks and the rest of the system isn't a lot better I think I'm just going to replace it eventually.

---

### Post by superpctech on 2007-01-04
more like UBUNTU sucks! I am really getting frustrated with Linux. Why cant xorg boot with a xgi volari card, instead of crashing everytime? i have tried ubuntu, xubuntu, and altenative installs (though no choice for video card during install) nothing works. Vesa, Trident, Voodoo, and others havent worked either. This is one reason that linux still isn't very popular, way to much hassle to get things to work!

---

### Post by HyperHacker on 2007-01-04
Well I dunno about Ubuntu but the card is definitely a piece of junk, or at least the Windows drivers are. It's agonizingly slow and likes to freak out at random.

Still, you'd think for something so cheap (~$100 when I bought it quite a while ago), someone would have hacked together a driver for it.

---

### Post by HellionDarkLord on 2007-02-22
I have the same video card.  You can make Edgy work (not very well considering you can't scroll up or sideways without the screen messing up terribly)  If you really want to go through the hassle of upgrading from within Dapper and doing the apt-get dist-upgrade method.  Then when you reboot hit escape and type in ```
sudo dpkg-reconfigure xserver-xorg

```

It will ask you if you would like to try and auto detect your card.  say yes or no, the outcome is the same becuse it says you don't have a video card installed.  on the next screen either hit enter if you told it to auto-detect or choose the trident driver.  just hit enter whre it asks for the name of the card and the ammount of ram on the card and let it choose the default setting for everything.  When it asks about the framebuffer It doesn't seem to make any difference on my machine.

This isn't a good way to do things, and I'm working on getting things to work the correct way, but I have a lot of work ahead of me on this one because I have to go through all the xorg settup documentation and find a better answer.

I don't like not being able to scroll back up in a browser or ANYTHING for that matter.  you can't work in Synaptic or anything.  Amazingly enough you can scroll down, but that's about it.

I don't want to loose all of my data and songs that I paid for so I'm going to make this work one way or another.  without rebooting.

hope that this helps.

---

