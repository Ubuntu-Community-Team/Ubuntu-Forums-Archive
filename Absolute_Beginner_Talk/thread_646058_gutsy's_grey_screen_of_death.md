---
title: "gutsy's grey screen of death"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by scholzilla on 2007-12-20
All was working well for me with gutsy until today. Now when I start up my Gateway MT-something laptop, the kernel loads then the screen goes blank--no flashing cursor or anything, just blank. I have an ATI graphics card, but my knowledge of such things is pretty rudimentary. I do not have the accelerated graphics card enabled. 

I can get gutsy to run from the install disk (which I've verified btw), but I get an error saying that the gnome settings daemon failed. 

Help?

---

### Post by ajmorris on 2007-12-20
Hi there,
in your fglrx section of /etc/X11/xorg.conf, add the following line:
```
Option      "BusType" "PCI"
```

---

### Post by scholzilla on 2007-12-20
Thanks for the response. I don't have this section in my /etc/X11/xorg.conf file, though. See attached for the whole of that file. It also gives specs of my graphics card. Your further help is GREATLY appreciated.

---

### Post by spai on 2007-12-20
> **scholzilla said:**
> Thanks for the response. I don't have this section in my /etc/X11/xorg.conf file, though. See attached for the whole of that file. It also gives specs of my graphics card. Your further help is GREATLY appreciated.
I think you need to change (shown in orange)
```

Section "Device"
       [COLOR="DarkOrange"] Option     "BusType"    "PCI"[/COLOR]
        Identifier      "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
        Driver          "ati"
        BusID           "PCI:1:5:0"
EndSection
```

fglrx stands for FireGL and Radeon X driver I think.

---

### Post by ajmorris on 2007-12-20
yeah, what i meant was to add it to the xorg.conf file, the place spai is suggesting is correct.

---

### Post by scholzilla on 2007-12-20
Thanks again for following up. Unfortunately, this didn't do the trick. The song remains the same.....Any other suggestions?

---

### Post by ajmorris on 2007-12-21
can you please add this to the top of you xorg.conf file (but below the commented out section):```
Section "Module"
    Load           "fglrx"
    Load           "glx"
EndSection
```

---

### Post by scholzilla on 2007-12-21
Thanks again. I don't want to place a SOLVED post yet, though. I get a normal display 50% of the time with the suggested modifications. Why it doesn't work 100% of the time drives the scientist in me crazy. It's the same computer with the same software, so shouldn't it behave the same way?  Is there a quantum effect that makes this performance stochastic? Is there a time dependence? Any explanation?

---

### Post by eolson on 2007-12-21
I think you might want to put that in Redneckese so's usn's can understand it.  :)

---

### Post by scholzilla on 2007-12-22
Soooo.....the original problem has returned, despite having made the suggested changes to the xorg.conf file. GRUB loads, kernel is alive, then the blank, grey screen. I've made no changes to the system beyond those recommended, so I really don't understand why the changes worked intermittently for a brief period and now don't work at all. I can still run everything fine from CD, but that is no solution. Help?

---

### Post by Moop on 2007-12-22
Does this happen only when booting? I also sometimes get a blank screen on booting up. It seems like the monitor isn't receiving a signal. 

If I just type in my user name and hit enter the display automagically appears and I type in my password and everything works. 

If I misunderstood your problem then just ignore this. :guitar:

---

### Post by scholzilla on 2007-12-22
Believe it or not, I tried this very hack, but alas, nothing but grey. Yes, this does happen only on boot up as far as I can tell.

Any other contestants? I'd really like to be able to see things on my screen.

---

### Post by scholzilla on 2007-12-22
After searching LaunchPad for similar bugs, I found the following fix:

"you can fix this problem by changing the values in /etc/usplash.conf to :

xres=1024
yres=768

and after this, run sudo update-initramfs -u"

This seems to have worked for me. Thanks to all who helped.

---

