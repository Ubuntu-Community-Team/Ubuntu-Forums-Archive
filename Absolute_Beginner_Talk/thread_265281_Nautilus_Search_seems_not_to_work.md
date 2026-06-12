---
title: "Nautilus Search seems not to work"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by GJS on 2006-09-25
Every time I attempt a search using Nautilus (Ubuntu 6.06) I get no results.  If I switch to a particular directory then search for a file I can actually see, it works.  However, being new to Linux I am spending a lot of time trying to find where certain files are located so I need to search the whole file system.  What am I doing wrong?

Any help appreciated.

---

### Post by TheMono on 2006-09-25
I've always wondered that myself actually, I'm not sure it does work properly lol.

Most files though don't need to be touched often, with the possible exception of 

/etc/X11/xorg.conf
and
/etc/apt/sources.list

---

### Post by andypaxo on 2006-09-25
When you do the search, you will see a bar across the top of the file area in Nautilus, which has a couple of drop down boxes.
The default is 'Location' and the name of your home directory.
If you want to search your whole computer, change the second box to 'File System'

Hope this helps

---

### Post by TheMono on 2006-09-25
Still doesn't work half the time for me lol. It's quite odd.

---

### Post by GJS on 2006-09-25
Thanks for your reply, andypaxo.  I made some progress.  I noticed that the search does work on an NTFS volume (old windows hard disk) that I have installed on the machine, so I though it might be a permissions thing.  I started nautilus as root (sudo nautilus) and success!  The search works.  The only problem now is that when performing a search, the location bar becomes the search term text box so I still cannot see the path to the files that are found.  Any ideas?  Or maybe there is an altogether easier way to locate a file and know it's path in Ubuntu?

Thanks for your help.

---

### Post by andypaxo on 2006-09-25
Good to hear that you have made progress - You may want to look at the chmod command if you need to change the permissions on files and directories

If you want to find out a file's location in Nautilus, just right click on it and choose properties and look right next to 'Location' (You can also use this window to change permissions if you prefer this to the command line)

---

### Post by William Gates on 2006-10-08
I created a custom apllication launcher for Nautilus (with root permission) on the panel of my admin login.

right click on panel
select: add to panel
select: custom application launcher
name: Nautilus
Command: gksu nautilus
select an icon and you're done.

When you click on the icon you will be prompted for the root password before launching Nautilus.
**[COLOR="Red"]Warning: You now have the ability to kill your system via a GUI! ;)[/COLOR]**

---

