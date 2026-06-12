---
title: "Just installed Ubuntu &amp; set it to dual boot, what's next"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by CoolRock on 2006-07-11
I've just installed Ubuntu with Dual boot windows XP. now what i'm facing is... username@computername:~$ ... a command line interface.. how do i proceed to the GUI mode or rather continue getting started? :confused:  Help please. Thanks in advance ;)

---

### Post by diepruis on 2006-07-11
Ubuntu should log you into the GUI automagically. Are there any error messages on screen?

---

### Post by scxtt on 2006-07-11
try **startx**, that'll give you the errors ... unless you installed the server version ;)

---

### Post by CoolRock on 2006-07-12
shucks. i installed the server version -.-"

---

### Post by Kilz on 2006-07-12
> **CoolRock said:**
> shucks. i installed the server version -.-"

Not a problem, type in 
```
sudo aptitude install ubuntu-desktop
```
and it will install a desktop for you.

---

### Post by CoolRock on 2006-07-12
cool. so what's the server and pc difference?

---

### Post by gmatt on 2006-07-12
I think I can answer that :)

Server is very basic and minimizes the amount of threads running on the "server box" at one time as to increase performance when it is requested to perform tasks for its clients. 

On the other hand desktop is your regular ol'fashioned human-friendly easy to use desktop. It can still do the same things as a server but most likey will have alot of whats called overhead (basically bullshit that takes up runtime memory) and will perform poorly.


Hope that helps :)

---

### Post by CoolRock on 2006-07-12
So if I install server plus GUI, will it be better or should i format and go for the PC one?

---

### Post by CoolRock on 2006-07-12
Oh yeah, just to add on, thanks for the replies you all have gave. it has been very useful. :)

---

### Post by SigmaX on 2006-07-12
You'll be fine having installed server, I imagine.  The nice thing about Ubuntu is installing/upgrading packages and system components is simple -- it'll handle the change to desktop Ubuntu seamlessly.

Personally not sure what all won't be installed automatically that woulda been there on the normal Ubuntu install...

> **CoolRock said:**
> Oh yeah, just to add on, thanks for the replies you all have gave. it has been very useful. :)

That's what Linux communities are all about :-).

SigmaX

---

### Post by CoolRock on 2006-07-12
weird. I installed the GUI with the command given in the above post. After 30 mins, all was done and i did a restart.

After i log in, i typed startx in the command line interface and this is what i get instead of the GUI window..

xauth: creating new authority file /home/jason/.serverauth.4940
xauth: creating new authority file /home/jason/.Xauthority
xauth: creating new authority file /home/jason/.Xauthority

X: cannot stat /etc/X11/X (No such file of directory), aborting

giving up.

xinit: Connection refused (errno 111): Unable to connect to X server
xinit: No such process (errno3): Server error.

any ideas..?

---

### Post by scxtt on 2006-07-12
this is what my /etc/X11 directory looks like:

```
:> ll
total 72K
drwxr-xr-x  2 root root 4.0K 2006-07-09 05:13 app-defaults
drwxr-xr-x  3 root root 4.0K 2006-07-09 05:07 config
drwxr-xr-x  2 root root 4.0K 2006-07-09 05:11 cursors
drwxr-xr-x  6 root root 4.0K 2006-07-09 05:07 fonts
lrwxrwxrwx  1 root root    6 2006-07-09 05:08 gdm -> ../gdm
lrwxrwxrwx  1 root root   13 2006-07-09 05:09 X -> /usr/bin/Xorg
drwxr-xr-x  3 root root 4.0K 2006-07-09 05:10 xinit
drwxr-xr-x 10 root root 4.0K 2006-07-09 05:09 xkb
drwxr-xr-x  2 root root 4.0K 2006-05-28 15:35 Xresources
-rwxr-xr-x  1 root root 3.9K 2006-03-20 07:29 Xsession
-rw-r--r--  1 root root 5.2K 2006-07-09 05:46 xorg.conf
-rw-------  1 root root  614 2006-07-09 05:07 Xwrapper.config
drwxr-xr-x  2 root root 4.0K 2006-07-09 05:40 Xsession.d
-rw-r--r--  1 root root  234 2006-03-20 07:29 Xsession.options
-rw-r--r--  1 root root  17K 2005-12-21 20:00 rgb.txt
```maybe you can just make a symbolic link ...

