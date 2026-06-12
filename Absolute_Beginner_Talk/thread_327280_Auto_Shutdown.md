---
title: "Auto Shutdown?"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by wilberfan on 2006-12-28
Is there a way to have Edgy shutdown automatically--say, at at specific time (11:00pm) or after a specific interval (ie, after 2 hours)?

I had a utility on XP that did that... 

Just curious.

---

### Post by DaBigEd on 2006-12-28
Using the command 

sudo shutdown 20

will tell the computer to shutdown in 20mins.

sudo shutdown -r now 

will tell the computer to restart now

Alternatively you could add an entry to the crontab file (this is kind of like a scheduled tasks folder in XP) to shutdown (or restart the computer) at a daily, weekly or monthly time

There is a GUI available for editing this file, check out
[http://gnome-schedule.sourceforge.net/](http://gnome-schedule.sourceforge.net/)

---

### Post by wilberfan on 2006-12-28
Sweet!!   I'll check it out; thanks so much for the very prompt reply!

:cool:

---

### Post by Drakkor on 2006-12-28
Also , say you want it shutdown at  11:30 Pm , it's     ```
sudo shutdown -h 23:30 &
```    :p

---

### Post by wilberfan on 2006-12-28
> **Drakkor said:**
> Also , say you want it shutdown at  11:30 Pm , it's  sudo shutdown -h 23:30 &  :p

Ooooh!   That's a LOT easier than gnome-schedule seems to be at this point!   (It keeps telling me, "no crontab for [user]"  ](*,)   And it wants a *script* instead of a command?   (A little beyond my noob-ish skills at this exact moment!) 

Say, if you entered the shutdown command for 11:30, but changed your mind before then, is there a way to cancel the command?

Thanks!

---

### Post by Drakkor on 2006-12-28
Yep, to cancel the scheduled shutdown enter
```
sudo shutdown -c
```   :p

---

### Post by Drakkor on 2006-12-28
To know that it's working you should get somethng like this:
drakkor@Ubuntu-Edgy:~$ sudo shutdown -h 23:30 &
[1] 23343
drakkor@Ubuntu-Edgy:~$ 
Broadcast message from drakkor@Ubuntu-Edgy
        (/dev/pts/2) at 20:37 ...

The system is going down for halt in 173 minutes!
:p

---

### Post by wilberfan on 2006-12-29
I HAVE gotten the command to work, but it seems like it doesn't "take" the first time I issue the command:

> wilberfan@AMD64:~$ sudo shutdown -h 22:02 &
[1] 5236
wilberfan@AMD64:~$ Password:


The cursor doesn't even give me a chance to enter my password--it just jumps down to the next line and sits there and blinks...

If I hit 'enter' at that point I get this:
> [1]+  Stopped                 sudo shutdown -h 22:02
wilberfan@AMD64:~$ 

I re-entered the comand and got this:
> [2] 5347
Password:
wilberfan@AMD64:~$     Again, no opportunity to enter my password!

A third (!) attempt got me this:
> wilberfan@AMD64:~$ sudo shutdown -h 22:02
Password:

Broadcast message from dsmoye@AMD64
        (/dev/pts/0) at 21:15 ...

The system is going down for halt in 47 minutes!

Obviously, the "third time's the charm".   Any idea what's going on??  :-k

---

### Post by Drakkor on 2006-12-29
Yeah, I think someone explained it  to me a long time ago, it has something to do with running the terminal in the background or something by appying the & on the end, try sudoing something first, like this: first just ```
sudo ls
```  it should list your home folder contents
then ```
sudo shutdown -h 23:30 &
```   

drakkor@Ubuntu-Edgy:~$ sudo ls
Password:
       Home Folder contents 

drakkor@Ubuntu-Edgy:~$ sudo shutdown -h 23:30 &
[1] 24980
drakkor@Ubuntu-Edgy:~$ 
Broadcast message from drakkor@Ubuntu-Edgy
        (/dev/pts/0) at 21:24 ...

The system is going down for halt in 126 minutes!
sudo shutdown -c
shutdown: Shutdown cancelled
drakkor@Ubuntu-Edgy:~$

---

### Post by wilberfan on 2006-12-29
Dude, your awesomeicity is, well, awesome!    That did the trick... 

(It would be interesting to find out WHY it works that way...  Maybe just penguin-weirdness)

:-D

---

### Post by Drakkor on 2006-12-29
Glad I could help ! :D , I was trying to find my old thread , but I quess it was too old,lol  :p

---

### Post by jdbartlett on 2007-04-13
Does anyone know of a better method to schedule a shutdown *and* return to prompt than the "&" (redirection?) operator (as in, "shutdown -h 1:00 **&**")? Using the "&" method as I have been, I can't logout and log back in from the same terminal afterward--the system waits for the background process to finish! This is because "&" executes the command as a background process in the current session; that process must have completed for logout to be possible (in the example, the background process won't have completed until 1:00 AM, when the system goes down for halt).

The man pages don't mention shutdown not returning to prompt, and other Unix-based systems I've used (such as OS X) do return prompt after a scheduled shutdown has been requested. Any idea why Linux doesn't?

Thanks!

---

### Post by Drakkor on 2007-04-13
The only thing I know is to put sudo shutdown -c  in the terminal to cancel the shutdown. :o

---

### Post by igknighted on 2007-04-13
> **jdbartlett said:**
> Does anyone know of a better method to schedule a shutdown *and* return to prompt than the "&" (redirection?) operator (as in, "shutdown -h 1:00 **&**")? Using the "&" method as I have been, I can't logout and log back in from the same terminal afterward--the system waits for the background process to finish! This is because "&" executes the command as a background process in the current session; that process must have completed for logout to be possible (in the example, the background process won't have completed until 1:00 AM, when the system goes down for halt).

The man pages don't mention shutdown not returning to prompt, and other Unix-based systems I've used (such as OS X) do return prompt after a scheduled shutdown has been requested. Any idea why Linux doesn't?

Thanks!

You could hit ctrl-alt-F1 and run it in tty1, then ctrl-alt-F7 back... then you wouldn't have a terminal open to worry about.

---

### Post by ciscosurfer on 2007-04-14
> **jdbartlett said:**
> Does anyone know of a better method to schedule a shutdown *and* return to prompt than the "&" (redirection?) operator (as in, "shutdown -h 1:00 **&**")? Using the "&" method as I have been, I can't logout and log back in from the same terminal afterward--the system waits for the background process to finish! This is because "&" executes the command as a background process in the current session; that process must have completed for logout to be possible (in the example, the background process won't have completed until 1:00 AM, when the system goes down for halt).

The man pages don't mention shutdown not returning to prompt, and other Unix-based systems I've used (such as OS X) do return prompt after a scheduled shutdown has been requested. Any idea why Linux doesn't?

Thanks!So here's the deal with background operations performed within a terminal session: they only work while the session is open.  In other words, if you background a task or app from within the terminal, and then subsequently close that terminal at a later time (or any time), the process of backgrounding that app or task officially halts and ceases to exist -- an annoyance for sure.  

One way around this is to read the following to brush up on your cron(tab)(ulous) skills. The Ubuntu Document Storage Facility goes into a brief discussion on how you can work with cron files via your cron tab file and manipulate it via the command line.  It also points out the aforementioned GUI apps **Gnome Schedule** and a new one, **kcron** (KDE-based but runs perfectly well within Gnome -- be aware though that installing Kcron, if you don't have other KDE apps already installed, will pull kde-base files over as well other files necessary for the correct functioning of **kcron**.  This isn't a message to discourage or frighten you, it's just a handy warning and reminder).  I've used both in the past and they are both great at working with cron.  Enjoy!

Link to UDSF: [http://doc.gwos.org/index.php/Cron_GUI](http://doc.gwos.org/index.php/Cron_GUI)
Link to Gnome Schedule: [http://gnome-schedule.sourceforge.net/](http://gnome-schedule.sourceforge.net/)
And **kcron** is in the repositories.

EDIT: igknighted's suggestion is also completely sound, and I sometimes do this also (I forgot to mention it).  Good thought igknighted!

---

### Post by jdbartlett on 2007-04-14
Thanks for the suggestions and explanations, igknighted and ciscosurfer. I was hoping to avoid setting up a cron job by instead using shutdown's own time argument--it seemed like a more graceful solution, but I guess it just doesn't work as I expected. I expected a scheduled shutdown to register as a sort of daemon or background service until shutdown time rather than becoming a foreground process and stealing prompt. I guess no system's perfect, eh?

Since I usually call shutdown from the command line via SSH, I think I'll probably set a scheduled task as you suggested, ciscosurfer, though I'll research igknighted's suggestion also. Thanks again to you both.

---

