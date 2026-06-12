---
title: "init help?"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by boobooq88 on 2006-10-07
Hi.  Im switchin from SUSE to Ubuntu and im tryin to install the NVIDIA driver which needs to be installed without X server running.  In SUSE I'd have to type *sudo init 3* to go to just text. what is the equivalent command in Ubuntu 6.06?

---

### Post by jordanmthomas on 2006-10-07
Wouldn't it be the same thing?

---

### Post by boobooq88 on 2006-10-07
well ive tried it but nothing happens.  and i mean nothing.

---

### Post by bisho on 2006-11-22
You could do:

sudo /etc/init.d/gdm stop

---

### Post by kinematic on 2006-11-22
or killall gdm as root.

---

### Post by turbojugend_gr on 2006-11-22
OR "sudo apt-get install nvidia-glx" to isntall from the repos, so you don't have to re-install everytime the kernel is updated.

---

