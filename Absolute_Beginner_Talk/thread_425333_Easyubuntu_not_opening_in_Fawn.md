---
title: "Easyubuntu not opening in Fawn?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by rikc on 2007-04-27
I installed Fawn on this computer while it was in Beta, and one of the first things I did was get Easyubuntu for MP3 support.  Since upgrading to the final version, I have not been able to open Easyubuntu.  The computer will actively load *something* for a second, but nothing will actually display on my screen aside from the cursor momentarily switching to "Hey I am loading something."

I've tried reinstalling the package, and I'm having the same problem.  Any ideas?  The only thing I need to get is support to unzip compressed formats like .7z, so if Easyubuntu sounds like it will be a problem, maybe there's an easier way to get that?

---

### Post by Seisen on 2007-04-27
Use Synaptic and download 7-zip.

---

### Post by timzak on 2007-04-29
I have the same problem with EasyUbuntu (acts like it's loading when you click the icon  but nothing happens).  If it's not working right, is there a way to fix it?  If not, how do you uninstall it?

---

### Post by jdandrea on 2007-05-06
Same problem here. I would like to uninstall it but can't find it listed in Add/Remove Applications.

---

### Post by jdandrea on 2007-05-06
Ah-ha! This worked.

1. Applications > Add/Remove ... > Preferences > Authentication and remove the Medibuntu GPG key (if installed)

2. Applications > Accessories > Terminal and run "sudo aptitude remove easyubuntu" to uninstall easyubuntu.

- Joe

---

### Post by thrawn86 on 2007-05-06
try copying packagelist-edgy.xml to packagelist-feisty.xml in the /usr/lib/easyubuntu folder.  worked for me, and I had the same problem.  Too bad it didn't really do anything as far as actually giving me mp3 support or ati drivers :(

---

### Post by freebird54 on 2007-05-06
The fawn has its own ways of getting these things done - you shoudn't need it any more.

---

