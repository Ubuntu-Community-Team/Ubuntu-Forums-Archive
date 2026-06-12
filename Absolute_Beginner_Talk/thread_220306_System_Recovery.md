---
title: "System Recovery"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by pandemic on 2006-07-21
I've had to make alot of changes to my ubuntu system the past couple of weeks in order to get my wireless networking, MySQL, Apache, etc.... working. The last thing I was working on was trying to get my nvidia drivers and aiglx installed, but it appears that I have seriously messed things up. The os still works but when logging in it can take 3-5 minutes for the desktop to show up and graphical apps like blender and 3d screen savers won't work.

Ok now that you know the background I was wondering if there was a way to get ubuntu to revert back to the default packages (by packages I mean the packages that one can fetch with apt-get). I would really like it if Ubuntu could just show me a list of things that has been added so I could remove them if I choose to. I'm hoping to get the system back to normal without having to re-install the os.

---

### Post by slimdog360 on 2006-07-21
not that I have used it, maybe someone else knows something better, but in automatix I happen to remember a backup util in there.

---

### Post by tuxinvader on 2006-07-21
The AIGLX X-server conflicts with the standard xserver so try re-installing the standard X server...

sudo apt-get install xserver-xorg

Or if you want to ensure you have all the standard ubuntu desktop packages:

sudo apt-get install ubuntu-desktop

You will also want to remove the aiglx repositories you added for aiglx support from you /etc/apt/source.list

HTH

---

