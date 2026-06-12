---
title: "Ubuntu Starting in Console Mode - Pls Help!"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by fatboysam on 2008-02-18
Hi,

Unsure what's happened but I tried installing IE4Linux and my current default session at login is KDE 4.

Unfortunately now, ,y Ubuntu 7.10 now always starts in console mode.

How can I start KDE 4 from console mode as when I try sudo /etc/init.d/gdm restart, it comes back telling me that this is not my default mode.

If I enter startx, I get a:

XIO: fatal IO error 104 (Connection reset by peer) on X server ":0:0"


I have no idea - I just want to get KDE 4 started up again.

Can someone pls help.

Thanks.

fs.

---

### Post by zerhacke on 2008-02-18
Since you've got KDE4 installed your default login manager is now KDM and not GDM.

---

### Post by fatboysam on 2008-02-18
no worries - so how to I start up kde from the console then as when I do a sudo /etc/init.d/kdm-kde4 start, nothing happens?

Can I via the console make gdm my default display manager?

---

### Post by fatboysam on 2008-02-18
bump - really need some help on this. Ubuntu is always starting in console mode.

is it possible to reset the default display default manager from within the console/terminal mode?

---

### Post by fatboysam on 2008-02-18
[SOLVED] - got rid of KDE4 and re-installed GDM using the following command:

sudo apt-get install --reinstall gdm && sudo apt-get -f && sudo dpkg-reconfigure kdm && sudo dpkg-reconfigure gdm

---

