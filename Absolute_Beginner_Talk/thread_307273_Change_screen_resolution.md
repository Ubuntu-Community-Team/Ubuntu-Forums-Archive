---
title: "Change screen resolution"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by baysl on 2006-11-26
How do I change screen resolution in linux?

---

### Post by baysl on 2006-11-26
can somebody please tell me????

---

### Post by bodhi.zazen on 2006-11-26
What desktop manager ?

What resolution do you now have?

What resolution do you want ?

Try the "system" menu and choose "Screen Resolution"

---

### Post by LLRNR on 2006-11-26
I suppose you DID install the drivers for your video card...

There's an applet that I find very useful, it's called "Resolution Switcher" and you can install it with:
```
sudo aptitude install resapplet
```
If it doesn't show up in Applications -> Accessories you can launch it through the terminal with **resapplet &** or you can hit Alt+F2 and type in "resapplet". You'll see a little square near the time&date, click on it and adjust your resolution accordingly.

If the resolution you want is not listed... you'd need to install your graphic card's driver first.

LLRNR

---

### Post by upinVermont on 2006-11-26
Add me to the list of users with screen resolution problems. I just tried installing Xubuntu on my old Compaq Armada and all I get is a teeny-tiny little window which is probably 640x480. The only other option I have is 600x800. Oops, no, scratch that. That dissappeared when I tried the sudo...xserver-xorg approach. Now I have no resolution options...

Anyway, I've tried the various options discussed so far, and none seem to work. I tried installing resapplet but linux couldn't find the package.

I have no connection to the internet with the Armada, by the way. I only have a PCMCIA Belkin Wireless Card which will need Ndiswrapper. I thought I would tackle *that* problem after the screen issue goes away. I don't get it... I tried an older version of Ubuntu and the screen worked fine but I couldn't get the wireless to work... so I put linux away and waited for the newer version. *Now* I can't get the screen to work... always something...

---

### Post by bodhi.zazen on 2006-11-26
> **upinVermont said:**
> Add me to the list of users with screen resolution problems. I just tried installing Xubuntu on my old Compaq Armada and all I get is a teeny-tiny little window which is probably 640x480. The only other option I have is 600x800. Oops, no, scratch that. That dissappeared when I tried the sudo...xserver-xorg approach. Now I have no resolution options...

Anyway, I've tried the various options discussed so far, and none seem to work. I tried installing resapplet but linux couldn't find the package.

I have no connection to the internet with the Armada, by the way. I only have a PCMCIA Belkin Wireless Card which will need Ndiswrapper. I thought I would tackle *that* problem after the screen issue goes away. I don't get it... I tried an older version of Ubuntu and the screen worked fine but I couldn't get the wireless to work... so I put linux away and waited for the newer version. *Now* I can't get the screen to work... always something...

Edit /etc/X11/xorg.conf

Under the monitor section, add you monitors HorizSync and VertRefresh rates.

Add a line "        Option          "UseEdidFreqs" "1""

So you should get something that looks like this:> Section "Monitor"
        Identifier      "Monitor1"
        VendorName      "DEL"
        ModelName       "DELL P1110"
        HorizSync       29-121
        VertRefresh     50-180
        Option          "UseEdidFreqs" "1"
EndSection

Of course you need the Horiz and Vert refresh rates for your monitor.

Re-start X (Ctrl-Alt-Backspace)....

---

### Post by upinVermont on 2006-11-26
Thanks Bodhi,

Before I follow your recommendation, I should have been more specific about my computer. It's an old Compaq Armada 1700 Laptop. 

It uses the "chips" driver for the Chips and Technology video chip and, from past experience, I think the default horizonal sync (28-50) and vertical refresh (43-75) rates will work.

I'll try out your recommendation. What the heck... I can always re-install and start from scratch if I totally screw it up. That's why I'm experimenting on this old laptop.

---

### Post by radj2 on 2006-11-26
try this it worked for me

