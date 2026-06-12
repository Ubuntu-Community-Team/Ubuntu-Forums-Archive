---
title: "Intel Driver Installation Help Needed"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by kenflipkick on 2006-08-16
I have a Mobile Intel(R) 915GM Express Chipset, and I downloaded the driver package from the official website, but I have no idea how to actually install the drivers.  The package came with a build document, but I'm still really new to Linux and I don't understand how to do any of it really.

If anyone could help, or at least direct me to better help, I would greatly appreciate it.

---

### Post by GoldBuggie on 2006-08-16
Instead of building it yourself and such why not use the package that is already in x/k/e/ubuntu.

so a ```
sudo apt-get install 915resolution
``` which will dl and install the driver you need. 

edit:
There is a wiki for dapper about this
[URL="https://help.ubuntu.com/community/i915Driver#head-6fcd801a3621b9769f7bf9f48fa4e3ad6e256654"]https://help.ubuntu.com/community/i915Driver#head-6fcd801a3621b9769f7bf9f48fa4e3ad6e256654
[/URL]
Hope that was of some help

---

### Post by kenflipkick on 2006-08-16
Thanks very much for making that easy to understand!  I installed it and everything, but I'm still having one problem.  When I run the glxinfo command, it still says "direct rendering: no".  Is there any way I can fix this?

---

