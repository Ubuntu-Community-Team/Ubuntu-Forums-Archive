---
title: "I dont have a /usr/bin/Xgl directory"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Rizla on 2006-09-14
Retard here again..  I've been following the how-to's to get Xgl/compiz installed on my new Nvidia card and I've followed the directions letter for letter.  WHen i rebooted i was getting an error that GDM cant start because a file doesnt exist in /usr/bin/Xgl.  I did all the apt-get installs that were listed..

Right now i cant get back into the gui because of this.. When i boot into the gui, it just turns the monitor off, but i can hear the login sound start.

F'n Ay..

---

### Post by Rizla on 2006-09-14
i tried doing apt-get install xserver-xgl but it says i have the latest version

---

### Post by Najand on 2006-09-14
Try:
```

locate Xgl

```
to  see  if you can find it or not.

---

### Post by Rizla on 2006-09-14
> **Najand said:**
> Try:
```

locate Xgl

```
to  see  if you can find it or not.

here's what turns up

/usr/share/apps/kdesktop/programs/xglobe.desktop
/usr/share/automatix/conf/ati/startxgl.sh (Should i get rid of this since i dont have ati?)
/usr/share/automatix/conf/ait/gnome/startxgl.sh
/usr/share/automatix/conf/ati/kde/startxlg.sh
/usr/share/automatix/conf/nvidia/startxlg.sh
/usr/share/automatix/conf/nvidia/startxlg.sh
/usr/share/automatix/conf/nvidia/gnome/startxgl.sh
usr/share/automatix/conf/nvidia/kde/startxgl.sh
/usr/share/automatix/conf/xgl.desktop
/usr/share/openclipart/svg/signs_and_symbols/foxglove_0_symbol_1m_bwh.svg

there might be a couple typos since i'm looking at two monitors, one with my busted linux and the other my windows whcih im typing on now

So it looks like i have it, but how come i have no xgl directory? in my usr/bin/xgl?

BTW, i cant even boot to gui anymore.  Screen just shuts off as if the computer was off.  I tried doing the xorg reconfigure process, but that didnt help

---

### Post by Najand on 2006-09-14
Try to remove and install it again.
```

sudo apt-get remove xserver-xgl && sudo spt-get install xserver-xgl

```

---

### Post by Rizla on 2006-09-14
> **Najand said:**
> Try to remove and install it again.
```

sudo apt-get remove xserver-xgl && sudo spt-get install xserver-xgl

```

just gave that a try, but once i restared its doing the same thing.  Goes into the gui and then the monitor shuts off again..

This is so ubelievably frustrating.  I dont want to have to reinstall ubuntu all over again to fix my display.  I've done too many reinstalls for the short time i've had ubuntu..

im actively monitoring this thread, so if you respond, i'll respond quickly.  ie. i refresh every 30 seconds.

---

### Post by Najand on 2006-09-14
Hmm... were you using xserver-xorg before installing xserver-xgl?

---

### Post by Rizla on 2006-09-14
> **Najand said:**
> Hmm... were you using xserver-xorg before installing xserver-xgl?

I believe so, but im not 100% sure.  Should i try removing xorg and reinstalling it like you suggested before?

---

### Post by Rizla on 2006-09-14
great news!! uninstalling xorg and resinstalling worked now its back up.  PHEW! now i need to install xgl/compiz on dapper.. the tutorial i worked on didnt seem to help

---

### Post by Rizla on 2006-09-14
I ended up following this guide:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29")

It seems to have worked, but I dont have any of that neat 3d stuff like the cube

---

### Post by Najand on 2006-09-14
What are you going to do next? And what is the current situation there?

---

### Post by Rizla on 2006-09-14
> **Najand said:**
> What are you going to do next? And what is the current situation there?

right now my desktop seems to be back in working order.  I see that i have the compiz settings manager in my system -> prefrences but I dont have those cool animated effects that I want.  Like the 3d cube.  WHen i press ctrl+alt+ (direction arrow)  it just shows up a 2d image of my screens. 

I followed the guide and did everything it said.

---

### Post by Rizla on 2006-09-14
correction, i typed thefuture and now it has the cool effects, but i did get an error gconf

---

### Post by Rizla on 2006-09-14
my alt keys dont work anymore... this shit never stops.  SOmething works, something breaks.  I cant alt+f4 to close a window.  Or ctrl+alt+arrow to switch desktops.  I do have the cube working, but only when i click on the desktop i want to switch it to.

---

### Post by Timothy Butwinick on 2006-09-14
> **Rizla said:**
> there might be a couple typos since i'm looking at two monitors, one with my busted linux and the other my windows whcih im typing on now

You wouldn't have to do that: There are command line web browsers as well. w3m, for example works great with ubuntuforums.org.

---

