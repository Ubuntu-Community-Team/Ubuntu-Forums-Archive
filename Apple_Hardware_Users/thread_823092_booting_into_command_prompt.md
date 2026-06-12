---
title: "booting into command prompt"
date: 2008-06-08
forum: Apple Hardware Users
---

### Post by Mariofreak64 on 2008-06-08
OK, i have tried control-option-F1, but it never works. I figured out that Hardy heron's gnome is crashing my g3 at boot up, so I want to go to comand prompt to uninstall gnome and install something else.I went through the CLI install, then installed gnome. I did every step. It only started having a problem after gnome was installed. Please help

---

### Post by stream303 on 2008-06-09
Ok, that's pretty typical of a G3 that needs a custom /etc/X11/xorg.conf modification.  Not too big a deal if you can get to a cli prompt.

See this faq for some great tips:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

See this nice report from snaglpus - even though he used a live-cd, I was extremely interested to see that he tried multiple times with a virtual terminal via CTRL-ALT-F1, but had to wait a few minutes between attempts before the cli showed up.

[http://ubuntuforums.org/showthread.php?t=820397](http://ubuntuforums.org/showthread.php?t=820397)

Btw, what model of G3 are you running, how much ram is installed, and is the hard drive original, or perhaps a larger replacement?

---

