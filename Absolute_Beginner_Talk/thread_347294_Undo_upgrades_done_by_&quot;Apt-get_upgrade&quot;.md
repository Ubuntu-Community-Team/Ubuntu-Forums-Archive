---
title: "Undo upgrades done by &quot;Apt-get upgrade&quot;"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Silverfox on 2007-01-27
Is it possible to undo an "apt-get upgrade"? The upgrade I did this afternoon upgraded the following files:

2007-01-26 17:09:10 upgrade libc6-i386 2.3.6-0ubuntu20 2.3.6-0ubuntu20.2
2007-01-26 17:09:11 upgrade libc6-dev 2.3.6-0ubuntu20 2.3.6-0ubuntu20.2
2007-01-26 17:09:12 upgrade locales 2.3.18 2.3.18.1
2007-01-26 17:09:13 upgrade libc6 2.3.6-0ubuntu20 2.3.6-0ubuntu20.2

The upgrade appears to have broken a game server (bf1942) that I had running flawlessly before the upgrade, it now dies with a "Fatal error: Failed to bind socket" error after about a 10 second pause. The only thing I've changed is the four packages noted above. Can I revert to a previous version?

Oh. almost forgot. Running 6.06lts AMD-64 LAMP server. The updates noted above appeared to be security updates. Also, assuming I can undo the above noted, is there a way to exclude them from being upgraded in the future?

---

### Post by riven0 on 2007-01-27
Apparently, there are problems with the libc6 updates. The best idea is to just leave it and wait for Canonical to sort it all out.

---

### Post by charles.g.moore on 2007-01-27
Im not sure about reverting back but you should check out this website:
[http://www.ubuntuforums.org/showthread.php?t=37736&highlight=aptitude+vs+apt-get](http://www.ubuntuforums.org/showthread.php?t=37736&highlight=aptitude+vs+apt-get)

---

### Post by Silverfox on 2007-01-27
Ok, now I see. I wasn't using aptitude for the "upgrade" chore because I didn't want to have to load up aptitude and look for upgrades. I wasn't aware aptitude could be used via the command line like that. Thanks for the pointer. I'll amend my errant ways. ;)

I've restarted the server box again, and now the game server appears to be running. I had restarted the system with "shutdown -r now" after the upgrade, but a new restart seems to have made my issue go away. Thanks for the prompt responses.

You guys rock. :guitar:

---

