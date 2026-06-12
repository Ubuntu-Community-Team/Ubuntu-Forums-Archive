---
title: "Does Ubuntu run programs in protected memory spaces?"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by billingsworld on 2007-01-25
Hi,

I have installed some games via Add/Remove and some of them hang my system big time forcing a power off.

I haven't experienced this kind of software failure since Windows 98.  Does Ubunutu use protected memory so that when applications hang the system doesn't lock up?


Thanks.

---

### Post by DSn0wMan on 2007-01-25
Sometimes games crash your xserver for whatever reason. In many cases you can hit ctrl + alt + backspace to restart your xserver.

If that doesn't work you can try hitting ctrl + alt + f1 to get to a command line.

If all else fails you can use ctrl +alt +sysreq +k to gracefully kill all processes before powering down.

---

