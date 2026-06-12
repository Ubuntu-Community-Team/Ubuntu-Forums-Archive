---
title: "Tried to uninstall gnome for a pure KDE install..."
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Andross707 on 2007-07-03
Ok, so I installed KDE desktop with aptitude while I had Gnome only

 ```
sudo aptitude install kubuntu-desktop
```

Then, I tried to uninstall Gnome (using this guide: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde) ) which told me to copy and paste the code at the bottom into the terminal prompt to uninstall gnome (or so I thought). After doing that I am left with a pretty broken looking desktop so I decide to restart. Upon restarting, I can now no longer access a any GUI and when attempting to type startx I am given an error message with a lot of text and at the end it says> Fatal Server Error:
No Screens Found

XIO: Fatal IO error 104 (connection reset by peer) on X server ":0.0"

Does anyone know of a way to get a pure KDE install from here while preferably not having to entirely uninstall  everything then installing Kubuntu?

---

### Post by davidjmayo on 2007-07-03
When you uninstalled gnome you probably removed somethings that other apps need to run

At the terminal reinstall gnome 

```
Code:
sudo aptitude install gnome-desktop-environment
```



For a pure KDE you will need to install kubuntu but I have had no problems with the choice of using either wether I installed gnome or kubuntu originally. Purists might say a clean pure KDE install is better?

---

### Post by Andross707 on 2007-07-04
How should I go about installing Kubuntu for a pure KDE install? Can I keep the partition I made and somehow replace Ubuntu with Kubuntu? I would like a pure KDE install.

---

### Post by sailor2001 on 2007-07-04
> **Andross707 said:**
> How should I go about installing Kubuntu for a pure KDE install? Can I keep the partition I made and somehow replace Ubuntu with Kubuntu? I would like a pure KDE install.

why bother? having both doesn't use up much space...you can ctrl/alt+backspace = sessions and make kde your default. assuming you do have KDE installed (synaptics/KDE)

---

### Post by mig5 on 2007-07-04
> **Andross707 said:**
> Can I keep the partition I made and somehow replace Ubuntu with Kubuntu?

If you have a separate partition for your /home mount then you can keep your personal data and a lot of program settings.

---

### Post by Andross707 on 2007-07-04
The main reason I want a pure install is just to clear up some of the gnome icons in the menu and to not waste any space because I'm honestly not sure exactly which apps are gnome and which are KDE besides the ones that start with 'k'. (maybe I'm just used to windows and its registry or something so perhaps linux keeps itself clean?)

---

### Post by Andross707 on 2007-07-05
As an update, now
1) I think I deleted startx.conf in hopes that it would regenerate and now typing startx in the console just hangs the computer.

2) Every time I try to burn a kubuntu live cd (even on the slowest setting) I get sectors missing on the CD. I've tried downloading it twice and burning it 3 times. Does anyone know of a decent burning program or a way to see if I'm just getting bad downloads?

---

### Post by davidjmayo on 2007-07-06
> 2) Every time I try to burn a kubuntu live cd (even on the slowest setting) I get sectors missing on the CD. I've tried downloading it twice and burning it 3 times. Does anyone know of a decent burning program or a way to see if I'm just getting bad downloads?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Just do what it says. Check the download is good with the MD5sum (you can check the downloads you have already) 
burn at a slow speed (4x or even 1x)

---

