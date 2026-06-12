---
title: "Cant boot properly after installing Ubuntu Studio"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by CAD-MAN on 2007-10-06
Hi.

I installed some parts of Ubuntu Studio over my Gutsy system. Now, when I boot, I select my kernel in GRUB, and then Ubuntu doesn't boot properly. All I get is some black command line that allows me to log on in non-graphical mode.

Here is what I did:

Added the Studio repository, then

```
sudo apt-get install ubuntustudio-theme ubuntustudio-icons ubuntustudio-look ubuntustudio-gdm-theme
```

I just wanted the look of Ubuntu Studio, but was happy with my system, so didn't see the point in doing a full install.

Then, having looked at and tried the 'Ubuntu studio look', I decided I liked it as it was before, so proceeded to:

```
sudo aptitude remove ubuntustudio-look
```

On reboot, I got the problem that I explained in the first paragraph; no GUI. Does anyone have any idea how I can get my system back to normal? I don't even want the Studio stuff anymore.


Thanks

---

### Post by taurus on 2007-10-06
Log in with your name and password and what happens when you run this command from a prompt?

```
startx
```

---

### Post by CAD-MAN on 2007-10-06
Thanks taurus, I did that, and at first it hung on what looked like some kind of primitive GUI, that was a blank screen (but dotted), with an X shaped cursor. After about 30 seconds, it loaded the GUI properly.

I got an error box when I logged in though:

```
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

Do you want to delete the applet from your configuration?
```

Shall I give it a yay or nay?


Thanks

---

### Post by taurus on 2007-10-06
Maybe when you installed Ubuntu Studio, perhaps it deleted some Gnome apps.  Try reinstalling them again with

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

p.s.  Nay for your question.

---

### Post by CAD-MAN on 2007-10-06
Thank you very much Taurus, everything appears to be fine now :)

---

### Post by vnskyhorse on 2007-10-24
thanks alot, problem has been solved

---

### Post by jimmydorsey on 2007-10-25
I have a similar issue, but that is about where the similarity ends. 

I loaded ubuntu studio 7.10 (64) on a newer compaq laptop (fresh).  It is a dual core amd64.  Everything seems to be working great.  I am actually really excited about this version.  Gimp is a lot faster for high res pictures or at least the perception is there.

My issue.  When I boot, the system it hangs right after grub.  It will hang there indefinitely if I do not touch it.  I lucked up and happened to push the power button for about 1 second trying to restart when that kicked it over to loading ubuntu studio.  I was going to hold it for 4 seconds, but let go thinking hmmmm.  I  did a restart too and the hang happens everytime.

Another symptom is that is does the exact same thing on shutdown.  It pauses indefinitely on the shutdown graphic until I press the power button for about 1 second.

Is there enough information here that someone knows what I can do to possibly fix this?  I loaded the OS with the **noapic** startup parameter for install.  My laptop doesn't boot standard ubuntu live CD without the it.  I thought I should use it when loading ubuntu studio.

Thanks in advance to anyone.  I can live with this just to use the os, but I am betting there is a solution.

---

### Post by taurus on 2007-10-25
Try editing /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and remove the** quiet** option at the end of the kernel entry.  Then, reboot and see which process is causing it to hang.

---

### Post by jimmydorsey on 2007-10-28
Taurus -

Thanks.  Got a stopping point.  

**[   15.353172] io scheduler cfg registered (default)**

That is the last line on the screen.  I am a little unfamiliar with this notation, but I am googling...

I assume the last line is where it is hanging, correct?

You help was great,  

stephen.

PS - Before posting, I do see some other help for this failure in ubuntu forums.  I'll probably find the resolution now.  Thanks again.

---

### Post by jimmydorsey on 2007-10-28
Taurus -

Seems apci=off needed to be added, but then I get no processor scaling.  hmmmm.  I'll stick with the crazy "have to push the power button twice" to start it - unless you know some other tricks?

Thanks again,

stephen.

---

