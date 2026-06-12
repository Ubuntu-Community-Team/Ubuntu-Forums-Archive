---
title: "root pw?"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by Angerman on 2006-04-12
I just tried the ubuntu 5.10 live cd, wanted to run an application from the system menu and then it asked me for the root pw.
I set the root pw to be "hallo" during the installation but it wont accept that for some reason, what gives?

---

### Post by mscman on 2006-04-12
ok, a few things:
1.  There is no "installation" for a live cd.  (Hence the name 'live')
and
2.  In an Ubuntu installation, the root account (and password) is disabled.  If it's asking you for a password it's probably your user password.  (I'm not sure offhand what the password is for the live cd)

---

### Post by davebgimp on 2006-04-12
[QUOTE=mscman]I'm not sure offhand what the password is for the live cd[/QUOTE]

AFAIK, there's no password.

---

### Post by aysiu on 2006-04-12
The live CD never asks for a password for *sudo* commands.

There's no active root account in an installation:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Angerman on 2006-04-12
I didn't specify any user password though, what to do?

---

### Post by aysiu on 2006-04-12
[QUOTE=Angerman]I didn't specify any user password though, what to do?[/QUOTE] Can you give more details?

Are you using a live CD, or did you install Ubuntu on your hard drive?

Did you do an expert install, a server install, or a regular install?

What questions did Ubuntu ask you during installation?

What task are you trying to accomplish now that requires a password? What error are you getting when you try it?

---

### Post by Angerman on 2006-04-12
[QUOTE=aysiu]Can you give more details?

Are you using a live CD, or did you install Ubuntu on your hard drive?

Did you do an expert install, a server install, or a regular install?

What questions did Ubuntu ask you during installation?

What task are you trying to accomplish now that requires a password? What error are you getting when you try it?[/QUOTE]
Been trying the live cd.

Used expert install to set the display drivers to vesa, otherwise the system would lockup.

It asked for a root passwod wich I specified, it also asked to setup a single user account; I have chosen yes, it didn't ask for any username or password here.

I want to format a drive. When it asked me for the root password, I entered the one I specified earlier since that's the only one I knew of. It said the password is wrong. :-k

---

### Post by davebgimp on 2006-04-12
[QUOTE=Angerman]Been trying the live cd.

Used expert install to set the display drivers to vesa, otherwise the system would lockup.

It asked for a root passwod wich I specified, it also asked to setup a single user account; I have chosen yes, it didn't ask for any username or password here.

I want to format a drive. When it asked me for the root password, I entered the one I specified earlier since that's the only one I knew of. It said the password is wrong. :-k[/QUOTE]

That doesn't sound like a Live CD.

---

### Post by Angerman on 2006-04-12
Replace expert install with live-expert, I always forget that I dont acutually install it.
I used the ubuntu 5.10 live cd for amd64.

---

