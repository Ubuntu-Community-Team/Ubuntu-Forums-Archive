---
title: "Xubuntu - DVD Playback"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by CrimsonRider on 2007-05-06
Hi, I am quite new here, not so new to linux, but all in all new to Xubuntu. I've got a low end machine that I wan to use to play DVD's.

Problem is, I can't get to work. I've searched around the internet and fora, but all solutions assume quite a bit of basic knowledge already. I have a clean Xubuntu install, and I want a lightweight DVD player program. Doesn't really matter wich one. Can anyone tell me how to do that?

Thank you.

---

### Post by jiminycricket on 2007-05-06
You need to install DeCSS (libdvdcss) to be able to decrypt the DVD first [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability)

Then, you could use  GUI program like mplayer/gmplayer/[smplayer]("http://www.getdeb.net/app.php?name=SMPlayer"), totem-xine (not gstreamer, it doesn't do menus as of yet) etc., to easily play it.  There are some in the Synaptic Package Manager, or you could install using [aptitude]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=aptitude&sourceid=mozilla-search&start=0&start=0") for a command line method.  You could also install apps by typing "sudo aptitude install application-name-goes-here".

---

