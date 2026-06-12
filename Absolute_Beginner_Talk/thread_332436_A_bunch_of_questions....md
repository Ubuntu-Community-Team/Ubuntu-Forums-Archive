---
title: "A bunch of questions..."
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Icemanyurt on 2007-01-06
My first set of questions involving Wine.

Is there a list somewhere of programs that work well with Wine?
If the install program has to install to 'C:\program files\file name,' where do the files end up? (Sounds simple I know, but I can't them anywhere) 
Is there an 'Idiots Guide to Wine: The mostly commonly used stuff in one compact form for a person without a CompSci Degree'?

My next set of questions are centered around the Ipod video.
Currently I am using Amorak to send music to my Ipod, is there a simple way to send video and audio books?  I have seen some guides, but they scare me.
Does itunes work while under Wine or is there a better emulator out there?
I have seen songbird, does it have the same functionality as itunes?

Some random questions
Are there any distros of Linux built for the Ipaq or LifeDrive?
What is the difference between KDE and Gnome?

Currently I am trying to convince myself to totally get off of WinXP, but it makes me very nervous.  Currently I am running a laptop (old 850mghz 256mb of ram Dell Latitude C600) which works really well, and an old Athlon 800mghz with 300something mb of ram which also runs quite nice.  My last system is my main system, which still has XP on it.

Any help or advice would be great.

---

### Post by meng on 2007-01-06
The files end up in:
~/.wine/drive_c/Program\ Files
(~ is shorthand for your home folder, btw, e.g. /home/yurt)

KDE and GNOME are different desktop environments. (Look in wikipedia for "desktop environments", it will probably explain much better than I can.)

Don't aim to leave Windows XP immediately if you are not sure. Take your time, you can dual boot until you've made a decision.

---

### Post by aysiu on 2007-01-06
> **Icemanyurt said:**
> 
Is there a list somewhere of programs that work well with Wine? [http://appdb.winehq.org/](http://appdb.winehq.org/)
> If the install program has to install to 'C:\program files\file name,' where do the files end up? (Sounds simple I know, but I can't them anywhere) /home/icemanyurt/.wine/drive_c/Program Files  > Is there an 'Idiots Guide to Wine: The mostly commonly used stuff in one compact form for a person without a CompSci Degree'? [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by Portable_Jim on 2007-01-06
> **Icemanyurt said:**
> 
Is there a list somewhere of programs that work well with Wine?

Wine Application database - the official list
> This is the Wine Application Database (AppDB). From here you get info on application compatibility with Wine.[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by griffinbeans on 2007-01-06
from a terminal you can type 'winefile' and pull up a windows explorer type file browser in which you can find your installed apps under wine>drive_c>program_files...
I found that useful when I was learning my way around.

itunes does not work well under wine, I haven't tried it on any other emulators though.

with wine, I have found it useful to test different apps just to see if they work, I have found several that work like a charm that are not on the official list.

---

### Post by Icemanyurt on 2007-01-06
Cool, thanks y'all...that is really useful stuff

---

