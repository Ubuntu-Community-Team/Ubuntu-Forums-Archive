---
title: "Azureus on Gutsy i86: A newbie's Hell"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by ReddyReal on 2007-10-23
Hey guys,
I am, yes, a total newbie to not just Ubuntu but all of Linux. I was enormously intrigued by the possibilities of Ubuntu courtesty of [this]("http://nerdica.com/?p=30") article and thought I'd give her the ol' college try. I am trying to install a headless server on my old AMD Athlon PC and then run Azureus off of it to do music/movie file sharing.I would then access the computer via VNC on my Mac G5 as  well as my computer at work. After trying to follow the  article line-by-line and getting held up at the Azureus part, I abandoned the section on Azureus and just tried to install Azureus on my own.

I have been able to install Gutsy fine. However, when I try to install Azureus from either a download off the website or the Applications > Add/Remove programs button, Azureus will pop up and then disappear. I even went back and tried to install Java via the Terminal but that did nothing.(I now have 1.6 version of Java).
 I've seen other people [comment]("http://ubuntuforums.org/showthread.php?t=582156&highlight=azureus+gutsy") on this but I can't figure out how the hell to replicate their success. For example, how does one "untar" and "cd directory?" :confused: Or is that even necessary to know?

Or is my problem that I'm doing all of this in Gutsy, when I should really only be using Feisty right now?  

Thank you SOO much for your time. My  bosses have no idea why I look like I've been out drinking the past few nights - computer hangovers!

-Reddy

---

### Post by PatrickMB on 2007-10-23
I had the same issue with Azureus from the Repos. What I did to install Azureus was to download the latest version off of sourceforge at this address [http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=215453](http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=215453). I selected the second file, the one for i386 systems. Once downloaded, I double clicked the file and extracted the contents to my home/azureus folder that I created. The clicked on the azureus program in that folder and viola working azureus.


Let me know if that makes any sense to you. If not I will be happy to explain it in more detail.  One further note, that is probably not the easiest way to install Azureus, but it was the way that worked for me, an Ubuntu retard.

---

### Post by crav on 2007-10-23
I suspect that I had this exact same problem with fiesty. Here's the thread that solved the issue for me: [http://ubuntuforums.org/showthread.php?t=413192](http://ubuntuforums.org/showthread.php?t=413192)

---

### Post by ReddyReal on 2007-10-23
PatrickMB, 
Christ! That did it. We Ubuntu retards must think alike:) Thank you for  the prompt replies, gentlemen.

Crav, I followed that link but it seemed to center around switching the Javas I'm using and that, well, freaked me out. 


Now, as for making this process more elegant: 
I guess one of the Nerdica article's cool little touches was making  Azureus start up on boot, automatically, in the background. Going into the desktop and clicking on that icon seems so much less *cool*!:) Have you figured out how to get that done, with azureus sitting on the desktop like that?

Thanks again

---

### Post by badguyanil on 2007-10-23
when i had 7.04 i faced similar problems with Azu2.X. That forced me to shift to some other torrent client (Dulge). But after installing 7.10 i followed the following tutorial to download and set up Vuze(Azu 3). And havent had any problem since then. you can follow the same and c.

> [http://azureus.sourceforge.net/howto_linux.php](http://azureus.sourceforge.net/howto_linux.php)

all it requires is to have Java 1.6 installed! and i guess you already have it so go ahead and give it a try!
hope for the best.

---

### Post by PatrickMB on 2007-10-23
> **ReddyReal said:**
> PatrickMB, 
Christ! That did it. We Ubuntu retards must think alike:) Thank you for  the prompt replies, gentlemen.

Crav, I followed that link but it seemed to center around switching the Javas I'm using and that, well, freaked me out. 


Now, as for making this process more elegant: 
I guess one of the Nerdica article's cool little touches was making  Azureus start up on boot, automatically, in the background. Going into the desktop and clicking on that icon seems so much less *cool*!:) Have you figured out how to get that done, with azureus sitting on the desktop like that?

Thanks again

Glad I could help. As for setting up to start automatically, no idea. All I have managed to do is to add it to  the internet tab under applications, which is slightly better than navigating to it on the desktop, I think.

---

