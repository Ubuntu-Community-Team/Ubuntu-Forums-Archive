---
title: "DID I do something wrong??"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by g0t0 on 2007-03-31
I am a complete noob to Linux so please help if you can. I installed the alternate cd onto my laptop, because the traditional one was not working (something about not having X graphics?).

This one actually installed but now I go through a basic login and password area, then brings me to this:  " "g0t0"@"g0t0":~$ " 

I have no clue how I came to this and where I should go to next. I am in the process of downloading 6.10 to see if that works out. There is no other os on the laptop as I scrapped Vista during installation. I can always reinstall if needed.

All help is appreciated.

---

### Post by hyper_ch on 2007-03-31
So you downloaded 6.06 ?

---

### Post by 3rdalbum on 2007-03-31
When you get the "g0t0@g0t0:~$", type:

```
sudo dpkg-reconfigure xserver-xorg
```

And press Enter. Answer the questions (accept the defaults if you don't know what they do) until you get to one about video card autodetection. Say "no" to that, and select the "vesa" driver. Move through the questions again until the program finishes. Then type:

```
sudo gdm
```

Vesa is unaccelerated video, but you'll be able to get to the desktop and do web surfing and find out what proprietry driver you need to install. ATI and Nvidia make drivers for Linux, so best go to their websites and download the drivers.

---

### Post by GSF1200S on 2007-03-31
> **3rdalbum said:**
> When you get the "g0t0@g0t0:~$", type:

```
sudo dpkg-reconfigure xserver-xorg
```

And press Enter. Answer the questions (accept the defaults if you don't know what they do) until you get to one about video card autodetection. Say "no" to that, and select the "vesa" driver. Move through the questions again until the program finishes. Then type:

```
sudo gdm
```

Vesa is unaccelerated video, but you'll be able to get to the desktop and do web surfing and find out what proprietry driver you need to install. ATI and Nvidia make drivers for Linux, so best go to their websites and download the drivers.

VESA driver?? Uhhh, my Xwindow crashed and I went through the configuration... I selected NV instead of Nvidia (nvidia drivers must have been wrong), not VESA.

This isnt a bad thing I hope... now im wondering if NV is OpenGL capable or not.. are NV drivers capable of accelerated graphics?

To the author- Youve had your Xwindow crash, and its likely the default drivers dont support your video card. Do the command listed above when at a prompt and select VESA- you should have no problems... good luck!

---

### Post by PurplePenguin on 2007-03-31
NV is a driver for nvidia cards that does not include the secret, closed-source accelerated stuff.  If you've got an nvidia card, this driver is fine to select.  If you want the 3D acceleration, you'll need to go to nvidia's site and download the proper driver for your card (these drivers are not included on the Ubuntu disc).

3rd album's instructions are short and sweet - should help anybody in the same situation who comes along.

g0t0, don't let your first experience with the command line scare you! :D

---

### Post by g0t0 on 2007-03-31
To hyper_ch, yes it is the 6.06 alternative cd. 

To 3rdalbum, I got a "xserver-org is not installed" when I inputed your command.

I just burned ver 6.10 and attempted a to install it and I got the same problem with the conventional 6.06, "failed to start X server (your graphical interface). It is likely that it is not set up correctly. WOuld you like to view the X server output to diagnose the problem?"  

So at this point the 6.06 alternative cd was the only one that actually installed something on my laptop.


Here are my laptop specs: 1.60 dual core, 1024mb ram, sata/raid 60g hd, intel 950 integrated graphics.

As far as giving up, I tend to be a pitbull when it comes to  problems, it takes me a while to let go. Especially if I have a good place to get help-Like here (sucking up right about now ;) )

---

### Post by picpak on 2007-03-31
> **g0t0 said:**
> To 3rdalbum, I got a "xserver-org is not installed" when I inputed your command.

Just a typo...it's sudo dpkg-reconfigure xserver-**x**org.

---

### Post by g0t0 on 2007-03-31
Sorry, MY typo. type it in right on the laptop, wrong here. retyped anyways and got the same answer with Xorg.

---

### Post by GSF1200S on 2007-03-31
> **g0t0 said:**
> Sorry, MY typo. type it in right on the laptop, wrong here. retyped anyways and got the same answer with Xorg.

Allow me to link you to my old thread as a reference... I crashed my window because I uninstalled my video drivers with envy, and envy wouldnt reinstall (I have feisty which isnt compatible).

[http://ubuntuforums.org/showthread.php?p=2379660#post2379660](http://ubuntuforums.org/showthread.php?p=2379660#post2379660)

With that thread being posted, I realize some of the commands may be a little foreign to you (as they were to me). When I tried to reconfigure Xorg, it asked alot of questions I didnt know the answer to. The code that worked for me without a hitch was:

sudo dpkg-reconfigure -phigh xserver-xorg

If I understand you correctly, youve never managed to get this working on this particular laptop. I might recommend you trying to install Ubuntu 7.04 (Feisty Fawn Beta). Yeah, its a beta release, but Ive had no problems and it actually cleared up a few hardware problems I had with 6.10... Good luck...

---

### Post by g0t0 on 2007-03-31
I tried the code and was given " Package 'xserver-xorg' is not installed and no info is available".

I will download 7.04 to see if that helps. Until then, does there seem to be something I'm missing or is my laptop too new?

---

### Post by picpak on 2007-03-31
Did you by any chance do a server install? That could do it.

---

### Post by halitech on 2007-03-31
{code]
sudo aptitude install ubuntu-desktop
[/code]

that will install the Gnome desktop. If you want KDE, do kubuntu-desktop and if you want XFCE, do Xubuntu-desktop.

---

### Post by g0t0 on 2007-04-01
> **halitech said:**
> {code]
sudo aptitude install ubuntu-desktop
[/code]

that will install the Gnome desktop. If you want KDE, do kubuntu-desktop and if you want XFCE, do Xubuntu-desktop.

lol, I'm going to have to do more reading to understand that one. Is that the command I use to get me to the desktop? because that is my problem overall.I cant get to it.

I only used the "start and install" selection when I ran the disk from bootup.

I also tried 7.04, but got the same issue as 6.06 ad 6.10. Ive reinstalled Vista until I can get Ubuntu figured out. is there a link i can get that will give me better step instructions and trouble shooting for this problem?

---

### Post by halitech on 2007-04-01
if you did a server install from the alt cd, then you don't have a desktop installed which would be why you can't configure it. You need to install a desktop environment (ie, Gnome, KDE or XFCE) using the commands I posted. 

If you did a normal text based install, then it's not seeing your videocard which seems wierd as it should start in at least the most basic of displays.

---

