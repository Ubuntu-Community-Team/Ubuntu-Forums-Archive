---
title: "How to install new icons on Xubuntu (XFCE)?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-01-15
Hi,

I installed Xubuntu and I'd like to change the icon theme. I've downloaded several tarballs from [www.xfce-look.org](www.xfce-look.org) but cannot achieve to install them. On Gnome I just had to double click on the tarball to install the new icon pack but this doesn't work in Xubuntu. 

Any ideas?

thanks

---

### Post by Pobega on 2007-01-15
Extract it to ~/.themes

---

### Post by floke on 2007-01-15
But watch out! There's a bug in XFCE (actually its not in XFCE but it affects it) that will crash your whole thing if you select an icon theme that it doesn't like. (see [https://launchpad.net/ubuntu/+source/xfce4/+bug/77445](https://launchpad.net/ubuntu/+source/xfce4/+bug/77445)) amongst others 

If your screen goes blank, then panic ye not. Simply use CTRL (or it might be ALT - can't remember off top of my tired head) and F2 - then enter 'xfce4-panel' - there's a load of other xfce4-XXXX things you'll need to use to get it back up and running - so I would look around for recovery intructions before messing with the icons ;) 

Good luck

---

### Post by kilou on 2007-01-15
@Pobega
Thanks for your help. I tried that but the icon pack is still not listed in the user interface dialog for icons :( What I did is to extract the icon pack (with full path) into the /.themes folder and then logout and login. Any other suggestion?

@Steve.K
Thanks for the info. It seems XFCE doesn't like customization...it's not its first purpose anyway. I must say that I switched to XFCE to have a smooth Beryl experience because KDE and Gnome were a bit laggy. But I'd like to add some eye candy to XFCE but it seems quite limited (no translucent panel, icon troubles....).

---

### Post by pissedoffdude on 2007-01-15
> **Steve.K said:**
> But watch out! There's a bug in XFCE (actually its not in XFCE but it affects it) that will crash your whole thing if you select an icon theme that it doesn't like. (see [https://launchpad.net/ubuntu/+source/xfce4/+bug/77445](https://launchpad.net/ubuntu/+source/xfce4/+bug/77445)) amongst others 

If your screen goes blank, then panic ye not. Simply use CTRL (or it might be ALT - can't remember off top of my tired head) and F2 - then enter 'xfce4-panel' - there's a load of other xfce4-XXXX things you'll need to use to get it back up and running - so I would look around for recovery intructions before messing with the icons ;) 

Good luck

That bug also affects fedora's xfce.  I was playing around with the thems the other day and it just crashed.

---

### Post by floke on 2007-01-15
On the plus side, you do learn not to panic when everything disappears from your screen!
This came in very useful today when Kicker crashed (again) in KDE - why does autohide do such dumb things?

---

### Post by kilou on 2007-01-15
Finally got the icon working. I had to copy the pack in /usr/share/icons and it's then available in the User Interface. Nuvola icons work great.

---

### Post by videodrome on 2007-01-18
Good luck. Icon themes never actually work right under xfce. Just try changing the icons in the settings manager for example. It's a mess and it's structure is a mess. I hate it. And there's no forum to talk about it in either. The xfce forum is on life support.

---

