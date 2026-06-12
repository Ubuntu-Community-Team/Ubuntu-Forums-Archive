---
title: "ATI mobility 7500 on old IBM thinkpad T40. How to optimize"
date: 2012-10-07
forum: Any Other OS
---

### Post by nahuel_89p on 2012-10-07
Hi, as the title says, i'm on an old IBM laptop with ati mobility 7500 graphics card. Everything runs "ok", but glxgears shows a performance of 400 fps. I read that this performance can be improved, but i didn't find a workaround yet in spite of the research i've done.

In this thread: [http://ubuntuforums.org/showthread.php?](http://ubuntuforums.org/showthread.php?) ... d+7500+ati i copied that corg.conf file, however, the glxgears fps didn't show any improvements.

> Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"radeon"
	Option 		"AccelMethod" "EXA"
	Option 		"AccelDFS" "True"
	Option 		"DynamicClocks" "off"
	Option 		"EnablePageFlip" "True"
	Option 		"MigrationHeuristic" "greedy"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


I've also read that a solution would be, like, matching the "memory" line in the xorg file with that of the RAM of my system (256), or downgrading the color depth, from 24 to 16. However im not sure if this can mess up things. I've never tweaked xorg.conf before. 

Particularly, i want to be able to watch youtube or vimeo videos, in fullscreen. There must be a configuration setting that optimize the performance allowing me to do this.

Im on an xfce session under mint 9. I guess it must be practically the same as xubuntu.

Thanks in advance!

---

### Post by Perfect Storm on 2012-10-07
Moved to Other OS/Distro Talk.

---

### Post by mips on 2012-10-08
Maybe have a look here, [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)
They also have a basic forum.

---

