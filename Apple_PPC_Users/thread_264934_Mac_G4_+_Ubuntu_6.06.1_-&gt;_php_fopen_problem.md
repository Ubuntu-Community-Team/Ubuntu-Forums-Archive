---
title: "Mac G4 + Ubuntu 6.06.1 -&gt; php fopen problem"
date: 2006-09-25
forum: Apple PPC Users
---

### Post by viragoLDR on 2006-09-25
Hi!

I've been trying to get linux to run on an old G4, which will function as a test web server. It used to just run Mac osX, but after reading several reports of how slow mysql is on osX, I decided to try linux.

So, I tried several distro's before Ubuntu (Yellow Dog and Fedora Core 5), but all have the same problem. A problem that doesn't occur on my Dell laptop, which is running the intel version of Ubuntu 6.06.1

Anyways, the main problem is that the php "fopen" refuses to work. If Yellow Dog and Fedora, people said it was causes by selinux blocking it, but even with selinux completely disabled, nothing worked. On my laptop, everything works fine, both from home and from work. On the G4 however, it gets blocked no matter what.

The fopen is being called by a CMS (webEdition), and it tries to access a php script on their servers to check for updates, and to handle registration etc, so I can't have done anything wrong with file rights. I know it's not the network or firewall or anything like that, since it works on the exact same hardware and settings running osX. The error message is "failed to open stream: HTTP request failed!"

(Oh, and Zend optimizer doesn't quite work either, crashes with a segmentation fault)

I'm running:
- Ubuntu 2.6.15-26-powerpc #1 Fri Sep 8 19:51:33 UTC 2006 ppc
- Apache 2.0.55
- PHP 5.1.2 (allow_url_fopen = On)
- MySQL 5.0.22

The same is running on my laptop. Both are clean installs, nothing extra installed, no config files edited etc, and the only difference I can see is that one is i386 and the other ppc.

Anyone have any insightful comments/ideas?

Martijn.

---

### Post by viragoLDR on 2006-09-26
So, no one ever came across this problem or something similar? I've been searching forums and google and mailinglists for the past 4-5 days, but I can't find anything.. Could it possibly be faulty hardware?

---

