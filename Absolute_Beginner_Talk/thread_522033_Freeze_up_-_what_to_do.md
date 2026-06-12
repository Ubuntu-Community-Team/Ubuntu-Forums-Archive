---
title: "Freeze up - what to do?"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Hybrid86 on 2007-08-10
In windows, when a program froze, ctrl+alt+del always cleared it right up. However, it seems that in ubuntu, when things freeze, the entire system stops and nothing short of a restart can bring it out.

Is there some key command/method I don't know of to get out of a freeze, or is it (as of now) impossible?

---

### Post by mcduck on 2007-08-10
First thing to try would be Ctrl-Alt-Backspace, which restarts X (your graphical UI).

If that doesn't work holding Alt-SysRq and pressing r-e-i-s-u-b will close all your programs, force frozen programs to quit, sync disks, remount them read-only and finally boot the machine. While not a perfect solution, this at least is cleaner way of shutting down a frozen machine than just pressing the power/reset button.

Of course it would be a good idea to find out what's causing your system to freeze, and then solve that problem.. ;)

---

### Post by Hybrid86 on 2007-08-10
Compiz fusion and running photoshop 7 in wine ocasionally cause them. I've gone back to using beryl, but photoshop is a must for me. Still, I should be able to get out of a simple freeze. I haven't had issues like that in Windows since Windows ME.

Thanks though. Though I've tried Ctrl-Alt-Backspace before to no avail, I'll try the other stuff you've mentioned next time it freezes.

---

### Post by adam15c on 2007-08-10
I have intermittent systems freezes too. Being completely new to everything linux (only installed 2 days ago) this is driving me crazy. I have searched these forums and there seem to be loads of possible answers but so far no-one has come up with a definitive answer. I actually tried Fedora today to see what, if any would be the differences. It worked with no problems at all. Unfortunately I prefer the look of Ubuntu so re-installed, the freezes are back again. There seem to be so many with this problem surely there would be an "official" fix? Any help would be appreciated. I am a complete nooby to this. Thanks.

---

### Post by Hube on 2007-08-10
Couple levels of access to hardware when using Linux:

- The X-window, which is the "pretty" environment
- command line (access this through ctrl-Alt-F1, you can use F2, F3 etc)

The command line (or TTY as it's sometimes known) probably won't be frozen.

Try accessing it, you will need to enter your login name and password (the same one used to access the X-window environment).

Try typing a command like this:

ps -ef | grep compiz

This will show any programs that are running called compiz.  Alternatively you can run:

ps -ef

To show all programs that are running (might be a bit scary!)

The | grep is a bit like a filter, in this case it is filtering for the word compiz

OK, a few things get returned to you when entering this command:

user process_id owner_process_id

If you type:

kill -9 process_id

You will kill the application that is running.

If you have any inkling in terms of what is crashing this can be used to get your machine running again.  If allelse fails you can use:

sudo reboot now

to reboot the computer.

To return to the X-window, use Ctrl-Alt-F7 (if that doesn't work try tome other F* numbers)

Once you know what's causing the instability you can then start looking for a solution, guranteed somebody else has encountered the same issue.

Good luck.

Hube

---

### Post by Hybrid86 on 2007-08-13
> **Hube said:**
> Couple levels of access to hardware when using Linux:

- The X-window, which is the "pretty" environment
- command line (access this through ctrl-Alt-F1, you can use F2, F3 etc)

The command line (or TTY as it's sometimes known) probably won't be frozen.

Try accessing it, you will need to enter your login name and password (the same one used to access the X-window environment).

Try typing a command like this:

ps -ef | grep compiz

This will show any programs that are running called compiz.  Alternatively you can run:

ps -ef

To show all programs that are running (might be a bit scary!)

The | grep is a bit like a filter, in this case it is filtering for the word compiz

OK, a few things get returned to you when entering this command:

user process_id owner_process_id

If you type:

kill -9 process_id

You will kill the application that is running.

If you have any inkling in terms of what is crashing this can be used to get your machine running again.  If allelse fails you can use:

sudo reboot now

to reboot the computer.

To return to the X-window, use Ctrl-Alt-F7 (if that doesn't work try tome other F* numbers)

Once you know what's causing the instability you can then start looking for a solution, guranteed somebody else has encountered the same issue.

Good luck.

Hube


What would I type to make it log out or restart X?

---

### Post by bwtranch on 2007-08-14
That should be Ctrl + Alt + Backspace

---

### Post by Hybrid86 on 2007-08-16
Sorry, I meant to ask "what would I type in *the command line* to log off/restart x".

---

