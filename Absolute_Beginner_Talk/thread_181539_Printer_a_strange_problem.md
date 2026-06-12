---
title: "Printer: a strange problem"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by utab on 2006-05-24
Dear all,

I have a very strange problem with my printer. When I am using a Windows network pinter, I sometimes can print the first parts of a document and sometimes can not print.

For instance today in the morning I could print some pages but now I can not print and it does not give any error messages. In brief, sometimes I can print sometimes I can not.

Does anybody have a problem like this before?

Regards,

---

### Post by an.echte.trilingue on 2006-05-24
How did you set up the printer?

---

### Post by youthforlinux on 2006-05-24
my windows shared printer works fine

---

### Post by uteck on 2006-05-24
Since you are printing to a printer shared by a windows machine, you are using Samba to communicate.  It could be that Samba is acting up.  Try restarting Samba with "sudo /etc/init.d/samba restart"  and send a print job again.  Also, make sure the windows machine is not locked up or in powersave mode.

---

