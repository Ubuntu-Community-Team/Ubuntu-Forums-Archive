---
title: "Can't get vlc"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by bedfojo on 2006-09-18
I'm trying to install vlc via synaptic but all I a getting is the following error message.  All help very gratefully received.

W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvbpsi4/libdvbpsi4_0.1.5-1_i386.deb](http://be.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvbpsi4/libdvbpsi4_0.1.5-1_i386.deb)
  404 Not Found


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/pool/universe/libt/libtar/libtar_1.2.11-4_i386.deb](http://be.archive.ubuntu.com/ubuntu/pool/universe/libt/libtar/libtar_1.2.11-4_i386.deb)
  404 Not Found


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxgtk2.6-0_2.6.1.2ubuntu2_i386.deb](http://be.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxgtk2.6-0_2.6.1.2ubuntu2_i386.deb)
  404 Not Found


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/pool/universe/x/xosd/libxosd2_2.2.14-1.2ubuntu2_i386.deb](http://be.archive.ubuntu.com/ubuntu/pool/universe/x/xosd/libxosd2_2.2.14-1.2ubuntu2_i386.deb)
  404 Not Found


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/wxvlc_0.8.4.debian-1ubuntu6_i386.deb](http://be.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/wxvlc_0.8.4.debian-1ubuntu6_i386.deb)
  404 Not Found


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-alsa_0.8.4.debian-1ubuntu6_i386.deb](http://be.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-alsa_0.8.4.debian-1ubuntu6_i386.deb)
  404 Not Found


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.4.debian-1ubuntu6_i386.deb](http://be.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.4.debian-1ubuntu6_i386.deb)
  404 Not Found

---

### Post by roberto22085 on 2006-09-18
I believe that you have to make sure that you are using the universe repository. After you enable the universe repository, go to your terminal (command line) and type "apt-get update" to make sure you have the newest repository addresses. Then retry adding VLC through synaptic.

I hope that helps!!!

---

### Post by thoolihan on 2006-09-18
It sounds like you may be having network problems.  Are you able to connect to the internet?  Can you ping a major site like [www.yahoo.com?](www.yahoo.com?)

#ping [www.yahoo.com](www.yahoo.com)

---

### Post by bedfojo on 2006-09-18
Thanks guys, but my connection is fine (as you can see!), Universe is enabled and sudo apt-get update runs OK.

Maybe a server is down somewhere?

---

### Post by bulldog on 2006-09-18
> **bedfojo said:**
> Thanks guys, but my connection is fine (as you can see!), Universe is enabled and sudo apt-get update runs OK.

Maybe a server is down somewhere?


When sudo apt-get update runs fine you should be able to install vlc.

sudo aptitude install vlc

There are some plugins which you might need.
Look for them in synaptic.

---

### Post by bedfojo on 2006-09-18
A little more investigation suggests a problem in the be.archive.ubuntu.com lists. Think it is a problem at that end, not my end!

---

### Post by bulldog on 2006-09-18
Just change be into nl and see if that goes.

---

### Post by bedfojo on 2006-09-18
Thanks for the tip - indeed the files are there using nl instead of be.  So how do I get to install those instead?

---

### Post by bedfojo on 2006-09-18
Solved it.  Used the Custom setting in Synaptic to shift to nl from be sources files.

Hope the be lists get sorted soon.

Many thanks for all the help, it really is appreciated.  Ubuntu and ubuntuforums are awesome as ever.

---

