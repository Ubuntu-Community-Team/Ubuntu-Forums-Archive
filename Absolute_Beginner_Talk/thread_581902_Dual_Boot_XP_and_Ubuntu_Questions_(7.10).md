---
title: "Dual Boot XP and Ubuntu Questions (7.10)"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by TopKnot1 on 2007-10-19
Dual Boot XP and Ubuntu Questions

I'm sure this post will look familiar but I'm going to ask my questions any way!

Set up to the question:
I have a regular 32 bit Windows XP Corporate Edition installation on my computer.  I tried Ubuntu 7.04 already.  It's on an old computer that I can no longer use.  But I sort of enjoyed using Ubuntu because I was using a KVM Switch so dual booting was not an issue.  Well, a severe thunderstorm took out my KVM Switch and I will not be buying another $80 switch.  So I would like to try a dual boot system.  I had my current computer dual booted with an earlier version of Ubuntu and the default OS was Ubuntu and this was kind of a pain.  I plan on keeping my current XP installation!!!!  Here are my questions:

1.  With a dual boot, I understand I can access/write to the NTFS file system.  Does this mean all of my files from the XP file system like Open Office Docs, Spreadsheets, music, pdf's  will be accessible while booted to Ubuntu?  And are Ubuntu files available to me while booted in Windows XP.

2.  Has there been any changes to the way the dual boot method works?  I know there were some hacks to change the boot ini but wasn't comfortable doing this.  So will there still be a Ubuntu default boot when I boot my computer each morning?

---

### Post by forestpixie on 2007-10-19
> 1. With a dual boot, ... And are Ubuntu files available to me while booted in Windows XP.
you can get an app to read ext files in windows - [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd) - is I think the right one. And yes if you've got read/write you can do both from Ubuntu, not sure if it changed in Gutsy but in Feisty you need the ntfs prog - [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

2 - as far as boot goes I'm not sure if there's been changes - but I would guess that yes Ubuntu will still be default until you change it - it's quite simple really

---

