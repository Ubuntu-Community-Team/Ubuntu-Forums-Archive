---
title: "directory/file for startup scripts"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by opexoc on 2006-09-21
Can you exactly say where can I find directory/file for my startup scripts, which will be executed right after logging? I have seen many threads on this forum about this problem. I don't want to use System->Preferences->Sessions, and I don't have ~/.gnome2/sessions directory or ~/.gnomerc file... In kde this problem was solved that there was some directory in my home directory where I can put such files... 

best,
opexoc

---

### Post by davmac on 2006-09-21
They're in /etc/init.d/

If you want to add a new script, have a read of [https://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](https://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/) for directions.

Hope this helps,

Dave Mac

---

### Post by skymt on 2006-09-21
@davmac: That works for boot-time spripts, but the OP wants scripts to run on login.

@opexoc: What's the problem with the Sessions control panel? It's worked for me, and it's the official, easiest, and least problematic solution.

---

### Post by opexoc on 2006-09-21
because it is interesting... that's all. 

davmac: yes... I don't need directory for boot scripts. I know where it is.

---

