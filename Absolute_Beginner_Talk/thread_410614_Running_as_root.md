---
title: "Running as root"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-04-15
I've ran into a situation that I don't know how to resolve. In order to run the drum synth, Hydrogen, in realtime mode (it changes tempo if not running in realtime), I have to run Jackd in realtime mode. Running these in realtime requires that I run as root. 

What can I do to avoid running as root and still get realtime access for these apps?

---

### Post by rsambuca on 2007-04-16
Can you run them from a root terminal?  

```
sudo -i
```

---

### Post by Patrick K on 2007-04-16
I'm currently running them from the menu with the command "gksu". I looked at the man page for the "sudo -i"  option but it didn't make sense to me. Perhaps you could explain it. here is the entry:> -i  The -i (simulate initial login) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.
           The command name argument given to the shell begins with a - to
           tell the shell to run as a login shell.  sudo attempts to change to
           that user’s home directory before running the shell.  It also ini&#8208;
           tializes the environment, leaving TERM unchanged, setting HOME,
           SHELL, USER, LOGNAME, and PATH, and unsetting all other environment
           variables.  Note that because the shell to use is determined before
           the sudoers file is parsed, a runas_default setting in sudoers will
           specify the user to run the shell as but will not affect which
           shell is actually run.


---

### Post by rsambuca on 2007-04-16
To be honest, I have never looked at the manual for this, nor have I really took the time to understand this particular command.  All I know is, when ever I have needed to run something as root, this one works.

---

### Post by Patrick K on 2007-04-16
Thanks for posting. Both apps run fine starting them with gksu. However, I'd like to run them as a regular user not as root. 

Anyone know how to do this?

---

### Post by Maestro23 on 2007-04-16
.

---

### Post by Patrick K on 2007-04-27
Bump

---

### Post by Cypher on 2007-04-27
I'm curious as to why running them as root means that they are running in realtime? The only advantage as root is that you can access various devices that users cannot. If this particular application uses some devices in the "/dev" directory you can try "chown" them to "777" and see if you can run the application as a regular user.

---

### Post by Patrick K on 2007-04-27
I can run the apps as a regular user but Hydrogen changes tempo, it speed up and slows down (not a good thing for a drum machine to do). To fix this Jackd (and Hydrogen) has to run in realtime. Neither will start in realtime unless they are run as root. I think the issue goes deeper than just accessing the files. 

I did turn up one possible solution. Recompile the kernel with the Linux Security Module (LSM). Which seems rather drastic if there is another way to go. Plus, I'm hesitant to do this do to future upgrade issues and I'm afraid of hosing my system having never compiled a kernel before.

---

### Post by Cypher on 2007-04-27
I'm not sure how running the programs in root will necessary make them more realtime and running a regular user makes them less so. The only thing that should be changing is the permission of the application to access files/devices.

Since I don't use/know these applications, perhaps I'm not understanding what "realtime" means in their context.

I come from a Embedded software engineering background, so "realtime" means something completely different to me..:)

---

### Post by Patrick K on 2007-04-27
I'm not clear on realtime either. I think it gives a much higher priority to apps by giving them almost direct access to the processor. At least, a much higher priority than they have as a regular user. This causes most all other processes to yield to them. Apparently, there is a security issue hence the need to be root to run them. I'm actually surmising this security issue from the one "solution" I found of recompiling with LSM.  

Jackd, which is a low latency patchbay type app and is required by many audio recording and editing software apps, has a realtime switch but has to run as root to use it. I really don't know what security risk there is running these apps as root but I'd rather not run as root if I can avoid it.

---

### Post by Cypher on 2007-04-27
Actually..running a program as Root or a regular user doesn't yield you any higher priority. Running something in Kernel space (as modules) as opposed to Application space is where the priority and other issues come to play.

Anyway, I don't want to muddy the murky waters anymore with my lack of knowledge with these apps, so hopefully someone who's played with these apps will have some better suggestions..

---

### Post by Patrick K on 2007-04-27
Thanks for your input. It could be Kernel space is where it needs to run. I was thinking inner ring. Whatever the case, they only run correctly as root. Thanks, again.

---

### Post by Patrick K on 2007-04-29
bump

---

### Post by Patrick K on 2007-05-02
bump

---

