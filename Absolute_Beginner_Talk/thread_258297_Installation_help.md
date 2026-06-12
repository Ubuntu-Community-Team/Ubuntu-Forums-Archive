---
title: "Installation help"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by ntroast on 2006-09-15
I booted up the live cd and my resolution is set to 640x480, I tried changing the resolution but it only gives me one option 640x480. I cant install ubuntu because the installer is larger than my screen resolution, I cant see the next button lol.

---

### Post by viniosity on 2006-09-15
Try using the server CD.  You can install and configure X afterwards!

---

### Post by ntroast on 2006-09-15
well i did some browsing around and i found this command
```
sudo dpkg-reconfigure xserver-xorg
```

I pressed ctrl+alt+f2 to get into the terminal then ran the command and set everything up. The only problem is I dont know how to get from the terminal back to the desktop lol

---

### Post by Xappe on 2006-09-15
ctrl+alt+f7

---

### Post by ntroast on 2006-09-15
ok i did all that and got back to the desktop but im still in 640x480. Im using dapper drake 6.06.1 and nvidia geforce mx400

---

### Post by bulldog on 2006-09-15
I think the trouble is there's no driver installed for your videocard.
It's been seen as a generic card with less options.

Try to install Ubuntu,after the install,get the nvidia driver and I'm pretty sure you can alter your resolution,if not done automaticly.

---

### Post by someusernoob on 2006-09-15
I dont know much about configuring X when using the live cd so im not going to give any suggestions on that part, but what i do know is that you can grab and move the windows with alt+left mouse button - so then you'll be able to move to and click the next button.

And yes, like bulldog says, after installing Ubuntu we can - if you need it - help you setting up the right resolution if it aint done automaticly.

---

### Post by Xappe on 2006-09-15
If you really need to alter your resolution when running the livecd you could try to tell the xserver wich refresh rates it should use for your monitor. Check in the monitor's manual for the Horizontal and vertical refresh rates, then:

1. sudo gedit /etc/X11/xorg.conf
2. add these two lines in the "monitor" section:

HorizSync min-max
VertRefresh min-max

where min and max are the minimum and maximum values of the refresh rates respectivly.

Save and hit <ctrl>+<alt>+<backspace>

---

### Post by ntroast on 2006-09-15
using alt+left click worked perfectly. I was able to install no problem. Now the resolution can be changed just fine. Thanks for your help :)

---

