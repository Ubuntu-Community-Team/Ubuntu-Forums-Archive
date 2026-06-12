---
title: "ubuntu won't load with new monitor"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Cholera on 2007-12-24
hey y'all,

i had to change the monitor associated with my ubuntu machine for non-technical reasons, and i now cannot get it to load up. it begins to load, then the screen flashes black and i can hear my computer working hard, but nothing happens. i can get into recovery mode, but i'm linux-dumb and have no idea what to do there.

the monitor i changed to is much smaller and worse than the one i was previously using, if that matters.

thanks if anyone can help me!

---

### Post by taurus on 2007-12-24
You need to reconfigure your X server.  You can do that by booting your machine to recovery mode from GRUB menu.  Then at the prompt, type

```
dpkg-reconfigure -phigh xserver-xorg
```
Then, reboot with

```
shutdown -r now
```

---

### Post by Rocket2DMn on 2007-12-24
The problem was most likely that the screen resolution you had before was too high for your monitor to handle.  Reconfiguring the X-server like taurus said will allow you to select the correct resolutions - use TAB to move around and SPACEBAR to select the new monitor's highest resolution and everything less (probably 1024x768 if that monitor isn't too good).
If you're stuck at getting to a command prompt to start all this, do CTRL+ALT+F1 to get to a tty.

---

### Post by InGunsWeTrust on 2007-12-24
It is possible that the new monitor cannot handle the the same resolution as your old monitor. If you have access to the old monitor the easy way to fix this is to hook up the old monitor and go to System > Preferences > Screen Resolution and select a lower resolution, then re-hookup the old monitor

If you do not then start in recovery mode and do the following command

```
vi /etc/X11/xorg.conf
```

Use the arrow keys to screen down the the "screen" section.

Mine looks like this:

> Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection

After the keyword modes you see your screen resolutuon. Mine is 1280x800

If yours is set to something similar use the right arrow key to navigate the blinking cursor over the 1 in 1280 and press the delete (not backspace) key on your keyboard until all that is left is the quotes. 

press the i key on your keyboard to insert text and type "800x600"

If your resolution is already "800x600" follow similar steps except enter "640x400"

If your resolutuon is already "640x400" then you probably have a different problem. And you should follow the step below to quit without saving changes and return here for more help.

Once you are all done making changes press the esc key on your keyboard to stop editing. Press Shift + : on your keyboard and you will be dropped to a prompt at the bottom of your screen. type wq at that prompt and press enter.

It will say that the changes have been saved to the file or something of that nature.

reboot your machine and your screen should be back.

if at any time you make any disaterous mistakes and you just want to do it over press esc to stop editing and then press Shift + : on your keyboard. Your cursor should go all the way to the bottom of the screen type !q then press enter to quit without saving changes and reissue the command
```
vi /etc/X11/xorg.conf
```

and start all over with editing.


I hope that solves your problem so you can resume using your machine!

---

### Post by Cholera on 2007-12-24
thanks so much! i'm now happily back on my ubuntu computer. i really appreciate it!

---

### Post by InGunsWeTrust on 2007-12-24
Just out of sheer curiousity, which solutuon worked? Haha

---

### Post by Cholera on 2007-12-24
i just tried tarus', as it was first, and that one worked.

---

### Post by InGunsWeTrust on 2007-12-24
Make sure to rename this title of the original post to [solved] ubuntu won't load with new monitor. So more people don't come accoss trying to solve it :)

---

