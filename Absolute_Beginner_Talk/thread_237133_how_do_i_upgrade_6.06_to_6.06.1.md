---
title: "how do i upgrade 6.06 to 6.06.1?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by walterius on 2006-08-15
Today I burned a CD of the new Ubuntu release, 6.06.1.

I have a nice mature 6.06 installation and I'd like to keep it and just upgrade whatever 6.06.1 changed.

Can I do that? If so, how.

Also, how can I tell what changed?

Many thanks. :KS :KS :KS

---

### Post by kaffelars on 2006-08-15
If you have all the updates for Dapper 6.06, then you already have 6.06.1, as this "new version" is the same as 6.06, only with bugfixes and security patches.

Installing 6.06.1 now would then be a normal reinstall of the whole OS.

---

### Post by meng on 2006-08-15
If you kept up-to-date with the update manager, you don't need to update further. The new ISO is for those who are contemplating fresh installs of 6.06, so that they don't have to download 200-300 updates which have occurred since then.

---

### Post by David Corrales on 2006-08-15
If you open another virtual terminal (press ctrl+alt+F1) you'll see the 6.06.1 LTS. Press ctrl+alt+F7 to go back to the GUI :)

---

### Post by orb9220 on 2006-08-15
lsb_release -a in a term window should give you something like:

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper

---

### Post by walterius on 2006-08-15
Many thanks to all. From what I just learned, I will consider my new 6.06.1 CD a backup, that can avoid 200+ updates next time I install. Whew.

:rolleyes:

---

