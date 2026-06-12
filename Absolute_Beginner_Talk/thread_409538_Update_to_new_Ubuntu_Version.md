---
title: "Update to new Ubuntu Version?"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by johnny sailor on 2007-04-14
Super newbie question here: If I have Ubuntu installed does it automatically update to the newest version once that gets released or do I need to actually install it myself and delete the old version?

Thanks!

---

### Post by qpwoeiruty on 2007-04-14
The update manager should automatically handle it when Feisty is released. It should say "New distribution release is available"

---

### Post by arochester on 2007-04-14
No it does not automatically update to a new version. You need to update (no need to delete) or do a clean install. You can only update one issue at a time e.g. Dapper to Edgy ot Edgy to Feisty - but not Dapper to Feisty.

---

### Post by chalex on 2007-04-14
once feisty is released you can upgrade to it by running a special upgrade program.  it won't upgrade automatically.

---

### Post by Quillz on 2007-04-14
I don't know if it's been changed or not, but in order for me to upgrade from 6.06 to 6.10, I have to manually enter a command to get Synaptic to recognize the update. Note, though, that in 7.04, the ```
sudo apt-get dist-upgrade
``` command is now recognized, so upgrading to future versions of Ubuntu will be done very easily via the Terminal.

---

### Post by qpwoeiruty on 2007-04-14
I thought that update-manager checks automatically in Edgy. Maybe it needs to be started with the -c option. -c -d will let you upgrade now to 7.04

---

