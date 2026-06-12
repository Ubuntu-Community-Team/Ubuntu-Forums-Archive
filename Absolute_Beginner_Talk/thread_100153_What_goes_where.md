---
title: "What goes where?"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Stone_Wolf on 2005-12-07
Hiyas

I've got a relatively simple question for those of you whom know...i hope.
What goes where in Ubuntu?

To give you an example.

Your personal documents go into "My Documents" in windows and more often than not "Home Folder" in Ubuntu. Your programs are installed to "Program Files" in Windows, but where in Ubuntu should they go?

A while back whilst i was still playing with Fedora Core i came across another Linux forum that had a suggested list of what each folders purpose was, and where you should save your personal data. Basically a template of how to keep your machine neat and tidy, with a place for everything and everything in its place. Is there such a thing for Ubuntu? I see when you mount something in Ubuntu, it's done in the "Media" folder instead of the "/mnt " folder like i did in FC.

I thought i'd just ask, seeing as this might be handy to others who are at a loss when they take a look under "File System"

Thanks in advance
SW

---

### Post by adduds on 2005-12-07
[QUOTE=Stone_Wolf]
I thought i'd just ask, seeing as this might be handy to others who are at a loss when they take a look under "File System"

Thanks in advance
SW[/QUOTE]

I've been thinking the same thing for a week, very good question!

---

### Post by aysiu on 2005-12-07
/boot - where your Grub configuration and accompanying boot files go.

/etc - config files for your Synaptic repositories and automounting parameters

/home - My Documents, My Pictures, Application Data, etc.

/usr/share/icons - icons
/usr/share/themes - themes
/usr/bin - executables for most programs
/usr/local/bin - where I put my own executables (not installed through Synaptic); really, you can put them anywhere, though.

/mnt - where things get mounted
/media - somewhere else where things get mounted

/dev - where your devices live--though, not where you access them. For example, my Windows partition lives at /dev/hda1, but I access it at /windows

/root - the /home for your root account

---

### Post by Stone_Wolf on 2005-12-07
Righty oh then...

Thanks for the speedy response. I hope this helps others also as it demistified Ubuntu that little bit more, now that i know what most of the folders are. Seems some of my guesses were correct though ^.^ 

Once again, thanks for the help.

Regards
SW

---

