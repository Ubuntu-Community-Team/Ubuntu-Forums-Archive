---
title: "How to quietly shutdown PC / get MPlayer to remember volume settings"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Momo88 on 2006-02-02
Hi,

I am new to Linux and would be happy if anyone could help me with the following two problems:

a) I like to listen to music before I go to bed and want my computer to automatically shutdown / power off after a specified number of minutes. Under Windows I had a program that was doing that for me. Now, how can I do that under Ubuntu?
I tried "sudo shutdown -h 30" which almost does the trick. The only thing that's still annoying is a beep about every minute. How can I get my PC to quietly shutdown?

b) I switched from Totem to MPlayer as my main media player, which I like better. The only thing so far that I don't like about MPlayer is that when I switch to the next movie in my playing list it always moves the volume slider back to max. How can I get MPlayer to remember my volume settings when moving from one video to the next?

Any help would be highly appreciated ;-)

Thanx,
Momo88


P.S.: Just upgraded to Ubuntu 5.10 - if that is of any help.

---

### Post by Estariel on 2006-02-02
1) I have exctly the same problem, but I haven't had time to look for a solution yet.

2) Try setting the volume not with mplayer, but with the gnome volume control. I know it is only a work-around, but it should work

---

### Post by Momo88 on 2006-02-09
Hi,

if anybody is interested, I found a way to quietly shutdown my PC. As I found out there are 2 commands under Linux that allow you to schedule commands: the first one is cron(tab) for commands that are repeated periodically, e.g., every day, week, hour, etc.; the second one is the "at" command that allows you to execute a certain command at a specified time.

For example, use the following command to shutdown your pc in 30 minutes from now:

sudo at now + 30 minutes [ENTER]

at the "at>" prompt type your command(s): sudo shutdown now -h [ENTER]

Use [STRG] + [D] to exit "at>".

With "atq" you can view the scheduled commands.
With "atrm" you can remove a scheduled command from the queue.

Hope this will be useful for other Ubuntu/Linux newbies as well.

Have fun,
Momo88 :KS

---

### Post by USA1 on 2006-02-15
Hi can you show me how to download mplayer and how to install it?

Thanks,
manny

---

### Post by ChrisSnow on 2007-04-29
> **Momo88 said:**
> Hi,
For example, use the following command to shutdown your pc in 30 minutes from now:

sudo at now + 30 minutes [ENTER]

at the "at>" prompt type your command(s): sudo shutdown now -h [ENTER]

Use [STRG] + [D] to exit "at>".
Momo88 :KS

Or perhaps use a time with shutdown. EG:

chris@desktop:~$ sudo su
Password:
root@desktop:/home/chris# shutdown -h 22:35

Broadcast message from chris@desktop
        (/dev/pts/1) at 22:28 ...

The system is going down for halt in 7 minutes!

---

### Post by Shinoda on 2007-05-07
> **USA1 said:**
> Hi can you show me how to download mplayer and how to install it?Assuming the multiverse repo is enabled (if not you may do so in System > Administration > Synaptic Package Manager > Settings > Repositories or similar),```
sudo aptitude install mplayer
```

---

