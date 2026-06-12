---
title: "new video card; - no desktop"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by anthonie on 2007-11-03
Hello all,

I recently upgraded my not so new Dell Optiplex GX260 computer, and treated it with a new grapic card, an ATI 9250 256Mb. 

I had Feisty installed on the machine with just the onboard intel graphic card (82845) and everything worked as a charm. Now it won't start X.

Any advise on what to do from the command line, since that is all I get at this point?

---

### Post by taurus on 2007-11-03
Go into your BIOS and turn off the onboard graphic card.  Then, boot into recovery mode from GRUB menu and reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
```
When you are done, you can reboot with

```
shutdown -r now
```

---

### Post by anthonie on 2007-11-03
Thnx Taurus, that did the job completely!

Any advise on some reading material where I can learn to troubleshoot these kind of problems, without having to ask at a forum? It is not always the case that I have the luxury of rebooting in windows and having an internet-connection available to ask on the internet.

---

### Post by daimaru on 2007-11-03
> **anthonie said:**
> Thnx Taurus, that did the job completely!

Any advise on some reading material where I can learn to troubleshoot these kind of problems, without having to ask at a forum? It is not always the case that I have the luxury of rebooting in windows and having an internet-connection available to ask on the internet.

[http://ubuntuguide.org]("http://ubuntuguide.org")

---

