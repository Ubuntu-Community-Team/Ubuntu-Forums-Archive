---
title: "Why can't I logon?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-04-01
when the screen up to type in the user name and password I type them in. It doesn't log on, it just gives me that screen back. No message about wrong user name or password. And it just keeps going in that cycle. I finally got my screen resolution changed and then this comes up. Always seems to be a challenge here.

Thanks

---

### Post by Bachstelze on 2007-04-01
Can you login through the console ? (Crtl+Alt+F2)

---

### Post by rillip on 2007-04-01
This EXACT thing happened to me.

What is happening is that xserver is failing to launch after you login.  Why is another question.  For me, it was because I had insufficient disk space.  Try starting in recovery mode and see if you have free space.  If not... make some! ;)

You might also try to go to a command line session (you can do this from the drop down menu) and run dpkg-reconfigure xserver-xorg

This will reconfigure your xserver.  Generally, you can just chose the default options if you don't know.  In my case I have an LCD monitor and it kept choosing too high a refresh rate, which was messing things up.

Let us know how it goes!

---

### Post by captgadget on 2007-04-01
I have done the sudo dpk-reconfigure xserver-xorg and it didn't work. I did the CRT-ALT-F2 and it asks me to logon so I put in my user name and then my password and then I get to this: captgadget@gpcom:~$ and then I don't know where to go from there.

Thanks again

---

### Post by captgadget on 2007-04-01
I had this posted on mulitmedia & video late last night and taurus asked for this info, but as of this morning no answer from him. I'll post it here to see if it means anything to you here.  Thanks

Fiilesystem size used Avail. Use% Mounted on
/dev/hda1 52G 3.6 46G 8% /
varrun 157M 88K 157M 1% /var/run
varlock 157M 0 157M 0% /var/lock
procbususb 10M 120K 9.9M 2% /proc/bus/usb
udev 10M 120K 9.9M 2% /dev
devshm 157M 0 157M 0% /dev/shm
lrm 157M 20M 138M 13% /lib/modules/2.6.17-generic/volat
ile

---

### Post by pppetter on 2007-04-01
captgadget@gpcom:~$ sudo dpkg-reconfigure xserver-xorg

It will probably ask for your password, then type it in and push enter.

And let's see if it works...

---

### Post by captgadget on 2007-04-01
I'm sorry. I did that and went through the xserver and it still would not allow me to log on.

---

### Post by bapoumba on 2007-04-01
> **captgadget said:**
> I'm sorry. I did that and went through the xserver and it still would not allow me to log on.
When in recovery mode, please enter **df -H** and post the output in here.

---

### Post by captgadget on 2007-04-01
Fiilesystem size used Avail. Use% Mounted on
/dev/hda1 52G 3.6 46G 8% /
varrun 157M 88K 157M 1% /var/run
varlock 157M 0 157M 0% /var/lock
procbususb 10M 120K 9.9M 2% /proc/bus/usb
udev 10M 120K 9.9M 2% /dev
devshm 157M 0 157M 0% /dev/shm
lrm 157M 20M 138M 13% /lib/modules/2.6.17-generic/volat
ile

---

### Post by taurus on 2007-04-01
After you log in from a console, <Ctrl><Alt>F2, what's the output of this command?

```
ls -la ~
```

---

### Post by captgadget on 2007-04-01
Gosh, I'm on my iMac right now because I can't log in on the Linux. And when I did your commands it returned a bunch of stuff but I don't know how to get it to you.

---

### Post by taurus on 2007-04-01
Did you say you can log in with another account but not the primary one that you want to use?  Look that the .xsession-errors to see what it says.

```
tail -20 ~/.xsession-errors
```

---

### Post by captgadget on 2007-04-01
Just a second here OK? I'll get there.

---

### Post by captgadget on 2007-04-01
tail: cannot open '/home/captgadget/xsession-errors' for reading: no such file or directory

---

### Post by captgadget on 2007-04-01
going back to the ls -la ~ Here's what it gives me for the xsession errors

-rw------ 1 captgadget captgadget  895 2007-04-01 10:06 .xsession errors

---

### Post by captgadget on 2007-04-01
Guess I'll just reinstall.

---

### Post by captgadget on 2007-04-01
thanks to everyone who tried to help.

---

### Post by rillip on 2007-04-01
Just looking at this, I'd be suprised if it's not the /var/lock folder having 0% free, as I know xserver writes a lock file for each session.

When you're at the command prompt, try "sudo startx."  It'll likely give you some error saying xserver is already running.  If it's not, please delete the lock file...

Then try rm /path/given/there/lockfile

Then try and startx again.

---

