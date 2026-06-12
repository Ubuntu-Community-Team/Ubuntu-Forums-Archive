---
title: "Not writable"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by cypherzero on 2008-01-04
I just reinstalled Kubuntu from the live CD and have a very strange problem.
When I click 'configure' on most applications I get a message:

[FONT="Lucida Console"]Will not save configuration.
File *(whatever)* not writable.
Please contact your system administrator.[/FONT]

This is even odder since the application does indeed save its configuration!

I tried using *Adept Installer* to update and possibly resolve the issue, but all the options are grayed out, even in *sudo *mode.

Has anyone had a similar problem?

All related posts I've read say to use sudo mode in Adept, but this doesn't seem to work for me.

---

### Post by FuturePilot on 2008-01-04
Did you launch Dolphin or any other app as root at all before the updates? If you did it might be this bug
[https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/155032]("https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/155032")

---

