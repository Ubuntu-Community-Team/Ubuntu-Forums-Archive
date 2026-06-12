---
title: "[SOLVED] Kde programme problems in gutsy"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-11-02
Hi,
Whenever I wish to start a kde application like k3b or kdenlive it says Dcopserver programme is not running.
However the application runs when I run it with sudo
Any adjustment needed here?
Any configuration required to be done?
Thanks for any help.

---

### Post by gupta_sumesh63 on 2007-11-03
BUMP!!!!!
:confused:

---

### Post by moocow1452 on 2007-11-03
Bump Seconded. Having the same problem with Amarok. I get five messages, saying that "dcopserver" isn't running.

---

### Post by moocow1452 on 2007-11-03
[IMG]http://i7.photobucket.com/albums/y281/YoshiMan1452/Screenshot-amarok-KDialog.png[/IMG]
[IMG]http://i7.photobucket.com/albums/y281/YoshiMan1452/Screenshot-DCOPcommunicationserrorK.png[/IMG]
[IMG]http://i7.photobucket.com/albums/y281/YoshiMan1452/Screenshot-DCOPcommunicationserrorA.png[/IMG]
[IMG]http://i7.photobucket.com/albums/y281/YoshiMan1452/Screenshot-DCOPcommunicationserr-1.png[/IMG]
[IMG]http://i7.photobucket.com/albums/y281/YoshiMan1452/Screenshot-Error-Amarok.png[/IMG]
[IMG]http://i7.photobucket.com/albums/y281/YoshiMan1452/Screenshot-kbuildsycoca-KDialog.png[/IMG]

Error Prompts in the order they show up.

---

### Post by schorsch on 2007-11-03
What is the output of the following commands:
```
ls -l /home/joey
ls -l /home/joey/.kde
ls -l /home/joey/.kde/share
ls -l /home/joey/.kde/share/config
```

---

### Post by moocow1452 on 2007-11-03
ls -l /home/joey=
```
total 580
drwxr-xr-x  3 joey joey   4096 2007-11-03 13:57 Desktop
drwxr-xr-x  5 joey joey   4096 2007-10-21 14:59 Documents
drwxr-xr-x  2 joey joey   4096 2007-10-18 19:06 Downloads
drwxr-xr-x  2 joey joey   4096 2007-10-03 23:18 dwhelper
lrwxrwxrwx  1 joey joey     26 2007-09-23 12:27 Examples -> /usr/share/example-content
-rw-r--r--  1 joey joey 542519 2007-10-22 18:26 Firefox_wallpaper.png
drwxr-xr-x  2 joey joey   4096 2007-10-19 23:48 Music
drwxr-xr-x  2 joey joey   4096 2007-10-19 23:48 Pictures
drwxr-xr-x  2 joey joey   4096 2007-10-19 23:48 Public
drwxr-xr-x 11 joey joey   4096 2007-10-27 13:46 sunbird
drwxr-xr-x  2 joey joey   4096 2007-10-19 23:48 Templates
drwxr-xr-x 13 joey joey   4096 2007-11-03 14:29 thunderbird
drwxr-xr-x  2 joey joey   4096 2007-10-21 19:00 Videos

```

ls -l /home/joey/.kde - Permission Denied
sudo ls -l /home/joey/.kde=
```
total 4
drwx------ 3 root root 4096 2007-09-23 17:37 share

```

sudo ls -l /home/joey/.kde/share
```
total 4
drwx------ 2 root root 4096 2007-09-23 17:37 config

```

sudo ls -l /home/joey/.kde/share/config
```
total 4
-rw------- 1 root root 35 2007-09-23 17:37 kdeglobals
```

What's it mean?

---

### Post by schorsch on 2007-11-03
You've managed to screw up the permissions of the .kde folder in your home directory so that only root is able to write to it.
```
sudo chown -R joey:joey /home/joey/.kde
```should fix this problem

---

### Post by moocow1452 on 2007-11-03
Wow, I have been trying to fix this forever! Thanks!

---

### Post by schorsch on 2007-11-03
Well, glad to hear that it seems to work for you now. Could you please mark this thread as solved?

---

### Post by maestrobwh1 on 2007-11-03
> **schorsch said:**
> You've managed to screw up the permissions of the .kde folder in your home directory so that only root is able to write to it.
```
sudo chown -R joey:joey /home/joey/.kde
```should fix this problem

Yep.  I sometimes get this and don't know how it happens.  I generally just open up krusader (file manager) in root mode, select my home directory, change the owner to myself and slelect "recurse directories"  There might be reasons why the whole home should not be me as a user, so you might what to just do the hidden .kde directory as suggested here.

The terminal method makes sense, but I tend to miss characters and have to type it in 3 times:-)

---

### Post by moocow1452 on 2007-11-03
I would, but the original poster has to.

---

### Post by schorsch on 2007-11-03
@moocow1452: Uhm, sorry, I forgot .....

@maestrobwh1: This can happen when you start a graphical application via "sudo". So use "sudo" when doing administrative tasks in a terminal session and use "gksu" oder "kdesu" when starting graphical applications in administrative mode.

---

### Post by gupta_sumesh63 on 2007-11-04
Thanks for the replies. That worked for me.

---

