---
title: "UNIX/Linux CHOWN - Looking for a solution"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by ctjohn23 on 2008-02-01
I am currently taking a UNIX/Linux course (which assumes prior knowledge that I don't have)... and we were presented with a case study.  Apparently a non-technical person had root access to a AIX system and ran the following command: chown -R plead:user *.  This command was run accidently on the /usr directory and now the system is no longer functioning (it should have been run on some files in his home directory).  

Now the system administrator needs to fix the problem.  The only solution I see is booting to single user mode and manually changing all the permissions back.  However, this is a tedious process and I am hoping there is a better answer.  Can you undo the chown command?  If not, would it be feasible to run the .UNCOFNIGURED startup script to reconfigure the system?  I apprecaite any help or guidance you can give me to solve this problem.

---

### Post by hyper_ch on 2008-02-01
he could just copy back a previous backup ;)

---

### Post by ctjohn23 on 2008-02-01
Well, yes that is the easiest answer to the case.  However, lets assume there is no backup (or the backup is 2 days old, because we know any prudent sys admin has a backup lol).

---

### Post by hyper_ch on 2008-02-01
files in /usr shouldn't change so backups should be possible...

but there is no unchown command as far as I know... so you'd have to chown manually everything back... I tend to think that all files in /usr are owned by root - but never actually checked it.

---

### Post by ctjohn23 on 2008-02-01
After a quick check on another system, it does appear everything in /usr is owned by root.  If a process has an account that is associated with a particular file or directory, could I just add that process user account to the root group?  Or make another group, with root a member, and add all process related accounts to it?

---

### Post by hyper_ch on 2008-02-01
I dunno...

---

