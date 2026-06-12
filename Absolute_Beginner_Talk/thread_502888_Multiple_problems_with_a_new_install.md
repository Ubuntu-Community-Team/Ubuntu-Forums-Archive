---
title: "Multiple problems with a new install"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by msnealer on 2007-07-17
I've installed Ubuntu 7.04 (Not Xubuntu. Thats on my Laptop) on my desktop and I'm having a set of nagging problems, most of which seem to be connected with the desktop.

Firstly If I open a movie to watch when I have another screen open, like firefox, or utorrent, I get purple lines all over the screen. If I swap to another virtual desktop, they go away.


Next. Totem media player when first installed, asked to download a load of codecs and after that, played all my movies etc with no problems. Now it just keeps on saying that it doesn't know how to play the files and suggests looking elsewhere for codecs. VLC plays them all without a problem.  Movie player and Kaffine have the same problem as Totem.

Next. Totem seems to bring down the whole system if it tries to play a MP3 file. It opens the file, plays for a minute and then loops. The whole screen then freezes as does the keyboard, mouse etc. I can't get the system to do anything and have to reboot. Before you ask, I have tired killing the desktop and it doesn't work either. Rhythembox plays the MP3's with no problem


Next. Wengophone. Don't know why as I get no messages or errors. When I open Wengophone, it opens and then shuts down after about 30 seconds. I've not had chance to change any settings or configure it other than request a userid. Please don't say use Ekiga. Don't like it

---

### Post by hamburglar6 on 2007-07-17
Go to Applications --> Add/Remove then in the top right change the setting to "all available applications".  In the "Other" category, look for 'macromedia flash player', and 'ubuntu restricted extras'.  In the sound & multimedia category get all of the gstreamer plugins, and the xine plugins and see if this fixes your problems.

---

### Post by msnealer on 2007-07-17
Have tried this one with the media files and at first it did work. All files were being played. Now however except for VLC they all say that I don't have the codecs and won't play them. 

I didn't uninstall them or anything. I have also tried re-installing the Gstreamer codecs and it had no effect what so ever

---

### Post by hamburglar6 on 2007-07-17
Did you install the xine and 'Ubuntu Restricted Extras'  ones as well? You might also try enabling the medibuntu repository: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

