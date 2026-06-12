---
title: "wireless, desktop effects,webcam error &gt;_&lt;"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by chips24 on 2007-10-20
my desktop effects dosnt work because i have nvidia?, i also cant seem to get my wireless to work , or my webcam:mad:

---

### Post by spenny on 2007-10-20
As for the desktop effects, are you sure they're on? 

I upgraded and didn't have them on by default. Try looking in System -> Preferences -> Appearance.

As for the wireless and webcam, I can't help you there sorry.

---

### Post by Espreon on 2007-10-20
Lots of webcams don't work with Linux (there are good ones that will work, there is a lost in the Ubuntu wiki, I believe)
For the nvidia problem goto: System>Administration>Restricted Drivers Manager and see if there is an unused, nvidia driver and if there is install it.
For the wireless problem, you might hava Wincard, don't worry though follow these instructions:

Look at the manufactures (or your OEM's) website and look for the drive (its usually in an .exe), extract it on Winblow$

You should look for an .inf file and a .sys file, if they are there good:

Now enter this:

```

sudo apt-get install ndisgtk ndiswrapper ndiswrapper-utils-1.9

```

Then goto: System>Administration>Windows Wireless Drivers

and drag and drop the .inf file on the blank space

Then enter this in the terminal:

```

sudo modprobe ndiswrapper

```

Enjoy!

If the instructions for the wireless card don't work and if there is no Nix driver your SOL.

---

### Post by chips24 on 2007-10-21
i have a SD.MS/Pro.MMC.XD wireless card

---

### Post by Espreon on 2007-10-21
For the driver (which I assume your lookin for) look at your OEM's site (an OEM is the company the comp was brought from, examples include, Gateway, Dell, HP, etc).
But is everything else ok?

---

### Post by chips24 on 2007-12-11
thankyou, ekiga is excellent for my wabcam, my c compilier cannot execute commands and i have no root privaliges

---

### Post by rockinlinux on 2007-12-11
> **chips24 said:**
> i have a SD.MS/Pro.MMC.XD wireless card

thats not a wireless card, thats a card reader for Sandisk, memory sticks and XD cards. :)

---

### Post by rockinlinux on 2007-12-11
and as for your nvidia card, look to see if the drivers are installed. jsut like you were told before go to System>>Admisitration>>restricted drivers. It should have your card there. if it is not there that please post the output to lspci and then we wil help you install the driver.

---

### Post by chips24 on 2007-12-11
ok, so r ya gonna answer my question or what, how come my c compilier dosent execute and how do log in as root?

---

### Post by chips24 on 2007-12-11
i forget how to post a thread.

---

### Post by rockinlinux on 2007-12-11
you dont need to log in as root. when you go to the terminal just type "sudo" (without the " ") and that makes you super user.

but first...let figure out what card you have. please go to a terminal and do this:

```
lspci
```

and please post the output. Also please check the restricted drivers for the wireless card just like you did the nvidea card.

---

### Post by rockinlinux on 2007-12-11
> ok, so r ya gonna answer my question or what, 

and just for your information, this kind of attitude will not get you very far in these forums. you should be polite and patient...your help is free and your should respect people.

dont take it personally, everyone gets this talk at one point :)

---

### Post by chips24 on 2007-12-11
oh yeah, my only internet connection is wireless, i daulboot vista, yhats my only connection

---

### Post by rockinlinux on 2007-12-11
thats fine, i need you to go into ubuntu and look to see about the drivers. while you are there give me the lspci, you can save it to a text file and put it on a cd, usb stick or your windows hard drive to get it to windows so you can post it here.

---

### Post by rockinlinux on 2007-12-11
so i see you got IE6, does that mean you have your wifi card working? if you have everything here working please mark as SOLVED

---

