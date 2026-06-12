---
title: "breezy to dapper upgrade problems."
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by confuciusquinn on 2006-09-03
it seems simple enough, i hit the big button that says 'upgrade' in the update manager, and it seems like its going fine until it gives me the following error: 
"Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz) Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz) Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz) Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz) Unable to fetch file, server said 'Failed to open file.  '
"


Does anyone have any thoughts on fixing this?

---

### Post by confuciusquinn on 2006-09-03
now that I'm messing around a bit more, It seems like apt-get doesn't work at all either. for some reason nothing wants to download.. though i've only tried to install ruby so far. maybe somethings wrong with the server..

---

### Post by confuciusquinn on 2006-09-03
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/README](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/README)

"This project is now in dormant state, as the plf/ubuntu team resigned due
to lack of time. If you want more detail or want to help, please contact 
misc, either on irc ( #plf@irc.freenode.net ), or send a email on 
misc at zarb.org ."

****. what do I do now?

---

### Post by Drakkor on 2006-09-03
I it were me, I'd just download the complete Dapper.iso and install that ! 
Good Luck 1 :)

---

### Post by confuciusquinn on 2006-09-03
Thanks.. but i still really enjoyed using apt-get.Is this problem resolved in Dapper?

---

### Post by daemonoid on 2006-09-03
I had real trouble with the switch over. In the end i just installed clean I had a spare HD to backup to though.

I've had no problems with apt-get on dapper at all.

---

### Post by confuciusquinn on 2006-09-03
cool, thanks.

---

### Post by Drakkor on 2006-09-03
Sure with Dapper you can still use apt-get in the terminal,or for a graphical input,the Synaptic Package manager !! :D

---

### Post by confuciusquinn on 2006-09-03
if anyone else is having this problem, and wants to know how to fix it, go here and read this article:


[http://ubuntuforums.org/showthread.php?t=92672](http://ubuntuforums.org/showthread.php?t=92672)

---

