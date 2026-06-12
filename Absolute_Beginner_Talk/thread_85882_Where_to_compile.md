---
title: "Where to compile?"
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by Gijith on 2005-11-03
Hi everybody.

I'm very new. I've just had my first experience with compiling something from source. I wanted to install the kmplayer frontend to go along with my kde. I followed the instructions I found here: [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html) . And through those instructions, I configured, and created the make file within my home folder. And so now there is a large  directory of files in my home folder, including the file that runs the program... Now, the program runs (I'm still can't play any video, but that's another thread). But, I'm wondering if I made a mistake by installing it at this location. Could it lead to any problems (could related permission issues be causing the 'vidix driver' error whenever I try video)? Can I successfully move it the whole directory? 

If it is a problem, where should I install next time?

Any help would be hugely appreciated. Thanks a bunch.

-Gijith

---

### Post by Kyral on 2005-11-03
Most of the time it won't matter where you compile, the "make install" (sudo the command mind you) should move everything to where it belongs in the filesystem proper (like /usr/bin and whatnot).

Still, most people prefer to have a directory where they compile, just so its easy to nuke it when they are done.

But I'm surprised that KMPlayer isn't in the repos...

---

### Post by Gijith on 2005-11-03
Thanks for the input.

I was surprised by that too. I'm sure it will be eventually. Considering the problems I'm having with it, I may uninstall and wait for it to show in synaptic.

---

