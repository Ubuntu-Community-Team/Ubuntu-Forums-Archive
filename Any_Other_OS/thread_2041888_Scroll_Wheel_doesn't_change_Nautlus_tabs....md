---
title: "Scroll Wheel doesn't change Nautlus tabs..."
date: 2012-08-13
forum: Any Other OS
---

### Post by Shakmatton on 2012-08-13
Hello there. It's my 1st time here, but I'm enjoying a lot the new Ubuntu 12.04 (Ubuntu Remix).

Well,  I used to have Ubuntu 10.10 running softly in my other machine. There, I  used to have the confort of changing minimized windows at the taskbar  by just scrolling them with the mouse wheel up and down.

The same  used to happen also to many other things, like for instance the opened  tabs in Nautilus... very confortable and usable (something that I didn't  find in Windows XP for instance...). It spares me from clicking too  much unecessarily...

Well, the point is, although I can do some  things with the scroll wheel (like changing up or down the volume), but I  can't do it in Mint.

I'd like to know if this this functionality was taken away from the newest versions of linux (ubuntu, mint, etc...).

How can I have this functionality back to my system ? Do I have to install Compiz to have it all working smoothly ?

(Well, actually I'm facing the same problem with Mint Cinnamon, but for now I'm focusing at Ubuntu for now.)

Thanks for any feedbacks in advance. Regardless, I am really enjoying Ubuntu 12.04 [IMG]http://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG]

---

### Post by Wexlatron on 2012-09-06
Me too.

I can't seem to scroll through the tabs with any GTK3 application. (GTK2 apps still work though) Does anyone know what changed or how to changed it back? (I assume it's something the Gnome developers messed with for whatever reason)

---

### Post by Wexlatron on 2012-09-07
OK I just stumbled upon these reports of the same issue:
[http://vanschouwen.info/nerdynotes/?p=498](http://vanschouwen.info/nerdynotes/?p=498)
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/872055](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/872055)

They pointed me to a patch where some *cough*doofus*cough* Gnome developer removed it because it "seems kind of awkward and unintuitive":
[https://bugzilla.gnome.org/show_bug.cgi?id=630226](https://bugzilla.gnome.org/show_bug.cgi?id=630226)

So far the only solution to this is the "undo no scroll" patch:
[https://launchpadlibrarian.net/101685319/undo_no_scroll.patch](https://launchpadlibrarian.net/101685319/undo_no_scroll.patch)

---

### Post by alecz20 on 2012-09-24
I cannot scroll with the mouse wheel in a window either.

Be it Firefox, or Nautilus, the wheel seems to be completely disabled.

I didn't know about the tab scrolling until now, but scrolling inside a windows, come on! Why remove that?

---

