---
title: "KDE/Konqueror question: move files to folder owned by root?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Emily on 2007-05-26
I've looked pretty extensively for an answer to this problem, and everywhere I go, I find the same answer, which doesn't seem to be current.

I installed LAMPP on my Kubuntu machine, which creates a folder, /opt/lampp/htdocs, where you put the things that you want to appear in [http://localhost](http://localhost). 

Unfortunately, I can't put anything there, because all of /opt/ seems to be controlled by root. When I try to move things there, it doesn't ask me to enter my password or anything.

The solution I keep finding is: "Rather than logging out then in again, you can launch Konqueror from the K Menu in Super User mode by selecting System->File Manager - Super User Mode . You will be asked for the root login password but as long as you can provide that Konqueror will be started up with full access privileges to all files on your system." ([http://docs.kde.org/stable/en/kdebase/konqueror/newname.html](http://docs.kde.org/stable/en/kdebase/konqueror/newname.html)) 

Problem: when I got to System, there is nothing called File Manager. 

I've considered moving the files individually using sudo in Konsole, but there are *tons *of them. There has got to be a better solution! Does Super User mode still exist?

---

### Post by Bachstelze on 2007-05-26
If you want to run Konqueror as root :

```
kdesu konqueror
```

I wouldn't recomment it but it's your system so do as you wish...

---

### Post by Happy_Man on 2007-05-26
EDIT: nvm....

---

### Post by aysiu on 2007-05-26
If you don't know where to put *kdesu konqueror*, press Alt-F2

---

### Post by santy_kushwaha on 2007-05-29
the easy solution which i tried and worked fine was login as a root but for that u have to go in /etc/kde3/kde/kdrmc  then on the file change the settings to Allowroot login = false   to   Allowrootlogin =true 
then u will be able to login as root and if u have any trouble email me i can give u more instrutions ok

---

### Post by aysiu on 2007-05-29
> **santy_kushwaha said:**
> the easy solution which i tried and worked fine was login as a root but for that u have to go in /etc/kde3/kde/kdrmc  then on the file change the settings to Allowroot login = false   to   Allowrootlogin =true 
then u will be able to login as root and if u have any trouble email me i can give u more instrutions ok
How is that the easy solution?

```
kdesu konqueror
``` is far handier. And if you use it enough, you can make a keyboard shortcut for the command or a panel launcher for it.

---

### Post by laura_glow on 2007-06-18
> **HymnToLife said:**
> If you want to run Konqueror as root :

```
kdesu konqueror
```

I wouldn't recomment it but it's your system so do as you wish...

why do you not recommend it?

---

### Post by vexorian on 2007-06-18
Well I think it is safe to do it (I do sudo naitulus sometimes) as long as you don't use the sudoed konqueror to:
- delete files on the system.
- lauhch executables
- Enter some webpages from the dark side of the web...

It should be fine to use kdesu konqueror, just do what you mean to do and then close the sudoed konqueror and keep using the other one until you need root access again.

---

