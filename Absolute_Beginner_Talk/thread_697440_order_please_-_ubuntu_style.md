---
title: "order please - ubuntu style?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by yrufset on 2008-02-15
i just recently completed my immigration from xp to ubuntu, and I'm pretty satisfied.
the only thing the keep on bugging me,
is the hard disk space hogging.
i have an 80 gb hd, and besides ubuntu i only installed a few external programs (swiftweasel, video codecs, pidgin, etc...) and yet, i have less than a giga of free space...
what is going on?
how can i see what's eating my space?
is there an easy way to go through the installed apps and uninstall the duplicated-targeted ones, like abiword and openoffice? going through synaptic's "installed list" might take years...
Xp had a neat little freeware called Ccleaner, which used to make order in the system. does ubuntu have similiar?

thanks for helping anyway...

---

### Post by drs305 on 2008-02-15
One of the built-ins in ubuntu is the Disk Usage Analyzer. You open if via System, Accessories, Disk Usage Analyzer.

A quick look at disk usage to show space used and remaining, although it doesn't show actual programs, is 
```
df -Th
```

I don't think you are going to find the duplication in ubuntu that you had in windows. That's why windows needed all those apps. You can click on the installed column in synaptic to get all the installed apps to move to the top of the list although there would still be a lot to go through.

Another thing to cut down on used disk space is to remove archive deb packages which you can reload if necessary at a later date. They are stored in /var/cache/apt/archive . Do a search to see the best way to remove them.

---

### Post by Borbus on 2008-02-15
There is no way Ubuntu is using 79GB of hdd space. You must have some other stuff on that partition.

---

### Post by yrufset on 2008-02-15
Thanks for the fast comment, both of you :)
i used Filelight to view my disk usage.
i notice ~/.local/share/Trash took 21 gb!!!
after searching the forums for a bit, i found out thar some non-Gnome applications might send they trash to a different directory then Gnome's trash dir.
this caused all of my downloaded-utorrent-thruoght-wine files to go to ~/.local/share/Trash and pile up there.

but now, is it ok for ubuntu to catch 60 gb??? or is there something else hidind on my drive, hogging my disk space...?

---

### Post by Trail on 2008-02-15
My ubuntu is 3-4Gb and it's pretty full of programs.

Are you sure you've mounted all your partionions?

There's also a little utility that shows you graphically the size of each directory (Accessories - Disk USage Analyser inUbuntu iirc), which might be helpful to pinpoint.

---

