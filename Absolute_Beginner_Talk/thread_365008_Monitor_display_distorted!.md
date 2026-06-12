---
title: "Monitor display distorted!"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Flufflebuns on 2007-02-19
You'll all have to forgive me for I am a COMPLETE noob to Ubuntu.  I just today installed Ubuntu 6.10 on an old Dell Laptop.  I used the CD installation and during the Live CD process I had a few major problems.  First error said exactly:

"There was an error starting the GNOME Setting Daemon. Some thing, such as themes, sounds, or background settings may not work correctly. The setting Daemon restarted too many times. The last error message was: Child process did not give an error massage, unknown failure occured. GNOME will still try to restart the Settings Daemon next tiime you log in"

The major problem is that my monitor is extremely distorted.  I can see all the icons sort of, but it's like someone took a knife and chopped it into pieces and pasted them in random vertical places.  My cursor will appear in two places, and I can only read windows by dragging them to the far left of the screen which appears perfect, and anything past that to the right is horribly distorted. 

So I thought maybe I could solve this by installing all the files, and so i fully installed Ubuntu on a fresh partition.  I now don't get that GNOME error, but the screen is just as distorted.  So then I updated all the software, and rebooted, and still doesn't work.  

I figure this has something big to do with my graphics card, but i have no idea where to begin updating it or doing a fresh install.  It has an 

ATI Mobility M4
16.0M
SDR SGRAM 1:1 / SDRAM

Maybe it's some other problem, but I have no idea how to fix this.  I also tried the Live CD of 6.06 and the same problem occurred.  Would switching to Xubuntu solve this sort of problem? 

Anyway I'd really appreciate some help, but please be patient with me I have NO idea what anything means, I've never used Ubuntu before, though I'm good at working with windows.

---

### Post by renzokuken on 2007-02-19
it may well be a grafix driver related problem.

when it has finished booting, to whatever messed up scramble you get, press

Ctrl+Alt+F1

this will take you to a TTY terminal screen (no grafix)

login and type

```
sudo nano /etc/X11/xorg.conf
```

scroll down to the **Section  "Device"** part and note the **Driver** line.....

it will probably look like

```

Section "Device"
      Identifier   "some text
      Driver       "ati"       (this is the line i'm interested in, could be a lot of other things than "ati")
End Section

```

if its not already, then change it to "vesa" so it looks like

```

Section "Device"
      Identifier   "some text
      Driver       "vesa"       
End Section

```

press Ctrl+X, Y and enter to save and exit. then reboot and see if anything changes. if it is already set to vesa then you could also try "ati".

---

### Post by Flufflebuns on 2007-02-19
Thanks a ton.  That helped.  I made default VESA and left everything I didn't know default!

---

### Post by renzokuken on 2007-02-20
no trubs, glad it worked. vesa is a very generic standard driver, which although doesnt give great performance, is very reliable and works with almost all cards/chipsets.

if you wanted to have better performance/acceleration, you should have a look into seeing if the fglrx driver (official ATI linux driver) works for your card

---

