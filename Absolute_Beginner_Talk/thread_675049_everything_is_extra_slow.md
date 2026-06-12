---
title: "everything is extra slow"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by missed her show on 2008-01-22
hi everybody....


so i was having some problems with flash, got it reinstalled and working fine, 


but now - Ubuntu runs super slow.  Firefox takes forever to start, scrolling pages and explorer windows is extremely slow, and my resources don't show anything excessively running i nthe background. 


Are ther dlagnostics i can run, or maybe service i can tick off?   Ugh.  this stinks.  thanks for your help.

---

### Post by hyper_ch on 2008-01-22
open a terminal, install htop

```

sudo apt-get install htop

```

then run htop by issuing
```

htop

```

it will - by default - show you how much cpu each process is using right now. So it might or might not be FF.

---

### Post by missed her show on 2008-01-22
nice, thanks.  i set up htop,  and it shows the memory consistently near the red at 260/1011 mb, with the cpu meter occasionally (every 20-3-s) pegging up at 92%.  not sure what else to make of all that info.

---

### Post by hyper_ch on 2008-01-23
well, the memory is displayed differently on there... better use
```

free -mem

```

That will tell you more precisly how much memory is actually needed for running programs and stuff and how much of it is chache...

What process does peak the cpu usage?

---

### Post by missed her show on 2008-01-23
Heres what happened: 

```
dewey@dewey-desktop:~$ free -mem
free: invalid option -- e
usage: free [-b|-k|-m|-g] [-l] [-o] [-t] [-s delay] [-c count] [-V]
  -b,-k,-m,-g show output in bytes, KB, MB, or GB
  -l show detailed low and high memory statistics
  -o use old format (no -/+buffers/cache line)
  -t display total for RAM + swap
  -s update every [delay] seconds
  -c update [count] times
  -V display version information and exit

dewey@dewey-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1011        713        298          0         17        367
-/+ buffers/cache:        327        683
Swap:         1906          0       1906
dewey@dewey-desktop:~$ 

```

 /usr/bin/X  seems to be hogging a lot of the CPU, firefox the memory..

---

### Post by Terry of Astoria on 2008-01-23
Thanks. I can now check that.
:-)

---

### Post by Terry of Astoria on 2008-01-23
How did you install flash?

---

### Post by nemilar on 2008-01-23
It looks like your memory situation is fine - you're not even hitting swap, so I doubt that's the source of your problems.

Please let us know which process is using all your CPU; use htop or top, and see which process is at the top of the list, using how much % of the CPU.  That's likely the culprit.

---

### Post by missed her show on 2008-01-23
the main culprit (top of the list in htop) is being used by th eroot user, the command being used is 
```
/usr/bin/x :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
```

thanks for the assistance

---

### Post by hyper_ch on 2008-01-24
you can't really stop that one ;)

---

### Post by missed her show on 2008-01-24
rrrrright...



could ktorrent be the culprit?  It's been running poorly/ineffeciently lately, and i've generally stopped using it....but i'm stuck, at a loss now.

---

### Post by hyper_ch on 2008-01-24
depending on the amount of torrents that are loaded it could be ktorrent... azureus would even be worse than ktorrent (in terms of system resources usage)

If you kill gdm you kill your login session... that's why I said that is not an option... however I think gdm may also get high load / high memory usage if you have advanced desktop effects activated.

---

