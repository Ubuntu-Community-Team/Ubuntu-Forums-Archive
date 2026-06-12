---
title: "Need to restore Ubuntu to an earlier date."
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Link360 on 2006-11-05
I messed up Ubuntu trying to download Compiz and XGL, which has 
3D effects like in the new Window Vista. Does anyone know how to restore Ubuntu to an earlier date. For example before I downloaded all that crap.Wthout being able to login.Thanks for your help.

---

### Post by taurus on 2006-11-05
You probably only need to reconfigure your X again so try to boot your Ubuntu into recovery mode from GRUB and at the prompt, run

```
dpkg-reconfigure xserver-xorg
(And if you are not sure about something, just use the default value...)
```
Reboot and see what happens!

---

### Post by Link360 on 2006-11-05
If you dont mind will you walk me through this. The first thing that comes up is. 
Attempt to autodetect video hardware. I clicked yes.Then i clicked ati as my video card and now im stumped.

---

### Post by taurus on 2006-11-05
> **Link360 said:**
> If you dont mind will you walk me through this. The first thing that comes up is. 
Attempt to autodetect video hardware. I clicked yes.Then i clicked ati as my video card and now im stumped.
What is the next screen then or does it hang at this point?

---

### Post by Link360 on 2006-11-05
The next screen it asks for an identifier for my video card
 I can click ok without typing anything, but i dont know if i should do that.

---

### Post by taurus on 2006-11-05
You can always run it again if it doesn't work after you've configured it.  I think you can type in the name of your card at that screen.

---

### Post by Link360 on 2006-11-05
I have gotten to a point where it says 
"The monitor synchronization ranges should be autodetected by the X server in most cases, but sometimes it needs hinting. This option is for advanced users, and shoud be left at its default. 
Write monitor sync ranges to configuration file?Yes or NO?"

Either way it asks me to slect my desired default color depth in bits.(15,16,24). I clicked 24 because it is recommended. Then at
the bottom this pops:
"xserver-xorg postinst warnin: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20061104235405"
Now it wants me to type something. What?

---

### Post by taurus on 2006-11-05
It just asks you if you want to overwrite your old /etc/X11/xorg.conf with the current one, the one you just have configured.  Answer yes in this case then.

---

### Post by Link360 on 2006-11-05
There is no yes or no option.

---

### Post by taurus on 2006-11-05
Just type it in!!!

---

### Post by Link360 on 2006-11-05
now my screen looks like this: 
y
y
y
y
y
y
y
y
y
y
y
y
y
y
y
y

---

### Post by taurus on 2006-11-05
That's weird!!!  Hold down <Ctrl> while press c to get out of that.  Then, see if your /etc/X11/xorg.org is the latest version or not by looking at the date that it has created.  If it's still an old version, run that command again...

```
ls -la /etc/X11/xorg.conf
```
Otherwise, see if you can start X again with

```
startx
```

---

### Post by Link360 on 2006-11-05
wow, im back at the Ubuntu desktop. Do I now have the 3D stuff I tried to install?

---

### Post by taurus on 2006-11-05
> **Link360 said:**
> wow, im back at the Ubuntu desktop. Do I now have the 3D stuff I tried to install?
So, X is working again!  I don't think you have any 3D stuff running right now.  You now need to install a driver for your ATI card and since I only use nVidia on my machines, you probably need to look at this link to install a driver for your graphic card.  Again, if you screw up your X, you now know exactly how to fix it...

[http://www.ubuntuforums.org/showthread.php?t=235145&page=10](http://www.ubuntuforums.org/showthread.php?t=235145&page=10)

---

### Post by Link360 on 2006-11-05
Thanks!!!:D :D

---

### Post by taurus on 2006-11-05
> **Link360 said:**
> Thanks!!!:D :D
You're welcome and good luck.

---

### Post by Link360 on 2006-11-05
Wait, I tried to shutdown and a pop-up comes up saying i need to start my dbus system. What is that and how do i do it.

---

### Post by Link360 on 2006-11-05
Please come back.

---

### Post by taurus on 2006-11-05
Sorry.  Thought everything is working fine with you there.  How did you reboot it?

```
shutdown -r now  <-- to reboot
shutdown -h now  <-- to shutdown
```

---

### Post by Link360 on 2006-11-05
I didnt reboot it yet. it wont let me.

---

### Post by taurus on 2006-11-05
Are you in X right now or are you still in the recovery mode?

---

### Post by Link360 on 2006-11-05
I think im in the Ubuntu desktop.

---

### Post by taurus on 2006-11-05
Did you reboot into DGM login screen or did you run "startx" from a terminal in recovery mode?

---

### Post by Link360 on 2006-11-05
starx from a terminal in recovery mode.

---

### Post by taurus on 2006-11-05
> **Link360 said:**
> starx from a terminal in recovery mode.
Then try to log out from it instead of rebooting.  And when you get back from the terminal which you should be root now, reboot it or shutdown with

```

shutdown -r now
-or-
shutdown -h now

```

---

### Post by Link360 on 2006-11-05
I logged out. It came up to the black screen and the prompt to type. I typed shutdown -r now. My computer rebooted. Then I clicked on Ubuntu to boot and the same thing that came up 5 hours ago came up again. So I typed in startx and got back to here.:-?

---

### Post by taurus on 2006-11-05
What does your /etc/X11/xorg.conf look like then?

```
more /etc/X11/xorg.conf
```
Maybe you need to start the gdm again...

```
sudo /etc/init.d/gdm start
(go that before you run the startx command)
```

---

