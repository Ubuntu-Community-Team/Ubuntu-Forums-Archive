---
title: "GRUB Error"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Byakira on 2008-01-17
Heyy all

When I try and install Linux, it would get to the Installing System stage, but would stop and give me the ERROR LOADING GRUB (h2o) or something like that.

Whats wrong?

---

### Post by pollywog on 2008-01-17
Have you verified that your CD has no defects? When you boot your live CD you can scroll down to the "Check CD for defects" option, and verify that all is OK. If the test verifies this as a good CD, I would delete the partitions that you just created (You can do this with a freely available GParted disk), and try the install again.  If you still get an error, you might try to install again with an "alternate Install" version of Ubuntu, or possibly and earlier version (Feisty). My guess is that you have a bad disk. It is really easy to end up with a bad burn.

---

### Post by Iowan on 2008-01-17
[THIS]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html") won't solve the problem at hand, but might give some insight into what the error means.

---

### Post by Byakira on 2008-01-17
> **pollywog said:**
> Have you verified that your CD has no defects? When you boot your live CD you can scroll down to the "Check CD for defects" option, and verify that all is OK. If the test verifies this as a good CD, I would delete the partitions that you just created (You can do this with a freely available GParted disk), and try the install again.  If you still get an error, you might try to install again with an "alternate Install" version of Ubuntu, or possibly and earlier version (Feisty). My guess is that you have a bad disk. It is really easy to end up with a bad burn.

So you think I should burn again? Will it fit into a CD-R? And can you give me a link to the alternate install version?

Thanks

---

### Post by Iowan on 2008-01-17
[HERE]("http://www.ubuntu.com/getubuntu/download") is the download page - notice the checkbox at the bottom for the laternate version.

---

### Post by pollywog on 2008-01-17
You should only re-burn the CD if you run the test that I mentioned, and it tells you that the medium is corrupted, and should not be used. The alternate install CD is great, in that it is not a live CD, just a simple text based install, nothing fancy. Has less to go wrong. You download it at the Ubuntu site. When you select the options (i.e. x86, nearest mirror..) you'll see a little box at the bottom that you check to download the alternate install CD.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

