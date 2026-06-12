---
title: "How do I save Quicktime movie trailers?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-19
I've followed this great tutorial in order to enable multimedia.
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
Previously I've been using Automatix to fix things.

Regarding the Quicktime movie trailers Firefox always used Mplayer to play the trailers and I could save them to my hard drive.  But when following that tutorial not relying on Automatix you instead make Firefox startup Totem Movie player instead which is nice.  But can it safe trailers to the hard drive like Mplayer could?

If so how do I accomplish that, are they like saved in a cache on my computer?
I would prefer not to go back the Automatix + Mplayer method since that created an enormous amount of media players on my menu.

---

### Post by asmoore82 on 2007-07-19
you can view the source of a page and "wget" the .mov file from a terminal;
then try to play it will with mplayer; it will fail and tell you the name of the real
.mov you need to get with wget... after a couple tries you will be able to see through their
naming scheme.

P.S. you can right-click on the MenuBar and pick "edit menus" and hide programs you don't want to see

---

### Post by Daveth on 2007-07-19
if you are accessing movie trailers then they are "saved" in the browser cache if you just access them, unless you  "save target as" when the Quicktime movie is saved in a file position of your choice. Both Mplayer and Totem will play/ open files if directed to them, but do not save them themselves. You can associate a file type to a program, so if you really like Totem or VLC or whatever you can select an example file and in properties select "open with". You can also tell browsers what handlers they should use for files- I use Opera rather than Firefox, but they all seem to operate in much the same basic manner.
Is this what you mean??

---

### Post by jingo811 on 2007-07-19
Mmm....I guess I should install Automatix and let it install Mplayer and then use the Firefox extension: MediaPlayerConnectivity like I used to do things.  It's ugly compared to the official Enable Multimedia method but things just work right away.

Tnx anyway.

---

