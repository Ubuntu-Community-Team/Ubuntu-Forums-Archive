---
title: "Locked out of sudo"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Lukian on 2007-06-16
Since the last updates or due to my own action (I was attempting edit my user group in Users & Groups recently), I'm locked out of sudo.

Typing "sudo <anything>" does nothing and update manager is complaining about not having access when trying to install the updates (and other package software which drew my attention to this also won't install).

---

### Post by bigken on 2007-06-16
dont know if this will help but its worth a try in the terminal type 

sudo passwd

---

### Post by JulianRoot on 2007-06-16
I think you aren't in the group 'admin'.
Boot your PC from a live CD and chroot your Ubuntu.
Now try to add your user to this group.

Julian

---

### Post by plcdfa on 2007-06-16
If you have removed your user from the sudoers group then you can add it back with adduser. You can gain root acces by selecting recovery mode from the grub menu.

---

