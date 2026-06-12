---
title: "Feisty Fawn CD"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by milesbh on 2007-06-15
Hello (again)

I have got the feisty fawn CD. I boot it up, and choose "Start or Install Ubuntu". After passing the loading screen, I am presented with a blinking cursor for about a minute or so, and then it says

```
[200.944000] Buffer I/O error on device fd0, logical block 0
[239.140000] Buffer I/O error on device fd0, logical block 0
```

I have also tried choosing "Start or Install Ubuntu in Safe Graphics Mode".

I am able to install Dapper Drake.

please help! I really want to get Ubuntu working!

---

### Post by the.phantom on 2007-06-15
i am not a expert !

did you try running a check on the cd ( one of those options with the start/install screen))

if you burned the cd, did you run a  checksum on the file?

try re-burning at a slower speed!

and you did burn a ISO and not a data copy?


that seems to help out most
good luck

---

### Post by Golyadkin on 2007-06-15
Is there a floppy in the floppy drive?

---

### Post by milesbh on 2007-06-15
I didn't burn the cd and there was no floppy in the drive. If someone has any better suggestions than running a check on the cd (since it takes a long time) then please say

---

### Post by milesbh on 2007-06-15
Can anyone help??

---

### Post by mattva01 on 2007-06-15
I'd say just run the check, it doesn't take that long and it would eliminate a possible cause

---

### Post by sooqing on 2007-06-16
i posted this question when feisty was released and nobody had the solution. i even tried to disable the fdd by adding the 3 boot parameter but they don't work, anyone has a solution to this?

floppy=0
floppy=0,16,cmos
nofloppy

---

### Post by Golyadkin on 2007-06-16
**Cesare Tirabassi  **says in on the [launchpad]("https://answers.launchpad.net/ubuntu/+question/7697"):

> 
Try blacklisting the module. In a terminal:

sudo kate /etc/modprobe.d/blacklist

and add this at the end:

# floppy driver since I don't have one
blacklist floppy

Also, if in the file /etc/fstab there is an entry like this:

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Add a # in front.

Reboot.


This worked for someone who had the same problem.

---

