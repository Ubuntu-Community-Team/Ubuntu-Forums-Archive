---
title: "firefox is crashing with certain forums"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by bhoughton on 2006-09-12
Hi,

Recently Firefox 1.5 has started crashing on certain forums (most notably 1src, a Palm handheld forum at [http://www.1src.com](http://www.1src.com)) when clicking on threads.  There doesn't seem to be any logic to how/why it crashes.  Deleting cache, etc does help for maybe 1 site visit.

Any thoughts on what might be the problem are welcome.  Any users of 1src that can chime in on this are appreciated as well.

Regards,
Brian

---

### Post by jmtjet on 2006-09-12
I've been experienceing that as well. Others on other forums are also reporting crashes. The general conscientious is it's related to flash or java in advertisements-namely an IBM ad that's making the rounds.

My crashes consist of Firefox closeing with no notice and with no message. It just closes like I hit the "X".

---

### Post by bhoughton on 2006-09-12
Thanks.  I had been thinking that I was crazy or something.  Your experience of FF just closing up like hitting "X" describes my situation perfectly.  Using Konqueror seems to solve the problem, although I really prefer Firefox.

Is there a way to turn off flash, java or another setting that might prevent it?

-Brian

---

### Post by xyz on 2006-09-12
I found this posted by **chrisrx**
> It's the flash plugin. it doesnt like the composite extension.

As far as I remember to fix it you put

**export XLIB_SKIP_ARGB_VISUALS=1**
in before the last line of /usr/bin/firefox
[http://www.ubuntuforums.org/showthread.php?t=132377&highlight=firefos+crash](http://www.ubuntuforums.org/showthread.php?t=132377&highlight=firefos+crash)
Also here:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Look for Macromedia HowTo.

---

### Post by bhoughton on 2006-09-12
> **xyz said:**
> I found this posted by **chrisrx**

**export XLIB_SKIP_ARGB_VISUALS=1**
in before the last line of /usr/bin/firefox
[http://www.ubuntuforums.org/showthread.php?t=132377&highlight=firefos+crash](http://www.ubuntuforums.org/showthread.php?t=132377&highlight=firefos+crash)
Also here:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Look for Macromedia HowTo.

Thanks for the info.  I have tried disabling Java and Javascript in the prefs and so far that seems to be working.

---

### Post by xyz on 2006-09-12
Great then! So long as it works! Happy 1src....

---

