---
title: "chroot '/bin/bash/ no such file or directory', yet they exist?!"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by koloatree on 2008-01-02
hi, i followed this tutorial and everything seemed to of gone fine..

[http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)


however, when i try to login, i get an error message saying bash/bin no such file or directory. i checked the chroot folder to make sure the folder and bash exist, and they do. :confused:

---

### Post by kevdog on 2008-01-02
What does your /etc/passwd look like for the chrooted user?

---

### Post by koloatree on 2008-01-03
hi, if worse case scenario, can i delete everything in the chroot folder and start again? maybe i dont have the correct lib/config files, but would that cause a the '/bin/bash file not found'?

---

### Post by Fixman on 2008-01-03
Have you already done ```
chroot ~/chroot
```

---

### Post by koloatree on 2008-01-03
i dont think so since im pretty sure it wasnt listed in the tutorial i followed?

> **Fixman said:**
> Have you already done ```
chroot ~/chroot
```

---

### Post by Fixman on 2008-01-03
Can you put ```
 ls /home 
``` and put here the results?

---

### Post by hyper_ch on 2008-01-03
wouldn't mysecureshell be sufficient?

---

### Post by koloatree on 2008-01-03
is that a special shell like rbash?

> **hyper_ch said:**
> wouldn't mysecureshell be sufficient?

---

### Post by hyper_ch on 2008-01-03
sort of... it allows sftp connections to it and locks users into their home dir. They can't connect to a terminal session...

Only drawback: You'll have to compile it on your own - which isn't that hard.

---

### Post by metanol on 2008-02-21
It's probably due to missing libraries.

Execute 'ldd /bin/bash' and see if all files are located in your chroot directory.
Most likely the file ld-linux-x86-64.so.2

---

### Post by hyper_ch on 2008-02-22
compilation of mysecureshell was easy (on gutsy). Haven't tried on hardy yet.

---

### Post by thequickbrownfox on 2008-07-23
> **koloatree said:**
> hi, i followed this tutorial and everything seemed to of gone fine..

[http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)


however, when i try to login, i get an error message saying bash/bin no such file or directory. i checked the chroot folder to make sure the folder and bash exist, and they do. :confused:

I had a similar problem. I solved it by creating a 'lib64' directory in the jail, in the exact same fashion that you created 'lib'. Next, for all the files that you copied from /lib/ to {your_jail}/lib/, copy the corresponding ones from /lib64/ to {your_jail}/lib64/  The names of the files might differ slightly, for example libname-64.so.0 instead of libname.so.0.

Peter D'Souza

---

