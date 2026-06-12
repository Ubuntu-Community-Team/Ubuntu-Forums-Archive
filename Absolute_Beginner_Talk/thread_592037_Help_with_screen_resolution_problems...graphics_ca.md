---
title: "Help with screen resolution problems...graphics card"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by tiger07 on 2007-10-26
Hey, I am pretty new to this so, you will have to walk me through slow.  I have a nvidia 6150 Go graphics card and it is on the list for being capable of using desktop effects, but right now i am having issues even keeping my resolution to the right size.  I am running 800x600  and that is the highest setting i have available.  I have downloaded envy and installed all of the drivers, but no luck.  When i go to the nvidia settings i get a message like this one:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server"

What the heck is this and please help....i am getting tired of all this huge screen action.

---

### Post by tiger07 on 2007-10-26
bump :)

---

### Post by taurus on 2007-10-26
What happens if you run that command from a terminal?

```
sudo nvidia-xconfig
```
When you are done, you can restart X with <Ctrl><Alt>Backspace.

---

### Post by tiger07 on 2007-10-26
I get nothing, i still get the error message and can't change the screen resolution

---

### Post by tiger07 on 2007-10-26
bump

---

### Post by tiger07 on 2007-10-26
bump :)

---

### Post by Drakkor on 2007-10-26
Yeah,having same problem, only my highest resolution is 640X480 ! 
Try doing ```
sudo gedit /etc/X11/xorg.conf
```
Then under your video card driver,change "nvidia" to "nv" , save and
log out and in again,
that should allow you to change your resolution. In my case that works
but as soon as I try to enable the nvidia restricted drivers,it reverts back
to only 640X480 ! I really wish someone would address this problem !!

---

