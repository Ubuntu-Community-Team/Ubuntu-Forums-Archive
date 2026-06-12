---
title: "Need help with loading ipfilter.dat in MoBlock"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-01
I installed MoBlock and I need to load my ipfilter.dat file into it. 

> By default it will load the block list from /etc/guarding.p2p and
   will log its activity to ./MoBlock.log, you can edit the script if you
   want to change them.
   You can specify a whitelist of ports in the start script as explained
   before.
   If you want to use new p2p.pdb files change this line in the start script:

	./moblock -p /etc/guarding.p2p MoBlock.log

   into this:

	./moblock -n /etc/p2p.p2b MoBlock.log

   or if you want to use ipfilter.dat files:

	./moblock -d /etc/ipfilter.dat MoBlock.log 

I'm new to Linux so I'm guessing I need to first move the .dat to /ect and then type that command in terminal? When I tried dragging and dropping it tell me I do not have permission. I tried logging into root to move it ,but then I couldn't find the file that I needed to move.

---

### Post by 449 on 2007-11-01
bump

---

### Post by Six_Digits on 2007-11-01
I hear it's frowned upon to bump... Be patient, someone will help. Keep searching on your own too :)

---

### Post by Maestro23 on 2007-11-01
> **449 said:**
> bump

Don't bump your post so soon. You can try to search the forums while waiting for someone to see/answer your posts. The link below is a Thread dedicated to setting up Moblock in Ubuntu.
Should help.

[http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock](http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock)

Good luck.

---

### Post by p0k3r808 on 2008-02-21
I am a new user to ubuntu gutsy and have no idea where to get ipfilter.dat, but I am trying to install moblock but I have no ipfilter.dat file that I know of.  Any help here would be great. Can I download this file and if so how do I copy it over to the correct section

---

### Post by jre on 2008-02-21
You can get lists from bluetack.co.uk.
If you use the ready compiled moblock packages from moblock-deb.sourceforge.net you'll get some lists automatically.
See this thread: [http://ubuntuforums.org/showthread.php?t=192559](http://ubuntuforums.org/showthread.php?t=192559) (already posted above) and [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

---

