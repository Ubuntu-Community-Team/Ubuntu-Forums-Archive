---
title: "[SOLVED] ubuntu 7.10 applcation bar gone"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by sloop on 2007-12-14
Hi to everyone.I have a little problem.On ubuntu7.10 on X face the top and bottom bars just disappear with no visible reason.Application button is gone too.Now with right click on desktop I have access to applications but this problem bothers me because this is bad symptom.

---

### Post by quinnten83 on 2007-12-14
you didn't accidentally select autohide, or accidentally clicked on the arrows to the side?

---

### Post by sloop on 2007-12-14
I do not think I did activate autohide and I do not know how to do it.I don't think I did arrows to side.

---

### Post by LinuxIsInnovation on 2007-12-14
Why dont you create a new panel and add all necessary buttons there..??

---

### Post by Tom Mann on 2007-12-14
Did you switch on desktop effects? This used to cause my bars to disappear (once upon a time)

---

### Post by quinnten83 on 2007-12-14
damn, you lost them both. I only know how to add an extra one, So at least 1 should be visible.
hope someone else knows this.
I am trying to find a solution though.

---

### Post by sloop on 2007-12-14
No I don't activate desktop effects.This problem happened to me with other ubuntu versions and with xubuntu.Sometimes after this appeared new problems and finely I reinstall becaus it is unable to log on.

---

### Post by sloop on 2007-12-14
sayakb, howto create a new pannel?

---

### Post by Tarmael on 2007-12-14
Press Alt + 2. Should bring up run application. Type gnome-panel.

Could do it.

If not, keep asking.

Bas.

Edit: Oh, you could also do this by creating a shortcut to the command I told you to run, right click desktop, create launcher, type gnome-panel for command, give it a name and optionally give it a comment.

Bas.

---

### Post by sloop on 2007-12-14
Thanks to everyone.The problem is solved.I'm afraid I don't know exactly how it happen.I think it was like this:1.ctrl+alt+F1; 2.type:
sudo apt-get --reinstall install xface xface-panel xface-panel-data;3.reboot;4.new session;5.xface

---

### Post by sloop on 2007-12-14
Oh, I forget to explain that gnome-desktop doesn't start at all.So I hoped to fix xface because the only problem there was top and bottom bars.Best wishes.

---

