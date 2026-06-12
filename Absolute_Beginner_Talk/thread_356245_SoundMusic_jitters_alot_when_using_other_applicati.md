---
title: "Sound/Music jitters alot when using other applications"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by ADT on 2007-02-08
Sound is behaving badly, my system is setup as follows.
Fresh install on a pentium 3 863.8 MHz with 192 MB RAM.


Installed xubuntu 6.10 command-line system
Installed   xorg 
		imlib11-dev 
		libxft-dev 
		libxrandr-dev
		checkinstall 
		build-essential
		cmus
		xmms
		opera
Configured, Built and installed
		icewm 1.2.30

Started x and icewm
Started cmus and played an audio file.
Started opera and created new tabs.
When each tab was created the audio file jittered.
When I opened a succession of xterms quickly the audio file jittered.
When I cycled through workspaces very quickly the audio file jittered.
The same problems occured when using xmms to play the audio file.

I then upgraded the system using aptitude after I disabled all universe, commercial and multiverse repositories.
The following was upgraded:
		bind9-host
		dnsutils
		gnupg
		info
		language-pack-en
		libbind9-0
		libc6
		libc6-i686
		libdns21
		libisc11
		libisccc0
		libisccfg1
		libkrb53
		liblwres9
		libvolumeid0
		linux-image-2.6.17-10-generic
		tar
		tzdata
		udev
		volumeid
		w3m
		x11-common

The audio file when played in cmus and xmms did not jitter when using opera, cycling through workspaces or opening xterms.

However when I rebooted the system the jitter was back.
Has any one else had this problem with playing audio while doing other things like browsing and using xterms or abiword.
It is strange that the jitter stopped when I upgraded the system but returned when I rebooted.

---

### Post by jpeddicord on 2007-02-08
The package 'libsdl1.2debian-all' does wonders to fix sound problems. Try installing it, it may help fix the jitter.

Jacob

---

### Post by ADT on 2007-02-09
Thanks for the reply.
I installed the package and sound works fine now.
Cheers.

---

