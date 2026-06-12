---
title: "i still cant get drivers to work for 7600gs  help!!!"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by nosfed438 on 2007-08-29
i have tried every thing i can find.  new, old, envy, aoutx and nothing after i load all the stuff it says to restart and when i do i get a x server is down no out put device  please help!!!

---

### Post by benhall on 2007-08-29
Are you running dapper or feisty? I realise that this won't help in itself, but the drivers ran out of the box on my feisty installation. Could you tell me what you tried, and in what order (ie restricted driver manager first, then envy). What do you have installed now? Can you get an xserver if you set the driver in xorg.conf to vesa?

---

### Post by nosfed438 on 2007-08-30
ok here we go. i down loaded ultimate 1.4. i have duel  boot  1.3 and 1.4  at the start of 1.4 it loads all the stuff by itself you just tell it yes yes yes then envy comes up. so i picked my card and yes yes yes then is says to reboot so i did !  now when it came back it went black screen then it said x server has a prob and did not start i am not to good with all the command stuff and i was lost so i dumped the os and reloaded it and tried again!  same thing  :confused:   so i came on here and read all the stuff i could find and i found  the command  "sudo dpkg-reconfigure -phigh xserver-xorg" and bam it was back  so then i tried automatrix and the same thing as before!!  so then i tried some way i found on here in a how to and the same thing !! so i went to synaptic and tried that was same thing  :confused: !!!    i have read every thing i can find and nothing works and now in my boot menu i have like 5 lines of this os to chose from why is that??  my card works fine in 1.3

---

### Post by nosfed438 on 2007-08-30
anyone??

---

### Post by Hobo Joe on 2007-08-30
Paste the output of:
```

glxinfo

```
If you can't paste it, tell us what it says for direct rendering and drivers and driver version.

---

### Post by Marat Galiev on 2007-08-30
don't use ultimate!
install normal 7.04 and install nvidia-glx-new package.works fine for me.

---

### Post by nosfed438 on 2007-08-30
here is what i got 
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

i went in to synaptic and dumped all the nividia stuff to try and get rid of all the boot up stuff

---

### Post by nosfed438 on 2007-08-30
> **Marat Galiev said:**
> don't use ultimate!
install normal 7.04 and install nvidia-glx-new package.works fine for me.


why isint the same just loaded up with software??

---

### Post by nosfed438 on 2007-08-30
i am a star :KS  help

---

### Post by benhall on 2007-08-30
Ok, well to get a simple (no 3d) xserver to start, try to reconfigure x to use a generic driver. This unfortunately involves editing a configuration file manually; this will be easier if you have a preferred console text editor (if so, substitute it where I say vim below and use the appropriate commands). In a console, type

> sudo vi /etc/X11/xorg.conf 

And enter your password. The console screen will fill with text from the configuration file. Find where the nvidia driver is specified using the following keyboard shortcuts (you might want to write this down)

> /Section "Device"

Then move the cursor using the arrow keys to the line which (probably) reads 

> Driver "nvidia"

Change this line (or the line beginning with "Driver" in this section) to read either

> Driver "vesa"
or
> Driver "nv"

To do this press "I", and see that "Insert" appears in the lower left corner. Use the keyboard to type and delete text, and when you are finished press escape to exit Insert mode (this should disappear from the lower left). Then type the following shortcuts to first save, then quit from vim (type enter after each new line below

> :w
:q

If the driver is already set to one of these alternatives, change it to one of the others. Then restart x with

> sudo /etc/init.d/gdm restart

Hopefully this should give you a login screen, and you should have a non-accelerated desktop. Please let me know if this works, then we can try to get 3d working; this desktop should be fine for most things

---

### Post by nosfed438 on 2007-08-30
i am on it right now but no 3d

---

### Post by benhall on 2007-08-31
Sorry, that wasn't clear to me that you had a working Xserver. Could you tell me what packages you have installed with "nvidia" in the name using APT (or synaptic), and what the "Device" line I discussed above reads (nv, nvidia, vesa etc)?

---

