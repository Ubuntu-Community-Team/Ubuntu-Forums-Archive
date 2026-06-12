---
title: "[SOLVED] Cant remove Wine"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-10-29
Whenever I try to apt-get remove wine I am presented with this:
```

steve@steve-laptop:~$ sudo apt-get remove wine
[sudo] password for steve:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wine
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 48.6MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 124508 files and directories currently installed.)
Removing wine ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```
Afterwards I notice that wine is sitll there. I think this may be related to the fact that I built wine from source once because I need an older version to support an app I was running.

Can anyone tell what I did wrong?

---

### Post by greenlegacy on 2007-10-29
You might try
```

sudo apt-get purge wine

```

Does wine still run after you use apt-get remove or are there just some spare files sitting around in your .wine folder?

---

### Post by zvacet on 2007-10-29
**home folder>veiw<show hidden files>delete .wine folder**

---

### Post by mevets on 2007-10-29
I tried both suggestions and yes wine does still exist. I can still run applications under wine and check the version number and so.

---

### Post by Inxsible on 2007-10-29
If you installed from source, do you still have the installation directory ?

If yes, then open a terminal, cd to that directory and do```
sudo make uninstall
```

---

### Post by Inxsible on 2007-10-29
If you don't have the installation folder then it might be a bit tedious. Check under all of the following folders and remove every instance of wine manually
```

/usr/local/bin/
/usr/local/bin/
/usr/local/lib/
/usr/local/share/locale/*
/usr/local/share/applications/
/usr/local/share/
/usr/local/include/
/usr/local/lib/pkgconfig/
```

---

### Post by steve.horsley on 2007-10-29
First off, find out where it's hiding. **which wine** will tell you that. There's a good chance that's a symlink to the full application install directory. If you think it's a directory that was created by your manual install, just delete the directory. Home-installs tend to go in /opt or /usr/local whereas the ones that Synaptic installs tend to go in /usr/lib or /usr/share

---

### Post by Inxsible on 2007-10-29
> **steve.horsley said:**
> First off, find out where it's hiding. **which wine** will tell you that. There's a good chance that's a symlink to the full application install directory. If you think it's a directory that was created by your manual install, just delete the directory. Home-installs tend to go in /opt or /usr/local whereas the ones that Synaptic installs tend to go in /usr/lib or /usr/share

#-oD'oh !!! Forgot about the which command. Thanks Steve.

---

### Post by so7777777os on 2007-10-29
> **mevets said:**
> Whenever I try to apt-get remove wine I am presented with this:
```

steve@steve-laptop:~$ sudo apt-get remove wine
[sudo] password for steve:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wine
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 48.6MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 124508 files and directories currently installed.)
Removing wine ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```
Afterwards I notice that wine is sitll there. I think this may be related to the fact that I built wine from source once because I need an older version to support an app I was running.

Can anyone tell what I did wrong?
Wait for expert account for it.......i want to know it ,too

---

### Post by Inxsible on 2007-10-29
> **so7777777os said:**
> Wait for expert account for it.......i want to know it ,too
See steve.horsley 's post above. He has given the solution.```
which wine
```

Remove all instances of wine files/folders from all the locations that are listed with that command.

---

### Post by mevets on 2007-10-29
I went through and deleted all those and then finally purged wine and it finally got rid of its self. thanks for the help.

---

### Post by Inxsible on 2007-10-29
Glad to know. Mark the thread as solved if your questions have been answered. :)

Don't just change the heading of the thread in the first post. It does not reflect the 'Solved' in the search.
Top right corner, Thread Tools --> Mark thread as solved.

---

