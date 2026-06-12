---
title: "root pass"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by joot on 2007-01-22
I ran linux many years ago just as a test. I learned some things and am trying to relearn commands and allot of other things. anyway... it's been since '96 and as far as I remember you set a root pass during install. I was never prompted for a root pass and the account that I was prompted to set up works fine, but the same pass I would assume might be set dosen't work. I've tried blank with no results. I need to get up for work tomorrow, so scouring the board is not an option at the moment. If anyone can assist in adjusting my ignorance, the help will be appreciated. I know the question seems stupid, but is there a default root pass for an ubuntu install? thnx in advance. for an answer and not flaming me.

---

### Post by meng on 2007-01-22
Root password is not enabled by default. Ubuntu encourages use of 'sudo' rather than 'su':
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tonyr1988 on 2007-01-22
In Ubuntu, the root account is disabled by default (security reasons).

Instead, we use what's called "sudo." When you need a command ran by root, it's run using sudo to setup a temporary root environment. Check this out for more information:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

