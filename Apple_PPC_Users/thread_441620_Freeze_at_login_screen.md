---
title: "Freeze at login screen"
date: 2007-05-12
forum: Apple PPC Users
---

### Post by iMacThere4iAm on 2007-05-12
On my brand new install of Ubuntu Fiesty, I can now boot it but it freezes on the login screen after about a second. I just have time to type half my username if I'm quick. 
Can anyone help me find out what's wrong?
Maybe a crash log would be a clue but I don't know where to find it...

---

### Post by stmiller on 2007-05-12
> **iMacThere4iAm said:**
> On my brand new install of Ubuntu Fiesty, I can now boot it but it freezes on the login screen after about a second. I just have time to type half my username if I'm quick. 
Can anyone help me find out what's wrong?
Maybe a crash log would be a clue but I don't know where to find it...

Check out the PPCFAQs at the link below. You have to get to a terminal window and kill the esd process which is making the stall.

---

### Post by iMacThere4iAm on 2007-05-12
I don't think this is relevant to my problem. This happens before I even log in. Also, I can't get a console by pressing ctrl+alt+f1...

---

### Post by stmiller on 2007-05-13
Okay sorry yeah I see. Try this:

Boot into single user mode so X won't start. (Note: your networking will not start either in this run level.)

At the yaboot prompt, type

Linux single

and hit enter.

Then check out these logs:

$ less /var/log/Xorg.0.log

look for any errors (EE)

and

$ less /var/log/gdm/:0.log

---

### Post by iMacThere4iAm on 2007-05-17
I still haven't got it to work. What I'm having is a kernel panic right after the login screen loads. Interestingly, this happens when graphical login is disabled, so it seems that's not what is causing the problem.

I can boot into single user mode, but of course that's no use - I don't want to be running as root all the time.
I think I need some help to troubleshoot the kernel panic. Like: Where can I find the log?

---

### Post by stmiller on 2007-05-17
> **iMacThere4iAm said:**
> I still haven't got it to work. What I'm having is a kernel panic right after the login screen loads. Interestingly, this happens when graphical login is disabled, so it seems that's not what is causing the problem.

I can boot into single user mode, but of course that's no use - I don't want to be running as root all the time.
I think I need some help to troubleshoot the kernel panic. Like: Where can I find the log?

No- the whole point of single user mode is to VIEW the logs. It will let you boot your computer with just the bare kernel (and no X) to see what happened. So boot into single user mode, and give us the output of the xorg and gdm logs.

---

### Post by iMacThere4iAm on 2007-05-19
Here are the logs. I'm not quite sure which I should be posting, so here are them all. Sorry.

