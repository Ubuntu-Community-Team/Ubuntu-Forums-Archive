---
title: "Mplayer and su"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by kmatth007 on 2007-02-13
Where can I find instructions on installing MPlayer. I can view .mp3 or wmv files? Also is there a default password for su. When installed Unbuntu I don't recall being asked to set it thanks.

---

### Post by Bachstelze on 2007-02-13
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Sqwishy on 2007-02-13
Well it should of asked you for your username and password, and your password for you username is what you use. Otherwise if you installed it with alternate or something the password is oem... i think.

---

### Post by kmatth007 on 2007-02-13
Thanks so much for the quick response. This site is helping so much in my switch from Windows to Linux.

---

### Post by Maestro23 on 2007-02-13
You can get Mplayer from the repositories via Synaptic(GUI) or apt-get(command line).  Might have to enable extra repositories to get it: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

In Synaptic search for "mplayer"

You will also need the win32 codecs: essential-20061022.tar.bz2
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

Another link to help you with command line:
RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The following link will help you get the codecs installed.  Start with step 3d for the codecs after you get Mplayer installed from the repositories.
[http://www.ubuntuforums.org/showthread.php?t=336706&highlight=win32+codecs](http://www.ubuntuforums.org/showthread.php?t=336706&highlight=win32+codecs)

Good luck.

---

