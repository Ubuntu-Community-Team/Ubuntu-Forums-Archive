---
title: "yWriter 5 freezing when data is saved"
date: 2012-07-16
forum: Any Other OS
---

### Post by Agent_Riot on 2012-07-16
I couldn't determine if there was a forum specifically for software, so i put this here. 
 
[LEFT]I downloaded yWriter5 from the Spacejock site [[COLOR=#000066](http://www.spacejock.com/yWriter5.html[/COLOR]]("http://www.spacejock.com/yWriter5.html")), and then I also grabbed the Mono engine. So it installed just fine and it runs... until I try to save something. If I choose the "new project wizard" and put in my book title and author name, then finish up, it brings me back to the main screen of yWriter, but it's like the program has frozen. I cannot click on any menus or tabs, and the only way to close the program is by "KILL"-ing it. This also happens if I start a new project without the wizard and try to save something like a character or place. More freezing occurs. My friend who's studying Linux certs told me it might be because my user didn't have write permissions to the yWriter folder. I ran the chown command with recursing to make those folders mine (they already were, but what they hey), and still no luck. The program functions fine until something has to be saved, then it freezes.[/LEFT]
 
[LEFT]My Windows Desktop may be fixed soon so I can try that, but since the creator of this software says it should work in Linux and since i've heard of people using it there I'd like to tinker with it to try for success. [/LEFT]
 
[LEFT]Thanks,[/LEFT]

---

### Post by Agent_Riot on 2012-07-18
Apparently it's a bug with Mono, and until further notice it can't be remedied. The suggestions are to use an older version of mono (with less functionality) or two try to get Mono connected to Wine and run the program through that.

---

