---
title: "Arch64+Gnome 2.22+Java=no trayicon?"
date: 2008-05-04
forum: Arch and derivatives
---

### Post by odiseo77 on 2008-05-04
Hi people. I just migrated my 32 bit Arch install to 64 bit (with the 2008.04-rc Core cd). I installed Gnome (2.22, the default), and after that, I installed Mercury Messenger (a java MSN client), but no matter what I do I can't get a trayicon for meercury on Gnome's notification area (yes, the notification area is active). I went to mercury installation directory, removed libtray.so and renamed libtray-x64-untested.so to libtray.so, but it didn't work at all when I restarted mercury. Other apps trays are fine (amarok, fusion-icon, emesene, etc), but not mercury. So I'm thinking that maybe there's a bug on 64 bits with the new notification area on gnome 2.22 and java apps that use the tray lib? (Either that, or the new notification area doesn't like java apps :().

Can anyone confirm this? Or does anyone has a clue about what might be wrong? (Mercury's tray lib is working like a charm on Ubuntu Hardy 64 bit here).

Thanks in advance.

---

### Post by jamesstansell on 2008-05-04
I noticed in Sun's bug parade not long ago some bugs about the tray icon.  I think one was keyed by window manager name.  So, for example (just an example because I don't remember exactly) metacity and compiz worked but beryl didn't, simply because the capability was keyed by WM name instead of checking that the tray area was actually present.

---

### Post by odiseo77 on 2008-05-04
Well, I started a fluxbox session, executed mercury and the trayicon showed up fine in the dock, so it definitely is a problem between java and the notification area of Gnome 2.22 on Arch 64 bits. I think I'm going to open a new topic on the Arch forum to see if it's a known problem, and if it's not, then fill a bug report.

---

