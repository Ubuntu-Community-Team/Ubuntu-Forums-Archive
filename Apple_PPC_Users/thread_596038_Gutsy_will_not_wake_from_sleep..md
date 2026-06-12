---
title: "Gutsy will not wake from sleep."
date: 2007-10-29
forum: Apple PPC Users
---

### Post by MacBookJoe on 2007-10-29
Hi, This is my first post.

I've read other threads from ppl with a similar issues but not any from the PPC comunity. I'm sorry if this has been answered.

I run a Apple Cube with a few upgrades (see Sig) I've just moved from Fedora 7 to Ubuntu Gusty and I'm very very new to linux, I'm tech savvy and i really try not to be or sound stupid. So i'm hoping someone can help me.

I had a hard time installing Gusty the Live CD would not boot and the Alt install dropped me into BusyBox, the guys over at the PPC wiki really helped and I'm now running 7.10 very smoothly, this sleep issue seems to be the last.

Originally i thought it was a waking from sleep issue, however i disabled sleep from the power manager and i still have an issue.

without warning and with no real pattern my monitor cuts out. linux drops the connection then my screen tells me there is no feed and turns off.

At a guess its a graphics driver issue, is there anything i can add to the xorg.conf?



thanks for your help.

J.

---

### Post by stmiller on 2007-10-29
What is your xorg.conf? Make sure the driver is specified as 'ati' or 'radeon'. The vesa driver probably won't work with sleep/wake.

And check the output of /var/log/syslog and /var/log/messages from the time when it goes to sleep. They may have some clues to the problem.

Sometimes having a USB device plugged in will be problematic with sleep/wake, if you have any odd usb devices plugged in.

---

