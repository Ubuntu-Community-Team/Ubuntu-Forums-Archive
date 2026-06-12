---
title: "[SOLVED] nVidia TwinView: Failed to set MetaMode"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Nerrep on 2008-02-07
**NOW FIXED**

Hey everyone,

Just taken (another) forray into desktop Linux, and I'm very impressed; things have moved on rapidly in recent months, and the difference between now and my first attempt (with RedHat 9) is huge!

I'm unfortunately not without problems, namely getting my dual monitor configuration to work. When I set things up (running "gksudo nvidia-settings"), I get the following error:

Failed to set MetaMode (1) 'CRT-0: 1680x1050 @1680x1050 +0+0, DFP-0: 1440x900 @1440x900 +1680+0' (Mode 3120x1050, id: 56) on X screen 0.

Can't seem to figure out a solution unfortunately; I've tried clicking 'Reset' then ctrl-alt-backspace, but that didn't seem to make a difference.

Any ideas?

Thanks,

---

### Post by Nerrep on 2008-02-07
Managed to fix things; I think the problem was due to junk left over in my xorg.conf file.

Running "sudo dpkg-reconfigure xserver-xorg", with all the default values (except the first page, changing "nv" to "nvidia", and whatever mouse/kb settings you want), then starting the nVidia tool again seems to work.

If you have issues with maximising windows, and the title bars spreading accross both screens then logging out and in again fixes them. I'm impressed; I've never managed to get this going under Linux before.

(Happy) Dan

---

### Post by schmy on 2008-06-01
Still getting "Failed to set MetaMode" error. Any other suggestions?

Thanks in advance.

---

