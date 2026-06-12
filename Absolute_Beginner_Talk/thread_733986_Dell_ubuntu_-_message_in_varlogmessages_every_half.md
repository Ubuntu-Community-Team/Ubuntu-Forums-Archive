---
title: "Dell ubuntu - message in /var/log/messages every half a second"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by zeroed on 2008-03-24
Hi!

I have a laptop, Dell inspiron 1501.

Since some time noticed that /var/log/messages in appended with the same message almost every half a second.

Here is the log:

```
z@zubuntu:~$ tail /var/log/messages
Mar 24 18:38:49 zubuntu kernel: [60545.524000] atkbd.c: Unknown key released (translated set 2, code 0x8d on isa0060/serio0).
Mar 24 18:38:49 zubuntu kernel: [60545.524000] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
Mar 24 18:38:50 zubuntu kernel: [60546.520000] atkbd.c: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
Mar 24 18:38:50 zubuntu kernel: [60546.520000] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
Mar 24 18:38:50 zubuntu kernel: [60546.528000] atkbd.c: Unknown key released (translated set 2, code 0x8d on isa0060/serio0).
Mar 24 18:38:50 zubuntu kernel: [60546.528000] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
Mar 24 18:38:51 zubuntu kernel: [60547.560000] atkbd.c: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
Mar 24 18:38:51 zubuntu kernel: [60547.560000] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
Mar 24 18:38:51 zubuntu kernel: [60547.568000] atkbd.c: Unknown key released (translated set 2, code 0x8d on isa0060/serio0).
Mar 24 18:38:51 zubuntu kernel: [60547.568000] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.

```

I have discovered this problem  using google, but no solution helped. And I think almost all of them are just workarrounds.

When I'm trying to do:

sudo setkeycodes e00d 129, my system begin to slow. When I try, for example, to scroll down a page, using "down" key, it srolls a little and then just stops, so I don't like this solution. 

Can anybody help me with this?

---

### Post by smurphy_it on 2008-03-30
There are a couple of things with this one.  The following may or may not fix your problem.

Update your bios to the latest version.
Then in your xorg.conf file change your keyboard driver to one of the following.

"Generic-105 (Intl) PC" or "Dell"

Other solutions were ppl trying to shut off the hotkey-setup which is started on every boot.

This is accomplished by doing a sudo apt-get install rcconf

then in a terminal typing sudo rcconf and deselecting the hotkey-setup so that it doesn't launch on bootup anymore.

---

