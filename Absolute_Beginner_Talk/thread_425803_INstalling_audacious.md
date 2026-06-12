---
title: "INstalling audacious???"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by cool_mast on 2007-04-27
I recently installed ubuntu 7.I want to install audacious1.3.2.SO,i downloaded in .tar.gz format.
Now after following basic instructions I am not able to install it.I extracted it,used ./configure command and make and then make install command.
BUT audacious was not installed .I dont know what to do????
pls help

---

### Post by deadgobby on 2007-04-27
[http://ubuntuforums.org/showthread.php?t=202430](http://ubuntuforums.org/showthread.php?t=202430)
[http://ubuntuforums.org/showthread.php?t=308286](http://ubuntuforums.org/showthread.php?t=308286)
[http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html](http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html)

---

### Post by crispy_420 on 2007-04-27
Look [here]("http://audacious-media-player.org/Downloads#4.20").

They mention it is Feisty repos.

Or there is the direct link to the debs for it [here]("http://mail.atheme.org/~soho/").

Just make sure you have dependencies met:

 > Dependencies

    * AutoTools (i.e. automake, autoconf)
    * GTK+ >= 2.8
    * libglade >= 2.3
    * libmcs >= 0.1.0
    * libmowgli >= 0.1.2 (SVN only, at present) 

Optional Dependencies
Feature 	Package(s)
Vorbis playback 	libvorbis >= 1.0
libogg >= 1.0
FLAC playback 	libvorbis >= 1.0

libogg >= 1.0
libFLAC >= 1.1.2
ALSA Audio output 	alsa-lib
esd(1) Audio output 	libesd >= 0.2

---

