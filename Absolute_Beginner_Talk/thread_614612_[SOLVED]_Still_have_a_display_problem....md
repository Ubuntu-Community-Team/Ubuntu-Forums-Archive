---
title: "[SOLVED] Still have a display problem..."
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by AndrewS on 2007-11-16
I have 7.04 installed on a PC which had a wide screen display, and have been unable to use the 1440x900 resolution which the monitor is capable of (and which Windows XP can use). I edited some of the configuration files for the display in 7.04, and succeeded in losing the display completely... I'm pretty sure the system still boots OK, because I can switch to a text console (ctrl + alt + F1).

Any suggestions as to how to fix this, preferably without a re-install? I'll be happy with pretty well any resolution (although 1440x900 would be nice).

Thanks in advance

Andrew

---

### Post by overdrank on 2007-11-16
> **AndrewS said:**
> I have 7.04 installed on a PC which had a wide screen display, and have been unable to use the 1440x900 resolution which the monitor is capable of (and which Windows XP can use). I edited some of the configuration files for the display in 7.04, and succeeded in losing the display completely... I'm pretty sure the system still boots OK, because I can switch to a text console (ctrl + alt + F1).

Any suggestions as to how to fix this, preferably without a re-install? I'll be happy with pretty well any resolution (although 1440x900 would be nice).

Thanks in advance

Andrew

HI from the command line ctrl + alt + F1. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by shuttleworthwannabe on 2007-11-16
AndrewS, try reconfiguring the xserver using
> $sudo dpkg-reconfigure xserver-xorg
 
Follow the prompts and fill in the screen resolutions your screen is capable of. Also note the type of graphics card you have, may mean installing drivers for this first.
 
Hope u come right,
 
EDIT: I guess I was slow at hitting the submit button; anyways follow the above suggestion.

---

### Post by alienexplorers on 2007-11-16
Once you get your display back running in the gui you can try adding a modeline to your xorg.conf file.  A sample modeline for 1440*900*60 would be:
> # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

This line should be inserted into the monitor section of xorg.conf. An example of this is:
> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Some Brand"
    HorizSync       31.5 - 68.7
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
    # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection


---

### Post by AndrewS on 2007-11-16
Thanks for your replies.  I fear it may be worse than I thought...  I tried the "sudo dpkg-reconfigure xserver-xorg" command from tty1, only to be told that "Package 'xserver-xorg' is not installed".  Does anyone see an alternative to a clean instal???  I think upgrading from a text console is a bit dangerous?

Thanks

Andrew

---

### Post by overdrank on 2007-11-16
> **AndrewS said:**
> Thanks for your replies.  I fear it may be worse than I thought...  I tried the "sudo dpkg-reconfigure xserver-xorg" command from tty1, only to be told that "Package 'xserver-xorg' is not installed".  Does anyone see an alternative to a clean instal???  I think upgrading from a text console is a bit dangerous?

Thanks

Andrew

HI could you view the xorg  try this command from the terminal 
```
cat /etc/X11/xorg.conf

```

---

### Post by Inxsible on 2007-11-16
> **AndrewS said:**
> Thanks for your replies.  I fear it may be worse than I thought...  I tried the "sudo dpkg-reconfigure xserver-xorg" command from tty1, only to be told that "Package 'xserver-xorg' is not installed".  Does anyone see an alternative to a clean instal???  I think upgrading from a text console is a bit dangerous?

Thanks

Andrewdid you run the command the way you have typed here? It also has -phigh in it```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Make sure its all lowercase. Linux is case sensitive. Please copy paste the commands that you use and errors that you get, so we can eliminate going down the wrong highway.

---

### Post by AndrewS on 2007-11-16
I'm pretty sure I included the -phigh (BTW, what does this mean?) but I'll try again in a while.  I'll also try cat /etc/X11/xorg.conf

Later

Andrew

---

### Post by AndrewS on 2007-11-16
OK, I just ran the following command:

sudo dpkg-reconfigure -phigh xserver-xorg

After a couple of seconds, the PC returned the following message:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf2007111700136

I then entered

sudo reboot

Still no GUI.

I could see (fleetingly!) an xorg.conf file when I typed the following command:

cat /etc/X11/xorg.conf

Was there anything specific I should look for?  Also, I can't remember how to show the contents of this file page-by-page (I think in Windows it's -P?).

Thanks again

Andrew

---

### Post by overdrank on 2007-11-16
> **AndrewS said:**
> OK, I just ran the following command:

sudo dpkg-reconfigure -phigh xserver-xorg

After a couple of seconds, the PC returned the following message:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf2007111700136

I then entered

sudo reboot

Still no GUI.

I could see (fleetingly!) an xorg.conf file when I typed the following command:

cat /etc/X11/xorg.conf

Was there anything specific I should look for?  Also, I can't remember how to show the contents of this file page-by-page (I think in Windows it's -P?).

Thanks again

Andrew

Hi and the only thing I wanted you to use that command for is to see it the file was there. You stated previously that when you ran the configure command that the xserver- xorg was not installed. What video card are you using on the system? And have you tried the vesa driver when reconfiguring your xorg ( the command with out the -phigh)

---

### Post by AndrewS on 2007-11-16
Right, I just ran the command without the -phigh, and was indeed led through a series of questions, which I answered as best I could.  At the end, I was again warned that I had overwritten a possibly-customised file etc.  Rebooting still did not give me a gui.

The PC has an Intel 82945G Express Chipset; it worked fine until I tinkered with it.

Thanks yet again

Andrew:(

---

### Post by AndrewS on 2007-11-17
I just re-ran the reconfiguration process, giving slightly different answers (specifically, omitting any reference to 1440x900 resolution) and I now have a gui (albeit 1024x768).  At least it works, and I can tinker with the configuration at my leisure (now I know how to fix it!).

Thanks to all for your help with this.

Andrew

EDIT - just had another tinker, now have 1440x900 resolution!

---

### Post by shuttleworthwannabe on 2007-11-18
Glad it worked; sometimes I wornder what the "bullet-proof" Xserver means--it is supposed to fall back to VESA drivers if it can't find the correct resolution or driver for your rig.

well, anyway, I am very impressed with Gutsy to complain!

---

### Post by SentientFluid on 2007-11-18
> **AndrewS said:**
> I just re-ran the reconfiguration process, giving slightly different answers (specifically, omitting any reference to 1440x900 resolution) and I now have a gui (albeit 1024x768).  At least it works, and I can tinker with the configuration at my leisure (now I know how to fix it!).

Thanks to all for your help with this.

Andrew

EDIT - just had another tinker, now have 1440x900 resolution!

Care to share what the last "tinker" was that got 1440x900 working for you? :)

---

### Post by AndrewS on 2007-11-18
As far as I recall, I just ran the command to reconfigure the xserver, and checked the box for 1440x900 resolution, and after sudo reboot, that resolution was available under System>Preferences>Screen Resolution.  The only frustrating thing is that I'm sure I'd tried that before...  Obviously not.

HTH

Andrew

---

