---
title: "SSH Question"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by CBribiescas on 2008-04-08
I'm still fairly new when it comes to linux/ubuntu, but I know how to ssh into my desktop and run applications with x11 and everything, however, what I don't know how to do, or even know if its possible, is can I ssh into my desktop, tell it to do something (run a program, download something) and then log off?  I know i can if i leave the ssh session open, but there has got to be a way for me to run applications remotely and just let them run and check on them periodically.  I think its probably simple, but i just don't know how to do it.  Can anybody help?

---

### Post by Jussi Kukkonen on 2008-04-08
You're looking for screen. 

I'll use *top* as the example program: Start your program with *"screen top"* and then detach from it by pressing "ctrl-a d". Now you can open another terminal and run *"screen -r"* to resume screen on that terminal .

---

### Post by mootah on 2008-04-08
If I understand you correctly, and you're looking to use your X Desktop via SSH, this tutorial should help you out: [http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

To use an SSH console (shell login) to download something while not at your computer, try this in the SSH window:

wget URL-of-target
Like, wget [http://www.somehostname.com/files/good1.zip](http://www.somehostname.com/files/good1.zip)

To check on a program from a remote SSH console login you can do:

ps aux | grep PROGRAM-NAME

This will just let you know if it's still running basically, so if you left something on and want to make sure it's still going you can do that. Another helpful command just to get a quick idea what's running on there is 'top'.

Good luck!

---

### Post by jseiser on 2008-04-08
your best bet is to run screen on your desktop.  then from work or w/e you are, ssh into the desktop, reattach screen, and say, use wget to dowload a torrent, and since rtorrent is already running in screen, that dvd you want to watch when you get off will be sitting there, ready :)  -- if you learn screen, htop, mc, rtorrent, elinks - you will be able to monitor the system, move/create/rm files, download files, surf the web etc.  There is nothing you cant do with screen+terminal prog

---

### Post by CBribiescas on 2008-04-09
Cool.  It sounds like screen is exactly what i was looking for.  I'll look into the man pages to see how to use it.  Thanks :-D.

---

### Post by The Cog on 2008-04-09
Screen is excellent. You can leave loads of things running, disconnect, comoe back later and pick up, and the screens are buffered so you see what was there before.

If you just want to launch something and disconnect, and never check up on it then you can put it in the background (launch it with an & symbol at te end of the launch command) and then use the command **disown** whch makes it immune to your logout/disconnection.

---

### Post by CBribiescas on 2008-04-09
Wait, so with screen can i leave somethign running while i log off? I can see how i could do that with disown.  But if i disown something, and it has to print to a terminal, what happens when i log off?

---

### Post by The Cog on 2008-04-10
If you disown it then it has no terminal. If you originally launched it with output redirected to a log file it will continue logging of course. But it's really a "Fire and forget" tactic.

Screen emulates one or more VT terminals (you can run multiple sessions inside screen). You can log off or discnnect, reconnect later, re-attach to screen and see all the VT displays still there as though you just stepped out for a coffee. It is worth remembering if you are doing anything remotely that must not be interrupted by a network fault for instance.

---

### Post by hyper_ch on 2008-04-10
a short introductory to screen:  [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

Btw, if you want to run multiple screen sessions it's good to give the sessions a name... much easier then the tty pid thing that you automatically get ;)

---