[Xorg.1.log](http://paste.ubuntu-nl.org/21627/)
[Xorg.0.log](http://paste.ubuntu-nl.org/21628/)

[/0.log.4](http://paste.ubuntu-nl.org/21629/)
[/1.log](http://paste.ubuntu-nl.org/21630/)

There were other GDM logs for /0 but each one just contained the following:```
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.
```

---

### Post by iMacThere4iAm on 2007-05-31
Bump!

---

### Post by stmiller on 2007-05-31
Hey okay in the file

/etc/X11/xorg.conf

try commenting out the lines

load "dri"
load "glx"

and see if it works.

---

### Post by iMacThere4iAm on 2007-05-31
That didn't really help, I still get a Panic when I try to startx. Ubuntu is being very badly behaved, however I now have the fun of surfing the web in elinks.
Any other ideas?

---

### Post by iMacThere4iAm on 2007-05-31
Good news! It works if I unplug my mouse! I twigged that it might be causing a problem because I just noticed that a Kernel Panic happened every time I moved the mouse, even if X was not running.
Unfortunately, the GUI is hardly much use without a mouse so I'm still using links...
I'm going to try it using different mice, different USB ports and so on.

---

### Post by iMacThere4iAm on 2007-05-31
Most odd... It happens with any mouse, and even before X is loaded, like if I turn off dri and glx. Any movement of the mouse causes a Kernel panic.
My graphics tablet works okayish.
The weirdest bit is, if after messing around for a bit after loading X, I then plug in a mouse, everything is fine! I am so confused.

---

### Post by stmiller on 2007-05-31
> **iMacThere4iAm said:**
> 
My graphics tablet works okayish.


Ah! That must be the problem. Have you tried it without the tablet?

---

### Post by iMacThere4iAm on 2007-05-31
Yes, I have. Even with it uplugged, the mouse still doesn't work right.

---

### Post by catphive on 2007-06-08
Hey,
I have exactly the same problem with the login freezing sometimes on fiesty.

I upgraded from the previous xubuntu release, that didn't have any such problems.

However, I'm not on a mac! I'm on a 1.5 ghz pentium M intel laptop with embedded graphics. So, this sounds like a problem with gdm and nothing PPC or apple specific (you are on a PPC machine correct?).

---

### Post by iMacThere4iAm on 2007-06-08
> **catphive said:**
> Hey,
I have exactly the same problem with the login freezing sometimes on fiesty.

I upgraded from the previous xubuntu release, that didn't have any such problems.

However, I'm not on a mac! I'm on a 1.5 ghz pentium M intel laptop with embedded graphics. So, this sounds like a problem with gdm and nothing PPC or apple specific (you are on a PPC machine correct?).

That is correct. I don't know why this happens or how to find out, but I've found a way to get around it.
It seems to work, if I unplug the mouse until after I've logged in, then plug it back in.

Possibly related problem: if I run top, it often shows that a process called mouseemu is causing 100% load on one of my CPUs. I can kill the process with no apparent ill-effects.

---

### Post by tcrroadie on 2007-06-08
Remove the package mouseemu and your mouse problem should be solved.  This has been a problem for some Linux PPC users. 

Open a terminal and enter this text

```
sudo apt-get remove mouseemu
```

Restart your computer with your mouse connected and post back with your findings. 

Thanks  :D

---

### Post by iMacThere4iAm on 2007-06-08
The funny thing is, a lot of the time now, it does work even if I boot with the mouse plugged in. I wish the problems would be more consistent.
It means I can't even conclusively prove whether that removing mouseemu would work.

I'm actually going to try a different distro for a bit, perhaps Yellow Dog Linux. I'm only playing with Linux for the learning experience, so I'm not too attached to it. (yet ;))

---

### Post by tcrroadie on 2007-06-08
> It means I can't even conclusively prove whether that removing mouseemu would work.

Did you try removing the package mouseemu as I recommended?  In case you are not sure what mouseemu is, here is the package description from apt.

> Description: Emulate mouse buttons and mouse wheel
 Mouseemu is a daemon to emulate mouse buttons on trackpads with only one
 button. It lets you: 
 * emulate middle and right click 
 * emulate mouse wheel 
 * block trackpad while typing 
   
 It was initially developed for Apple PowerBooks and iBooks, but it may be
 useful on other architectures as well.

By the way, what machine are you installing PowerPC Linux on?  

> I'm actually going to try a different distro for a bit, perhaps Yellow Dog Linux. I'm only playing with Linux for the learning experience, so I'm not too attached to it. (yet )

Nothing wrong with shopping around.  Yellow Dog is a good PowerPC distribution to start with.  Actually, the fist PowerPC Linux distribution I installed on my late model iBook G4 was Yellow Dog Linux.  I installed the latest version (5.0.1) about 3 weeks ago and used it for about 3 or 4 days.  Installation is easy, documentation is good, and at least in my case on my iBook, everthing just worked.  Even hibernation.  

There are many negative aspects of Yellow Dog Linux compared to Ubuntu though, at least for me.  I wrote a short post a few weeks ago about my experiences with Yellow Dog Linux and Ubuntu.  You can find it here. 

[A happy Apple ibook G4, Ubuntu Feisty user]("http://ubuntuforums.org/showthread.php?t=449431&highlight=happy+ibook+user")

Hope to see you back after you shop around some.  :D

---

### Post by iMacThere4iAm on 2007-06-09
> **tcrroadie said:**
> Did you try removing the package mouseemu as I recommended?  In case you are not sure what mouseemu is, here is the package description from apt.I haven't done that because it works anyway now, most of the time. I haven't really got the inclination to keep rebooting over and over to try and work out if it helped.



> **tcrroadie said:**
> By the way, what machine are you installing PowerPC Linux on?  A PPC (Quad G5)



> **tcrroadie said:**
> Nothing wrong with shopping around.  Yellow Dog is a good PowerPC distribution to start with.  Actually, the fist PowerPC Linux distribution I installed on my late model iBook G4 was Yellow Dog Linux.  I installed the latest version (5.0.1) about 3 weeks ago and used it for about 3 or 4 days.  Installation is easy, documentation is good, and at least in my case on my iBook, everthing just worked.  Even hibernation.  

There are many negative aspects of Yellow Dog Linux compared to Ubuntu though, at least for me.  I wrote a short post a few weeks ago about my experiences with Yellow Dog Linux and Ubuntu.  You can find it here. 

[A happy Apple ibook G4, Ubuntu Feisty user]("http://ubuntuforums.org/showthread.php?t=449431&highlight=happy+ibook+user")

Hope to see you back after you shop around some.  :DThat's interesting. We'll see how it goes. :)

---

### Post by tcrroadie on 2007-06-09
> **iMacThere4iAm said:**
> 
A PPC (Quad G5)


Just for future reference since you are using a desktop PC, if mouseemu gives you problems you can just remove it, since it is not needed for your system. 
```

sudo apt-get remove mouseemu
```

---

