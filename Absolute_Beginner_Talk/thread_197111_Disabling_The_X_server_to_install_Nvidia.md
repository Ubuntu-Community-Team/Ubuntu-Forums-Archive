---
title: "Disabling The X server to install Nvidia?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by algoart on 2006-06-15
Hi all,
Absolute beginner here! Sorry!
I've been trying to install Nvidia drivers via the root console, the install starts, but then a message informs me that X server is running and should be closed down. How do I do this?:-& 
I've checked various places (everywhere I could find) but still don't have an answer!

---

### Post by taurus on 2006-06-15
How did you try to install it?  There is a nvidia driver in the repo so why not install it the easy way (from a terminal)...
```

sudo apt-get install nvidia-glx

```
Now, edit your /etc/X11/xorg.conf and replace the "nv" with "nvidia" as your Driver...
```

sudo gedit /etc/X11/xorg.conf
-or-
sudo nano /etc/X11/xorg.conf

```

---

### Post by Jagot on 2006-06-15
After:

```
sudo apt-get install nvidia-glx
```

You just need to run the following command and xorg will be updated after restart - no manually editing it

```
sudo nvidia-glx-config enable
```

---

### Post by algoart on 2006-06-16
Thanks for your help on installing Nvidia. I think, in the end, the problem is my ATI chipped motherboard.
Gave up on my new Nvidia 7300, plonked my old ATI back in, quick reinstall of Ubuntu - perfect.
Now I can go and waste today trying to get my SB Audigy 2ZS running. **Anything** to get away from XP Media Center!:D 

Thanks

---

### Post by nudnik on 2006-06-16
If anyone is interested, the command to stop x-server in gnome is :

sudo /etc/init.d/gdm stop

To restart:

sudo /etc/init.d/gdm start

---

### Post by xenblend on 2006-06-16
personally, I would boot using the failsafe kernel version to get straight into a console and do it that way.  You could also enter into the console 'sudo rc 1' to enter single-user mode (xserver won't be running in here) and do it that way.  GOod luck.

---

