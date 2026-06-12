---
title: "Mozilla Plugin problems"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Refined Power on 2006-12-13
Hi, I am having problems trying to install plugins for firefox 2.0 I have tried using automatix2 and synaptec, but Firefox does not recognize the plugins i.e. when I type about;plugins nothing is shown. I have tried following several tutorials and have searched the net with no success. 

Also there seems to be problems with update manager since I get this when I try and update:

W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxdecore0_1:5.0.1-1_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxdecore0_1:5.0.1-1_i386.deb)
  The HTTP server sent an invalid reply header


W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxencore0_1:5.0.1-1_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxencore0_1:5.0.1-1_i386.deb)
  Bad header line


W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mplayer_0.99+1.0-pre8-0ubuntu4_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mplayer_0.99+1.0-pre8-0ubuntu4_i386.deb)
  The HTTP server sent an invalid reply header


W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mozilla-mplayer_3.31-3v1ubuntu2_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mozilla-mplayer_3.31-3v1ubuntu2_i386.deb)
  Bad header line


W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/xserver-xorg-input-synaptics_0.14.6-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/xserver-xorg-input-synaptics_0.14.6-3v1ubuntu0_i386.deb)
  The HTTP server sent an invalid reply header


W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mencoder_0.99+1.0-pre8-0ubuntu4_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mencoder_0.99+1.0-pre8-0ubuntu4_i386.deb)
  Bad header line

Any suggestions? I really do not know what to do.

---

### Post by meng on 2006-12-13
Perhaps the repository was down temporarily, you could try again later. I don't have any problem fetching those files right now! Otherwise try the automatix forums.

---

### Post by Refined Power on 2006-12-13
> **meng said:**
> Perhaps the repository was down temporarily, you could try again later. I don't have any problem fetching those files right now! Otherwise try the automatix forums.

Well its still not working, but I get the impression that its something with my system not the repositorys

---

### Post by ardvark71 on 2006-12-13
> **Refined Power said:**
> Well its still not working, but I get the impression that its something with my system not the repositorys

Well, if Synaptic works you can try installing packages "mozplugger" and "flashplayer-mozilla." If PDF's don't work under mozplugger, you can replace it with "acroread-plugins" and "acroread."

Best Regards...

:KS

---

### Post by Refined Power on 2006-12-13
> **ardvark71 said:**
> Well, if Synaptic works you can try installing packages "mozplugger" and "flashplayer-mozilla." If PDF's don't work under mozplugger, you can replace it with "acroread-plugins" and "acroread."

Best Regards...

:KS

Well I tried senaptic and it installed but for some reason FF is not taking the plugins.

---

### Post by ardvark71 on 2006-12-15
> **Refined Power said:**
> Well I tried senaptic and it installed but for some reason FF is not taking the plugins.

The only thing I know to suggest is to try reinstalling Firefox using aptitude or synaptic.

Best Regards...

---

### Post by DarkN00b on 2006-12-15
> **Refined Power said:**
> Hi, I am having problems trying to install plugins for firefox 2.0 I have tried using automatix2 and synaptec, but Firefox does not recognize the plugins i.e. when I type about;plugins nothing is shown. I have tried following several tutorials and have searched the net with no success. 

*SNIP*

I noticed you wrote "about;plugins" here (with a semicolon). Is that a typo or did you type that into the address bar? (Sorry if that sounded rude, I didn't mean it that way.)
Anyway it should be ```
"about:plugins"
``` with a colon, not a semicolon. You should get a list of plugins when you type that into the address bar.

---

