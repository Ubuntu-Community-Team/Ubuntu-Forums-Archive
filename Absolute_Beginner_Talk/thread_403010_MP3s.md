---
title: "MP3s"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Biscuitpie on 2007-04-06
I installed Amarok, and tried to play an MP3 file and it said it had to download something. I installed it once, and restarted Amarok. Still didn't work, same message. This time it asked me for my password, and still didn't work. Did it again and wasn't asked for my password, but also didn't work.

Then I went here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Neither of those options work, the repositories menu doesn't have an "add" button that I can see. Maybe it just needs to be pointed out. =/

---

### Post by tgm4883 on 2007-04-06
What version are you using?  Dapper, Edgy, or Feisty

---

### Post by Obor on 2007-04-06
its in synaptics menu and also in preferences or admin. can't remember which as I'm in KDE now.  See the link below.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by szymon_g on 2007-04-06
hm...
try to type in terminal (konsole or gnome-terminal)

sudo gedit /etc/apt/sources.list

if you use kubuntu, write kedit

go to this page

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

and select good options (version of ubuntu/kubuntu, country etc)
you will have a sources list

copy and insert it into your /etc/apt/sources.list file
thas save it.
type sudo apt-get update
or 
sudo aptitude update

and now 

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

it should works :->

---

### Post by Biscuitpie on 2007-04-06
> **Obor said:**
> its in synaptics menu and also in preferences or admin. can't remember which as I'm in KDE now.  See the link below.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

That link said to go to Software Properties... I don't have that.

How do I check my version? I got it from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Biscuitpie on 2007-04-06
Thanks, szymon_g! That worked!

---

### Post by szymon_g on 2007-04-06
your welcome :->

---

