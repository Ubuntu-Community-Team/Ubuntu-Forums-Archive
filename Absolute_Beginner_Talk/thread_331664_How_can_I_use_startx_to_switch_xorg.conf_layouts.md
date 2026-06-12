---
title: "How can I use startx to switch xorg.conf layouts?"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Zoinks on 2007-01-04
I know I can use the -layout option with startx to choose between different server layouts I've setup in the xorg.conf file.  But how do I get to a situation where I can use that command - looks like I need to shutdown xserver somehow, but I don't know how to do that without rebooting.

Is there a command I can use from a terminal inside of an active xserver session that will allow me to restart with a specific -layout argument?

I'd like to do this because I need to switch between layouts on my laptop when I am no longer connected to an external monitor.  I'm using KDE on Kubuntu.

Thanks for any help!

---

### Post by Zoinks on 2007-01-05
Anyone?  There must be a way to exit/restart x from the command line.

I'm open to any other suggestions on how to swap monitor layouts on a laptop.  Right now when not connected to the monitor I get applications opening offscreen, and I don't have a way to reach them.

---

### Post by OffHand on 2007-01-05
```
sudo /etc/init.d/gdm stop
```
```
sudo /etc/init.d/gdm start
```

---

### Post by Ocxic on 2007-01-05
there is a "server layout" section in the xorg.conf file, I beleve be adding your different layouts and changing the identifer you will be able to do it.

the the command would be "startx -layout (custom identifier)"  the bit in brakets would be the layout you wish to use, just leave out the brakets.

this is all a guess, I've never done this b4, just letting you know.

---

### Post by Zoinks on 2007-01-05
> **OffHand said:**
> ```
sudo /etc/init.d/gdm stop
```
```
sudo /etc/init.d/gdm start
```

Thanks for the reply.  I get command not found for gdm.  Is this a Gnome thing?  I'm running KDE - is there an equivalent?

---

### Post by ajmorris on 2007-01-05
gdm is the display manager. if it's not found you are most likely using KDM.

---

### Post by OffHand on 2007-01-06
> **l337 h4x0r said:**
> gdm is the display manager. if it's not found you are most likely using KDM.

That's right. If you use KDE use:

```
sudo /etc/init.d/kdm stop
```
```
sudo /etc/init.d/kdm start
```

---

