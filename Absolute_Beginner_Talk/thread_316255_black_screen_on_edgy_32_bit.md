---
title: "black screen on edgy 32 bit"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by Usedpants on 2006-12-10
so i have been messing around with ubuntu for about a week now. I had the x64 edgy and after trying to install nvidia drivers from automatix2, the card stopped sending a signal to my monitor. I tried the command that they gave me on install to rollback but that did not work. That happened again after reinstall. So i decided to go to the 32 bit edgy. Now when it gets past the loading screen, it turns black and thats it. it is still sending a signal but its black. i restarted and ran in safe graphics. Same Thing! If i go back even farther to 6.8 i believe, would i be able to install nvidia drivers for 64 or even 32 bit? My current card is an XFX Geforxe 7600GT XXX Edition thats overclocked to 590core and 1600mem speeds from the factory. I really want to run ubuntu and i can get everything working perfectly except the video and i dont want to have to run windows for as little as video drivers :( someone please help!

---

### Post by bscbrit on 2006-12-10
First of all, lets get a working basic system rather than worrying about overclocking and specialised drivers.

Restart the system in Recovery Mode.  Once logged on as root (which is automatic - don't actually do anything to log on, type:

dpkg-reconfigure xserver-xorg

The wizard that starts will reconfigure your system back to a basic working system.  If you do not know the answer to a question, accept the default by pressing [Enter].

When the wizard is complete type:

reboot -f

Let the system start without any input from you.  Let me know when you have recovered the GUI or if you don't succeed.

---

### Post by Usedpants on 2006-12-10
going to try that now. and i was stating it was overclocked incase thats a reason why it might not be identifying the card correctly. be back

---

### Post by Usedpants on 2006-12-10
ok so i did that. and it switched from my 1280x1024 NEC monitor to my 1440x900 samsung widescreen. i cannot get any resolutions over 1024x768. Any ideas?

---

### Post by bscbrit on 2006-12-10
Did you select any resolutions greater than 1024x768 in the wizard?

How many monitors / graphic cards have you got installed?

---

### Post by Usedpants on 2006-12-10
2 monitors and 1 card. its weird i made a backup of my xorg.conf on my desktop and edited it by switching resolution in every "depth" section from 1024x768 to 1440x900 and added a depth "32" and set that as default. i then stopped X and was in a text mode, i typed "sudo cp /home/nick/Desktop/xorg.conf /etc/x11/xorg.conf" which i believe copies the xorg.conf from my desktop over the one my system uses. i did "reboot-f" and i actually saw my other monitor turn on and display up till the log on screen.  After i logged in i saw that nothing changed in xorg.conf and my 2nd monitor is black again. any ideas? Sorry for bugging everyone.

i am also on the ubuntu edgy 6.10 x64 release just so you know.

---

### Post by bscbrit on 2006-12-10
Are you sure that the graphics card can show that resolution at that depth?  I don't know the card so it seems a reasonable question to ask.

Try stepping up from 1024x768 a resolution at a time and see where the problems begin.

Sorry, other than that I don't think I can be much help.

---

### Post by Usedpants on 2006-12-10
it displays it at that resolution easily on windows. Does ubuntu support 32 bit depth?

---

### Post by bscbrit on 2006-12-10
I'm not sure how to switch between screens in xorg.conf, but check the contents to see if you might be selecting the wrong screen.

Why xorg.conf is unchanged after copying a new version across is a mystery, but try it again, check it is there, and then log out and back on to restart x - or simply hit Ctrl-Alt-Backspace.

---

### Post by Usedpants on 2006-12-10
i still do not know why it switched screens. But i would rather use my 19" widescreen over my 17" square. I thought about it and when dpkg-reconfigure xserver-xorg did not work it was my fault. When it came to resolution i highlighted what i wanted and hit enter. I guess i had to select it with spacebar and then hit enter, but just in case, i deselected all other resolutions. Something also happened to make it correctly detect my video card and now i have nvidia settings and all this other great stuff. Now im off to figure out how to add another monitor to xorg.conf . I heard its best to run it off livecd with my 2nd monitor attached and my main unplugged, then copy the contents of xorg.conf and add them to my installs xorg.conf when i reboot. I am just gonna look around to make sure though . Thank you sooo much for your help. i really appreciate it.

---

### Post by bscbrit on 2006-12-11
You're welcome - see you around the forum. :-D

---

