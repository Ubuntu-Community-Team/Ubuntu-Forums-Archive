---
title: "PPC screen width issue"
date: 2007-07-29
forum: Apple PPC Users
---

### Post by Sanchoclaus on 2007-07-29
To any anyone who can help.
I posted the same qustion on another thread. But in case nobody saw it.
Ever since I installed Ubuntu 7.04 last week the left and right sides of the screen seem to be caving inward. In fact the border on all aplication and browser seem caved in. 
My idea was to change the screen resolution from 1024x 768 to 800x600, but it's fixed on 1024x768. 
Can anyone help me change this, or come up with an idea as what  the problem is and how to fix it?
Many thanks.

---

### Post by pxwpxw on 2007-07-29
It would help if you gave name of  your Mac model, and if separate - monitor, graphics card, and is the screen  ok in Macos (if you are dual booting). Screen shot or photo may help. 
By "caved in" do you mean sides  like ) (   or /   \   or can you describe it better?

---

### Post by Sanchoclaus on 2007-07-30
Yes, I should have been more specific.
I have a Emac with these characteristics:

    * 1.42 GHz G4 processor
    * 167 MHz system bus
    * 768 MB DDR SDRAM (can be upgraded to a maximum of 2[citation needed] GB DDR SDRAM, unofficially)
    * ATI Radeon 9600 graphics (64 MB dedicated DDR SDRAM)
    * 17-inch flat CRT display
    * Built-in 18-watt stereo speakers
    * Built-in microphone
    * CD-ROM drive, Sony SuperDrive (16x,DVD+R DL/DVD±RW/CD-RW)
    * 80 GB HD
    * Built-in USB 2.0 and Firewire ports
    * AirPort Extreme Ready
    * Bluetooth
    * External Display Port
  

[edit]

---

### Post by Sanchoclaus on 2007-07-30
And yes, by "caved in" I mean that the all the windows on my disktop in Ubuntu, look like this: )(.
Also have Ubuntu 7.04 natively, not with dual boot. 
Thanks!

---

### Post by pxwpxw on 2007-07-30
Good information thanks.

For the eMac CRT display, variation in width like  )  (   would most likely be a CRT problem (power supply etc) rather than X windows resolution setting, but you do need to confirm what is the normal resolution for the eMac CRT, 1280x960 ? , and there are some eMac howtos about xorg.conf settings for eMac. See below.

But have you ever seen a [  ] straight sided display on it. You could also check that by 
Contol-Alt-F1 (or F2.. function keys) which will give a text console and should not have the problem unless it is with the CRT.
 
I am not sure if the caved in effect is your main problem, or whether changing resolution will help, but you may be correct there.

Have you looked at this thread - Getting Started with a 700MHz eMac
[http://ubuntuforums.org/showthread.php?t=468671&highlight=emac]("http://ubuntuforums.org/showthread.php?t=468671&highlight=emac")

---

### Post by Sanchoclaus on 2007-07-31
Thank you!
However after typing into the terminal what the link to that thread says, I got something really strange.
It seems my system thinks the computer is an "imac" and not and emac.
where I was supposed to get this:
Section "Monitor"
              ...
          HorizSync            71-73
          VertRefresh          70-140
          Modeline "1280x960" 122.24 1280 1328 1424 1696 960 961 964 1002 +HSync +VSync
EndSection

The "modeline" part is not there, so I was wasn't able to add the "1280x960" resolution parameters.

When I typed "screen I got this:
Section "Monitor"
        Identifier      "iMac"
        Option          "DPMS"
        HorizSync       71-73
        VertRefresh     70-140
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200]"


But as you can see in "Screen"  it says Default Screen.
So does this mean I can't change it?

---

### Post by pxwpxw on 2007-07-31
You have to edit xorg.conf to add the figures and the Modeline.
You should post a copy of /etc/X11/xorg.conf.

---

