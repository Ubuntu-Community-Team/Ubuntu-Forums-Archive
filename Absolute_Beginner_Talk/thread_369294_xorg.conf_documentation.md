---
title: "xorg.conf documentation?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Ansible on 2007-02-24
I have a second monitor that I want to use for my laptop, and I've been able to get it to its native resolution by adding "1920x1200" to this section of xorg.conf:

	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1920x1200"
	EndSubSection

However, the laptop monitor itself is blank with the second monitor plugged in.  Help would be appreciated in specifically how to deal with this problem, but what I really want is a guide that tells me what everything in the xorg.conf file means, and how to configure it.  

I've seen a lot of references on this forum to the xorg.conf file, but documentation on all the settings and the structure of the file seem to be missing.  I found one on google, but its for gentoo.  

If the xorg.conf file is so basic to setting up your computer, shouldn't there be a guide to configuring it in the ubuntu docs?  As far as I can tell this is missing from both the official and the User Documentation wiki.  It would be nice to have the basics included like where is the file in my file system, how to edit it and save the changes, how to restart gnome once changes have been applied, etc.  I feel like this is important to new users; the first thing someone is going to want to do is set up the system to take advantage of their hardware, not lump along with one monitor at half resolution.  Getting the specific info from the forum on what to change is all well and good, but from that I get only bits and pieces of how to do things, and not the big picture.

For that matter, when things are missing from the user docs, is there a way to request that they get added?  Sorry if I sound petulant, but I'm starting to get frustrated after searching around for a few hours, because it seems like adding a second monitor shouldn't be this hard.

---

### Post by tagra123 on 2007-02-24
Using the menu:

Applications>Accessories>Terminal

type

man xorg.conf

---

### Post by 42Wired on 2007-02-24
[This]("http://www.ubuntuforums.org/showthread.php?t=221174") helped me set up dual monitor support on my laptop. It's pretty simple once you know what you're doing.

---

### Post by Ansible on 2007-02-24
Good stuff.  I wonder why there isn't a link to this from either the official or the community docs?  in the community docs it has a link "can't find what you're looking for", but that just directs you to an index of the same docs that don't contain the information you want.  Why not have a page that says "try the man pages" and "look at the sticky topics in these forums <link>"?  I'm sure going to the man pages and the forums is the first instinct of the non-noob, but for the noob, maybe not so much.  

That said, maybe I'll get up the nerve to go in and edit the user docs wiki myself to have these changes...

---

### Post by brettr on 2007-03-24
i would just like to note though that even after reading the  manual pager about xorg.conf and the i810 driver, there seems to be a gabillion other options that are available, that i have seen in other proples posts. So heh either i am really blind and can't see them or i don't know :D

---

