---
title: "Ubuntu like bash on Windows 7"
date: 2012-09-25
forum: Any Other OS
---

### Post by najdorfchess on 2012-09-25
Hi all, I know this isn't the right place to ask but just out of curiosity (or to start a topic of discussion) what is the best way to run terminal emulator (like bash that can run all linux commands) in Windows 7 operating system. I have tried cygwin but I wanna hear more opinions on that! 

**Reason why I'm asking this?** 
Experiencing lot of laptop power related issues in ubuntu (my laptop overheats too much that it automatically shuts down often or freezes!)and thinking of restricting Ubuntu usage only to desktop and using only Windows 7 on my latop, but I badly want a good terminal for Vim and ssh. Comments, criticism, discussion all welcome!

PS. This also brings another point, how can I restrict my laptop from running the processor at full throttle all the time, which is something that happens a lot in ubuntu.

---

### Post by papibe on 2012-09-25
Hi najdorfchess.

Take a look at [Cygwin]("http://www.cygwin.com/").

Alternatively, for native Windows scripting capabilities you can go with [Windows PowerShell]("http://en.wikipedia.org/wiki/Windows_PowerShell").

Just a thought.
Regards.

---

### Post by lykwydchykyn on 2012-09-26
> **najdorfchess said:**
> Hi all, I know this isn't the right place to ask but just out of curiosity (or to start a topic of discussion) what is the best way to run terminal emulator (like bash that can run all linux commands) in Windows 7 operating system. I have tried cygwin but I wanna hear more opinions on that! 


You'll pardon my cheekiness in recommending Emacs to a Vim user :D, but if you download Emacs for Windows, it comes with a mode called "Eshell", which is a POSIX-like shell built in to Emacs.  Unlike the regular shell mode (which  just opens the default shell in a buffer window), eshell is actually a complete shell in its own right, so even on windows it works in a very BASH-y way. 

You can read up on eshell [here](http://www.masteringemacs.org/articles/2010/12/13/complete-guide-mastering-eshell/)

Keep in mind, you can use VIM shortcuts in emacs using VIPER mode, so this may be a total BASH + Vim solution in one package.

> 
PS. This also brings another point, how can I restrict my laptop from running the processor at full throttle all the time, which is something that happens a lot in ubuntu.

I use cpufreqd on my laptop; there's a bit of a learning curve setting it up, but once you get it going it works great.  That's assuming your hardware cooperates, of course.

---

### Post by qyot27 on 2012-09-27
MSys provides bash.
As already mentioned, Cygwin provides it.
Git for Windows provides it (uses a customized install of MSys').

All of these can easily be added to Windows' PATH so that they're callable from within the Command Prompt (for Git's, you can simply use 'bash -l' to switch; it's also the only one that keeps you within the directory you called it from, as MSys and Cygwin jump you to their $HOME directories).

Another option is [clink](http://code.google.com/p/clink/), which extends the capabilities of cmd.exe itself (although it still has some quirks that need to be ironed out).

---

### Post by matt_symes on 2012-09-27
Hi
 
You can also install Jupiter to control the cpu speed.

[http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html)

You can also accomplish this from the terminal
```

echo powersave | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

Kind regards

---

### Post by najdorfchess on 2012-09-27
Wow! I'm kinda overwhelmed by the responses I have got for this "lame" question! :D 

Here we go: 

@papibe Thanks, I have already installed cygwin and I'm interested in only bash like unix terminal, not windows! 

@qyot27 MSys is also okay but it's not native "Unix in Windows" as specified on their website. So I think I will stick with cygwin. But unfortunately most of the bash commands like ssh, clear etc don't work on cygwin. How to fix this? 

@lykwydchykyn You are being real cheeky there ain't you?! ;) I have used emacs and that doesn't offer me a permanent solution! What if I want to edit my code using 'original' vim?! :p And as far as cpufreqd goes, do you have a good documentation on it? And how does it fare against Jupiter as someone had suggested? 

@matt_symes Thanks for the suggestion. If I can control the over-heating and freezing problem on ubuntu, I have no reason to use windows! I will use Jupiter and get back to you in a couple of days!

---

### Post by erind on 2012-09-27
> **najdorfchess said:**
> [...]
@qyot27 MSys is also okay but it's not native "Unix in Windows" as specified on their website. So I think I will stick with cygwin. **But unfortunately most of the bash commands like ssh, clear etc don't work on cygwin. How to fix this**? 
[...]

To get the** clear** command you need to install the **ncurses **package, (run* setup.exe* again), or you can get the same effect by pressing **Ctrl+L**.
For ssh I normally use *Putty*; check this link on how to install ssh in Cygwin:

[http://www.howtogeek.com/howto/41560/how-to-get-ssh-command-line-access-to-windows-7-using-cygwin/](http://www.howtogeek.com/howto/41560/how-to-get-ssh-command-line-access-to-windows-7-using-cygwin/)

> Hi all, I know this isn't the right place to ask but just out of curiosity (or to start a topic of discussion) what is the best way to run terminal emulator (like bash that can run all linux commands) in Windows 7 operating system. I have tried cygwin but I wanna hear more opinions on that! 
[...]IMHO *Cygwin* is the closest Unix-like shell for windows that is out there.

---

### Post by qyot27 on 2012-09-27
> **najdorfchess said:**
> @qyot27 MSys is also okay but it's not native "Unix in Windows" as specified on their website. So I think I will stick with cygwin. But unfortunately most of the bash commands like ssh, clear etc don't work on cygwin. How to fix this?
That's because ssh isn't part of bash, nor is clear; they are their own separate utilities that are simply part of the userland.  Getting it working on Windows requires you to install ssh on its own.  It's provided with Git for Windows; for instance, I was on Cygwin at this point:
```
$ which ssh
/cygdrive/c/Program Files/Git/bin/ssh
```

I guess the point I was making is that you don't have to pick just one.  I listed all of those because I use all of those solutions in what has essentially become a fused environment (except for clink; I had it for a while, but its autocompletion had some bugs and I've not attempted to try and compile the current HEAD to know if they've been fixed yet).

The main issue is that no solution will get you one-to-one parity with the userland on a typical *nix OS; they all have their advantages and disadvantages.  And there are some features that Windows as an OS just simply cannot support the way those features are understood under Linux, no matter which POSIX solution you go with (like mkfifo named pipes).

---

### Post by lykwydchykyn on 2012-09-28
> **najdorfchess said:**
> 
And as far as cpufreqd goes, do you have a good documentation on it? And how does it fare against Jupiter as someone had suggested? 


I've never used Jupiter, so I can't say.  Using cpufreqd is as simple as installing it and editing the config file, which comes with its own pretty decent man page.

Basically, you create profiles (minimum and maximum frequency ranges, and a behavior policy), then you create rules for when to apply different profiles.  The rules let you specify conditions like battery level, AC adapter plugged in or not, certain programs running, cpu temperature, etc.

It comes with a sample configuration that's pretty well documented, if you don't mind a bit of reading it works fine.

---

