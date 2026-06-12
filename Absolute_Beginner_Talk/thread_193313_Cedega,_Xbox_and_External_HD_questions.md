---
title: "Cedega, Xbox and External HD questions"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by incubusnb on 2006-06-09
I'm completely(no dual boot) switching to Ubuntu from XP over the weekend and I have a couple of questions that I'd like to clear up beforehand.

1: One of the main reasons I've been reluctant to switch was, not only the availability of major commercial games but, the ability to patch and/or modify those games post-install.  For example, I know Civ 4 is supported by cedega, but recently the 1.61 patch was released, and the game itself is highly customisable, but the Transgaming website doesn't seem to mention patches or mods.  Does Cedega usually have any problem supporting them?

2: My X-Box 360 allows me to connect to my computer through Windows Media Center in order to play mp3s, videos and view pictures on my TV.  Is there an open source replacement for Media Center that is capable of connecting to the 360?

3: I have an external 250GB HD that tends to get connected to alot of Windows computers. what file system would be most compatable with Ubuntu, and Windows XP for both read and write privelages? I was told Fat32 would be fine, but some people have said i'd need to use Fat16.

thanks in advance for your help.

P.S. For the curious, I'm not really "new" to Linux as I run a Web Server using Fedora, but I am new to using it as a desktop OS

---

### Post by darkali on 2006-06-09
1. You can apply paches in cedega just fine. I don't know about mods but problably yes.

2. Bump.

3. Fat32, because NTFS write is still experimental in Ubuntu and Fat16 only allows disks up to 4 Gb.

Hope that helps.

---

### Post by incubusnb on 2006-06-10
Thanks for your reply, those where my 2 biggest concerns, I can live without Media Center if I have to until a replacement is developed.  Nonetheless, if anybody has any knowledge of a project, I would be Grateful.

---

### Post by nalmeth on 2006-06-10
How does the XBOX 360 connection work?

I have a modded xbox hooked up to my router, and I can connect to Xbox Media Center through firefox by entering it's IP in the address bar. If I want to watch media from my computer on the xbox I use samba through XBMC, through my computer on firefox.

Is this similar to what you're trying to do? I'm kind of doubting they'd make it that easy to use with non-MS products, but it might be worth a try if you can't find anything else.

---

### Post by Xecuter on 2006-06-10
[QUOTE=nalmeth]How does the XBOX 360 connection work?

I have a modded xbox hooked up to my router, and I can connect to Xbox Media Center through firefox by entering it's IP in the address bar. If I want to watch media from my computer on the xbox I use samba through XBMC, through my computer on firefox.

Is this similar to what you're trying to do? I'm kind of doubting they'd make it that easy to use with non-MS products, but it might be worth a try if you can't find anything else.[/QUOTE]

Yeah, but it's not the same with the 360.

I've been thinking about the same incubusnb. Have you tried emulating Windows Media Connect? That program is for people without Media Center, but you can only stream music and pictures. There's another program that lets you stream DivX, but I haven't tried that. Tell me if it works.

---

