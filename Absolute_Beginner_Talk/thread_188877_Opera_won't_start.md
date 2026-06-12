---
title: "Opera won't start"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by p1r0 on 2006-06-04
Hi

I've installed Opera Browser with automatix and it won't start.
This are the error messeges it gives me:
```

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
opera: Preference initialization failure. Generic failure (-1)
```

And when I did apt-get install opera trying to fix this issue it says that Opera is already installed in my systes, what is true, but I can't fix the problem.

thanks p1r0

---

### Post by uzi09 on 2006-06-04
sorry, i may not be much help, but try this out:

remove opera, never used automatix, but if u can, do it from there, otherwise do it using apt:
```

sudo aptitude remove opera

```

then reinstall (using apt)

```

sudo aptitude install opera

```

give it a try now.

ps: not sure whether or not it's just called "opera" but try using tab to autocomplete it and you'll find out for sure

---

### Post by harishg on 2006-06-04
Are you sure if you have opera installed not just for root?

---

### Post by uzi09 on 2006-06-04
if i understand correctly - no using these commands won't just install opera for root user.

you must be root to USE SYNAPTIC to install any program, not just opera

---

### Post by p1r0 on 2006-06-04
Thanks but none of the above worked.
I found a working solution here:
```

http://www.ubuntuforums.org/showthread.php?t=189164
```

p1r0

---

