---
title: "[SOLVED] By the way: How do i uninstall something?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by thomas7.10 on 2008-03-16
I never got in touch with that problem before. But now it is here: How do i uninstall something?

I was using BOINC with the ABC - project but now i was looking in the gnome-system-monitor and it turned out that the ABC-project had two processes open and that came up to 100% processor usage.

So i used this installation tool in programs to get rid of BOINC. It seemed to work but there a still files left in /etc/lib/boinc-client/ and the ABC-project process is still running.

So how can i really get rid of that. Is there a nice way like using one command or do i have to erase everything by hand?

---

### Post by Oldsoldier2003 on 2008-03-16
> **thomas7.10 said:**
> I never got in touch with that problem before. But now it is here: How do i uninstall something?

I was using BOINC with the ABC - project but now i was looking in the gnome-system-monitor and it turned out that the ABC-project had two processes open and that came up to 100% processor usage.

So i used this installation tool in programs to get rid of BOINC. It seemed to work but there a still files left in /etc/lib/boinc-client/ and the ABC-project process is still running.

So how can i really get rid of that. Is there a nice way like using one command or do i have to erase everything by hand?

```
sudo apt-get purge boinc boinc-manager
```

---

### Post by scragar on 2008-03-16
```
sudo apt-get --purge autoremove boinc boinc-manager
```but only if your running gutsy, not sure if it will work in fiesty

---

### Post by wesley_of_course on 2008-03-16
What program did you try  to use for removal of the packages ?

Synaptic Package Manager is one way , also sudo apt-get remove blah blah,(insert package name).

---

### Post by thomas7.10 on 2008-03-16
I don't know the name it is the last one in Programs. I can't imagine it is called "Add/remove Applications application" 

It has uninstalled a port of it at least so that "sudo apt-get --purge autoremove boinc boinc-manager" can't find something.

```

thomas@thomas-desktop:/var/lib/boinc-client$ sudo apt-get --purge autoremove boinc boinc-manager
[sudo] password for thomas:
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
E: Kunde inte hitta paketet boinc <-- means: "Couldn't find the package boinc"

```

but the ABC process is still runinng.

---

### Post by Oldsoldier2003 on 2008-03-16
> **thomas7.10 said:**
> I don't know the name it is the last one in Programs. I can't imagine it is called "Add/remove Applications application" 

It has uninstalled a port of it at least so that "sudo apt-get --purge autoremove boinc boinc-manager" can't find something.

```

thomas@thomas-desktop:/var/lib/boinc-client$ sudo apt-get --purge autoremove boinc boinc-manager
[sudo] password for thomas:
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
E: Kunde inte hitta paketet boinc <-- means: "Couldn't find the package boinc"

```

but the ABC process is still runinng.

ps aux and kill -9  any boinc processes

---

### Post by thomas7.10 on 2008-03-16
That command didn't work but i could kill it with ps -afx and the number but how do i know that this isn't a cron job? How can i list all cron jobs?

---

### Post by Oldsoldier2003 on 2008-03-16
> **thomas7.10 said:**
> That command didn't work but i could kill it with ps -afx and the number but how do i know that this isn't a cron job? How can i list all cron jobs?

crontab -l

---

### Post by thomas7.10 on 2008-03-16
Ok there are no crontabs neither for my user name nor for root.

Isn't cron the equivalent to autostart on windows?

---

### Post by Oldsoldier2003 on 2008-03-16
> **thomas7.10 said:**
> Ok there are no crontabs neither for my user name nor for root.

Isn't cron the equivalent to autostart on windows?

no cron is the equivalent of task scheduler.

---

### Post by thomas7.10 on 2008-03-16
Ok good to know and what is the autostart? 

I thought that i was able to kill the jobs from abc but they are appearing again and again every time i kill that job a new one starts.

Is it possible that all this happens on purpose?

---

### Post by thomas7.10 on 2008-03-16
ok got it solved there is something called boinc-client. so it wasn't about the boinc-manager. 

I think i got it deleted now with ```
 sudo apt-get --purge autoremove boinc-client
```

Thanks for your help anyway

---

