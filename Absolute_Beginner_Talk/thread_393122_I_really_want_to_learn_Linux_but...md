---
title: "I really want to learn Linux but.."
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by donamai on 2007-03-25
Hey community!

I really want to learn Linux but I am having such a hard time with the system that I don't know. I may take some time for me to get used to it. 

why?

Well, it was fine when I first installed it now it is getting slow. Maybe I am messing with something I shouldn't. Anyway, I might take some time to pick up the good stuff.

I have a basic question. When I use the gksudo gedit /etc/X11/xorg.conf command to open my xorg fle, the file comes up empty. Yup! zero on inside the xorg. 

I have restored it with another command but so far nothing.

What do you guys guess it is?

Thank you!

---

### Post by taurus on 2007-03-25
What's the output of this command from a terminal?

```
ls -la /etc/X11
```

---

### Post by kelbizzle on 2007-03-25
man...I dunno I copied the same command and pasted into a terminal window my xorg.conf is fine. I tried a google search for "empty xorg.conf". and the very first link the guy was leaving out the / before /etc/X11/xorg.conf. Try copy and pasting your command.

---

### Post by donamai on 2007-03-25
Hey taurus! thanx for checking

This is what I get from the command  in the terminal
```

total 100
drwxr-xr-x   9 root root  4096 2007-03-25 07:55 .
drwxr-xr-x 102 root root  4096 2007-03-25 07:54 ..
drwxr-xr-x   2 root root  4096 2006-10-25 06:39 app-defaults
drwxr-xr-x   2 root root  4096 2006-10-25 06:37 cursors
-rw-r--r--   1 root root    14 2006-10-25 06:39 default-display-manager
drwxr-xr-x   3 root root  4096 2006-10-25 06:28 fonts
lrwxrwxrwx   1 root root     6 2007-03-24 07:41 gdm -> ../gdm
-rw-r--r--   1 root root 17371 2006-06-11 20:40 rgb.txt
lrwxrwxrwx   1 root root    13 2007-03-24 07:41 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2006-10-25 06:31 xinit
drwxr-xr-x  10 root root  4096 2006-10-25 06:28 xkb
-rw-r--r--   1 root root  4071 2007-03-24 14:22 xorg.conf~
-rw-r--r--   1 root root  5165 2007-03-24 12:52 xorg.conf.20070324125250
-rw-r--r--   1 root root  4065 2007-03-24 13:03 xorg.conf.20070324130304
-rw-r--r--   1 root root  4065 2007-03-24 13:12 xorg.conf.20070324131241
-rw-r--r--   1 root root  4065 2007-03-24 13:15 xorg.conf.20070324131557
drwxr-xr-x   2 root root  4096 2006-10-20 11:02 Xresources
-rwxr-xr-x   1 root root  4157 2006-10-12 08:33 Xsession
drwxr-xr-x   2 root root  4096 2007-03-24 16:04 Xsession.d
-rw-r--r--   1 root root   265 2006-06-11 20:40 Xsession.options
-rw-------   1 root root   614 2006-10-25 06:26 Xwrapper.config
```


I am tring to change the resolution of my screen because it is crawling as a scroll up or down. I see the screen flicker and then going back to the same settings. Frustrating!

Anyway, thanx for  the help!

---

### Post by kelbizzle on 2007-03-25
well.. theres your problem. you don't have one. :-P cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf

---

### Post by taurus on 2007-03-25
Yip.  You don't have /etc/X11/xorg.conf.  However, you have a backup file (a few, actually) so from a terminal, do

```
sudo cp /etc/X11/xorg.conf~  /etc/X11/xorg.conf
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by kelbizzle on 2007-03-25
.

---

### Post by donamai on 2007-03-25
Hey! thanx a lot!

Kell, do I have to run that in the terminal? It seems those commands are a little different.

By the way, where can I get a book or a reference to learn Linux commands?
:guitar:

---

### Post by Lanky Juggler on 2007-03-25
There are tons of books on linux (various distros) in stores like barnes and noble and borders, for instance.

But going to cheap and easy route, there are lots of websites that give a short introduction to what some of the basic commands do and how things tend to work.
[http://www.linux.org.mt/node/49#N10074](http://www.linux.org.mt/node/49#N10074) is a little longwinded on the basics.

Beyond that, there are some "dictionaries" of terminal commands.
[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

And the Linux Documentation Project has tons of information from guides to man pages, so i bet you could find something useful there:  [http://www.tldp.org/](http://www.tldp.org/) 


Yes, you do want to run Kel's commands in the terminal.  gksudo is a lot like sudo, it still grants root powers, but you use it for more complex (often graphical) applications that might need to go back and keep getting root privelages.  For instance, you might use "sudo cp" to copy something from a root-controlled folder, but to give gedit root privelages until you close it you would use "gksudo gedit".

Keep trying on linux, though.  We're here to help, and its all a matter of learning how to do the things you want to do in a slightly different way, like switching media players.

---

