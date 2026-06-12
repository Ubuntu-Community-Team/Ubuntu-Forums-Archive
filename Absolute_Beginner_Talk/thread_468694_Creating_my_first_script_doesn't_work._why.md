---
title: "Creating my first script: doesn't work. why?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Cecilio on 2007-06-09
Hi, I am totally new with Linux. I am trying to start with scripts but I am unable to run even the simplest one unless I invoke bash explicitly. Here is a sample. Any one could tell me where is the problem? Thank you very much

```

cecilio@homer:/media/sdb1/usr/Desarrollo_wx/lenmus/scripts$ test2
bash: test2: orden no encontrada     <-- translation: command not found

cecilio@homer:/media/sdb1/usr/Desarrollo_wx/lenmus/scripts$ ls -l
total 96
-rwxrwx--- 1 cecilio users  857 2007-06-09 08:59 pack_sources.sh
-rw-rw---- 1 cecilio users 1188 2007-06-09 08:54 pack_sources.sh~
-rwxrwx--- 1 cecilio users 1624 2007-05-22 18:43 test1.sh
-rwxrwx--- 1 cecilio users   57 2007-06-09 10:01 test2
-rw-rw---- 1 cecilio users   41 2007-06-09 09:51 test2~
-rw-rw---- 1 cecilio users   49 2007-06-09 09:48 test2.sh~

cecilio@homer:/media/sdb1/usr/Desarrollo_wx/lenmus/scripts$ cat test2
#! /bin/bash         
echo Hello world
exit 0          #success

cecilio@homer:/media/sdb1/usr/Desarrollo_wx/lenmus/scripts$ whereis bash
bash: /bin/bash /etc/bash.bashrc /usr/share/man/man1/bash.1.gz

cecilio@homer:/media/sdb1/usr/Desarrollo_wx/lenmus/scripts$ bash test2
Hello world


```

Thank you in advance,

---

### Post by yurimxpxman on 2007-06-09
> **Cecilio said:**
> Hi, I am totally new with Linux. I am trying to start with scripts but I am unable to run even the simplest one unless I invoke bash explicitly. Here is a sample. Any one could tell me where is the problem? Thank you very much

You have to put **./** before the file name, like **./test**.

---

### Post by Cecilio on 2007-06-09
Thank you. It works now! :D

But, why is it necessary to put './'? isn't it redundant?

---

### Post by AtrejuT on 2007-06-09
as far as I understand it: normally the shell only looks in the folders in your PATH environment like /bin etc... whenever you want to use an executable sitting in some other folder you have to give the complete path or use ./

---

### Post by hyper_ch on 2007-06-09
if it's a shell script (which I suppose) you could also run it with:

```

sh script

```

---

### Post by Regel on 2007-06-09
or you could just copy it to /usr/bin. Then it can be run like a normal command.

---

### Post by Cecilio on 2007-06-09
Tt is clear now :D

Many thanks to all by your time and help.

Regards,

---

