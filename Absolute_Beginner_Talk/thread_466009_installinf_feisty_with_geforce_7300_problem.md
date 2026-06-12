---
title: "installinf feisty with geforce 7300 problem"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-06-06
I have just build a new system and I am trying to get the Live CD to run, it all worked fine till I plugged in the new Nvidia geforce 7300LE video card and went to reinstall Feisty.
Now I get the menu and the loading screen but I never get the Desktop up to install Fiesty.

could there be a problem with my video card??

---

### Post by greenstar on 2007-06-06
> **ianb72 said:**
> I have just build a new system and I am trying to get the Live CD to run, it all worked fine till I plugged in the new Nvidia geforce 7300LE video card and went to reinstall Feisty.
Now I get the menu and the loading screen but I never get the Desktop up to install Fiesty.

could there be a problem with my video card??

There could be, but I don't have enough info to answer that. Sounds like you're using the Desktop CD to install.

If this is true, have you tried using the alternate install CD? That's the one I use, as it's a much better installation tool. I'd give that a go.

Also, you should check your BIOS and make sure that it is set to display on the desired video adapter. If the motherboard has on-board video, the BIOS should detect that a new Graphics card has been installed and switch to that automatically. Occasionally this doesn't work as it should and needs to be changed manually.

Consult your motherboard owner's manual & docs for the specifics on your particular BIOS.

Hope this helps,
Greenstar

---

### Post by ianb72 on 2007-06-06
> **greenstar said:**
> There could be, but I don't have enough info to answer that. Sounds like you're using the Desktop CD to install.

If this is true, have you tried using the alternate install CD? That's the one I use, as it's a much better installation tool. I'd give that a go.

I have used both the Desktop CD to install and the alternative install CD, the card works fine in XP which I just installed to try the card out.

The card is a Inno3D PCI Express x16 Geforce 7300 LE and is set up in the Bios and default, with the Live CD I can not get to the Desktop to Install and with the Alternative CD I go all the way through the install and reboot then when it comes to showing up the Login screen it is all black.

---

### Post by Songwind on 2007-06-06
> **ianb72 said:**
> I have used both the Desktop CD to install and the alternative install CD, the card works fine in XP which I just installed to try the card out.

The card is a Inno3D PCI Express x16 Geforce 7300 LE and is set up in the Bios and default, with the Live CD I can not get to the Desktop to Install and with the Alternative CD I go all the way through the install and reboot then when it comes to showing up the Login screen it is all black.

We had this exact issue with my gf's computer, a Dell Dimension 3000 with a PCI FX5500.  What happened was, the setup program detected the onboard video controller and set that up by default.  Try plugging the monitor back into your onboard VGA plug and see if it is displaying there.

I just had to add definitions to xorg.conf for the new card and restart X and everything was fine.

Edit: If you press Ctrl-Alt-F1, does it give you a text login?  If so, look in xorg.conf for the Device section of your video card.  If it is loading i810 (or another appropriate driver for your onboard video) you can bet it's doing what I described above.

---

### Post by ianb72 on 2007-06-06
Cheers I'll give that a go in a bit once it's all re-installed as I couldn't stand Windoze on my spanking new system LOL

---

### Post by ianb72 on 2007-06-06
> **Songwind said:**
> We had this exact issue with my gf's computer, a Dell Dimension 3000 with a PCI FX5500.  What happened was, the setup program detected the onboard video controller and set that up by default.  Try plugging the monitor back into your onboard VGA plug and see if it is displaying there.

I just had to add definitions to xorg.conf for the new card and restart X and everything was fine.

Edit: If you press Ctrl-Alt-F1, does it give you a text login?  If so, look in xorg.conf for the Device section of your video card.  If it is loading i810 (or another appropriate driver for your onboard video) you can bet it's doing what I described above.

OK I tried plugging my monitor into my onboard Nvidia 6100+ video with the 7300 PCI Express card in the system and got no display.
The Ctrl+Alt+F1 didn't do anything, it starts up booting fine with the Ubuntu screen then when the bar fills up the screen just goes black, but the power light stays Green on my monitor

Ian

---

### Post by greenstar on 2007-06-06
Do you have a Biostar GeForce 6100-M9 mobo?

---

### Post by ianb72 on 2007-06-06
> **greenstar said:**
> Do you have a Biostar GeForce 6100-M9 mobo?

No I have a Foxconn 6100M2MA

I have also tried using the 64Bit version of the Live CD and I still get the same problem!!

---

### Post by ianb72 on 2007-06-06
> **ianb72 said:**
> I have just build a new system and I am trying to get the Live CD to run, it all worked fine till I plugged in the new Nvidia geforce 7300LE video card and went to reinstall Feisty.
Now I get the menu and the loading screen but I never get the Desktop up to install Fiesty.

could there be a problem with my video card??

Well I have finally managed to resolve my problem and this is how I did it:

I installed Feisty using the onboard video, then installed the nvidia-glx new driver from [Latest Feisty Driver]("http://doc.gwos.org/index.php/Latest_nvidia_feisty")
I then rebooted my system and enabled the Nvidia 7300LE PCI Express card in the Bios as the default and plug in my monitor and bingo it all booted up great.

I hope that helps anyone out who has the same problem

Ian

---

### Post by greenstar on 2007-06-07
There seems to be a common thread, that being the Geforce 6100 chipset. I think it may be at the root of the problem, it seems to not want to relinquish control of video without manual intervention. Glad you were able to get your box running.

Greenstar

---

