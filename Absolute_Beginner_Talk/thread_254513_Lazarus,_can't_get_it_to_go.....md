---
title: "Lazarus, can't get it to go...."
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Niloc on 2006-09-10
I downloaded the Lazarus package 'lazarus-0.9.16.tar.gz', unpacked it but what do I do now? I read the INSTALL.txt and tried to find the source and did the 'make' as suggested but nothing happened, it just said 'lazarus is up to date' but when I type just 'lazarus' nothing comes up! There are no new commands, applications anywhere. Where is it supposed to be? How is it supposed to be started?

---

### Post by Sef on 2006-09-10
To compile you need build-essential, have you downloaded it?

If not, then do the following:

Applications > Accessories > Terminal

sudo apt-get update

sudo aptitude install build-essential

---

### Post by Niloc on 2006-09-10
Thanks Sef, I did all that and did another MKE CLEAN ALL id the comilation aborted with 'Cant find Unit glib' what do I do now?
I am gettung closer!!

---

### Post by marcelm on 2006-09-17
See the Lazarus FAQ (google 'lazarus' and pick the first one :D )
You need a lot of packages to get it work, and also install the free pascal source. B.t.w. lazarus is started with 'startlazarus'.

---

