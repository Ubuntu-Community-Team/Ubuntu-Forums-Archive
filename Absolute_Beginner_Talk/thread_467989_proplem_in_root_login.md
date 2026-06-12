---
title: "proplem in root login"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by sindbad_x on 2007-06-08
I have ubuntu 7.04 fiasty

when i try to login on root

found this message

the system administrator is not allow to login
plz help

---

### Post by neo.patrix on 2007-06-08
Hi,

Login in as root is not allowed even on TTY, I think it is allowed to login as root only during Failsafe sessions. 

As far as design of Ubuntu is concerned , I find sudo & gksudo sutiable to do admin work. There is no particular need to login as root.

---

### Post by Crafty Kisses on 2007-06-08
> **sindbad_x said:**
> I have ubuntu 7.04 fiasty

when i try to login on root

found this message

the system administrator is not allow to login
plz help

Are you on a network?

---

### Post by pxwpxw on 2007-06-08
```

gksu xterm

```
At your own risk

---

### Post by Crafty Kisses on 2007-06-08
> **pxwpxw said:**
> ```

gksu xterm

```
At your own risk

I havn't tried this in a while but does,
```
sudo -i
```

still work for getting root access?

---

### Post by mmendez on 2007-06-08
> **sindbad_x said:**
> I have ubuntu 7.04 fiasty

when i try to login on root

found this message

the system administrator is not allow to login
plz help

I have found that on ubuntu, root is not allowed to login into X unless you boot into a kernel in failsafe then type "startx"

but you should be able to login on any TTY, I have done so many times and just tried again to confirm.
Ubuntu ships with no password set for root, you can see this when you boot in safe mode it goes straight to cmdline without asking for password. 

well sorry for the long winded foreward, here is what you want to know:

You can set a password for root while logged in as a normal user (I believe in Admin group) just type
```
sudo passwd root "whateverpasswordyouwant"
``` 

you should be able to login on any TTY as root with your new password.

You will not be able to login into a gui as root unless you booted in failsafe and then after you login (if you created a password) type startx

---

### Post by RTrev on 2007-06-08
> **neo.patrix said:**
> Hi,

Login in as root is not allowed even on TTY, I think it is allowed to login as root only during Failsafe sessions. 

As far as design of Ubuntu is concerned , I find sudo & gksudo sutiable to do admin work. There is no particular need to login as root.

I just noticed under Applications | System Tools we have a "Root Terminal."  I haven't used it much yet, but it seems like that would be a good option for the folks who don't care for sudo?

---

### Post by ghost_ryder35 on 2007-06-08
go to system, administration, login window, security(tab), then check allow local system administratior logon

---

### Post by sindbad_x on 2007-06-09
> **ghost_ryder35 said:**
> go to system, administration, login window, security(tab), then check allow local system administratior logon

thanks all brothers, and thx u specially coz i try to do all and i success with ur helping

---

