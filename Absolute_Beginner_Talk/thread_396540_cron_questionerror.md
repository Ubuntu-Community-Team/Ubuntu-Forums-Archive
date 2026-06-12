---
title: "cron question/error"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by zappadragon on 2007-03-29
When I ssh to my ubuntu box I get a you have new mail message then when I go to read the message i get the following:

From root@Filekeeper  Wed Mar 28 07:36:20 2007
X-Original-To: root
From: Anacron <root@Filekeeper>
To: root@Filekeeper
Subject: Anacron job 'cron.daily' on Filekeeper
Date: Wed, 28 Mar 2007 07:36:19 -0400 (EDT)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink


What does this mean and how do I fix it?

Thanks

---

### Post by nixclusive on 2007-03-30
> /usr/share/man/man1/rmic.1.gz is a symbolic link that is part of the update-alternatives system. It'll be fixed when you have java installed in there.. but if its really annoying to know you might satisfy it by finding out where it points (supposed to be a sequence of symlinks) and create a new empty file by that name.

---

### Post by zappadragon on 2007-03-30
I still don't understand. Can someone please explaine?

---

