---
title: "Kill screensaver from terminal"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Miguellint on 2007-03-08
Hi all...I'm just messing about with the terminal. Some advice please. (Xubuntu 6.10)

I want to stop my screensaver from the terminal command line. I use......

ps aux

to get a list of active processes. (Is this the same as Menu/System/Process Manager in Xfce?)

Then I find the PID of xscreensaver (e.g 6455) and then I use...

kill 6455 

to stop the screensaver.

If one of you knowledgeable types found yourself in the terminal and needed to stop your screensaver would you do what I've just described. Or is there a more accepted way of killing processes from the terminal.

Many Thanks
Miguel

---

### Post by 23meg on 2007-03-08
Instead of killing its process, you can use *xscreensaver-command* to tell *xscreensaver* to deactivate gracefully. 

```
xscreensaver-command -deactivate
```

---

### Post by go2dell on 2007-03-08
That will work fine, with the general caveat that you'd better be certain about what process you're killing.  Death is immediate, and can have undesired side-effects. ;-)

**edit:**  On second thought, if you're running Xubuntu, are you sure you want to eat cycles with something as useless as a screensaver?  They haven't been particularly useful on CRTs for at least 10 years, and they are completely worthless on an LCD.  I would suggest going into Settings Manager and either turning the screensaver off or setting it to Blank Screen Only.  If your display is capable of power management, such as an LCD or newer CRT, then leave Power Management turned on; otherwise turn that off, too.

---

### Post by 23meg on 2007-03-08
Killing a process is far from ideal when it presents an interface for making itself terminate. And in this case, I think the user just wants to deactivate the screensaver (i. e. emulate mouse activity), not kill the screensaver daemon altogether; the latter would cause the screensaver functionality not to work in the rest of the session. If that was what they wanted, there's also a way to do it via xscreensaver-command: ```
xscreensaver-command -exit
```

---

### Post by Miguellint on 2007-03-08
Thanks all for the replies.

That "process hyphen command space hyphen argument" thing looks interesting. Something new to play around with. Is there a name for that that I can search on.

Regards
Miguel

---

### Post by kinson on 2007-03-08
I'm probably asking a stupid question here, but isn't a screensaver supposed to go off when you hit a key or move the mouse?

I get what you guys are trying to do, but woulding typing into the terminal stop the screensaver? Obviously I'm missing something here, but I'd kinda like to know what it is, eheh :p

Cheers,
Kinson

---

### Post by 23meg on 2007-03-08
> **Miguellint said:**
> 
That "process hyphen command space hyphen argument" thing looks interesting. Something new to play around with. Is there a name for that that I can search on.


It's not a generic thing that applies to all processes; xscreensaver-command is a helper application that comes with xscreensaver which lets you control it via command line arguments. It's specific to xscreensaver. gnome-screensaver has something similar called gnome-screensaver-command. Other applications may or may not have helper applications, DBUS interfaces or direct command line arguments that do similar things.

My point was, if a certain application has such a feature, it's better to use that, rather than kill it. And as I pointed in my last post, the functional outcome may be different as well.

For more information on the usage of xscreensaver-command, see its manual page. ```
man xscreensaver-command
```

---

### Post by go2dell on 2007-03-08
> **23meg said:**
> Killing a process is far from ideal when it presents an interface for making itself terminate. And in this case, I think the user just wants to deactivate the screensaver (i. e. emulate mouse activity), not kill the screensaver daemon altogether; the latter would cause the screensaver functionality not to work in the rest of the session. If that was what they wanted, there's also a way to do it via xscreensaver-command: ```
xscreensaver-command -exit
```

Killing a process is *never* ideal, but often necessary or there wouldn't be a command specifically designed for doing it.

Considering the user is using a terminal and typing, simply deactivating the screensaver doesn't make sense; hitting a key to type in the terminal deactivates the screensaver.  Trying to kill the screensaver usually means the screensaver has gone berzerk, which happens frequently on my Xubuntu systems.  Ditto switching to terminal, but that's another thread entirely. :lol:

---

### Post by 23meg on 2007-03-08
> **kinson said:**
> I'm probably asking a stupid question here, but isn't a screensaver supposed to go off when you hit a key or move the mouse?

I get what you guys are trying to do, but woulding typing into the terminal stop the screensaver? Obviously I'm missing something here, but I'd kinda like to know what it is, eheh :p


You may use a virtual terminal or a remote one to stop a local or remote screensaver. Or use xscreensaver-command in a script to automate a task.

---

### Post by kinson on 2007-03-08
> **23meg said:**
> You may use a virtual terminal or a remote one to stop a local or remote screensaver. Or use xscreensaver-command in a script to automate a task.


Lol, I get it now. Good point :)

Thanks,
Kinson :)

---

### Post by 23meg on 2007-03-08
> **go2dell said:**
> Killing a process is *never* ideal, but often necessary or there wouldn't be a command specifically designed for doing it.

More like a dozen or so commands, actually.

> **go2dell said:**
> Considering the user is using a terminal and typing, simply deactivating the screensaver doesn't make sense; hitting a key to type in the terminal deactivates the screensaver. 

You're not always supposed to be killing a local screensaver and doing it interactively, hence the reason of existence of xscreensaver-command in the first place. 

 > **go2dell said:**
> Trying to kill the screensaver usually means the screensaver has gone berzerk, which happens frequently on my Xubuntu systems.  Ditto switching to terminal, but that's another thread entirely. :lol:

Not necessarily; it may be running on a remote X server, or as I said in my second post, you may want to just deactivate the screensaver (make it act as if you'd moved the mouse), not kill the screensaver daemon and make it stop functioning (if you do that, it won't reactivate n minutes later; there's a difference in function). And besides, xscreensaver-command lets you do more; check out its manual page.

This isn't about what to do to a process that isn't responding; if the screensaver isn't responding to input, it almost certainly won't respond to xscreensaver-command either anyway.

---

### Post by OliverN on 2007-12-10
I use ```
killall [whatever the process command is]
``` after doing ```
ps aux
``` once.  That saves me the time of identifying new pids every time, and it also makes me a bad boy.

---

