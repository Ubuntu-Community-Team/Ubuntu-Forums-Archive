---
title: "Please help! Nvidia 8600gt no desktop!!!"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Alistair1234 on 2007-11-15
Hi, I'm having major problems sorting out my graphics card (nvidia 8600gt). I have inserted it in the computer and attempted to boot ubuntu 7.10 which was working before on ATI integrated graphics but it gets to the line "running local boot scripts (/etc/rc.local)" and then stops. I can get a comand line which lookes the same as it did in terminal before but don't know how to get the wireless internet connection working to download the correct driver (if this is even the problem!). I just can't get a desktop and don't know how to speak computer!

The I am a total newbie when it comes to ubuntu so any replies in baby talk please :)

---

### Post by njparton on 2007-11-15
If I were you I'd reinstall chosing the safe graphics mode on the menu reinstall. You may also have to remove quiet and splash from the options to avoid a black screen.

Otherwise boot into the command line and edit your xorg.conf file so that you're using the VESA drivers to start off with for your new card.

There are loadsa posts on this if you search the forum.

---

### Post by nikolas68 on 2007-11-15
To install support for Nvidia cards, follow these steps:
1. Select System &#10148; Administration &#10148; Synaptic Package Manager.
2. Click the Search button and enter nvidia-glx as a search term. In the list of results, click
   the check box next to nvidia-glx and also nvidia-settings, so that both are marked for
   installation. Then click Apply.

---

### Post by BCRailrodder on 2007-11-15
> **Alistair1234 said:**
> Hi, I'm having major problems sorting out my graphics card (nvidia 8600gt). I have inserted it in the computer and attempted to boot ubuntu 7.10 which was working before on ATI integrated graphics but it gets to the line "running local boot scripts (/etc/rc.local)" and then stops. I can get a comand line which lookes the same as it did in terminal before but don't know how to get the wireless internet connection working to download the correct driver (if this is even the problem!). I just can't get a desktop and don't know how to speak computer!

The I am a total newbie when it comes to ubuntu so any replies in baby talk please :)

This may not be related to that (or any new) card as I had the same issues with an older TNT card.

I did reconfigure my xserver and rebooted removing the spash and quiet commands.

The machine halts the same place and will not proceed until I press enter and get passed it, dropping   me to tty1.

Checking the dmesg doesn't show anything glaring with the following exceptions - apparently I have no HIGHMEM available but 382 mb Lowmem is available and EISA detected 0 cards (which is strange as I have had sound available previous to the clean install)

This is on an older HP 7940 1ghz machine with 384 megs memory doing a clean install.

Hope that this helps,

Kent

---

### Post by Crafty Kisses on 2007-11-15
What are all your specs?

---

### Post by astoltz on 2007-11-15
You've got to switch drivers from the ATI driver that you were using to the nvidia driver for you new card.  Boot up the computer, and when it gets to the terminal, login with your userid and password.  Then put in the these commands: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
```Put in your password again when it asks.  You should then have your xorg.conf file open for editing.

Scroll down and find the section labeled "Device".  In that section there is a line for Driver.  Change that line from whatever is there to:```
Driver     "nv"
```Save the file (ctrl O) cross fingers and then re-boot.  If it still doesn't work, you might try "vesa" instead of "nv".

---

### Post by mitchtanz on 2007-11-15
Hi Alistair

Don't take this the wrong way but when you installed the Nvidia 8600gt did you plug in the power strap. 

[http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=230&p_created=1110911781](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=230&p_created=1110911781)

Later Nvidias have to have this or they will not display and in under a week cook-out. 

I've been there and nearly done that...so...

Hoping all will be good soon

Best Wishes
Mitch

---

### Post by Alistair1234 on 2007-11-16
Thanks for your responses.

I have tried what astoltz suggested as it was the only one I understood, but still nothing.

The xorg.conf file has a section for the card which I changed the driver as suggested (do I need to change the identifier- still ATI...- or the busid PCI:1:5:0).

There is also another section "screen" below this with device "ATI tech..." - do I need to change this aswell. If so, what to?!

I am still in the same situation as before.

The card and drivers work fine in XP which is dual-booted on the same system so I dont think its the power supply.

Please help!

---

### Post by Jense on 2007-11-16
you can check for the correct bus id by 

lspci

even if the xserver hangs on start up you can open a new console by 

strg + alt + any f-key except 7,

otherwise try 

sudo dpkg-reconfigure xserver-xorg 

this will let you reconfigure the xserver, but you will have to enter lots of stuff manually, so you should have a working system near by to google the information you need.

hope this helps

---

### Post by Alistair1234 on 2007-11-16
Hmmm. not really sure what that means! I dont have another computer so have to keep rebooting to ubuntu to try stuff and then when it doesnt work, go back to xp to get on the internetto find some more fun things:(

Sorry for being so lame but I have no idea what to do!

This is turning into a nightmare as I am stuck back in windows land which is something I thought I had got away from.

---

### Post by Jense on 2007-11-16
start your computer.
when the system hangs you push Ctrl+Alt+F3. This will open a new console.
There you enter:

sudo dpkg-reconfigure xserver-xorg 

This will put you into a small prog to reconfigure your xserver (xserver is the grafical user interface for linux), among other things like keyboard layout. Pay attention when you are asked to give sync rates for you monitor, cause getting it wrong can destroy your sceen. However, there should be some safe or default option which you can use. 
If you need to find out stuff, you can allways open a new console by Ctrl+Alt + example:F5.
For example you will be prompted for the busId of you grafic device, which you can find out by lspci. It will print out a bunch of stuff, but there should be a line with Nvidia or something. 
But really, reinstalling is the easiest way for you to fix this. If you set up your home directory on a different partition from your os, then you woun't even loose you configuration.
You will just have to reinstall some progs

---

### Post by jryprt on 2007-11-16
Try Ctrl+Alt+F2 than  sudo dpkd-reconfigure xserver-xorg  then answers the stuff about keyboard & stuff when it ask for video drivers put in VESA  THAT SHOULD HELP  . you may need to code  ( startx ) after

---

### Post by bcn17 on 2007-11-22
See here. [http://ubuntuforums.org/showthread.php?t=460765](http://ubuntuforums.org/showthread.php?t=460765)

---

