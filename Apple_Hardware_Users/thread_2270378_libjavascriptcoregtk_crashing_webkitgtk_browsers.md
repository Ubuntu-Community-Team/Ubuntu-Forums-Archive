---
title: "libjavascriptcoregtk crashing webkitgtk browsers"
date: 2015-03-22
forum: Apple Hardware Users
---

### Post by rican-linux on 2015-03-22
Back in December I noticed in Debain Jessie that webkigtk browsers like Midori or luakit kept crashing on me. I placed a bug report [here]("http://lists.alioth.debian.org/pipermail/pkg-webkit-maintainers/2014-December/003715.html"). It looks javascript is crashing these browsers. This bug is still present in Debian and I am still waiting for an upate on when it will be patched (I emailed them as of this morning asking for an update). I also this bug in 14.04 and 15.04 I have opened a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/webkitgtk/+bug/1432965"). To see that this is javascript issue just run a backtrace against midori and make sure you have the debugging packages for midori and libjavascriptcoregtk-1.0.0 installed as well. I have also updated the PowerPC known issues page with this information.

---

### Post by rican-linux on 2015-03-24
Great news! I recieved patch webkitgtk packages from a debian developer and after installing them I can now surf the web on webkitgtk browsers. There are still some issues but this is a huge step forward.

---

