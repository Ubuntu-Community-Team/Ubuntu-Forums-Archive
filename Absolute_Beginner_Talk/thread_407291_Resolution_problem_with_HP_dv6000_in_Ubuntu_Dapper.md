---
title: "Resolution problem with HP dv6000 in Ubuntu Dapper"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by disandov on 2007-04-12
I installed Ubuntu 6.06 in my HP dv6000 and the default resolution is 1024x768 not letting me change it to 1200x800.

I already checked [FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto") and tried every solution.

I installed the i915 driver and actually works fine for the GDM, but when I try to login it fails and take me back to the GDM.

So I followed the instructions listed in the [Howto]("https://help.ubuntu.com/community/FixVideoResolutionHowto#head-84978c53ee5461d0924f8298527f4fbc891328c9")
and tried to access the gconf editor with the command ```
sudo startx gconf-editor
``` but I got the following error:

> xauth:  creating new authority file /home/domingo/.serverauth.16586

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


I renamed the .X0-lock and also didn't have success.

I suspect I can solve the problem accessing the gconf editor but really don't have a clue how to solve this.

I would really appreciate if you can help me as I don't what to go back to Vista :???:

---

### Post by Martin on 2007-04-28
Hi, this maybe a silly question - have you tried editng the xorg.conf file directly?

---

