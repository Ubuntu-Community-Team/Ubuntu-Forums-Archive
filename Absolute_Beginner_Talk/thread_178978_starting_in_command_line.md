---
title: "starting in command line?"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by stallprophet on 2006-05-18
fairly new, installed ubunta a while ago and like a fool forgot password.  I am trying to reset the main_user paswd but seems I can only do that from comman line.  How can I access comman line before the GUI starts up?

Please...ASAP.  Or is there any other way to retrieve password beside highly intuitive brain testing.

cheers.

---

### Post by mlind on 2006-05-18
one way of doing this is going to runlevel 1 instead of 5

When booting, you see grub menu for short while

* press ESC
* navigate to kernel you want to boot using cursor keys
* press 'e' to edit
* append '1' (without hyphens) to the kernel line, so it will look something like

```

/vmlinuz-2.6.15-22-k7 root=/dev/mapper/VolGrp00-LVRoot ro **1**

```

* boot

(after bootup, you'll be logged in root terminal)
* issue command *passwd login_name* where login name is your username

---

### Post by Dr. Nick on 2006-05-18
You can also use the recovery option from grub to get a terminal I believe

---

### Post by nalmeth on 2006-05-18
boot into recovery mode (hit ESCAPE while grub is loading, and select recovery)
type:
```
passwd user
```
Replace user with your username. Enter your new password.

---

### Post by S{yndrom}e on 2006-05-19
is it possible to use the "root" password to change a user's current password?

---

### Post by cyracks on 2006-05-19
[QUOTE=S{yndrom}e]is it possible to use the "root" password to change a user's current password?[/QUOTE]

```

sudo passwd user

```

---

### Post by Ecthelion on 2006-05-19
[QUOTE=mlind]one way of doing this is going to runlevel 1 instead of 5

When booting, you see grub menu for short while

* press ESC
* navigate to kernel you want to boot using cursor keys
* press 'e' to edit
* append '1' (without hyphens) to the kernel line, so it will look something like

```

/vmlinuz-2.6.15-22-k7 root=/dev/mapper/VolGrp00-LVRoot ro **1**

```

* boot

(after bootup, you'll be logged in root terminal)
* issue command *passwd login_name* where login name is your username[/QUOTE]

I wondered what those runlevels are...
I know that each time you log off it says changing to runlevel..., but what are these runlevels?

---

### Post by cyracks on 2006-05-19
[QUOTE=Ecthelion]I wondered what those runlevels are...
I know that each time you log off it says changing to runlevel..., but what are these runlevels?[/QUOTE]

When ubuntu starts it executes everything in **/etc/rcS.d/**, after that starts runlevel specific programs defined in 
**/etc/rcX.d where X is the number of runlevel**. 
(For example: runlevel 2 starts everything in /etc/rc2.d, runlevel 3 starts programs in /etc/rc3.d...). 
Startup scripts for all startup programs can be found in **/etc/init.d** so in /etc/rcX.d are just links to the programs in /etc/init.d/
To add a program to start with specific runlevel use command **update-rc.d** 
To select the default runlevel to start at boot edit the file **/etc/inittab**

---

### Post by mlind on 2006-05-19
I guess the scripts are performed 'alphabetically', where all scripts that begin with K
(kill) are run first, after that scripts that begin with S (start). Intergers define order
on kill/start sequence.

Debian distros, like Ubuntu use only runlevels 1 (Single user mode) and 2-5
(Multiuser modes). Runlevels 2-5 don't are basically the same, but admin can
configure them like he/she wants to.

Classic runlevel ordering is known as
1 	Single-User Mode
2 	Multi-User Mode
3 	Multi-User Mode with Networking
5 	X11

---

### Post by cyracks on 2006-05-20
[QUOTE=mlind]I guess the scripts are performed 'alphabetically'[/QUOTE]
No they are started according to the number included in the link name, for example:
/etc/rc2.d/S**20**postfix

---

### Post by catlett on 2006-05-20
I never used it but can't you use > Ctrl+Alt+Del To restart the computer in console mode? Again I never used it but I have seen it posted in the 5.04 starter guide.

---

### Post by mlind on 2006-05-21
[QUOTE=cyracks]No they are started according to the number included in the link name, for example:
/etc/rc2.d/S**20**postfix[/QUOTE]

yes, but starting letter is the most relevant thing. It has to be either K or S
and K's are executed before S'. the next relevant thing is the number.

---

### Post by auburn on 2006-05-22
run levels are really cool. They're synonymous with F8 boot options in windows.For example, run level 1 is equivalent to "safe mode". When i first started linux, with debian, I didn't know how to shutdown until I learned you can simply tell it to change to run level 0... like this: $sudo init 0
rebooting is: $sudo init 6

---

