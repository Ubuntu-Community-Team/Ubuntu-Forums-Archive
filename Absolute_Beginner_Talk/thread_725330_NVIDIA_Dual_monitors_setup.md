---
title: "NVIDIA Dual monitors setup"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by madbeader on 2008-03-15
I appreciate any help on this as I just installed 7.1 Ubuntu dual boot with Vista without any problem.  I have a NVIDIA 8600 and dual Samsung momitors connected by DVI.  Both monitors are showing the same desktop (cloned) not spanning the desktop.
I've looked under Administration/screens and graphics and the "secondary Screen" is not selectable and Screen 1 is listed as a custom monitor with no second monitor listed.  Up to this I've been able to figure everything out but I'm stumped on this.
Thanks in advance for any help

---

### Post by dokdoom on 2008-03-15
It may not seem like it right now but you are very fortuante. I've tried getting dual display working with a lot of cards (well... 3 ati, intel and nvidia.) and nvidia is the only one with an easy gui. Not the one in the OS but nvidia has it's own. 

on your command line type nvidia -h or --help and it should have an option like nvidia-display (Not 100% sure but something of that manner. You may have to check and play with each one.) But what I do know for sure is there is a gui you can run where you simply drag the monitors to the correct side and choose the correct resolution. 

Let me know what you find.

---

### Post by forrestcupp on 2008-03-15
> **dokdoom said:**
> 
on your command line type nvidia -h or --help and it should have an option like nvidia-display (Not 100% sure but something of that manner. 

It's nvidia-settings.  If you have the proprietary drivers installed, you can type nvidia-settings in a terminal, and it will bring up a GUI for your card's settings.  There is a place to set your screens in that.

---

### Post by drubin on 2008-03-15
In windows it is called "dual view"

I think in linux it is called "twinview" Havent set it up in my ubuntu though

---

### Post by herbster on 2008-03-15
You want nvidia-settings as mentioned, but what you want here is to modify your /etc/X11/xorg.conf file, and running nvidia-settings without root permissions will not save any changes you make upon a reboot. So just run:

```
sudo nvidia-settings
```

I have been running dual monitors for quite some time now with a couple Nvidia cards, as said the GUI is very easy to configure them. You want to select TwinView in the X Server Configuration:

[img]http://www.bobgill.net/nvidiasettings.jpg[/img]

When you've got the Twinview going (Dualview on Windows is the equivalent, merely a naming issue), hit Save to X Configuration File and you're done. Let me tell you, the moment you've got it going the way you want, BACK UP YOUR /etc/X11/xorg.conf. Whenever I reinstall, my xorg.conf takes care of everything for my visuals upon driver install. You don't want to keep setting it up again and again.

---

### Post by forrestcupp on 2008-03-15
> **herbster said:**
> You want nvidia-settings as mentioned, but what you want here is to modify your /etc/X11/xorg.conf file, and running nvidia-settings without root permissions will not save any changes you make upon a reboot. So just run:

```
sudo nvidia-settings
```

Good call on the 'sudo'.

---

### Post by madbeader on 2008-03-21
Thanks for your help on this issue.  I got it working just fine, it was relly quite simple in the end.

---

### Post by ForceUser on 2008-04-09
> **herbster said:**
> You want nvidia-settings as mentioned, but what you want here is to modify your /etc/X11/xorg.conf file, and running nvidia-settings without root permissions will not save any changes you make upon a reboot. So just run:

```
sudo nvidia-settings
```

I have been running dual monitors for quite some time now with a couple Nvidia cards, as said the GUI is very easy to configure them. You want to select TwinView in the X Server Configuration:



When you've got the Twinview going (Dualview on Windows is the equivalent, merely a naming issue), hit Save to X Configuration File and you're done. Let me tell you, the moment you've got it going the way you want, BACK UP YOUR /etc/X11/xorg.conf. Whenever I reinstall, my xorg.conf takes care of everything for my visuals upon driver install. You don't want to keep setting it up again and again.

Nevermind I fixed it

---

### Post by Hobo Joe on 2008-04-09
> **ForceUser said:**
> I'm trying to setup my other monitor, but whenever I try to save to the X configuration file it says "Unable to create new X config backup file". Any idea how to fix that?

You have to use sudo to give the nVidia control panel the administrative power to modify the xorg file.

So use
```

sudo nvidia-settings

```

---

