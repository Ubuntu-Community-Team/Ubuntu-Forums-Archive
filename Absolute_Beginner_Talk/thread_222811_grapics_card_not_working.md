---
title: "grapics card not working"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by notjohn101 on 2006-07-25
ok so i have my Radeon 9250 PRO installed but it dosent dislay anything after  the boot up...only the onboard works...i installed the latest drivers with easyubuntu...what else do i need to do

---

### Post by taurus on 2006-07-25
You need to disable your onboard video card from the BIOS if you plan to use the add-on graphic card!!!

---

### Post by notjohn101 on 2006-07-25
yea i no...but when i do...it black screen after bootup

---

### Post by echo $USER on 2006-07-25
> **notjohn101 said:**
> yea i no...but when i do...it black screen after bootup

You have to uninstall the old driver and reinstall the driver for the new card.

---

### Post by notjohn101 on 2006-07-25
ok were are the drivers located

---

### Post by Dr. Nick on 2006-07-25
try this

from a terminal run 

gksudo gedit /etc/X11/xorg.conf

look at the driver line under your video card, what does it say currently?

If it does not say "vesa" then change it to say "vesa" then
look at the busid line, If the 9250 card is AGP then make sure it looks like this

BusID           "PCI:1:0:0"

save the file and then shutdown the computer. 

Move the monitor over into the 9250 then power it back up and go into your bios and disable the onboard.

Then as it restarts let it load ubuntu, if you get thrown to a command line after a blue error message screen then run

sudo nano /etc/X11/xorg.conf and make sure it all saved correctly. If it is all correct looking then run this command from the command line while the onboard video is disabled, you can probably just accept the defaults if you are unsure

[COLOR=#0000df][B]sudo dpkg-reconfigure xserver-xorg
[/B][/COLOR]

---

### Post by notjohn101 on 2006-07-25
yea i cant disable it...i look everywere...the only thing u can change is weather the default is on PCI or AGP...its set to PCI cuz i dont have a AGP slot but the onboard still works

---

### Post by Dr. Nick on 2006-07-25
ok, so your new ati is a pci card, and I assume your onboard is using the pci bus aswell.

What exactly happens if you plug your monitor into the ati, is the screen totally black or do you just get a command line login?

---

### Post by notjohn101 on 2006-07-25
ok after bootup (whitch is fine) a white dash flickers and then the nongraphic logon flickers then the "xserver failed...." error comes up

---

### Post by Dr. Nick on 2006-07-25
ok then, have you edited your xorg.conf as above to read "vesa" on the driver line?

Log in the text console and run

[COLOR=#0000df][B]sudo nano /etc/X11/xorg.conf

[COLOR=Black]make sure dirver is [/COLOR]"vesa" [COLOR=Black]without quotes

edit, [/COLOR][/B][COLOR=Black]after making that change type[/COLOR]**[COLOR=Black] startx [/COLOR]**[COLOR=Black]when you get a command back, see if it gives a error

If you get a error then run 
[/COLOR][/COLOR][COLOR=#0000df]**sudo dpkg-reconfigure xserver-xorg**[/COLOR]

---

### Post by notjohn101 on 2006-07-25
is vesa a universal driver or something?

and heres my output

boys@boys-desktop:~$ sudo startx
xauth:  creating new authority file /home/boys/.serverauth.4543

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


xinit:  unexpected signal 2.

---

### Post by Dr. Nick on 2006-07-26
yes, I should have mentioned that vesa is a pretty much universal driver, once you get the GUI going off the ati then you can set up better drivers.

You do not need sudo infornt of startx. If you changed to vesa then restart using the new card you should see the GUI. If you end up back at the command prompt then run the dpkg-configure i mentioned before.

Do you have a manual for the system? I had a computer that required you to set a jumper on the motherboard itself to disable the onboard video, you couldnt do it from the bios.

---

### Post by ShAdEd_PaSt on 2006-07-28
I've been trying for ever to get my radeon 9250 to work instead of showing an x-server error. I'm so pleased to anounce it works! sudo dpkg-reconfigure xserver-xorg fixed it for me! YAY!

---

