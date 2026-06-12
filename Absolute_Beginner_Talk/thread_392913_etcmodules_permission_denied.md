---
title: "/etc/modules permission denied"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Punker on 2007-03-25
hey when I try to add my sound card to boot with my PC  I get this and I'm log in at root

```
 /etc/modules snd-soundcard
bash /etc/modules: Permission denied

```

---

### Post by 7llusion on 2007-03-25
I think you should do it as a super user,
use sudo infront of what you want to do then enter your password(enter it blindly then press enter)
Illusion

---

### Post by Punker on 2007-03-25
```

sudo: /etc/modules: command not found

```

this is what I get now???

---

### Post by Punker on 2007-03-25
Let me explane myself better 
```

sudo /sbin/modprobe snd-soundcard

```

my sound works fine but my speaker icon looks muted its not I log out and log in everything work's great no little red x I reboot have to do command all over to get sound.
```

sudo: /etc/modules: command not found

```
now I get this when I want to add the soundcard

---

### Post by kinematic on 2007-03-25
/etc/modules is a config file to wich you have to add that driver.
```
sudo gedit /etc/modules
```
that opens the file as root with gedit for you to add the driver.

---

### Post by Punker on 2007-03-25
thank you wheir do I put the command line
this is what is says. I just want to make sure
thanks a lot 
```

# /etc/modules: kernel modules to load at boot time.
# 
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

```

---

### Post by meborc on 2007-03-25
you should just add snd-soundcard at the end of the file (on a new line)

---

### Post by Punker on 2007-03-25
I'm sorry about this but I'm new and I just want to do it right

where below
```

lp

```

---

### Post by Punker on 2007-03-26
can anyone help me out here I been looking in the forum 
sorry to seem like a dummy thank's

---

### Post by chili555 on 2007-03-26
Yes, you could sudo gedit /etc/modules to make it look like:```
# /etc/modules: kernel modules to load at boot time.
# 
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
snd-soundcard
```Save and exit. [SIZE="3"]BUT...[/SIZE]

Are you sure this is the module you want? You didn't say which version you are running, but in my Feisty install, there is no module named snd-soundcard. I hate for you to go to the effort to modify your /etc/modules file and find out it doesn't fix your problem.

Shall we investigate further? Show us:```
lspci -v
```and let's see what kind of soundcard it is and what module it really loves.

---

### Post by Punker on 2007-03-29
well with your help in this forum I got the info and its now fixed I haven't been on line in a while 
but here it is thanks alot for the help now when I reboot it works above the lp ??????
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

snd-cs4236

lp

```

---

### Post by chili555 on 2007-03-29
Ah! Looks much better! The proof is it works. Good luck and have fun.

---

