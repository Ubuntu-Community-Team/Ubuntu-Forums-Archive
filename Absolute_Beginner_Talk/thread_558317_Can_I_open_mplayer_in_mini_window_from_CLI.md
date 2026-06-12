---
title: "Can I open mplayer in mini window from CLI?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by say2sky on 2007-09-23
I hope to open mplayer from command line but only have an icon in gnome-panel ie the mplayer window is minimized. 

Anyone know which switch or command can be used.

I remember in Windows batch file start and min can be used to open an app in minimized state. How in Linux or Gnome?

---

### Post by kerry_s on 2007-09-23
open a terminal and type>** man mplayer**

---

### Post by say2sky on 2007-09-23
> **kerry_s said:**
> open a terminal and type>** man mplayer**

I already try man mplayer but I cannot find solution.

---

### Post by kerry_s on 2007-09-23
i don't see that option in the man page. what you can do is use alltray(sudo apt-get install alltray) alltray can dock any program.

alltray mplayer

man alltray

---

### Post by say2sky on 2007-09-23
> **kerry_s said:**
> i don't see that option in the man page. what you can do is use alltray(sudo apt-get install alltray) alltray can dock any program.

alltray mplayer

man alltray

alltray is so cool for mplayer and you are great:popcorn:

The only thing is that alltray firefox seems cannot dock Firefox, any idea?:confused:

---

### Post by kerry_s on 2007-09-24
that's weird, it use to work on firefox. 

[http://alltray.sourceforge.net/faq.html](http://alltray.sourceforge.net/faq.html)
on the bottom.

just in case you didn't find it yet, there should be a menu entry for alltray, you don't have to run it from command line most of the time.

---

### Post by say2sky on 2007-09-24
> **kerry_s said:**
> that's weird, it use to work on firefox. 

[http://alltray.sourceforge.net/faq.html](http://alltray.sourceforge.net/faq.html)
on the bottom.

just in case you didn't find it yet, there should be a menu entry for alltray, you don't have to run it from command line most of the time.

You are right, I can access alltray menu entry then click Firefox window to dock it.

I also try to use
alltry /usr/bin/firefox and
alltry /opt/firefox/run-mozilla.sh /opt/firefox/firefox-bin
but this way failed

In fact what I try to do is when reboot let mplayer and Firefox all run automatically but minimized in dock. :)

---

### Post by andrew.46 on 2007-09-25
Hi,

 Saw your discussion about mplayer:

> **say2sky said:**
> I hope to open mplayer from command line but only have an icon in gnome-panel ie the mplayer window is minimized. Anyone know which switch or command can be used.

 Do you actually mean *gmplayer*? This is the gui of mplayer that will open as a window in the way you describe. Or window + remote control gadget depending which version you  have.

               Andrew

---

### Post by say2sky on 2007-09-25
> **andrew.46 said:**
> Hi,

 Saw your discussion about mplayer:



 Do you actually mean *gmplayer*? This is the gui of mplayer that will open as a window in the way you describe. Or window + remote control gadget depending which version you  have.

               Andrew

its gmplayer

---

