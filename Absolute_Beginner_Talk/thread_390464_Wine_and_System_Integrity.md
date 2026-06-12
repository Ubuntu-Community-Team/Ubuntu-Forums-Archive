---
title: "Wine and System Integrity"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by kainlongshot on 2007-03-22
So I just made the jump to Ubuntu. I managed to install Wine on my AMD64 system. Still having some sound issues but so far I can run WoW fairly smoothly. 

It made me kind of wonder from a Windows standpoint the first thing I install, even before the updates is a firewall and an anti virus. A firewall is a no brainer for me. I always have one installed regardless of the OS. But I read that virii have a hard time infiltrating a linux box. (For good reason) so its not a big deal to run around with out an antivirus. Mainly for the reason that most virii are written for windows. 

Now I do run Wine which is sorta like running windows. (it can run windows apps, but isn't an emulator). Will I be exposing a big chunk of the linux "armor" if I don't have an antivirus for the sake of Wine? Should I have one installed just because I have Wine onboard?

---

### Post by Josh1 on 2007-03-22
If you are wanting to use Windows applications that aren't games (lol, main reason everyone uses WINE I guess) there is probably a Linux alternative.

Or you can just use the linux version of ClamAV.

---

### Post by ardchoille42 on 2007-03-22
[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

[http://www.ubuntuforums.org/showthread.php?t=72598](http://www.ubuntuforums.org/showthread.php?t=72598)

Wine will run Windows viruses/trojans/worms and some can affect your Linux files - read the above two links for more information.

The 8th post in the second link was particularaly surprising - proof that running a Windows virus can affect files outside the .wine directory.

---

### Post by kainlongshot on 2007-03-22
Thanks thats what I needed to know.  

To the 2nd poster, I guess I didn't clearly state or misinterpreted. I do run mostly games and some utility programs . . . but mostly games. You're absolutely right I can usually find a linux flavored utility . . . but games is why I run wine. 

The information is presented in the links is very interesting. . . . Now I'm kinda questioning wether its a good idea to run wine in the first place.  .  .  . anybody got any suggestiongs in shoring up this potential secturity risk (aside from abstaining from using wine?)

I usually a pretty cautious person. I try to make sure that I download from reputable places. However I went ahead and downloaded ClamAV, ran winecfg and removed everything other than C drive: "/Storage" (separate drive partition), removed Z drive: "/". Anything else I'm missing?

How do I do the following?

> Just run wine as an underprivileged user that only has read and write access to ~/.wine ( I would't even give it read access to / as it could read and transmit sensitive data ). Windows privilege escalation attacks don't work in wine ( the emulation isn't THAT good ) and the virus will think that it has Administrator privileges and access to the entire ( fake ) C: drive anyways, it's like a chroot jail.

-Kain

---

