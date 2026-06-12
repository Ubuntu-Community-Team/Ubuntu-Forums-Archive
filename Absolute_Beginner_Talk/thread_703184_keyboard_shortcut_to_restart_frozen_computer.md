---
title: "keyboard shortcut to restart frozen computer?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-02-21
Is there a keyboard shortcut I can use to restart my computer? Gutsy freezes a lot and I have to hit the power button.

---

### Post by kathryn on 2008-02-21
If the crash is at the windows manager level, you can try restarting the x server.

ctrl + alt + backspace

---

### Post by jan quark on 2008-02-21
you can also try this combination

ctrl + print + K

---

### Post by HereInOz on 2008-02-21
Or you could try CTRL-ALT-F1, which will get you to a command line, log in with your username and password, then enter the command:

sudo shutdown -r now

After you give your password again, the machine should restart.

---

### Post by jasonkb on 2008-02-21
When you say it is freezing a lot, what is normally happening before a freeze occurs?  This seems unusual, and perhaps there may be a problem with the installation?

What are your system specs?

---

### Post by kleo skywalker on 2008-02-21
> **jasonkb said:**
> When you say it is freezing a lot, what is normally happening before a freeze occurs?  This seems unusual, and perhaps there may be a problem with the installation?

What are your system specs?

I feel like an idiot saying this but I'm not sure what my system specs are! I know I have an Intel Pentium processor (a 32-bit one), 512MB RAM, a 250 GB HDD, and no additional graphics or sound cards that I know of - is that enough?
Things were fine while I was using Feisty, and with Gutsy too in the beginning.
Now it just freezes all the time - I mean several times a day even. The troubling thing is, I can't put a finger on any one application that might be on when this happens. Mostly I do a lot of stuff at one time so it's impossible to point at one thing. At other times though, I may be just browsing the internet (Swiftweasel) or listening to music (Exaile) or using Open Office or even just trying to open a folder, when it freezes.

---

### Post by kathryn on 2008-02-21
Have you considered or tried a re-install of Gutsy?  (A pain in the butt but it helped me)

One of my first Gutsy installs was fine for a while too, before things went awry.  The cause of my troubles was similarly hard to diagnose.  I'd posted on this forum several times while troubleshooting that problem (Compiz, Nautilus, user permissions were all suspected at one point or another).  In the end I fixed it with a fresh install of gutsy.  It was perhaps a drastic solution, but tweaking the OS only seemed to make things worse.

Best of luck, I hope things work out for you.

---

### Post by 3rdalbum on 2008-02-21
When it freezes, do the little lights on the top-right of your keyboard start blinking? If so, then that's a kernel panic. You will probably be able to find an error message in /var/log/kern.log or /var/log/kern.0.log.

If those lights aren't blinking, you can do a force restart. First press Alt-PrintScreen-S, to attempt to sync data to disk and avoid data loss. Wait a couple of seconds, and then press Alt-PrintScreen-B to reboot.

The "PrintScreen" key might also be labelled "SysRq".

---

### Post by jasonkb on 2008-02-24
hmmm... Doesn't sound like that ought to be the problem.  When you went to Gutsy did you use a fresh install or upgrade?  This is probably being a little superstitious but Im a little wary of upgrading from one to the other directly... I always hear mixed results from people.  Some find it works perfect and others have had issues...

If you are not too in depth into the system (ie not so much data on your disk) maybe consider doing a fresh install...? If the problem persists there may be some crazy conflict or something like that, but it should not be crashing all the time like that!

Jason.

---

### Post by kleo skywalker on 2008-02-27
I'm not entirely sure of this, but it seems that most of the time I'm using Exaile when things freeze.
And I'm going to have to do a reinstall in a couple of months anyway (when Hardy comes out), so that really is a pain.

---

### Post by toobuntu on 2008-02-28
To safely reboot a frozen system:
1. Alt+SysRq [Print Screen], it’s a key combination
2. Now, without letting go of either of those keys, type (there will not be a visible terminal):
```
reisub
```
   You will not see any output at all, save hopefully a few flashes of the hard drive activity light after pressing the “s” of the sequence, and the machine rebooting after the “b.” They should be entered in slow succession, giving the system a chance to complete earlier steps before moving on to subsequent ones. Typing the sequence slowly may allow the system to safely terminate most or all processes before the more drastic kill command is invoked. Also, to minimize the chance of data corruption, it is a good idea to wait between the disk synchronization command and the unmount and finally the reboot command.
3. Holding down Alt+SysRq in Ubuntu for a few seconds, opens up ton of screen capture dialog boxes and causes 100% processor use. Then, you must continue pressing the REISUB part.
4. It can be remembered as the word "BUSIER" in reverse.
5. Explanation:
> Alt+SysRq+R takes the keyboard out of raw mode (gives back control)
Alt+SysRq+S attempts to sync all mounted filesystems (synchronizes data on disk with memory)
Alt+SysRq+E sends the SIGTERM signal to all processes except init
Alt+SysRq+I sends the SIGKILL signal to all processes except init
Alt+SysRq+U attempts to remount all mounted filesystems in read-only mode (to prevent a fsck at reboot)
Alt+SysRq+B immediately reboots the system, without unmounting partitions or syncing
6. Command line access and configuration
If the machine is headless or is being accessed remotely, magic commands may be run on the command line. This is, however, contingent upon being able to shell into the machine. To run magic commands, echo the desired trigger code to the SysRq trigger in the procfs. For example:

```
echo b > /proc/sysrq-trigger
```

This is equivalent to the key combination Alt+SysRq+B which reboots the machine.
7. An alternative to issuing the REISUB/RSEIUB keystrokes is to just press Alt+SysRq+R, followed by Ctrl+Alt+Del. This is the equivalent of issuing a shutdown now command at a root console; it does take a short while for the system to shut down after the Ctrl+Alt+Del keystroke. However, not all Linux systems support this easier method.
8. The R in REISUB is not always necessary.
9. To reboot or poweroff from the command line, you could issue:
```
sudo reboot
``` or
```
sudo poweroff
```

---

