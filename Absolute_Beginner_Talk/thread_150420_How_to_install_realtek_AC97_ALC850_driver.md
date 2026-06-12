---
title: "How to install realtek AC97 ALC850 driver"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-03-26
Hi,

I downloaded the linux version of realtek's AC850 AC97 driver software package from realtek.com.tw. How do I get that installed? Is there a program out there that will install it for me or do I have to do it from the console? If console, can someone point me in the right direction, or give me info on the commands that needs to be done?

I"m using a new AMD Sempron 64, with 64 bit breezy, on a gigabyte GA-K8N51GMF MATX mobo with an SATA drive. Everything works great....but I have no sound!! All the installs in the past have been with with ALC650, and it has been no issue at all. Thanks...I'm not very experienced in this.

regards
gordo

---

### Post by Enter on 2006-03-26
wow didnt know they have drivers for linux, thanks mate!
have you tryed reading the read me in realtek-linux-audiopack-3.5-6.tar.bz2 ? :D
anyway what i did is just untarred the thing the in directory read readme which said rund the install so just double click the install file then click run in terminal and the twhing will install by it self youll see loads of output in the terminal window

//edit

haha it fundged up my system when i gave it sudo xD so be careful

---

### Post by gordong11 on 2006-03-26
Well I installed the  install by " run in terminal"...bu tthat is as far as I got.

My problem is, Linux is not detecting my onboard sound. Is it possible that my board is bad? Everytime I have installed Ubuntu, it always detected my realtek 6 chanell audio from my MSI boards and ran perfect out of the box...this time I have 8 channell from gigabyte mobo...and Nothing...not even startup sound, nothing in my device manager...nothing.

Is there a way to test the sound in bios or something? Could it be this new Universal Audio Jack funsctionality, thats fubarrring it? I dont know why ubuntu is not seeing onboard sound, realtek!

Gigabyte boasted "out of the box functionality" [http://www.gigabyte-usa.com/Motherboard/Products/Products_GA-K8N51GMF.htm](http://www.gigabyte-usa.com/Motherboard/Products/Products_GA-K8N51GMF.htm) for its sound,

---

### Post by stuntmaster on 2006-04-07
i have the same driver problem, it works Fine in Fedora Core 4 but not in ubuntu.
the reason is simple, it wants to use the make command and for some reason its missing in Ubuntu Breezy.

can anyone help in the install of this driver.

all you do is sh install at the termianl but if you look in the error it says:

unknown command: 'make'

hope this helps .

i really need this to work too.

---

### Post by dvarsam on 2006-04-08
[QUOTE=stuntmaster]
I have the same driver problem, it works Fine in Fedora Core 4 but not in Ubuntu.
The reason is simple, it wants to use the "make" command and for some reason its missing in Ubuntu Breezy.

Can anyone help in the install of this driver.

All you do is sh install at the termianal but if you look in the error it says:

unknown command: 'make'
[/QUOTE]

You sometimes do NOT need to install any driver to make your Ubuntu "spit" some sound...

Launch a "Terminal" window (from the Menu, select "Applications\Accesories\Terminal) & type"

```
alsamixer
```

This nice picture should help you out:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/Screenshot5.png[/IMG]

Look for the "Front" Speakers.

> To move around on that window, you use the following keys on your keyboard:

    a. "left" & "right" arrow keys: to select an "audio out" device (e.g. from "Front" to "Center", etc.)

    b. "up" & "down" arrow keys: to increase/decrease the volume of the selected "audio out" device 

    c. "m" (lowercase) key: to mute/unmute an "audio out" device (e.g. the "Front" or "Center", etc.)

        Note:
        Whenever you change this, an indication of "MM" will change to "00" meaning "unmuted".
        Pressing it again, does the opposite (e.g. changing an "00" to "MM" means "mute").

    d. "ESC" key: to exit the "alsamixer" configuration window.

        Note:
        You MUST press this twice to work.

    e. "h" key: Launches the "Help" window showing to you all available commands you can type.

_Make sure_ your "Front" Speakers are "Unmuted", before you "Exit" the "alsamixer" window & make sure your speakers are "powered on" & that you have connected your speaker's wire to the correct "audio out" of your Mobo or Audio PCI card.

I am making a Tutorial on this & will put it in this Forum's "Customization Tips & Tricks" section when finished.

Good Luck!

P.S.> Post back if you have problems.

---

