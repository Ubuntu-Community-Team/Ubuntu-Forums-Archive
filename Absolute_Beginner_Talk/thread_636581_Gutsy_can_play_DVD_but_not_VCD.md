---
title: "Gutsy can play DVD but not VCD"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by poisonblack on 2007-12-10
Greetings.!!

Installed Gutsy Gibbon just yesterday,my first ever encounter with linux.!! I installed all the necessary plugins like gstreamer ubuntu-restricted-extras,VLC player and Beep music player.Now I am able to play most of the media files except video CDs.:( DVDs [.vob] files are working perfectly though.

Also,I am not able to play any flash content on webpages.I had installed Gnash SWF player in FF and it worked fine there.But I switched over [my browser of choice from my windows days],and it can't play and flash content.

How do I get over these problems.??Any help will be phenomenal.!!:KS

---

### Post by nikoPSK on 2007-12-10
install flash-nonfree

---

### Post by poisonblack on 2007-12-10
Hi nikoPSK.!!

> poisonblack@poisonblack-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 145 not upgraded.
poisonblack@poisonblack-desktop:~$ 


So the flashplugin-nonfree has already been installed.

---

### Post by nikoPSK on 2007-12-10
well, can't help you any more. Sorry.

---

### Post by thelatinist on 2007-12-10
What software are you trying to play your VCD in?  And what codecs do you have installed?

Just so you know, DVDs use MPEG-2 encoding whereas VCDs use MPEG-1.  They are quite different encoding formats, so the ability to play one is not necessarily at all related to the ability to play the other.

---

### Post by atoc on 2007-12-10
> **poisonblack said:**
> Hi nikoPSK.!!



So the flashplugin-nonfree has already been installed.

Uninstall all Flash (free and non free) including any config files, then install using the download from the Macromedia Flash site.
This was addressed in another thread and the solution worked for me.

---

