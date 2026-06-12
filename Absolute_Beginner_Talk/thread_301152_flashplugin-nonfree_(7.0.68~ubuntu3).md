---
title: "flashplugin-nonfree (7.0.68~ubuntu3)"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by mep on 2006-11-16
Hello,

I am using Symatic Package manager to download flashplugin-nonfree (7.0.68~ubuntu3) to my system ( Ubuntu 6.10 ).  The download process failed and gave me the message to use the following command:

```
sudo dpkg --configure -a
```

This starts up the download again for the flashplugin but it has been 3 hrs and it has not yet finished.  I think it may have failed again.

My questions are:  

How do I stop this installation process of this flashplugin nonfree??  

How do I clean it up after I stop it?

Thanks in advance,

-mep

---

### Post by LLRNR on 2006-11-16
Hi. You could try first
```
sudo aptitude purge flashplugin-nonfree
```see if it helps. I also had a somehow similar problem with Synaptic, but it can be solved.

---

### Post by snay on 2006-11-16
Sory I cant help with your specific problem, but if I were you, Id try [http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/)
Its the beta linux port of flash player 9, but it plays all the flash 8 stuff. Its pretty good. Ive not had any problems with it.

---

### Post by mep on 2006-11-16
Thanks LLRNR  That command worked.  Probably a command that I should put to memory.  Mine!!  In Ubuntu what prg is best suited for use with Flash? Reading Flash tutorials on web. I am a newly converted from Xandros Business 3.02 user.  I am using Ubuntu 6.10 but as I read in this forum stickies I should have probably used 6.06.1.   I have been able to install vmware, nvidia drivers and samba is up..  My samba question was answered earlier and now I am progressing along.

Excellent community and forum!

-mep

---

### Post by LLRNR on 2006-11-16
You mean for _reading_ Flash contents ? (I have a very personal issue with Flash, as I really need to get Macromedia Flash 8 precisely to work within Wine... So far it seems it's possible. I haven't tested it extensively though, but it works.) For simply viewing Flash contents on the web, I'd go for the flash plugin 9 beta provided by Adobe, mine is working ok. Here's a [HowTo](http://ubuntuforums.org/showthread.php?t=279990).

Good luck!

LLRNR

---

### Post by mep on 2006-11-16
Thanks snay LLRNR  I downloaded the adobe labs plugin from the above link provided by snay and followed the instructions in the readme.txt file,  created a plugin directory and pasted the plugin.  I am now able to read flash on web..  Thanks!

-mep

---

