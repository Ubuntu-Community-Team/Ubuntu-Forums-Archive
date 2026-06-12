---
title: "reconnecting mythtv to back end"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-08-06
is there an easy way to reconnect mythtv to the back end? Ever so often I get a message that the server is not running/connected. A simple restart fixes this, but I would like to avoid having to restart the machine. Happens when I use mythweb mostly, but is not something that occurs all the time.

---

### Post by jba6511 on 2007-08-08
anyone

---

### Post by NT4usB on 2007-08-08
type:```
/etc/init.d/mythtv-backend start
```in a terminal.
I made a desktop shortcut so all I got to do is click it whenever I need to start the backend.

---

### Post by jba6511 on 2007-08-09
how did you make a desktop shortcut? newbie here

---

### Post by NT4usB on 2007-08-09
toolbar shortcut actually.
iirc, right click>new shortcut (or whatever Ubuntu calls it) and browse to /etc/init.d/mythtv-backend.

---

### Post by MenZa on 2007-08-09
Another thing you could do is create an alias for it in your .bashrc. Try doing *gedit .bashrc*, scroll to the bottom then write:

```

alias *foobar*='sudo /etc/init.d/mythtv-backend'

```

Replacing 'foobar' with whatever you'd want to run it with. After that, restart your terminal and type 'foobar<enter>' (provided that's what you chose). You could e.g. write startmyth or similar.

---

### Post by jba6511 on 2007-08-10
blake@e6300:~$ sudo /etc/init.d/mythtv-backend start
Password:
mythbackend already running, use restart instead.
blake@e6300:~$ 


BUt when I go to my myth page, I get :

Error

Unable to connect to the master backend at 192.168.1.101:6543.
Is it running?

---

### Post by BillDozer on 2007-08-10
Try **sudo /etc/init.d/mythtv-backend restart** instead.

---

### Post by jba6511 on 2007-08-10
sorry jumped the gun

sudo /etc/init.d/mythtv-backend restart works. Will try the shortcut tonight

---

### Post by jba6511 on 2007-08-10
> **MenZa said:**
> Another thing you could do is create an alias for it in your .bashrc. Try doing *gedit .bashrc*, scroll to the bottom then write:

```

alias *foobar*='sudo /etc/init.d/mythtv-backend'

```

Replacing 'foobar' with whatever you'd want to run it with. After that, restart your terminal and type 'foobar<enter>' (provided that's what you chose). You could e.g. write startmyth or similar.

I did this except I wrote alias startmyth ='sudo .etc.init.d/mythtv-backend restart'

but when I run startmyth from terminal,  I get :

blake@e6300:~$ startmyth
bash: startmyth: command not found

and if I change it to mythbackend instead of mythtv-backend I get
blake@e6300:~$ startmyth
Usage: /etc/init.d/mythbackend {start|stop|restart|force-reload}
blake@e6300:~$ 
Event though I have /etc/init.d/mythbackend restart

---

### Post by jba6511 on 2007-08-11
anyone

---

### Post by jba6511 on 2007-08-13
bump

---

### Post by BillDozer on 2007-08-17
> **jba6511 said:**
> I did this except I wrote alias startmyth ='sudo .etc.init.d/mythtv-backend restart'

but when I run startmyth from terminal,  I get :

blake@e6300:~$ startmyth
bash: startmyth: command not found

and if I change it to mythbackend instead of mythtv-backend I get
blake@e6300:~$ startmyth
Usage: /etc/init.d/mythbackend {start|stop|restart|force-reload}
blake@e6300:~$ 
Event though I have /etc/init.d/mythbackend restart

When you write **startmyth** the system will look for an executable program in you path environment. If you want to execute the program in your local directory you will have to write **./startmyth**. So when you changed the filename to mythbackend the system finds the file /etc/init.d/mythbackend and wants to execute this one.

Hope this helps you.

---

