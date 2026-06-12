---
title: "editing xorg permission problems"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Pethegreat on 2007-12-24
I am trying to edit my xorg file so that I can get my monitor to work properly. I changed what I needed to, but it won't allow the changes to be saved. It says that I do not have the proper permissions. I know I need to be root, but I don't have any idea on how to log in as root. I was able to view my xorg file in the root terminal, but I do not know how to edit it. 

I also don't know how to have the system run only at 1280x1024@60hz vertical 64kHz horizontal.

---

### Post by overdrank on 2007-12-24
> **Pethegreat said:**
> I am trying to edit my xorg file so that I can get my monitor to work properly. I changed what I needed to, but it won't allow the changes to be saved. It says that I do not have the proper permissions. I know I need to be root, but I don't have any idea on how to log in as root. I was able to view my xorg file in the root terminal, but I do not know how to edit it. 

I also don't know how to have the system run only at 1280x1024@60hz vertical 64kHz horizontal.

HI and try this to edit your xorg
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by LowSky on 2007-12-24
add sudo at the begining of the command your using
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by autocrosser on 2007-12-24
Code is:

sudo gedit /etc/X11/xorg.conf

this will allow editing with root permissions...

What card are you using?

---

### Post by LowSky on 2007-12-24
> **Pethegreat said:**
> 

I also don't know how to have the system run only at 1280x1024@60hz vertical 64kHz horizontal.

Make sure you have enabled your graphics card. Under System>Admin>Restricted Drivers, and turn it on.

---

### Post by Pethegreat on 2007-12-24
Both commands did the same thing... 

I got this message before it opened up my xorg file 

```
root@XXXX-desktop:/home/XXXX# sudo gedit /etc/X11/xorg.conf

(gedit:6781): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

Should I worry about this problem?

---

### Post by taurus on 2007-12-24
> **Pethegreat said:**
> Both commands did the same thing... 

I got this message before it opened up my xorg file 

```
root@XXXX-desktop:/home/XXXX# sudo gedit /etc/X11/xorg.conf

(gedit:6781): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

Should I worry about this problem?

You don't have to log in as root to edit it.  Those commands assume you are doing it from your user account.  But since you log in as root, try

```
nano -Bw /etc/X11/xorg.conf
```
Save the changes with <Ctrl>o and exit with <Ctrl>x.

p.s.  And please use _gksudo_ if you use gedit editor.

---

### Post by ~LoKe on 2007-12-24
Do **not** use sudo with graphical applications.  Use gksudo or gksu.

---

### Post by Pethegreat on 2007-12-24
I got it to 1024x768. 1280x1024 just gives me a black screen for 15 seconds in the test mode. I know my monitor supports 1280x1024 since that is how I ran it back on windows XP.

> What card are you using?
x1650. I used envy to get the drivers working.

---

### Post by lgambett on 2007-12-24
Manually editing X configuration files could be very difficult; try from command line
*sudo dpkg-reconfigure xserver-xorg*
Good luck !

---

### Post by Pethegreat on 2007-12-24
> **lgambett said:**
> Manually editing X configuration files could be very difficult; try from command line
*sudo dpkg-reconfigure xserver-xorg*
Good luck !
That just gives me 800x600. It does not recognize my monitor or video card. I though that would have made everything correct, but it did not.

I am getting extremely poor performance from my video card. I am running nexuiz at default settings, and I am getting around 15-20fps. I assume that the game is based on an older quake or unreal engine. I would think that my x1650 would give me a decent frame rate.

---

### Post by autocrosser on 2007-12-24
what driver are you using?  You should be able to look in xorg.conf & see fglrx--if not, you are using a low performance driver.

---

### Post by Pethegreat on 2007-12-24
I did see the fglrx driver in my xorg. 

That is odd. I am running a 6800gt in a windows machine, and it has no problem with source engine games such as CS:S Looking at the specifications for the x1650 it would seem that it was as good if not better than the 6800gt.

---

### Post by ~LoKe on 2007-12-24
ATi driver support in Linux, for now, is terrible.  However, that's not necessarily the problem here.

---

### Post by autocrosser on 2007-12-24
I'm not much of a ATI guy--I find that nVidia is better supported in Linux---running a 7600 GS PCIe & UT2004 with very good framerates---effects turned almost all the way up....play IG CTF online...

---

