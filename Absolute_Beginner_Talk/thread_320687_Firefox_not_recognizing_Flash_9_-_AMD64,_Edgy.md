---
title: "Firefox not recognizing Flash 9 - AMD64, Edgy"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by themikeflynn on 2006-12-17
Hello everyone! I'm trying to get Flash 9 working with Firefox 2.0 on Edgy. I'm using an AMD64 processor, and I'm pretty sure that's where my problem is. I've searched the forums but can't find a solution. Swiftfox and plugins installed via Automatix does nothing.

The guide I followed is:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

about:plugins doesn't show any sign of flash at all. I never installed Flash 7. 

Is there any guide/thread, or anybody willing to help with this?

---

### Post by ciscosurfer on 2006-12-17
> **themikeflynn said:**
> Hello everyone! I'm trying to get Flash 9 working with Firefox 2.0 on Edgy. I'm using an AMD64 processor, and I'm pretty sure that's where my problem is. I've searched the forums but can't find a solution. Swiftfox and plugins installed via Automatix does nothing.

The guide I followed is:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

about:plugins doesn't show any sign of flash at all. I never installed Flash 7. 

Is there any guide/thread, or anybody willing to help with this?This page will help: [http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/)

Download either the standalone player or the plugin, then opne the Readme/Install files to see where to copy the plugin.  If you still need help, please let me know. ;)

---

### Post by themikeflynn on 2006-12-17
Okay well, thanks for the reply but Adobe's instructions don't help either.

I have "libflashplayer.so" in the following directories
/usr/lib/firefox/plugins/
~/.mozilla/plugins
~/.mozilla/firefox/plugins

Firefox still is not recognizing the plugin.

---

### Post by ciscosurfer on 2006-12-17
> **themikeflynn said:**
> Okay well, thanks for the reply but Adobe's instructions don't help either.

I have "libflashplayer.so" in the following directories
/usr/lib/firefox/plugins/
~/.mozilla/plugins
~/.mozilla/firefox/plugins

Firefox still is not recognizing the plugin.Try throwing it here to make it effective system-wide```
/usr/lib/mozilla-firefox/plugins

as well as here:

/usr/lib/firefox/plugins
```

---

### Post by Sef on 2006-12-17
Are you using the 32 or 64 bit Ubuntu?  There are many problems with running applications on 64bit systems.

---

### Post by igknighted on 2006-12-17
Browse the 64bit help forums, the install is not as simple as 32bit, but there are workarounds.

---

### Post by themikeflynn on 2006-12-17
Thanks again for the speedy reply, ciscosurfer. However, it seems no matter where I put libflashplayer.so, Firefox doesn't want to use it. Just tried those directories, even restarting, and it still won't give.

I'm using the amd64 optimized version of Ubuntu Edgy. I understand the conflict, but that's why I'm making this thread! There has to be some workaround...

---

### Post by themikeflynn on 2006-12-17
Is there anyway I can recompile Firefox as a 32bit version? I have a feeling that might work out.

---

### Post by nick_ed on 2006-12-17
Yes that would sort it - see [http://www.ubuntuforums.org/showthread.php?p=1174435](http://www.ubuntuforums.org/showthread.php?p=1174435)

I had  the same problem myself. Eventually I just gave up on 64 bit ubuntu and installed the standard 32bit distro. I don't think you loose much performance wise, and everything works a lot better! I don't think 64bit Ubuntu is quite ready for the end user who wants to do stuff like watch flash stuff, install proper nvidia drivers etc. Hopefully this will all develop over the coming year as 64bit technology gets more mainstream

---

### Post by themikeflynn on 2006-12-17
That did the trick! Thanks! :KS 

For anyone having the same problem (Can't use Flash 9 in Firefox with Ubuntu AMD64 version):

Download and use the following packages (in order):
[http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb](http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb)
[http://home.comcast.net/~deletebox/firefox32-1.5.0.7-2-ubuntu-amd64.deb](http://home.comcast.net/~deletebox/firefox32-1.5.0.7-2-ubuntu-amd64.deb)
[http://home.comcast.net/~next/firefox32-2.0-ubuntu-amd64.deb](http://home.comcast.net/~next/firefox32-2.0-ubuntu-amd64.deb)

and then follow this guide for Flash 9:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

