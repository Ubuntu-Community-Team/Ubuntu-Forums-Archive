---
title: "Epiphany as webbrowser"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by NikoC on 2007-02-27
Hello folks, I've been using firefox and metacity as a window manager without any troubles, now I wanted some eyecandy and installed beryl from the feisty repos ([link]("http://www.ubuntuforums.org/showthread.php?t=357501&highlight=beryl+nvidia")). Managed to fix the beryl problems due to latest updates with the following solution [link]("http://www.ubuntuforums.org/showthread.php?t=362266"). However when opening firefox and running beryl at the same time, my windows respond annoyingly slowly (confirmed problem on the beryl and ubuntu forums) so I decided to try out epiphany as a browser: works great so far, the only problem I'm having is that the back and forward buttons on my logitech mx310 do not work in epiphany yet they do in firefox. Any ideas?

---

### Post by erkki70 on 2007-02-27
Hi,
This looks like a known bug.
Check here for a fix:
[https://bugs.launchpad.net/epiphany-browser/+bug/55077](https://bugs.launchpad.net/epiphany-browser/+bug/55077)
Hope it helps...

---

### Post by NikoC on 2007-02-27
Hmmz thanks for the quick reply, yet still not being near an expert I was wondering were to add the two lines mentioned in the bug report...

---

### Post by george29 on 2007-02-27
it looks like you should find them in about:config.

go to the browser address bar and type in

```
about:config
```

hit enter 

then search for mousewheel and change the lines to read as below

mousewheel.horizscrool.withnokey.action 2
mousewheel.horizscrool.withnokey.sysnumlines false

---

### Post by NikoC on 2007-02-27
Aha great, I was looking for a config in my file system... no luck of course ;-)
Changing these two lines does the trick for me! Thanks a bunch!!!

---

