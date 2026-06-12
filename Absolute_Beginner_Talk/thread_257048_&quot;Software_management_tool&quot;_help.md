---
title: "&quot;Software management tool&quot; help"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2006-09-14
Today I downloaded the .deb file for "openTTD".  When opened the installer, it said that I needed the game files from the original game, but I pressed install anyway.  Halfway through the installation I decided to exit because I thought I might need the game files first.  I tried to exit it but it was frozen.  So I restarted the computer and tried to install it again.  Now it says "Only one software management tool is allowed to run at the same time please close the other application e.g. 'Update Manager', 'aptitude', or synaptic first."
grrrrr, plus no dial-up :-(

---

### Post by Najand on 2006-09-14
Use:
```

ps aux > ActiveProcesses

```
to see running processes...
Use```

less ActiveProcesses

```
to see the output and look for any of synaptic, dpkg, apt-get, aptitude, gdebi.
If any of them were available, use the process number:
```

kill <process numeber>

```
to  teminate the process.

---

### Post by yota on 2006-09-14
When a software management tool is executed it locks a file (/var/lib/dpkg/lock) to avoid concurrency. If it fails, it means that another process has already locked it and so it quits.

The 'lsof' (list open files) command can help you to see which process is using the file and so preventing other software management tools to open. (use sudo or be root) 
 
```

root@linbook:/var/lib/dpkg# lsof |grep  /var/lib/dpkg/lock
synaptic  7453       root    7uW     REG        3,3        0    2246464 /var/lib/dpkg/lock

```

Hope this helps.

---

### Post by Najand on 2006-09-14
> **yota said:**
> When a software management tool is executed it locks a file (/var/lib/dpkg/lock) to avoid concurrency. If it fails, it means that another process has already locked it and so it quits.

The 'lsof' (list open files) command can help you to see which process is using the file and so preventing other software management tools to open. (use sudo or be root) 
 
```

root@linbook:/var/lib/dpkg# lsof |grep  /var/lib/dpkg/lock
synaptic  7453       root    7uW     REG        3,3        0    2246464 /var/lib/dpkg/lock

```

Hope this helps.

Great comment. I think I have to add if there is no process using it, just remove the lock file.
```

rm -f /var/lib/dpkg/lock

```

---

### Post by fontenot_1031 on 2006-09-14
Thank you for all of your helpful replies.  I will try them when I get home!:)

---

