---
title: "I need to shift my display"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by clarkth on 2006-07-20
Hello, I just installed ubuntu on my desktop (dual boot with XP) and have a dell 17" LCD monitor with the resolution set to 1280x1024 @ 75hz.  The display is shifted off to the left so I can't see the top right portion of the screen, and a black line about 3/4" wide is on the left side.  With XP the display is fine at these settings.  What can I do to shift the display to the right?  I looked at xvidtune, but couldn't figure out how to move the display (kept getting an error that my hardware didn't support my settings).  Thanks in advance for your help.

---

### Post by Kilz on 2006-07-20
> **clarkth said:**
> Hello, I just installed ubuntu on my desktop (dual boot with XP) and have a dell 17" LCD monitor with the resolution set to 1280x1024 @ 75hz.  The display is shifted off to the left so I can't see the top right portion of the screen, and a black line about 3/4" wide is on the left side.  With XP the display is fine at these settings.  What can I do to shift the display to the right?  I looked at xvidtune, but couldn't figure out how to move the display (kept getting an error that my hardware didn't support my settings).  Thanks in advance for your help.

Most monitors have adjustment buttons on the front to center the image. You may want to look at the monitor's user manual to learn how it is done on your monitor.

---

### Post by clarkth on 2006-07-21
I tried this, and while I could get it lined up in Ubuntu, it was then off in XP.  I'm hoping there is a way to adjust the xorg.conf file (or some other file or program or setting) to shift the display to the right for Ubuntu only.  Thanks

---

### Post by Sefianix on 2006-07-23
> **Kilz said:**
> Most monitors have adjustment buttons on the front to center the image. You may want to look at the monitor's user manual to learn how it is done on your monitor.

I'm having the same problem, however, I have a laptop and don't have any adjustment buttons.  Does anyone know how to adjust this?

---

### Post by Jagot on 2006-07-23
I had the same problem and installing the proper drivers for my Nvidia graphics card sorted it out.

---

### Post by crystal on 2006-07-23
> I tried this, and while I could get it lined up in Ubuntu, it was then off in XP.
After using the auto-adjustment button on my LCD monitor this was fixed for both Ubuntu Linux and Windows XP.

---

### Post by slimdog360 on 2006-07-23
you have to change the HorizSynch and VertRefresh in your xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```
that will open it for you and create a backup incase you completely stuff it.
Just try changing the numbers a little in the HorizSynch and VertRefresh parts. You can google around a little and maybe find some. There is also a little about it in my blog(link is in my sig).

---

### Post by woedend on 2006-07-23
hehe changing your xorg isn't going to help.  I have the same problem when switching between nv and nvidia drivers

---

