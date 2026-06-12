---
title: "firefox 64bit and gksudo"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by struess on 2006-09-05
i'm running amd64 dapper and loving it.  a while back i followed Kilz's excellent HOWTO ([http://www.ubuntuforums.org/showthread.php?p=1174435](http://www.ubuntuforums.org/showthread.php?p=1174435)) on forcing firefox to run flash and java on machines using a 64bit processor.  This has been working very well (with the exception of a few YTMNDs not loading), but every now and then when i launch firefox, it will tell me its updating extensions and then load mozilla's homepage or the ubuntu homepage instead of loading my default homepage.  a little quirky, and i didnt' even think twice about it until i read this:  

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

This page describes the importance of launching graphical apps from the commandline with *gksudo* instead of with regular *sudo*.  like anyone looking for an answer, i saw the content of that page and thought, "that's my problem, so this must be my answer!"  i searched kilz's HOWTO and around the forums for related topics, but didn't find much.

long story short:  i launch firefox with a shortcut button on my main panel, but i believe its quirky homepage changing is related to the sudo/gksudo issue.  is there a way to on check this?  i don't know why firefox would require a sudo-caliber command in order to launch, but again, that page exactly described my problem, so its possible, i guess. 

any help would be great.  thanks :)

---

