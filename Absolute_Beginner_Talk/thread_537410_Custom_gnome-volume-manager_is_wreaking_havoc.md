---
title: "Custom gnome-volume-manager is wreaking havoc"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2007-08-28
I wanted windows CDs to autorun when inserted into my stock UbuntuStudio install.

After some research, I found this article on how to do this:
[https://wiki.ubuntu.com/autorun]("https://wiki.ubuntu.com/autorun")

I followed the instructions to the T and compiled my own gnome-volume-manager with patch. However, not only did the autorun functionallity not work at all, but there were a ton of other things that would not work.
For example, inserting a DVD would not automount and would not open totem anymore - inserting a music cd would not automount nor start playing on its own.. etc etc etc.

Frustrated, I uninstalled it (sudo apt-get --purge remove gnome-volume-manager) which also uninstalled some dependancies like ubuntu-desktop.

So then, after the full uninstall, I reinstalled via synaptic (sudo apt-get install gnome-volume-manager ubuntu-desktop

Now everything seemed like it was back to normal, but CDs and DVDs won't automount, and now I'm also having problems with flashplugin-nonfree..  Any online flash-based music or video player (myspace, youtube, etc) will only play the first 10 seconds or so of audio or video and just abruptly stops - almost as if it caught up to the buffered stream - but thats it, it just stops playing. This problem only appeared after this whole gnome-volume-manager mess - everything worked great before.

Does anyone know of a way to get everything working again??

thanks,
Jon

---

