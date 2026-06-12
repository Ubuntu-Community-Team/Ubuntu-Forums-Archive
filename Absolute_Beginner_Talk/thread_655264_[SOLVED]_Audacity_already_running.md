---
title: "[SOLVED] Audacity already running?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by bigboyman2 on 2008-01-01
I'm just trying to go in and edit some songs to create ringtones, when I click on Audacity, this pops up in an error message

The system has detected that another copy of Audacity is running.
Running two copies of Audacity simultaneously may cause
data loss or cause your system to crash.

Use the New or Open commands in the currently running Audacity
process to open multiple projects simultaneously.

"Wait, what?", I think to myself. I just clicked on it. I wasn't running earlier. So I go in and kill the process, then try to start it. I click it, nothing happens. I click again, I get the same message. 

Okay. I'm a Linux noob, but I went in, killed process. Uninstalled via add/remove program. Reinstalled. Same issue keeps coming up. I try launching via terminal, nothing comes up. Only thing that does, is when I kill the process. I checked the second desktop. I have no clue what's going on. A little help, even if it's helping diagnosing the root cause of the issue?

---

### Post by blueridgedog on 2008-01-01
Ok, when you run it the first time, the time when nothing happens, do a pa ax | grep audacity to see if it is actually running (before you click it a second time).  I suspect that is is, but you can see it.

---

### Post by bigboyman2 on 2008-01-01
I'm sorry, but you're gonna have to dumb that down for me. Like I said before, I'm a Linux and Ubuntu newb. So, some things I haven't quite got a hold of yet, or I haven't had to do before

---

### Post by vanadium on 2008-01-01
Open a terminal, then type

ps ax | grep audacity

You will see a list of all processes with the name audacity. There will be at least one, the "grep audacity" you typed yourself. If audacity is running, there will also be the one of audacity itself, just named "audacity".

You can then stop the "audacity" process typing

killall audacity

If you noted the number in the first column of the output of ps, then you can also use kill, e.g:

```

~$ ps ax | grep audacity
 5995 pts/0    Sl     0:00 audacity
 5999 pts/0    R+     0:00 grep audacity
~$ kill 5995
~$ 
[1]+  Terminated              audacity
~$ 

```

This "gently" terminates the program. For a process that is "blocked", you can terminate with "brute force":

kill -s 9 5995

or

kill -KILL 5995

---

### Post by bigboyman2 on 2008-01-01
And either way, if I go through the system processes and kill it, or if I kill it in any way you showed me through the monitor, when I click it the first time, nothing happens. Then I click again, it gives the duplicate audacity message. I assume it's not popping up like it should when it starts up, but I can't find a way for it to show itself

---

### Post by bigboyman2 on 2008-01-01
> **bigboyman2 said:**
> And either way, if I go through the system processes and kill it, or if I kill it in any way you showed me through the monitor, when I click it the first time, nothing happens. Then I click again, it gives the duplicate audacity message. I assume it's not popping up like it should when it starts up, but I can't find a way for it to show itself

Also, I've tried rebooting Ubuntu, nothing (different)  happened. I looked through the forums via the search, and I still didn't see anything close to my problem

---

### Post by blueridgedog on 2008-01-01
I still think knowing if it is running after you click it the fist time will help.

So, click it once, then run:
```

ps ax | grep audacity
```

I want to know if it is simply running, but hasn't generated a display.  The next step will be to try running it in a terminal manually and seeing if there is any output that could be helpful.

---

### Post by bigboyman2 on 2008-01-01
> **blueridgedog said:**
> I still think knowing if it is running after you click it the fist time will help.

So, click it once, then run:
```

ps ax | grep audacity
```

I want to know if it is simply running, but hasn't generated a display.  The next step will be to try running it in a terminal manually and seeing if there is any output that could be helpful.
Sadly, it is running with that command, the grep one, and the standard audacity. And when I kill the process, then start the program from the terminal, there's no information that comes up in the terminal. The only thing that comes up. And it's still the same message in the standard error window when I try to run audacity from the terminal, or click on it

---

### Post by blueridgedog on 2008-01-01
Can you post the output of:

ps ax | grep audacity

After clicking just once?  You see you will see one line that is the grep line, and another (perhaps) that is potentially the program.  

Just copy and past from the terminal.

---

### Post by bigboyman2 on 2008-01-01
> **blueridgedog said:**
> Can you post the output of:

ps ax | grep audacity

After clicking just once?  You see you will see one line that is the grep line, and another (perhaps) that is potentially the program.  

Just copy and past from the terminal.
Sure here we are
One with it running already
```
joel@Ninja:~$ ps ax | grep audacity
 6031 ?        S      0:00 audacity
 6034 pts/0    R+     0:00 grep audacity
```

And nothing is appearing. So then I kill the process, then do the ps ax command

```
joel@Ninja:~$ ps ax | grep audacity
 6042 pts/0    R+     0:00 grep audacity
```

Again, it's running, just not displaying. Very confusing >_<

---

### Post by blueridgedog on 2008-01-01
Ok, so it is running.

Lets try and start it with a command line in a terminal and see if it complains in a way that we can understand:

Lauch a terminal, klling off any currently running versions of audacity and then enter

audacity

Perhaps it will complaint in some way.

---

### Post by bigboyman2 on 2008-01-01
Yeah, I had tried that, nothing at all came up. I typed in audacity in the terminal, all there was was a blank line. Nothing else came up..

---

### Post by blueridgedog on 2008-01-01
Darn.  Is there anything in the log about it?

```
cat /var/log/messages | grep audacity
```

---

### Post by bigboyman2 on 2008-01-01
Hold up now. I seem to have gotten audacity working, it pops up now when I type in the terminal. But there's an error as well
```
sh: jackd: not found
Expression 'ValidateParameters( outputParameters, outputDeviceInfo, StreamMode_Out )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 1206

```

---

### Post by bigboyman2 on 2008-01-01
Eh, I eventually figured it out. To fix a completely unrelated issue with sound in youtube or flashes, I deleted a necessary codec by accident.

At first, it wouldn't display. I have no clue how that worked itself out. Then, it couldn't open any file. Again, didn't know how I did that. Then, it wouldn't play any file. That, I know I fixed by messing with the settings and the way sound is supposed to work. I'll mark this as solved, though =p

---

