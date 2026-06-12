---
title: "Please Help Omw"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by stfury on 2007-10-25
hi guys,

i wanted to change something through root. so i went to users and set a password for root.

then i went to exit, switch user. 

the screen went black - then my monitor says no signal and thats it.

i rebooted monitor works fine, grub loads bla bla as it gets to the point where it wud display the login screen my monitor goes black then no signal.

i dual boot with windows and i can still work perfectly in windows.

PLEASE HELP PLEASE

---

### Post by stfury on 2007-10-25
pls help guys this is really urgent i need to use my linux for something really important and i dont want to re-install and lose everything

---

### Post by Ziox on 2007-10-25
> **stfury said:**
> hi guys,

i wanted to change something through root. so i went to users and set a password for root.

then i went to exit, switch user. 

the screen went black - then my monitor says no signal and thats it.

i rebooted monitor works fine, grub loads bla bla as it gets to the point where it wud display the login screen my monitor goes black then no signal.

i dual boot with windows and i can still work perfectly in windows.

PLEASE HELP PLEASE

If you can boot into a terminal, try this command:

sudo passwd -d

This effectively erases the password for the root account, thus disabling it.

---

### Post by mikeyphi on 2007-10-25
Try to open a command line from the Grub page:

Read here for next things to try: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#User_Administration](http://ubuntuguide.org/wiki/Ubuntu:Feisty#User_Administration)

---

### Post by stfury on 2007-10-25
no i cant. soz but i told u wen it boots up as it is about to load the login screen it just goes blank and says no signal? it shows the ubuntu logo and when it reaches full it says no signal

when i clicked switch user it just went to the blank screen and said no signal and then i pressed the reset button and now every time i reboot it just gives me a blank screen.

cheers

---

### Post by mikeyphi on 2007-10-25
> **stfury said:**
> no i cant. soz but i told u wen it boots up as it is about to load the login screen it just goes blank and says no signal? it shows the ubuntu logo and when it reaches full it says no signal

when i clicked switch user it just went to the blank screen and said no signal and then i pressed the reset button and now every time i reboot it just gives me a blank screen.

cheers

Don't you get a Grub screen to select either windows or Ubuntu?

---

### Post by slibuntu on 2007-10-25
> **mikeyphi said:**
> Don't you get a Grub screen to select either windows or Ubuntu?

From the sounds of it he's not dual-booting

---

### Post by kvonb on 2007-10-25
Sounds like you stuffed your xorg.conf up.

Boot to Linux, at the black screen press <ctrl><alt><f1>, enter your username then password when asked

Then type this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.stuffed
sudo dpkg-reconfigure -phigh xserver-xorg

```
and select "vesa" as your video driver, or if you know what video card you have, and are sure of the driver, then select it.

When finished, press <ctrl><alt><f1> again to get back to the black screen, and press <ctrl><alt><backspace> to restart the X server (desktop).

You should see a picture now.

---

### Post by stfury on 2007-10-25
i do and i can select the recovery version shud i do that?

---

### Post by stfury on 2007-10-25
omw it just started working? i reboot for the 4th time and now it reboots and logins perfectly wtf?


anyway thanks aload guys

---

