---
title: "Questions from a Neophyte"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by myke on 2005-11-20
Howdy.  I have a barely 6 month old HP Compaq Presario M2000 running XP.  I've been really wanting to try out Linux and have been doing research for a couple of weeks and have decided to try either Unbuntu or Kubuntu (leaning toward K).   I'm running the Kubuntu live cd now and it seems a little easier to customize than the gnome environment but that's just an initial impression.  Here's a couple of quick questions that I was unsure of still after looking through the forums.

1)  If I initially partition the harddrive and later decide to ditch XP all together, how would I remove XP and reclaim the space for use with linux?

2)  I really liked some of the customized screenshots posted on the forum for both the G & K environments.   I can't figure out how to do this .. mainly with icons.  How do I find and install some of the various icons?

3)  If I install a program and want to put it on the desktop but it isn't in the applications menu, where do I find it on the drive?  I understand that linux installs files based on similarity rather than grouping whole programs together.  I simply am not sure what file I would need to create a launcher for that would start the program itself.  

4)  Is it a real pain in the ass to install the other desktop platform so you can use both the G & K alternately?   

Thanks for any help you might give.  I'm wanting to give Linux a big try and am a power user but am definitely not a programmer so I'm a little wary of command lines.  I hope to therefore make the transition as smooth as possible with as little use of command lines as necessary.

---

### Post by Kyral on 2005-11-20
1) You'd just use something like GParted/QtParted to delete the NTFS partition and make a Linux partition (ext2/3, ReiserFS) in its place and edit fstab to mount it.

2) Icon themes can be found at [www.gnome-look.org](www.gnome-look.org) and [www.kde-look.org](www.kde-look.org) among other places. I know for GNOME all you gotta do is download the tar.gz and fire up the Theme selector and install it from there. 

3) There is such a thing as the "Debian Menu". Almost anything that comes from Apt makes an entry there.

4) GNOME, KDE, and all the other WMs behave nicely and coexist with each other. All you have to is install them with Apt.

And if you are afraid of the Command Line (Which you shouldn't :D) I have written a tutorial on it. Its the first link in my sig

---

