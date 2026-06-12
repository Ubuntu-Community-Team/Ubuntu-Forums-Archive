---
title: "Firefox problems installing Greasemonkey and Adobe Flash"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Esther on 2007-09-23
Hi all,

This forum already has been a lot of help to me, but now I have a problem that I cannot find an answer to.

Tried to install Flash Player and Greasemonkey. The computer runs the whole installation process, no error messages or anything. But (also after restarting), I don't see the plugins in Firefox....no website with flash works and no monkey in the corner of the browser. Any tips and ideas how to solve this?

---

### Post by jrib on 2007-09-23
Let's troubleshoot one thing at a time.  Flash first.  How are you installing it exactly?  Have you used any third-party repositories or installation scripts?

---

### Post by Esther on 2007-09-24
Yes, I am installing it normally....I used the package installation program for it. First I tried to do it manually, but I had no idea how to do that. And the synaptic package manager also indicated that Adobe Flash is installed.

---

### Post by alienexplorers on 2007-09-24
Are you making sure the plugin for flash is being sent to your Firefox profile plugin directory.  If you are running flash you sould see 2 files in there named:
> flashplayer.xpt
libflashplayer.so
Greasemonkey can be found at:
> [https://addons.mozilla.org/en-US/firefox/addon/748](https://addons.mozilla.org/en-US/firefox/addon/748)  
If your Firefox is working correctly it should install with no problems.

---

### Post by jrib on 2007-09-24
Paste the output of this command:

```

apt-cache policy flashplugin-nonfree; ls -l /usr/lib/firefox/plugins ~/.mozilla/plugins

```

---

