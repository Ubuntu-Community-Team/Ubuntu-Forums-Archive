---
title: "[SOLVED] Uninstall Pidgin"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by z|x on 2008-01-20
I think i messed up by trying to install pidgin over and over again. I want to do a clean reinstall but i am not able to uninstall pidgin from my system.

I uninstalled it from the package manager but i still find it in the menu and it still runs like as if it were installed.

Please help.

Thanks

---

### Post by Malta paul on 2008-01-20
Hi, you could try going to Synaptic Package Manager, search Pidgin, then right ckick and mark for complete removal, apply. Then do a clean reinstall.
Good luck:)

---

### Post by Arthur Archnix on 2008-01-20
Paste this in a terminal:
```
sudo apt-get remove --purge pidgin
```

---

### Post by z|x on 2008-01-20
I tried doing both right now, but pidgin's still there

---

### Post by Christmas on 2008-01-20
Did you compile Pidgin from source? In that case go to the directory where you compiled Pidgin and type 'sudo make uninstall'. What does 'whereis pidgin' command say?

---

### Post by z|x on 2008-01-20
> **Christmas said:**
> Did you compile Pidgin from source? In that case go to the directory where you compiled Pidgin and type 'sudo make uninstall'. What does 'whereis pidgin' command say?
i first installed it using a .deb. It had some problem so i installed from source. that had some problem too, so i installed from the repos. neither of them worked properly. I managed to uninstall from the package manager and the one that i compiled, but its still there.

Here's what I get:

```
ian@wanderer:~$ whereis pidgin
pidgin: /usr/local/bin/pidgin /usr/local/lib/pidgin

```

---

### Post by zipperback on 2008-01-20
What version of Ubuntu are you working?

- zipperback
:popcorn:

---

### Post by z|x on 2008-01-20
> **zipperback said:**
> What version of Ubuntu are you working?

- zipperback
:popcorn:
2.3.1

---

### Post by Christmas on 2008-01-20
Well if it's in /usr/local/bin then it's the one you installed by compiling it. You can do the following: Compile it once more then don't delete the directory in which you issued the command 'sudo make install', and type 'sudo make uninstall'. It should remove it properly this time. If you installed it from a .deb with 'sudo dpkg -i pidgin-whatever.deb' uninstall it using 'sudo dpkg -r pidgin'. One of these should work.

---

### Post by z|x on 2008-01-20
> **Christmas said:**
> Well if it's in /usr/local/bin then it's the one you installed by compiling it. You can do the following: Compile it once more then don't delete the directory in which you issued the command 'sudo make install', and type 'sudo make uninstall'. It should remove it properly this time. If you installed it from a .deb with 'sudo dpkg -i pidgin-whatever.deb' uninstall it using 'sudo dpkg -r pidgin'. One of these should work.
Ah thanks man!! It worked!!

Ubuntu's support is simply great!!

---

### Post by Arthur Archnix on 2008-01-20
You can help future users with similar problems by marking your thread as solved. Use the thread tools button near the top.

---

### Post by genbuntu on 2008-02-04
ah.. Yess , this thread helped me get rid off my pidgin 2.2 and install pidgin 2.3.1 successfully. :)

---

