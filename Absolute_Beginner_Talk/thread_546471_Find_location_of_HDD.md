---
title: "Find location of HDD"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by FLCLFan on 2007-09-08
Hello, I think i have done this before but right now i cant figure it out. I'm trying to edit my boot menu (menu.lst) to triple boot, but i cant find the location of my 2 other HDDs. Where do i find it the locations?

heres part of my menu.lst:

> title		Windows Vista x64
root		(???)
makeactive	
chainloader	+1

title		Windows XP x64
root		(???)
makeactive	
chainloader	+1

I need to find the "(???)"s.

Thank you.

---

### Post by chrome307 on 2007-09-09
I would suggest using Gparted:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754)

---

### Post by FLCLFan on 2007-09-09
That doesnt tell me what i need to know. :(

---

### Post by FLCLFan on 2007-09-09
[B]*Solved*
[/B]
Through trial and error I figured out the answers. It ended up being hd2,0 for vista and hd1,0 with 2 maps for XP.

---

