---
title: "wine doesnt seem to work"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by etomic13 on 2007-09-02
I got a new box and I tried to install wine first in synaptic and I still can run exe's. I used sudo apt-get and still doesnt work. I really dont know whats wrong.

---

### Post by Outrunner on 2007-09-02
Yep, we don't know what's wrong either. I, for one, don't understand what you're trying to do. Do you want to install WINE?

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
```

```
sudo aptitude update && sudo aptitude install wine
```

Or do you want to run an .exe file?
```

wine filename.exe
```

---

### Post by etomic13 on 2007-09-02
sorry tired, supposidly wine is installed but it isnt working.

---

### Post by etomic13 on 2007-09-02
I tried the codes you suggested and they seemed to run fine until I tried to execute again.
taylor@taylor-desktop:~$ wine QuemuInstall-0.7.2.exe
wine: could not load L"c:\\windows\\system32\\QuemuInstall-0.7.2.exe": Module not found
taylor@taylor-desktop:~$

---

### Post by Outrunner on 2007-09-02
Are you in the working directory of QuemuInstall-0.7.2.exe? For example, if it is located on your Desktop, then you have to cd(change dir) to Desktop

```
cd ~/Desktop
```

Or if it's on a CD
```

cd /media/cdrom0
```

---

### Post by Deedlit on 2007-09-02
I have that exact same problem.

deedlit@Eeyore:~$ wine hstinst.exe
wine: could not load L"c:\\windows\\system32\\hstinst.exe": Module not found
deedlit@Eeyore:~$ 


I am totally at a loss as to how to make this dumb program work.

---

### Post by Outrunner on 2007-09-02
> **Deedlit said:**
> I have that exact same problem.

deedlit@Eeyore:~$ wine hstinst.exe
wine: could not load L"c:\\windows\\system32\\hstinst.exe": Module not found
deedlit@Eeyore:~$ 


I am totally at a loss as to how to make this dumb program work.

Do a ```
ls -l
```

and post the output here.

---

### Post by Deedlit on 2007-09-02
okay, here's what I got:

deedlit@Eeyore:~$ ls -l
total 4564500
-rw-r--r-- 1 deedlit deedlit    5700255 2007-08-30 01:00 01 Makka na Chikai.mp3
drwxr-xr-x 3 deedlit deedlit       4096 2007-01-14 03:38 azureus
drwxr-xr-x 3 deedlit deedlit       4096 2007-09-01 00:13 Azureus Downloads
drwxr-xr-x 2 deedlit deedlit       4096 2007-08-30 15:00 Bit Torrents
drwxr-xr-x 2 deedlit deedlit       4096 2007-09-01 01:51 Desktop
lrwxrwxrwx 1 deedlit deedlit         26 2006-07-31 19:27 Examples -> /usr/share/example-content
drwxr-xr-x 2 deedlit deedlit       4096 2007-08-01 21:58 firefly
drwxr-xr-x 2 deedlit deedlit       4096 2007-08-30 15:06 Gaim Icons
drwxr-xr-x 2 deedlit deedlit       4096 2007-08-11 12:06 Manuals
drwxr-xr-x 4 deedlit deedlit       4096 2007-08-09 21:03 Music
-rw------- 1 deedlit deedlit         20 2007-08-25 18:40 nano.save
drwxr-xr-x 2 deedlit deedlit       4096 2007-08-09 19:30 Photos
drwxr-xr-x 2 deedlit deedlit       4096 2007-07-26 10:05 Robin Hood
drwxr-xr-x 2 deedlit deedlit       4096 2007-08-27 11:18 Sounds
drwxr-xr-x 2 deedlit deedlit       4096 2007-08-27 19:53 St_Luminous 1-13
-rw-r--r-- 1 deedlit deedlit 4663711232 2007-08-30 06:30 [T-N]Densha Otoko.tar
-rw-r--r-- 1 deedlit deedlit          0 2007-08-11 12:15 wget-log
deedlit@Eeyore:~$

---

### Post by Outrunner on 2007-09-02
Well, here's the problem, there's no hstinst.exe in your /home directory. Maybe you should consider reading my post about working directories?

> Are you in the working directory of QuemuInstall-0.7.2.exe? For example, if it is located on your Desktop, then you have to cd(change dir) to Desktop

```
cd ~/Desktop
```

Or if it's on a CD
```

cd /media/cdrom0
```

---

### Post by Deedlit on 2007-09-02
Okay, here's what I got:

deedlit@Eeyore:~/Desktop$ ls -l
total 10908
-rw-r--r-- 1 deedlit deedlit 11149800 2007-09-01 01:51 hstinst.exe
deedlit@Eeyore:~/Desktop$

---

### Post by Outrunner on 2007-09-02
Well, there you go, it's om the Desktop. Now simply run ```
wine hstinst.exe
```

---

### Post by Deedlit on 2007-09-02
It started up, gave me an error. Could the problem be it asks me what file to put in into and its a c\program files...... pathway?

---

### Post by Deedlit on 2007-09-02
the actual error is 0x80020005 and then says set up will now terminate

---

### Post by meindian523 on 2007-09-02
Bot exactly same,but wine works with some rograms and doesn't with others....

eg:

```
easwarh@l1nuxr0cks:~$ wine /media/Disk-F/games/x24gam~1/bbchess.exe 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".


```
works but
```

easwarh@l1nuxr0cks:~$ wine /media/Disk-C/Documents\ and\ Settings/CEH/Desktop/Unused\ Desktop\ Shortcuts/LimeWireWin.exe 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
easwarh@l1nuxr0cks:~$ 

```

doesn't.That is the game bbchess works but the setup for Limewire Windows doesn't though the same error is shown......

---

