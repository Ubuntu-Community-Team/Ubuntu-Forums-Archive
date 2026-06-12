---
title: "Stop process, restart comp?"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by veraction on 2006-02-22
I know I can stop a process with Ctrl-Z.
I know I can list all stopped processes with jobs
I know I can start them again by using %[#]
But, can I stop a process, restart computer, then load it back up?

[unrelated] can I use mysql to specify where/what hard drive to store my db on?

---

### Post by Kimm on 2006-02-22
What do you mean?
Do you want it to start automaticly at startup?

Preferences -> Sessions -> Startup Programs -> Add ;)

---

### Post by steve.horsley on 2006-02-22
You cannot stop a process with ^Z, reboot, and have it resume from where it was. Not unless the process is written to save its current progress and resume later, but this is extra specific programming work. Server processes generally try to do it.

I think the database location is specified at inatall time, but check the MySQL documentation.

---

### Post by veraction on 2006-02-23
Ok, thanks. 

A similar question: If I'm ssh'ed into my server, can I start a process then logout so that the process will not quit when I log out?

i.e. Log into server through ssh. *./runprogram &*. Logout & still have it running after logout?

I just tried now and it seems to stop the process/job once I log out - even with using the '&' with the command.

[ currently, I have to use vnc to connect to my server then start terminal & run process. This is a pain cause the computer/workstations I usually use don't have X servers -- so can't use vnc. just plain PuTTY ]

---

### Post by Iowan on 2006-02-23
[QUOTE=veraction]I just tried now and it seems to stop the process/job once I log out - even with using the '&' with the command.
[/QUOTE]How about **fork** - or am I confusing distros?

---

### Post by Kurt` on 2006-02-23
[QUOTE=veraction]A similar question: If I'm ssh'ed into my server, can I start a process then logout so that the process will not quit when I log out?[/QUOTE]
Yes.

For this use "screen".

> screen

After typing that, your screen will appear to clear itself. What happened is you are now in a 'virtual terminal'. Run your program normally, ./whatever . Once it is running, press Ctrl-A, release both, then press D. This will cause you to detach from the virtual terminal, and lets the process run in the background. Now you can logout or do other tasks.

To reconnect to the virtual terminal your program is running in, login and type:

> screen -raAd

That will bring that terminal to the foreground, and resize it to fit your window (not always necessary, but good to know).

Now when you are done with that program, exit it by whatever means you normally do (sending SIGTERM, ctrl+C, etc.), then type:

> exit

to close the virtual terminal.

Not too difficult, but extremely useful. Type "man screen" to see even more cool stuff you can do. ;)

---

### Post by uopjohnson on 2006-02-23
Fantastic!  That is why it is always fn to browse aroudn the forums... you never knwo when you are going to learn something brand new.

---

