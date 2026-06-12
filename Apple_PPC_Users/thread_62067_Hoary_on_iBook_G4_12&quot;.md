---
title: "Hoary on iBook G4 12&quot;"
date: 2005-09-03
forum: Apple PPC Users
---

### Post by bibao76 on 2005-09-03
I've bought a new iBook g4 12" 1,33GHz. I wanted to install Kubuntu Hoary ppc. It's everything ok except for:
-Touchpad is not recognized
-Audio card. It works only with hearphones and not with internal speakers.
-I've tried to recompile the kernel. But yaboot doesn't boot with the new kernel.

Who can help me?

---

### Post by sulobanks on 2005-09-03
I'm certainly not an expert, nor have I tried Kubuntu, but I run Ubuntu Hoary on an ibook G4 14" which I bought new about 3 months ago and it works perfectly.  Perhaps if you check your media to make sure you don't have some corrupted packages?  Also, if you've changed yaboot.conf, don't forget to run ybin before rebooting. Otherwise, the changes don't make it to the boot partition.

---

### Post by bibao76 on 2005-09-03
The install media is ok. 
I've tried to reconfigure x.org with dpkg-reconfigure xserve-xorg but my touchpad doesn't work.
The same matter for the sound. It works only with hearphones, I've tried to reconfigure alsa-source and playing with the mixer settings but nothing happened.

Obviously I lauch ybin -v to install the new configuration of my kernel.
I'd like to have a working installation of Kubuntu on my apple, please help me...

---

### Post by lixus on 2005-09-06
For fixing sound see
[http://ubuntuforums.org/showthread.php?p=336445#post336445](http://ubuntuforums.org/showthread.php?p=336445#post336445)

---

