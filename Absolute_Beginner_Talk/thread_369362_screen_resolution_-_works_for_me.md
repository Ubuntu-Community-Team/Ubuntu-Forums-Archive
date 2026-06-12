---
title: "screen resolution - works for me"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Mozork on 2007-02-24
I'm using Ubuntu Edgy (6.10) and I installed it now several times, and finally found something that worked for me regarding the common screen resolution problem.

I'm using a ATI graphics card, and I'm quite convinced, that it only works for users with ATI cards. ;)

There is a huge amount of different solutions mostly for nvidia or intel cards, but I've found near to no information on what to do, when you cant set the screen resolution properly, and you have a ATI card, apart from installing the driver.

So, here what I've come up with (it's somewhat a patchwork solution):[LIST]
[*]First: Install easyubuntu (that's a really useful .deb package and provides a solution for many common problems with ubuntu (e.g. also mp3 support)) and don'f forget to select to install the ATI driver. ;)
[*]Restart. After that it might be, that it already works. For me id didn't. Also didn't reconfiguring the xorg.conf file, or other xserver related things work.
[*]So, here's part two: Open a console and type:
```
aticonfig --initial
```
[*]Restart. It should work now (at least it did now for me ;))[/LIST]I know, it's not really a questio0n or something, but I just wanted to share, in case someone other finds it useful resp. has the same problem.

---

