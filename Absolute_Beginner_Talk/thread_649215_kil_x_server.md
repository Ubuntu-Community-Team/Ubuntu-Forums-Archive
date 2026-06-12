---
title: "kil x server"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by hackxxcrack on 2007-12-24
How can i kill x server to use a terminal?

---

### Post by hackxxcrack on 2007-12-24
No one?

---

### Post by hackxxcrack on 2007-12-24
please?

---

### Post by diatribe on 2007-12-24
hit ctrl alt F! to go to terminal

---

### Post by hackxxcrack on 2007-12-24
Yes but the X server is still running...

---

### Post by hackxxcrack on 2007-12-24
no one?

plZ?

---

### Post by Majorix on 2007-12-24
Have you tried killing the Xorg program through System Monitor?

PS: Don't bump your post every 10 mins. It won't get you anywhere.

---

### Post by diatribe on 2007-12-24
when you get to the terminal just use the kill command to kill x and your login manager

---

### Post by overdrank on 2007-12-24
> **hackxxcrack said:**
> no one?

plZ?

Hi and maybe this link will help
[http://www.cyberciti.biz/faq/how-to-stop-xorg-server/](http://www.cyberciti.biz/faq/how-to-stop-xorg-server/)
```
sudo /etc/init.d/gdm stop
```

---

### Post by hackxxcrack on 2007-12-24
Well i cant use anything only a command line... My problem is im trying to install nvidia drivers and it tells me to exit the x server before i start:confused:

---

### Post by Perfect Storm on 2007-12-24
hackxxcrack, don't bump your post so frequently. It's bad etiquette to do so.

Thanks.

regards
A.I. Dude
Ubuntu Forum Staff

---

### Post by hackxxcrack on 2007-12-24
My problem is with logging out of x-server  I'm comfortable enough with the command line to run the installer (sh NVIDIA-Linux-x86-1.0-5336-pkg1.run) but... I have no idea how to exit x-server (as seems to be required to install the driver). I've read that I need to simply "log-off" or hit Ctrl+Alt+BkSp... when I do this, I am brought back to the ubuntu login prompt and, when I login, I'm brought back to the gui. How can I start up in a terminal window? 

thank you

---

### Post by diatribe on 2007-12-24
dude just switch to the terminal like I said and kill gdm, its not complicated

---

### Post by hackxxcrack on 2007-12-24
> **diatribe said:**
> dude just switch to the terminal like I said and kill gdm, its not complicated

How can i kill gdm?

---

### Post by Perfect Storm on 2007-12-24
Check post 9

---

### Post by diatribe on 2007-12-24
kill -9 PID
replace pid with whatever the process id from ps aux|grep gdm is

---

### Post by Majorix on 2007-12-24
> **hackxxcrack said:**
> How can i kill gdm?
As follows:
> **overdrank said:**
> Hi and maybe this link will help
[http://www.cyberciti.biz/faq/how-to-stop-xorg-server/](http://www.cyberciti.biz/faq/how-to-stop-xorg-server/)
```
sudo /etc/init.d/gdm stop
```

---

### Post by selmore on 2007-12-24
Okay, i'm completely new to this distro, so I googled it:

> sudo /etc/init.d/gdm stop

---

### Post by hackxxcrack on 2007-12-24
> **selmore said:**
> Okay, i'm completely new to this distro, so I googled it:

Thanks! i will try now to install my driver

---

