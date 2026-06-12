---
title: "Stuck in Limbo - Can't Login!"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by th3gh05t on 2007-10-29
Hi,

Once I finally fixed the problem I've addressed [_here_]("http://ubuntuforums.org/showthread.php?t=590782") (I had to switch the hard drive boot sequence.), I ran into a small problem this morning.

I decided to 'Hibernate' my system last night, and when I turned it on this morning, I had completely forgotten that I left the Ubuntu CD in the drive. And since my BIOS boots to the CD first, it loaded up the Ubuntu Live CD system. Realizing that I was in the Live CD, instead of my desktop, I rebooted the computer.

I rebooted in the computer and took the Live CD out, and booted into my regular Ubuntu OS. After I typed my username and password, the system couldn't login me in. It gave me an error window that said:

[INDENT]"Your session only last less than 10 seconds..." [/INDENT]

The only session that I can log onto is the "Failsafe Terminal". And this leads me to my questions:

When I "sudo bash", I can gain root access, then I wanted to see who was logged onto the system. So I did a "who" command. There are two "derek" logged onto the computer.

1. How do I log one of these users off off the computer?

2. Which user should I logoff and how do I know which one to select?

I know that this can be done with some simple linux commands, I just don't know them.

Thanks, th3gh05t

---

### Post by taurus on 2007-10-29
Isn't derek your login name since you just logged into a safe session?  If you want to force a user to log off, just kill his login shell.

```
ps -A
```
What's the output of this command from a terminal?

```
df -h
```

---

### Post by th3gh05t on 2007-10-29
Thanks! I will try those when I get home

What do the commands do exactly? Which one will kill users?

Should I try this command?

ps -ax | grep derek

---

### Post by th3gh05t on 2007-10-29
Now, I am having some major problems. 

After a reboot, the computer goes into automatic "fsck"  check, but that process fails and says:

[INDENT]An  automatic file system check (fsck) of the root filesystem has failed. A manual fsck must be preformed, then the system restarted. The fsck should be preformed in maintence mode with the root filesystem mounted in read-only mode.

* The root filesystem is currently mounted in read only mode. A maintenance shell will now be started. After preforming system maintenance, press Control-D to terminate the maintenance shell and restart the system.[/INDENT]

I have a command line that reads:

root@ghost:~#

PLEASE tell me what commands I need to enter to repair my system and get it back to normal!

Thanks, th3gh05t

---

### Post by taurus on 2007-10-29
At that prompt, type

```
fsck -y /dev/sda1  <-- **_assuming_** /dev/sda1 is your root partition
```

---

### Post by th3gh05t on 2007-10-29
> **taurus said:**
> At that prompt, type

```
fsck -y /dev/sda1  <-- **_assuming_** /dev/sda1 is your root partition
```

Taurus!! Thank you so much! That works!!!

---