[http://www.ubuntuforums.org/showthread.php?t=281905&highlight=screen+resolution](http://www.ubuntuforums.org/showthread.php?t=281905&highlight=screen+resolution)

---

### Post by bodhi.zazen on 2006-11-26
> **upinVermont said:**
> Thanks Bodhi,

Before I follow your recommendation, I should have been more specific about my computer. It's an old Compaq Armada 1700 Laptop. 

It uses the "chips" driver for the Chips and Technology video chip and, from past experience, I think the default horizonal sync (28-50) and vertical refresh (43-75) rates will work.

I'll try out your recommendation. What the heck... I can always re-install and start from scratch if I totally screw it up. That's why I'm experimenting on this old laptop.

LOL upinVermont :lol:

First backup your xorg.conf:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then KEEP YOUR horizonal sync (28-50) and vertical refresh (43-75) rates !

Just add the "one liner" I gave you, Like this:
> HorizSync 28-50
VertRefresh 43-75
Option "UseEdidFreqs" "1"

If that fails, please post your xorg.conf.

PS How is the skiing ?

---

### Post by bodhi.zazen on 2006-11-26
> **radj2 said:**
> try this it worked for me

[http://www.ubuntuforums.org/showthread.php?t=281905&highlight=screen+resolution](http://www.ubuntuforums.org/showthread.php?t=281905&highlight=screen+resolution)

If you are referring to "sudo dpkg-reconfigure xserver-xorg", yes this is often very effective and the first step I usually advise !

Add the -phigh option to accept the defaults for everything but resolution. This is often easier for users unfamiliar with xorg.conf;

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by upinVermont on 2006-12-03
OK Bodhi,

I finally got some time to sit back down with this. Carpentry and children get in the way.

So... I guess it's been a long time since a tooled around with Linux because all of my old editing commands aren't working. Is EMACS out of favor?

SUDO isn't even in my "Linux In a Nutshell" handbook. I gather what it does but I don't know any of the command options.

What do I use to edit /etc/X11/xorg.conf? What's the command?

(I clearly need to update my linux books...)

---

### Post by LLRNR on 2006-12-03
upinVermont, for editing documents within the command line you can use **vi**, **vim** or **nano**. If you're familiar with vi, I guess it's OK, but if you're not... then go for *nano*.

Ubuntu uses **sudo** for gaining root privileges. There's no root account by default. [Here](https://help.ubuntu.com/community/RootSudo)'s a little more info on root vs. sudo.

To edit certain documents that require root privileges, you use "sudo" in front of the command for editing them, something like:```
sudo nano /etc/X11/xorg.conf
```

LLRNR

---

### Post by bodhi.zazen on 2006-12-03
> **upinVermont said:**
> OK Bodhi,

I finally got some time to sit back down with this. Carpentry and children get in the way.

So... I guess it's been a long time since a tooled around with Linux because all of my old editing commands aren't working. Is EMACS out of favor?

SUDO isn't even in my "Linux In a Nutshell" handbook. I gather what it does but I don't know any of the command options.

What do I use to edit /etc/X11/xorg.conf? What's the command?

(I clearly need to update my linux books...)

Nice to see you are back upinVermont :p

At this point I trust you found LLRNR 's post helpful and are up and running.

emacs in still with us. In fact, since you asked, see here: [Colorize EMACS](http://doc.gwos.org/index.php/ColorizeEmacs) if you like !

If we can be of further assistance you know where to find us !

---

### Post by upinVermont on 2006-12-05
Whoa! Holy snowman! That worked. My whole screen is back.

OK, who can tell me what package NDISWRAPPER is in? I saw an Ubuntu Hacks Handbook at the bookstore. Maybe I should have picked it up. Anyway, I'll start looking around for it...

---

### Post by bodhi.zazen on 2006-12-05
Welcome to Linux... :p

Try ndiswrapper-utils

You can install it with synaptic or aptitude.

```
sudo aptitude install ndiswrapper-utils
```

Hey, how's the snow upinVermont? Early season has been kind in Montana !

---

### Post by upinVermont on 2006-12-05
Bad year for snow. All of New England has been warm until last week-end, setting records. Winter finally showed last week-end with just a dusting of snow. Sneeze and you'll grass.

I've been checking instructions for installing my Belkin 54g F5d7010. It looks like a nightmare.

Since I don't have a way to update files on the linux computer, I just can't see how I can realistically install the card.

So... any advice on plug and play USB or PCMCIA Wireless Cards for Ubuntu?

---

### Post by Ubluedog on 2007-03-07
hello, 
i have a compaq armada 1700 with the screen stuck at 800/600 and the only options i get are 800/600 or 640/480. i have  used gedit to examine the xorg.conf file and its got the 1024/768 option already in it. i cannot make it go into 1024 mode.

 i managed to fix the acpi fault ok, it stays on now and doesnt stop after an hour anymore, i would like to hear the fan come on though, am hoping the hardware is going to control it.
i have read, and read and read , now i must ask , can someone help?

a secondary fault i found while trying to use admin mode was the error message "none of the authentification protocols specified are supported and host based authenification failed"

any help appreciated, hoping to get a full screen
thanks from the bush in australia

---

### Post by Ubluedog on 2007-03-08
ok my broadband satellite service is back up , the fix for the screen problem involves the depth setting in the xorg.conf file
heres how to fix it
click applications , select accessories , terminal
type     sudo gedit
it asks for your password , type that in
the editor will open so select open file, navigate into the file system , click on the directory etc, then click on the directory xll, then scroll down and look for xorg.conf
open this file and scroll down looking for default depth, once you find that, mine was set to 24 , so change that to 16 , then click on save file
restart your computer and its all fixed.
cheers

---

