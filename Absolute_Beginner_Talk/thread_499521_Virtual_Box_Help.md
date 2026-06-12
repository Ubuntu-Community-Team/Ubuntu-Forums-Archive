---
title: "Virtual Box Help"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by StephanGFX on 2007-07-12
I installed virtual box on my ubuntu linux os (fiesty version), and it works like a charm. But the only problem is, when I make it set to full screen I'm not able to see the start menu (bar) at the bottom of the screen in virtual box. So is there any way I can hide the bottom and top bar in ubuntu, so that I only see the windows screen?

Thanx:KS

---

### Post by StephanGFX on 2007-07-12
bump...

---

### Post by spalaciob on 2007-08-20
> **StephanGFX said:**
> I installed virtual box on my ubuntu linux os (fiesty version), and it works like a charm. But the only problem is, when I make it set to full screen I'm not able to see the start menu (bar) at the bottom of the screen in virtual box. So is there any way I can hide the bottom and top bar in ubuntu, so that I only see the windows screen?

Thanx:KS

The same happened to me and there are two things you can do:

1. When the system is starting and it shows the window with the blue loading bar beneath, you press Ctrl+F (or the shortcut you have configured to switch to full screen). Just before it shows you the "Welcome" screen.

2. If you want to skip this process, you can download the "Guest Additions". Go to "Devices > Install Guest Additions..." in the top menu of the window where you have your VM running. You'll have to reboot your VM but after that, you'll feel more comfortable working. It detects whether the mouse is over the VM or over your real machine so you don't need the escape key anymore and it also helps you managing your host-guest sharing folders (but that's a feature I haven't been able to configure yet. If somebody knows how, please post.)

Ok, I hope this can help you.

---------------------------------------------
Sebastian P.
[http://spalaciob.googlepages.com](http://spalaciob.googlepages.com)
[http://spalaciob.blogspot.com](http://spalaciob.blogspot.com)
[http://antiprisma.wordpress.com](http://antiprisma.wordpress.com)

---

### Post by hellhound_x on 2008-07-15
I found that I could not run guest edditions without being root so to get this taken care of in the terminal I used - 
sudo /media/cdrom/VBoxLinuxAdditions.run

---

