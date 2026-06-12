---
title: "I can't configure my screen settings.."
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Exershio on 2007-03-03
hey, I just installed Ubuntu 6.06 and when I try to change the screen resolution, it flashes between resolutions for a second and then logs me out. Also, when I push the buttons on my monitor to adjust the screen size/shape, nothing happens.

I really need to adjust these two things because my resolution is too low, and because my screen is funny shaped and partly off the viewing area on my monitor.

---

### Post by luke411 on 2007-03-03
dpkg-reconfigure xserver-xorg

Type that in the terminal as root and you will get a menu that will walk you through several steps in setting up your graphics card. Most of these screens you can leave as they are and try adjusting for different resolutions and refresh rates. You may have to run through them a few times until you find something that works. Also, after each change, make sure you do a complete restart of the system to see the effect the last change had on it.

If you should set it to a point that won't into your desktop at all and you only get a cursor, don't fear, you can launch the same program from the console, again, after logging on as root and reversing your changes. Just try to keep track of what changes you make so that you can change them back if need be.

---

### Post by Exershio on 2007-03-03
It's telling me I have to run that command as root, but I don't have a root user. It never added one.

What do I do? XD I'm new to linux obviously

---

### Post by Spin Doctor on 2007-03-03
In your terminal, type:
```
sudo dpkg-reconfigure xserver-xorg
```It will ask you for your admin password, and there you are now editing with root rights! =)

---

### Post by linux_trg on 2007-03-05
i also have a problem too. 
after install ubuntu...
then i restart, to test the loading
it was appear this 
i hope someone can help me to solve this problem :confused: :confused:

---

### Post by jamyskis on 2007-03-05
That's your monitor telling you that it can't display the resolution you've selected at the optimal screen refresh rate that you've given. In short, it's either trying to update the picture on your screen either too quickly (more likely) or too slowly.

Start up in recovery mode and run dpkg-reconfigure xserver-xorg. When you're given the option to select a monitor frequency range, select simple and then the size of your monitor.

---

