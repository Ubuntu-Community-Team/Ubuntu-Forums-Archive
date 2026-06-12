---
title: "Can't boot to Ubuntu Desktop"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Seamus13 on 2007-04-01
I installed using the mini.iso found [here](https://help.ubuntu.com/community/Installation/MinimalCD), but when I boot up it only gives me a command line.  I've managed to log in, but I have no clue what to do after that.  I was under the impression that after installation is complete, it should take me to the Ubuntu desktop, but I can't seem to figure out how to get there.  Any help would be greatly appreciated.

My apologies if the answer is here somewhere already, I read the stickied topics and did some searching and couldn't find anything relevant.  Thanks in advance.

---

### Post by haricharan on 2007-04-01
the minimal CD has only the required components to start up a system in command line. The other packages would be download later. Do you have an internet connection? 

can you type the contents of /etc/apt/sources.list and ifconfig
```
ifconfig
```
```
cat /etc/apt/sources.list
```

---

### Post by Bachstelze on 2007-04-01
AS it's name suggests, the Minimal ISO only has a minimal system, with no GUI. To install a standard system, install with an ISO from [http://www.ubuntu.com](http://www.ubuntu.com)

---

### Post by Seamus13 on 2007-04-01
Wow thanks for the fast replies.

As for the minimal CD installation, the reason I went that route is because the standard Ubuntu .iso wasn't working for me.  It would boot into the root menu, but if I tried to boot into the desktop with the live CD it would freeze at about 9/10 of the way through the loading bar.  I ran the DC integrity check and that checked out fine, so I looked for alternatives.

I was hoping that the minimal CD meant it would only install enough to connect to the internet, and then install the other files for the GUI (yes, the computer I'm attempting to install Ubuntu on is connected to the internet).

I'll try to get the results of those commands in a few minutes.

Thanks again.

---

### Post by 3rr0r on 2007-04-01
Try burning the live cd iso at a slower speed. That has been known to help people before.

---

### Post by Bachstelze on 2007-04-01
Then to install a GUI, do :

```
sudo apt-get install xorg
```

and then install ubuntu-desktop, kubuntu-desktop or xubntu-desktop depending on the DE you want.

---

### Post by jvc26 on 2007-04-01
The issue you are having with the desktop cd not installing seems to be a common one - if you dont have very much RAM this is likely to be the cause, the alternative is to install from the alternate cd, and try that out, it definitely makes a difference if you dont have loads of RAM. If you have plenty of RAM, then this is obviously not the case, but it may well be worth trying the alternate install, or building up the GUI from your minimal install.
Il

---

### Post by Seamus13 on 2007-04-01
Well, I attempted to boot into Ubuntu again and ran those commands you suggested, haricharan, and it was just too much to write down (I only have one PC available at the moment, so unfortunately I can't just run the commands and type the output on another PC).  Is there anything in particular I should be looking for?

Also, I have 1GB of RAM, so I doubt that's the problem.  Thank you for the help though, I suppose I should have posted my basic system specs from the get-go.  I think I will try HymnToLife's suggestion first, then try the alternate install if that fails.

Thanks again everyone for all the great help.

---

### Post by haricharan on 2007-04-01
you could give a try from alternate CD..sometimes that works...also please post your system specifications..

---

### Post by Seamus13 on 2007-04-01
> **HymnToLife said:**
> Then to install a GUI, do :

```
sudo apt-get install xorg
```

and then install ubuntu-desktop, kubuntu-desktop or xubntu-desktop depending on the DE you want.

I entered this command and it downloaded a bunch of stuff, and then asked me for my display resolution, but nothing after that.  Entering the command again only tells me that there's nothing to update.  Did I do something wrong here?

System specs are as follows:
ABIT AN8-V Socket 939 NVIDIA nForce4 ATX AMD Motherboard
AMD Athlon 64 3500+ Venice 2.2GHz Socket 939 Processor
OCZ Value Series 1GB (2 x 512MB) 184-Pin DDR SDRAM DDR 400
ASUS EAX800XL/2DTV/256 Radeon X800XL 256MB GDDR3 PCI Express x16 Video Card

---

### Post by Bachstelze on 2007-04-01
You can type

```
startx
```

To test if Xorg is working correctly. If you see some kind of black-and-whire grid and a X-shaped cursor, your Xorg works, type Crtl+AlT+Backspace to exit. Now you need to install a desktop environment, do 

```
sudo apt-get install ubuntu-desktop
```

forthe standard Ubuntu (Gnome) desktop. You can also use *kubuntu-desktop* for a Kubuntu (KDE) desktop, *xubuntu-desktop* for a Xubuntu (XFCE) desktop or *kde-core* for a basic KDE desktop.

---

### Post by Seamus13 on 2007-04-02
Well, that definitely did the trick as I am now posting here using Ubuntu-Desktop.  Thank you so much for the help.:)

---

### Post by rkillcrazy on 2007-04-10
I've just followed these steps and they work out well.  I've used both the live CD & the minimal before but am simply playing around with Linux and trying to learn.  My question is....can you have Ubuntu & Kubuntu?  Meaning, after you run

```
sudo apt-get install ubuntu-desktop
```

can you run...

```
sudo apt-get install kubuntu-desktop
```

and have the option to choose from both of them at logon?

---

### Post by rsambuca on 2007-04-10
> **rkillcrazy said:**
> I've just followed these steps and they work out well.  I've used both the live CD & the minimal before but am simply playing around with Linux and trying to learn.  My question is....can you have Ubuntu & Kubuntu?  Meaning, after you run

```
sudo apt-get install ubuntu-desktop
```

can you run...

```
sudo apt-get install kubuntu-desktop
```

and have the option to choose from both of them at logon?That will work perfectly.

---

### Post by rkillcrazy on 2007-04-10
OK, I thought so and ran the command.  However, how or where do I get the option to boot into either Kubuntu or Ubuntu?

---

### Post by rsambuca on 2007-04-11
You do it at the login screen.  In the bottom left there is an options tab, then select sessions, and you should see gnome (ubuntu), kde (kubuntu), etc...

You can also add xfce (sudo aptitude install xubuntu-desktop)

There are other desktop environments you can add such as e17, and the list goes on.  Each one is a little bit different.  xfce is quite light on resources, kde tends to use a little bit more.

---

### Post by rkillcrazy on 2007-04-11
I figured it was at the login screen where I'd see an option.  However, I did not see it.  I installed Ubuntu 1st and then Kubuntu (no reboots between).  Then I ran... ```
startx
```

It took me right to Kubuntu.  I'll see if I can get some screen shots for you to look at.  Maybe I'm not seeing what you are.

---

### Post by rkillcrazy on 2007-04-11
**UPDATE**

I have a VMWare/Ubuntu setup and I loaded it with the Live CD.  Although we're largely discussing the minimal CD here, some of this is still helpful...

Since I already had Ubuntu installed, I figured I'd boot into it and try to install Kubuntu from a terminal session via... ```
sudo apt-get install kubuntu-desktop
```

Sure enough - it began the download/install just like it has in the past when I'd try it from a minimal install.  However, this time it "knew" about the Ubuntu install and at one point, it asked me if I wanted to use Ubuntu or Kubuntu as a default desktop manager or environment (don't quote me on this but it was something like that).  I wish I had a screen-shot of that!

I have screen-shots of some of the menus I had after the install was finished.  See the zip file full of JPGs.

So, I guess I got it to work since Ubuntu was already there.  I'm guessing there was some file full of settings that could be manually created/configured from the minimal install so that it would then ask you which desktop environment you wanted to get into.

---

### Post by Bachstelze on 2007-04-11
The things it asked you to choose between are the *display managers*. As far as the user is concerned, the display manager is just the graphical login scren. As you perhaps already know, Ubuntu and Kubuntu each come withtheir own dm but obviously, only one can be used at a time. This is what it asked you : which graphical login manager wou want to be launched when you start your computer. The choice you ake there wil have no incidence on the desktop environments themselves and youcan change it later, if you wish.

---

