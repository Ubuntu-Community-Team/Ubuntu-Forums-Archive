---
title: "help finding files"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by oxboy on 2006-07-19
Hi all,

I recently installed ubuntu onto my laptop, and I'm not sure what's going on.  I've been trying to follow some How-To's and a lot of them seem to ask me to do things in the ~/ directory (for example, searching and editing files there, etc.)  Problem is, I can never find the files there!  For example, I've been trying to look for my .gnomerc file, but I can't find it in the home directory.

I follow how-to's that tell me to install things using apt-get, and to go to the ~/ to find them, but again, I can't find them.](*,)   Any suggestions? Thanks!


just some other files I'm looking for, to make this less vague.  I'm looking for my .themes file and .config.  where can they be!?

---

### Post by Ragazzo on 2006-07-19
Files that start with a dot are hidden files. In Nautilus (Ubuntu's file manager) select View->Show hidden files to show them.

---

### Post by oxboy on 2006-07-19
I've tried looking for them with that option selected, and I still can't find them.  Is this because I have the root and home as separate partitions?

---

### Post by Ragazzo on 2006-07-19
> **oxboy said:**
> I've tried looking for them with that option selected, and I still can't find them.  Is this because I have the root and home as separate partitions?

I don't have .gnomerc either. What howto are you following?

---

### Post by oxboy on 2006-07-19
how to use openbox in Gnome, by stormy eyes

[http://www.ubuntuforums.org/showthread.php?t=75471](http://www.ubuntuforums.org/showthread.php?t=75471)

---

### Post by Ragazzo on 2006-07-19
I believe you need to create the .gnomerc file.

---

### Post by Skia_42 on 2006-07-19
Another way to see hidden files is to go to your home folder and press control+H.

---

### Post by Ragazzo on 2006-07-19
> **oxboy said:**
> 
just some other files I'm looking for, to make this less vague.  I'm looking for my .themes file and .config.  where can they be!?

They seem to be directories in your home folder (~).

---

### Post by oxboy on 2006-07-19
Thanks for your help =).

Even though I may have to create the .gnomerc file... I still can't find the .themes and the .config folders.  Do I need to do something to create those to?  I thought those should be created for you when you install.


I've tried looking for the hidden files using both ctrl+h and the search functions but no luck =/.

---

### Post by oxboy on 2006-07-19
i've tried looking for the folders (not files, thanks for the correction) in both ~ and ~/username  with no luck =/.

---

### Post by Ragazzo on 2006-07-19
> **oxboy said:**
> Thanks for your help =).

Even though I may have to create the .gnomerc file... I still can't find the .themes and the .config folders.  Do I need to do something to create those to?  I thought those should be created for you when you install.


I've tried looking for the hidden files using both ctrl+h and the search functions but no luck =/.

If you don't have .themes and .config folders, you can just create them. ;)

---

### Post by oxboy on 2006-07-19
I guess I could... but it seems like I need a config file from one of the hidden folders.  I wouldn't mind creating them if that would work :p

---

### Post by Ragazzo on 2006-07-19
> **oxboy said:**
> I guess I could... but it seems like I need a config file from one of the hidden folders.  I wouldn't mind creating them if that would work :p

Have you tried running "openbox --replace" once? It could create the config file then.

---

### Post by oxboy on 2006-07-19
yea I did.  openbox now runs instead of metacity, but I can't find the xml file that configs it... weird huh?

---

### Post by Ragazzo on 2006-07-19
> **oxboy said:**
> yea I did.  openbox now runs instead of metacity, but I can't find the xml file that configs it... weird huh?

Change a theme with obconf (Applications->Other or "obconf" in terminal) and it creates it :)

---

### Post by oxboy on 2006-07-19
I was trying to create .config and .themes and then run openbox -- replace, but I got some nasty errors that forced me to reboot...  Here's what I got:

I/O warning : failed to load external entity "/home/oxboy/.config/openbox/rc.xml "
I/O warning : failed to load external entity "/var/lib/openbox/debian-menu.xml"

(openbox:5222): ObParser-WARNING **: unable to find a valid menu file '/var/lib/ openbox/debian-menu.xml'
I/O warning : failed to load external entity "/home/oxboy/.config/openbox/debian -menu.xml"
I/O warning : failed to load external entity "/etc/xdg/openbox/debian-menu.xml"

(openbox:5222): ObParser-WARNING **: unable to find a valid menu file 'debian-me nu.xml'
I/O warning : failed to load external entity "/home/oxboy/.config/openbox/menu.x ml"

seems like I got other problems.... hehehe

---

### Post by Ragazzo on 2006-07-19
> **oxboy said:**
> I was trying to create .config and .themes and then run openbox -- replace, but I got some nasty errors that forced me to reboot...  Here's what I got:

I/O warning : failed to load external entity "/home/oxboy/.config/openbox/rc.xml "
I/O warning : failed to load external entity "/var/lib/openbox/debian-menu.xml"

(openbox:5222): ObParser-WARNING **: unable to find a valid menu file '/var/lib/ openbox/debian-menu.xml'
I/O warning : failed to load external entity "/home/oxboy/.config/openbox/debian -menu.xml"
I/O warning : failed to load external entity "/etc/xdg/openbox/debian-menu.xml"

(openbox:5222): ObParser-WARNING **: unable to find a valid menu file 'debian-me nu.xml'
I/O warning : failed to load external entity "/home/oxboy/.config/openbox/menu.x ml"

seems like I got other problems.... hehehe

Try removing the openbox folder in .config and run "obconf". It created the config files for me when I changed a setting there.

---

### Post by oxboy on 2006-07-19
> **Ragazzo said:**
> Try removing the openbox folder in .config and run "obconf". It created the config files for me when I changed a setting there.


Yep, that worked.  Thanks a lot!

---

