---
title: "File system read-only??"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by ShadowRavenWings on 2005-08-16
Hi. I just installed Ubuntu earlier today, and when I tried to start the OS, I got some error message about the file system being read-only. So I went back to the installation to see if there was something I had done wrong, and in the partitioner part (because I was also installing WinXP), where it says mount options it was set to default. So I went in to see if I could change it, and one of the things it says is "ro - mount the file system read-only." Is this something I should change, and if so, how? =\

---

### Post by TGDuff on 2005-08-16
Only root is allowed to write to the filesystem with the exception of your home folder which users may write to.  To become root temporarily for a task, type "sudo" before a command requiring increased priveleges such as:

sudo apt-get install *filename*

Limited access keeps unix-based systems secure.

---

### Post by ShadowRavenWings on 2005-08-16
[QUOTE=TGDuff]Only root is allowed to write to the filesystem with the exception of your home folder which users may write to.  To become root temporarily for a task, type "sudo" before a command requiring increased priveleges such as:

sudo apt-get install *filename*

Limited access keeps unix-based systems secure.[/QUOTE]
 But it never even loaded the OS properly.. *is more confused*

---

