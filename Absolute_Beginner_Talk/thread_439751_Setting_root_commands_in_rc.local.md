---
title: "Setting root commands in rc.local??"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by b_chris on 2007-05-11
Hello, I have Cron downloading my podcasts view hpodder and I want to delete the podcast folder every time I run the computer, at the moment I am trying to do it via /etc/rc.local but I do not know how to set up a root command in rc.local..... can anyone help??

Is this the best way to do it.  Also, how do you set a root command in gnomes' Schedule??


regards.

---

### Post by girishv on 2007-05-11
Hi,

instead of running it as a cron job by root, why not setup the cron job as the user. You can setup to remove the directory when you logout by specifying the required command in .bash_logout

All the commands in rc.local will be executed as root by default

Girish

---

### Post by b_chris on 2007-05-11
Cheers, thanks for that.

---

