---
title: "a few questions about ubuntu 6.06"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by smile-its-smiley on 2006-06-04
1) can you still get a live cd and a install cd seperate?
2)how much ram do you need to install 6.06
3)how can i be certain that my dell latitude c600 supports ubuntu i have looked in the wiki it doesn't say nothing about my laptop
4)how will i be able to run windows programmes on ubuntu?
5)how much space is used up on the hard drive after the installation?
6)how can i be certain ubuntu supports my cannon pixma ip1500 printer and canoscan d1250u2? again it doesnt say in the wiki
7)is open office compatible with microsoft office?
8)i have partitioned my hard drive 1 with windows installed and the other side will have ubuntu installed will i beable to access the windows partion? i have used ntfs

---

### Post by taurus on 2006-06-04
1.  Yes, they are seperate.  You now have Live, Desktop, & Alternate.
2.  192MB for GUI.
3.  Your Dell should be fine with Ubuntu.
4.  You can run some Windows programs in Ubuntu (or other Linux distros) with wine (free) or CrossOver Office (~$39).
5.  Depends on what you plan to install.  5GB should be enough but if you plan to install and download a bunch of stuff, then 10GB then.
6.  Your Cannon printer should be good to go and you can always check with your scanner one you have Dapper up and running!
7.  OpenOffice can read and save docs to .doc format because I do that all the time since almost everybody at work is using XP!  ](*,)
8.  You can use GRUB to boot Dapper and your XP and you can access your NTFS partition from Ubuntu with at least read permission.

---

### Post by dabear on 2006-06-04
1) can you still get a live cd and a install cd seperate?
Yup, the desktop-cd is the live cd, and the install cd is called alternate now.

2)how much ram do you need to install 6.06
I would reccomend 256 or more, you may go as low as 128 mb or 64 mb on a pure server install.

3)how can i be certain that my dell latitude c600 supports ubuntu i have looked in the wiki it doesn't say nothing about my laptop
It probably will. You may have some trouble with your wireless card though, but I don't know which model you have.

4)how will i be able to run windows programmes on ubuntu?
You wont. Cedega, crossover office and wine is there, but they won't always work. If you want to use windows programs, use windows.


7)is open office compatible with microsoft office?
Yeah, except some macros and visual basic scripting. Other than that, it works great.

8)i have partitioned my hard drive 1 with windows installed and the other side will have ubuntu installed will i beable to access the windows partion? i have used ntfs
Dualbooting is no problem. You can access your ntfs partition from ubuntu, but read-only.

---

### Post by smile-its-smiley on 2006-06-04
i think i have a problem then i only have 128mb of ram on my laptop:-?

---

### Post by smile-its-smiley on 2006-06-04
my model number for my laptop is PP01L

---

### Post by taurus on 2006-06-04
[QUOTE=smile-its-smiley]i think i have a problem then i only have 128mb of ram on my laptop:-?[/QUOTE]
What kind of problem are you talking about?  With 128MB of RAM, Gnome will be REAL slow so you need at least 256MB of RAM to run Gnome.  Even with 256MB, Gnome is still kind of slow to me so I always go with XFce4.  And if you have 512MB of RAM, then it's a whole new story...  ;)

---

### Post by smile-its-smiley on 2006-06-04
i actually have 256mb ram so this should be allright for installing and running ubuntu

---

### Post by taurus on 2006-06-04
[QUOTE=smile-its-smiley]i actually have 256mb ram so this should be allright for installing and running ubuntu[/QUOTE]
With 256MB of RAM on your laptop, you should be okay, not great but okay, running Gnome.  However, you may want to consider using XFce4 as your window manager since it's a little lighter on the system resource.  Or yet, go for fluxbox...

---

### Post by smile-its-smiley on 2006-06-04
can you explain what XFce4 and fluxbox are please

---

### Post by taurus on 2006-06-04
Those are two of somewhat lightweight window managers!!!  Instead of explain what each one is (don't have time for that), why don't you check out the websites and see some screenshots for yourself then...

XFce4:
[http://www.xfce.org/](http://www.xfce.org/)

Fluxbox"
[http://www.fluxbox.org/](http://www.fluxbox.org/)

---

### Post by IYY on 2006-06-04
256 MB is perfectly fine for Gnome. Runs very fast for me. However, you should give other window managers (Fluxbox, IceWM, XFCE) a chance. No matter how much RAM you have, they will always be faster and some (including me, when it comes to IceWM and Fluxbox) even find them to be more comfortable.

---

