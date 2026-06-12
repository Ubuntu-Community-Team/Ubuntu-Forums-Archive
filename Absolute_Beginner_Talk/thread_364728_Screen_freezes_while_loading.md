---
title: "Screen freezes while loading"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by nirpius on 2007-02-18
Hi,

I'm using an old Thinkpad T20 and I've installed Dapper Drake. Everything is working fine when it loads, but 80% of the time the screen freezes while loading.

It happens just after the brown ubuntu thingy gets to 100% and just before the splash-screen when the thing that looks like a terminal screen shows a flashing '_'.

I assume it has frozen because the '_' stops flashing and doesn't change. It does this every time but like I say, 4 out of 5 times nothing happens thereafter.

Anyone know what I can do? Or is it just that I have an old laptop?

---

### Post by solar george on 2007-02-18
Do you mean just after the boot menu?

---

### Post by nirpius on 2007-02-18
Yep, that's right.

---

### Post by solar george on 2007-02-18
> s it just that I have an old laptop?

No, I've had ubuntu running on a compaq armarda M300 and a [thinkpad 600e]("http://www.dealtime.com/xPF-IBM-ThinkPad-600E-2645-26455JU")
Those are both old machines.

Now to be constructive, have you had this problem ever since you have been using linux on this machine or has it just started.

If it has just started have you installed or upgraded anything recently.

---

### Post by nirpius on 2007-02-18
It's always been that way. I tried reloading Windows (sorry) and it loaded fine and now I've put Ubuntu back and it's back to the same problem.

---

### Post by solar george on 2007-02-18
> I tried reloading Windows (sorry)
Don't worry.

Here's a secret - I dual boot.............. Some times, when I have no option

Can you post the contents of your /boot/grub/menu.lst

```
$less /boot/grub/menu.lst
```

---

### Post by nirpius on 2007-02-18
I'm not dual-booting, but I typed that code anyway.

First it said:

bash: /boot/grub/menu.lst: Permission denied

so I tried:

sudo $less /boot/grub/menu.lst

and I got:

sudo: /boot/grub/menu.lst: command not found

---

### Post by STREETURCHINE on 2007-02-18
i have the same problem with dapper ,it sometimes freezes just after i sign in,
this is only recent as it never used to happen,
i am running beryl svn but that is not the problem as it was doing it before i installed beryl,

it is a frustrating little bug,but i just have to reboot and it usually fires up ok,

---

### Post by nirpius on 2007-02-19
OK, well thanks anyway guys

---

### Post by solar george on 2007-02-19
> sudo $less /boot/grub/menu.lst

leave out the $ in the command. That represents the command prompt or terminal.

---

