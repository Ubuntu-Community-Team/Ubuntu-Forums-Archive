---
title: "Add/Remove can't fetch a program"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by ClearyA on 2008-04-03
I am trying to install avidemux and i went to add/remove programs to do it because i kept getting an error message saying i could not fetch the program any other way.  And again i get the following error message

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.97-0.0_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.97-0.0_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/a/avidemux/avidemux_2.3.0-0.0ubuntu3_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/a/avidemux/avidemux_2.3.0-0.0ubuntu3_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)


..this is unbelievably frustrating to me... any ideas?

---

### Post by mikewhatever on 2008-04-03
Well, perhaps Canadian servers are down or something, nothing too frustrating. Try using a different server, preferably somewhere near your geographical location.

Update: That in fact appears to be the case, cause pinging 129.97.134.71 returns 100% loss.

---

### Post by ClearyA on 2008-04-03
how do i go about choosing a different server than?
is there a server list somewhere? :)

---

### Post by forestpixie on 2008-04-03
Open software sources in system > admin menu - there is a dropdown list for servers

---