```
sudo ln -s /usr/bin/Xorg /etc/X11/X
```

---

### Post by CoolRock on 2006-07-12
Err.. sorry, but may I ask how do u do a symbolic link?

---

### Post by crystal on 2006-07-12
> Err.. sorry, but may I ask how do u do a symbolic link?
If you dont want to do it from the command line as scxtt suggested, then you should be able to use the graphical file browser: right click on the file's icon, then use 'make link'.

---

### Post by scxtt on 2006-07-12
i added the symbolic link code above - probably while you were typing your question :p

crystal, C.R. is working on getting X going - no GUI presently ...

---

### Post by CoolRock on 2006-07-12
> **scxtt said:**
> i added the symbolic link code above - probably while you were typing your question :p

crystal, C.R. is working on getting X going - no GUI presently ...

Thanks! but I got this instead;

ln: creating symbolic link '/etc/X11/X' to '/usr/bin/Xorg': Permission denied :(

---

### Post by CoolRock on 2006-07-12
> **crystal said:**
> If you dont want to do it from the command line as scxtt suggested, then you should be able to use the graphical file browser: right click on the file's icon, then use 'make link'.

haha, i can't even access the GUI ;)

---

### Post by scxtt on 2006-07-12
you'll have to use sudo, i edited the command ...

---

### Post by majesticturkey on 2006-07-12
Do the same code you did before to make the symbolic link - only add the word "sudo" in front!

Sudo is a command that lets you do something as root (administrator in Linux-speak). It asks for your password to make sure it's really you, and then it should work just fine.

---

### Post by CoolRock on 2006-07-12
placed the leet "sudo" in it. when i startx again, i got this..

xauth: creating new authority file /home/jason/.serverauth.4949
xauth: error in locking authority file /home/jason/.Xauthority
xauth: error in locking authority file /home/jason/.Xauthority
xauth: error in locking authority file /home/jason/.Xauthority

/etc/X11/C is not exectuable
giving up.

xinit: Connection refused (errno 111): Unable to connect to X server
xinit: No such process (errno3): Server error.
xauth: error in locking authority file /home/jason/.Xauthority

---

### Post by scxtt on 2006-07-12
it's not "/etc/X11/C" it's "/etc/X11/X" -- looks like you mistyped ...

and make sure you have a line like this:```
lrwxrwxrwx  1 root root   13 2006-07-09 05:09 X -> /usr/bin/Xorg
```when you do **ls -l /etc/X11** ...

---

### Post by CoolRock on 2006-07-12
oops. it was a typo on the forum post. it's a X instead of a C. So the problem still lies there

---

### Post by scxtt on 2006-07-12
what do you get for the rest of what i posted?

---

### Post by CoolRock on 2006-07-12
total 64
drwxr-xr-x 2 root root 4096 app-defaults
drwxr-xr-x 3 root root 4096 config
drwxr-xr-x 2 root root 4096 cursors
drwxr-xr-x 6 root root 4096 fonts
-rw-r--r-- 1 root root 17371 rgb.txt
lrwxrwxrwx 1 root root 13 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root 4096 xinit
drwxr-xr-x 10 root root 4096 xkb
drwxr-xr-x 2 root root 4096 Xresources
-rwxr-xr-x 1 root root 3911 Xsession
drwxr-xr-x 2 root root 4096 Xsession.d
-rw-r--r-- 1 root root 234 Xsession.options
-rw------- 1 root root 614 Xwrapper.config

---

### Post by nanotube on 2006-07-12
well, i don't know why it's not seeing your X, but since you just installed and have nothing to lose, you might as well try a fresh install with a "desktop" version. :)

---

### Post by scxtt on 2006-07-12
what do you get for:
[indent]ls -l /usr/bin/Xorg[/indent]if you get something like (or nothing at all, as you did below):```
:> ll /usr/bin/Xorg
-rwxr-xr-x 1 root root 1.5M 2006-05-14 22:49 /usr/bin/Xorg
```then go w/ a full install of the desktop or alternate disk ...

---

### Post by CoolRock on 2006-07-12
> **scxtt said:**
> what do you get for:
[indent]ls -l /usr/bin/Xorg[/indent]

ls: /usr/bin/Xorg: No such file or directory

---

