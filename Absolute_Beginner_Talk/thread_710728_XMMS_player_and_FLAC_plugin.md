---
title: "XMMS player and FLAC plugin"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by trexgrec on 2008-02-28
I  have installed XMMS in Ubuntu Linux 7.10 AMD64, and FLAC files cannot be played at all. I checked the posts for the issue but they say something about downgrating from libflac 7 2.1 to 2.0. First, in Synaptics there is no libflac 7 at all, only libflac8. Second, libfla8 says that this is a valid plugin for XMMS. 

Do you have any suggestions, or should I try NOT to use FLAC with xmms ?

Thanks

---

### Post by oedha on 2008-02-28
have you install the gstreamer ?
and also ubuntu-restricted-extras ?

---

### Post by timbosity on 2008-03-06
Hi. had same problem and fixed it by installing flac1.2 from source [http://flac.sourceforge.net/]("http://flac.sourceforge.net/") and adding libxmms-flac.so to ~/.xmms/Plugins. Aparently its something about gutsy forgetting the xmms-flac plugin???? [https://bugs.launchpad.net/ubuntu/+source/xmms/+bug/139754]("https://bugs.launchpad.net/ubuntu/+source/xmms/+bug/139754")

Anyway, xmms is the best audio player for X by far. so light on resources and yet so versatile...:guitar:
 Hope this helps

---

### Post by trexgrec on 2008-03-11
OK, so there is some sort of a bug after all. Thats good, cause I am in the right track. Since I am an absolute beginner with Linux in general, can you be more specific as to the libflac that I need to download and install. I was checking in the web page and there are many libraries for Debian, and some of those are for XMMS but which one exactly?

Thanks for the quick info, I will try (really hard) to fix it myself too.

---

