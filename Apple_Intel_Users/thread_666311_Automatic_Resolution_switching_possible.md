---
title: "Automatic Resolution switching possible?"
date: 2008-01-13
forum: Apple Intel Users
---

### Post by jslmg on 2008-01-13
Mac users will be familiar with this: You've got a monitor and a t.v., or maybe just two monitors, or even an overhead projector. Each has a different resolution and refresh rate. When you need to use another monitor, you simply switch out the VGA cables on the back of your mac. Mac OS X automatically creates a new video profile for each monitor the first time, then loads that profile automatically thereafter. The switch is instaneous.

I tried this on Ubuntu, and no go. Is there a program or config that will allow Ubuntu to automatically detect a monitor with all its necessary specs, then create a profile for it?

I need it so I can switch between the computer monitor that Ubuntu is now set for, and my T.V. set, which is the old-fashioned, CRT 21-inch kind. Mac handles it, no questions asked, but will Ubuntu?

If not, well, it's still gonna be Mac for viewing DVDs or watching Internet T.V.

---

### Post by cyberdork33 on 2008-01-13
while I think this can be done by adding various screen sections in your xorg.conf file, I really can't help much since I have no experience.

But, I wanted to note that Xorg (the graphic system under Gnome in Ubuntu) is currently transitioning to a completely different method of setting properties for various monitors. The next release on Ubuntu will have completely upgraded to this new version which allows for monitor hotplugging. This is partially working in Gutsy right now, but you have to restart the xorg server to get it to detect all the connected monitors, etc...

Sorry that I cannot be of more help directly to your problem, but I wanted to make sure that you knew that in a couple of months, you may not have that big of an issue here anymore.

---

### Post by jslmg on 2008-01-13
> **cyberdork33 said:**
> while I think this can be done by adding various screen sections in your xorg.conf file, I really can't help much since I have no experience.

But, I wanted to note that Xorg (the graphic system under Gnome in Ubuntu) is currently transitioning to a completely different method of setting properties for various monitors. The next release on Ubuntu will have completely upgraded to this new version which allows for monitor hotplugging. This is partially working in Gutsy right now, but you have to restart the xorg server to get it to detect all the connected monitors, etc...

Sorry that I cannot be of more help directly to your problem, but I wanted to make sure that you knew that in a couple of months, you may not have that big of an issue here anymore.

That would be great news indeed! It's one of the things I like about Linux... the constant, rapid improvement. An awareness of what's going on in other systems, particularly Mac, and a desire  to match it.

I'll wait for hardy heron to see what develops.

---

### Post by cyberdork33 on 2008-01-13
> **jslmg said:**
> That would be great news indeed! It's one of the things I like about Linux... the constant, rapid improvement. An awareness of what's going on in other systems, particularly Mac, and a desire  to match it.

This would actually even be different than what OSX does if it generates a "profile". This would literally just be the server changing itself on the fly to realtime events.

---

