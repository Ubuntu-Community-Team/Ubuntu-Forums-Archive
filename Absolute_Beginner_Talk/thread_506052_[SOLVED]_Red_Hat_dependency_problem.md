---
title: "[SOLVED] Red Hat dependency problem"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Flyvapnet on 2007-07-21
For the past day or so, whenever I install something, the following dialog box appears just at the end of the installation process:

[img]http://flyvapnet.com/myPictures/CompyStuff/ScreenshotX320.png[/img]

So I went to the Synaptic Package Manager and reinstalled "redhat-cluster-suite" and "system-config-cluster," but this problem persists.  I'm not sure what's not being configured or what effect that's having on applications, but I'd sure be a lot happier if this dialog box quit showing up.

Any advice on how I might fix this problem would be greatly appreciated.  Thank you!

:confused:

=^..^=

---

### Post by Koybe on 2007-07-21
You'll need to open a terminal. Then try to repair installations :

```
sudo apt-get -f install
```

---

### Post by Flyvapnet on 2007-07-21
Thank you, **Koybe**, for that code!  Well, the problem is now solved because (realizing that I must have seriously messed up somewhere) I reinstalled Ubuntu.

:KS

=^..^=

---

