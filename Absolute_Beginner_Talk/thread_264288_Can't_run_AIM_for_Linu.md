---
title: "Can't run AIM for Linu"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2006-09-24
Hello,

I just installed Aim 1.5.286 for Linux. I installed the executable file in /usr/local/bin and the library files in /usr/local lib.

I type in /usr/local/bin/aim in the terminal to run the program and I get this message.

---------------------------------------------------------------
andrew@andrew-desktop:~$ /usr/local/bin/aim
/usr/local/bin/aim: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
andrew@andrew-desktop:~$
----------------------------------------------------------------

What am I doing wrong?

---

### Post by GuitarHero on 2006-09-24
It seems you are missing a dependency.  Search for it in synaptic and try installing it.

The better advice would be to just use gaim, most find it works better.

---

### Post by andrew222 on 2006-09-24
Thank you for the reply. How would I do a search for the named file in Synaptic? 

I will look for Gaim, it sounds good for now.

Thanks again,

Andrew

---

### Post by nts on 2006-09-24
Use Gaim its wicked, however i should get the dependency anyway, you might need it later.

---

### Post by petit.padavoine on 2006-09-24
To get to Synaptic, just ```
synaptic
``` in Terminal. Once in there, use search or just start typing the first letters of the package name to just scroll down to it.

---

### Post by andrew222 on 2006-09-24
Thank you for the tips, I successfully installed Gaim. This is my second week of using Linux. I am getting more and more used to the commands and think it is a more proficient OS than Windows. I like the fact that I am using a great forum for the usage of open source software.

~Andrew

---

### Post by Brunellus on 2006-09-24
> **andrew222 said:**
> Thank you for the tips, I successfully installed Gaim. This is my second week of using Linux. I am getting more and more used to the commands and think it is a more proficient OS than Windows. I like the fact that I am using a great forum for the usage of open source software.

~Andrew
GAIM should already have been installed by default in a standard Ubuntu install.  Incidentally, I note that AIM for Linux is probably abandonware:  AOL hasn't shown any desire to maintain it since maybe 2001 or so.  This is one of the instances where the Free Software alternative is actually better than the version allegedly supported by the vendor.

For general program installation help and tips, please see

[http://wiki.ubuntu.com/InstallingSoftware](http://wiki.ubuntu.com/InstallingSoftware)

---

### Post by LookTJ on 2006-09-24
> **nts said:**
> Use Gaim its wicked, however i should get the dependency anyway, you might need it later.
for AIM? none of the users are online :|

---

