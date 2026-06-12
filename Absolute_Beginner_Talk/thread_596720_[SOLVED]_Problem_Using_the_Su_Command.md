---
title: "[SOLVED] Problem Using the Su Command"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by plinydogg on 2007-10-29
Hi people,

I suspect that this has a simple answer, but I'm trying to enter root mode using the ```
su
``` command. When I type ```
su
``` in the terminal and enter my password when prompted I get the following error message:

```
su: Authentication failure
Sorry.
```

What's the problem? I entered my password properly? 

TIA,

Plinydogg

---

### Post by Dr Small on 2007-10-29
> **plinydogg said:**
> Hi people,

I suspect that this has a simple answer, but I'm trying to enter root mode using the ```
su
``` command. When I type ```
su
``` in the terminal and enter my password when prompted I get the following error message:

```
su: Authentication failure
Sorry.
```

What's the problem? I entered my password properly? 

TIA,

Plinydogg
Apparently SU does not have a password set.
Please read here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by tencent on 2007-10-29
im not sure the specific reason as my fedora core server doesn't do it and I haven't had to do this on any other distro but in ubuntu its one of the minute differances.

sudo su

that should solve your root switching problems.

---

### Post by black_magician on 2007-10-29
try this:

```
sudo -i
```

---

### Post by plinydogg on 2007-10-29
Thanks Dr. Small!

For others: the link that Dr. Small posted basically says that using the sudo command to obtain root privleges on an ad hoc basis is preferred in Ubuntu and so using a separate root mode is not allowed. In other words, when you need root privileges, you've got to use the sudo command.

---

### Post by plinydogg on 2007-10-29
black_magician: Thanks! 

Well, to amend what I just said: Su is not enabled by default (see Dr. Small's comment) but can be enabled (see black_magician's comment). Thanks to you both!

---

### Post by Dr Small on 2007-10-29
:)
Please remember to mark your threads as solved from Thread Tools for other's who may encounter your problem, can look for a solution in your thread!

Dr Small

EDIT:
Oopps. It looks like I was a little slow :p

---

### Post by plinydogg on 2007-10-29
Done!

---

