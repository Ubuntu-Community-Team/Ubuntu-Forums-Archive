---
title: "NVIDIA glx problem"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by gator_grabber on 2007-06-16
Man, I hate being a newbie again! No sooner did I get 7.0.4 Ubuntu running on my AMD64, I've run into trouble with nvidia-glx. Following MaximumPC's directions, I went to synaptic package manager and installed nvidia-glx (from top of supplied list). I applied it as directed and rebooted. On startup I get the "Failed to start the X server (graphical interface)" message. Being the noob that I am, I have no idea what I did wrong or how to fix it. My video card is a NVIDIA GeForce 6800 Ultra. Any words of wisdom? Thanks!

---

### Post by Jimmyfj on 2007-06-16
You type the following:

sudo dpkg-reconfigure xserver-xorg

try eventually with the option -a

---

### Post by bodhi.zazen on 2007-06-16
> **gator_grabber said:**
> Man, I hate being a newbie again! No sooner did I get 7.0.4 Ubuntu running on my AMD64, I've run into trouble with nvidia-glx. Following MaximumPC's directions, I went to synaptic package manager and installed nvidia-glx (from top of supplied list). I applied it as directed and rebooted. On startup I get the "Failed to start the X server (graphical interface)" message. Being the noob that I am, I have no idea what I did wrong or how to fix it. My video card is a NVIDIA GeForce 6800 Ultra. Any words of wisdom? Thanks!

You like likely need to configure X a little.

```
sudo aptitude install nvidia-glx nvidia-kernel-common
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup *#This makes a backup of your current xorg.cong*
sudo nvidia-xorgconf
sudo /etc/init.d/gdm restart *#Restarts X*
```

---

### Post by logos34 on 2007-06-16
> I applied it as directed and rebooted.

You mena you ran 'sudo nvidia-glx-config enable'?  And did you do anything else before rebooting like download and install updates?  If so the kernel updated and that means you have to reinstall the graphics driver.

Go through the interactive X config:
[B]
sudo dpkg-reconfigure xserver-xorg[/B]

---

### Post by gator_grabber on 2007-06-16
Reconfiguring Xserver did the trick, thanks!

---

### Post by Sailor-Moon on 2007-06-18
same problem but i have a g force 5200 
i tried the solution posted here, when trying to make a back up system could not make back up, following command was not recognised (in the list above posts)

---

### Post by RomeReactor on 2007-06-18
Hi. Do you mean these commands posted by **bodhi.zazen**?
> sudo aptitude install nvidia-glx nvidia-kernel-common
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup #This makes a backup of your current xorg.cong
sudo nvidia-xorgconf
sudo /etc/init.d/gdm restart #Restarts X
If so, try the second command using sudo:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
and as for the third command, I think it's:
```
sudo nvidia-xconfig
```

---

### Post by Sailor-Moon on 2007-06-20
thank you it worked!


it was my fault, i was typing Xll  not X11 but after typing your code, it came up on the screen it was reading from X11 so i then followed the instructions, did the reset and it works great!:p

---

