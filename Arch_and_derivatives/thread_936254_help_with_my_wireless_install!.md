---
title: "help with my wireless install!"
date: 2008-10-02
forum: Arch and derivatives
---

### Post by kforum on 2008-10-02
ive been trying to get my wifi working for arch and its been a while...
you can check my post here:
[http://bbs.archlinux.org/viewtopic.php?id=56153](http://bbs.archlinux.org/viewtopic.php?id=56153)

as it says, i can get dhcp to work, but not static ip, and since there are a lot of people in ubuntu forums, maybe one of you will know a way. :)


thanks in advance.

---

### Post by SomeGuyDude on 2008-10-06
Which Intel card do you have? I was having issues, but basically it came down to this:

1) Install iwlwifi-3945-ucode

2) Put iwl3945 in "MODULES" and "DAEMONS" in your rc.conf

3) Follow the instructions to install Wicd on the Arch wiki. That fixed everything that wouldn't work whenever I just did the standard manual connections.

---

