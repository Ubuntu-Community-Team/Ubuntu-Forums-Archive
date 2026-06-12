---
title: "Ubuntu+laptop fear!"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2006-07-02
I experienced a weird situation with my laptop that made me a bit scared about using ubuntu.
I had some shortcuts in the gnome panel for firefox and terminal. I had also installed gdesklets and I was trying to configure the icons for the launch bar widget so I could get rid of any shortcuts in the desktop and the panel. 
To set the icons in the bar I opened the launcher properties from both the existing panel shortcut and the widget so I could copy its properties.
Then, all of the sudden the fans went crazy and my cpu was at 2.0Ghz **constantly!!!**
This went on for some time and only stopped after I manually killed the **gnome-panel** service that was using all of my cpu recources.

Anyone with similar experience?
Should I worry that my laptop may be damaged?
Any ideas/suggestions on what might have caused it and how to avoid it?

---

### Post by mips on 2006-07-02
Running at 2GHz with full Fans is fine. You must start worrying when the fans STOP running.

---

### Post by Sef on 2006-07-02
The fans remove the heat from your laptop.  Heat is a major factor in laptop failure. (And computer failure in general.)

---

### Post by geokok1981 on 2006-07-02
Thanks but my problem was not the fans running but 
the fact that for no apparent reason the cpu (pentium M 2.0 Ghz)
was working at **full throttle for a long time (seemed to be stuck actually)** with all the power being consumed by **gnome-panel ** without any apparent reason (obviously it was a case of a sort of crash...). I described exactly what I was doing at the time in case somebody could explain the 
"crash".

---

### Post by muep on 2006-07-02
It probably was just gdesklets or some other program crashing. You can check which process is taking all your CPU time with the top command, like this:

1) Open Terminal from Applications -> Accessories -> Terminal (will be different for non-English settings)

2) type following:

top

and press enter.

You can also use Gnome System Monitor for the same thing:
1) press alt+f2
2) type:
gnome-system-monitor
3) press enter

---

### Post by geokok1981 on 2006-07-03
I did checked it at the time and it was the gnome-panel using 90-100% of cpu without me doing anything else at the time.
Any reasons for the crash?

---

