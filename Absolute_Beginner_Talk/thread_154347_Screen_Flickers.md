---
title: "Screen Flickers"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-04-02
I have a quick question, I installed Ubuntu on to a Dell Desktop Computer (it's an old Dell running on a Intel Celeron processor(don't really know how fast), 10 gigs.  When the log in screen comes up and I log on, the screens starts to flicker.  Do you think it might the configuration or maybe a hardwar:( e problem?

---

### Post by halitech on 2006-04-02
could be the video card or monitor dying although if you weren't having any troubles under windows, probably a sreen refresh setting. You could try System - Preferences - Screen Resolution and change the refresh rate there or check here for post#14

[http://http://ubuntuforums.org/showthread.php?t=153006&page=2&highlight=xorg]("http://http://ubuntuforums.org/showthread.php?t=153006&page=2&highlight=xorg")

---

### Post by IYY on 2006-04-03
Look (as root) at your /etc/X11/xorg.conf file. Look at the Monitor section, the HorizSync and VertRefresh options. Here's mins as an example:

> Section "Monitor"
        Identifier      "DELL M781mm"
        Option          "DPMS"
        Option "HorizSync" "30-85"
        Option "VertRefresh" "50-160"
EndSectio

These values differ from one monitor to the next, and can be found either in the monitor's manual, or somewhere in the monitor settings (clicking on the physical buttons on the monitor).

---

### Post by darkwarrior0404 on 2006-04-03
Not really sure on all the technical stuff such as post above this one, not that advanced yet lol, but check your monitor settings-ex: refresh rate, if you follow all of there directions and it still continues, best guess for me is to try a different monitor, and if it continues to do it, possibly video card problem, Dell's at a school I attended for computers, most of them that flickered after log on was due to hardware failure, good luck and wish you the best of luck, someone can probably give you alot better idea of what to do 8)  but I'll help if I can

---

### Post by Jason_25 on 2006-04-03
I would concur with IYY , and say that it is most probably a refresh rate problem.  Editing the xorg file as he describes will get you going.

---

### Post by NeoGreen on 2006-04-03
Okay, I'll give it try to see what happens:)

---

