---
title: "ubuntu and kde died. wheres KDE?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by jklslvch on 2007-04-30
hey i installed Ubuntu and wanted kde so i installed the KDE packages ( sudo aptitude install kubuntu-desktop ) waited 3 hours for it to download and install, logged out it ran great but when i rebooted it kde nor gnome wanted to work anymore so im running SLAX (livecd ww.slax.org) right now. Now what i want to know is if those packages for kde are still on my HDD and where at and what to do to reinstall everything again but without having to download KDE all over again (for me 217MB = 3hours:( )????

---

### Post by Seisen on 2007-04-30
Can you change the session to log into KDE or won't it even let you do that?

---

### Post by Wiebelhaus on 2007-04-30
I tried this awhile back and it blew up , honestly gnome for ubuntu is better anyway.....

I'm sure someone will disagree but If you dig KDE go with a Suse installation.

---

### Post by jklslvch on 2007-04-30
i get to the login screen (i think KDM the kde one not the gnome one) and it ask for usr name and pass i put them in and it jsut stays on the kubuntu screen (just the wallpaper and mouse) i can move the mouse around but i cant do anything.

i dont want to wait all that time to download the KDE packages so could somebody tell me where those files were saved to when i firt downloaded them? or where they just installed and deleted?

---

### Post by Wiebelhaus on 2007-04-30
you tried safe graphics mode?

I'm sure you have to remove gnome when installating kde tho'.

---

### Post by Seisen on 2007-04-30
You don't have to remove gnome when you install KDE. You can boot into recovery mode and uninstall KDE and see if that works. 

```
sudo apt-get remove kubuntu-desktop
```

---

### Post by jklslvch on 2007-04-30
hey i started ubuntu with the second onption in grub (safemode i think) and it takes me to a terminal screen and i try startx and ubuntu boots, i logout and type kdm and the manager comes out and i can log into GNOME and KDE and they both work. i dont know what it is but its working is there anyway i can fix the problem with the normal grub boot option? or whats going on whys is working in safemode and not normally?

---

### Post by Seisen on 2007-04-30
But does itshow up as the Gnome Display manager or KDE Display manager or neither..

---

### Post by walesmd on 2007-04-30
I did the exact same thing you did and it continued to boot into Gnome. You have to manually change your session (whenever you enter username and password) to use KDE as your dekstop manager. Once you do it the first time it should remain at KDE until you change it.

I believe Ubuntu by default, launches the last used desktop manager - which in your case, is Gnome until you change it.

---

### Post by jklslvch on 2007-04-30
once i boot it in the second option in grub the safemode one it shows me whats going on whats loading and everything and drops me off at a terminal screen so i can type off from there and the command startx takes me to ubuntu (as if it were to boot normally ) i log out of it and again i get droppped off at the terminal screen and i type KDM wich is the kde account manager and it loads as if i were to boot it normally. i dont know what the deal is why the first boot option in grub doesnt work for me anymore as it used to. the only thing that bugs me now is that i get left at the terminal screen. it really isnt a problem for me (im a bit more used to slackware and i can get around in a terminal) but i know that its not suppsed to be like that. well i guess i have no problem actually but that itch knowing that its suppsed to boot up and take me to the KDM screen to login.

---

### Post by walesmd on 2007-04-30
I didn't even mess with grub when I did it - I found a tutorial just now that steps through how to install and use Kubuntu on top of Ubuntu.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by jklslvch on 2007-04-30
> **walesmd said:**
> I didn't even mess with grub when I did it - I found a tutorial just now that steps through how to install and use Kubuntu on top of Ubuntu.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)


i used this page to install kubuntu over ubuntu but something must have went wrong because after the 2nd or 3rd boot it stopped working. and instead of having to do that over again i wanted to know where the files that i downloaded were originally stored so that i could just copy them reinstall Ubuntu and copy those files back and install them.

---

### Post by Wiebelhaus on 2007-04-30
> **Seisen said:**
> You don't have to remove gnome when you install KDE. You can boot into recovery mode and uninstall KDE and see if that works. 

```
sudo apt-get remove kubuntu-desktop
```

My apologies , I would have sworn I read that you had to remove gnome.

---

### Post by jklslvch on 2007-04-30
found where the downloaded files went :

/var/cache/apt/archives

---

