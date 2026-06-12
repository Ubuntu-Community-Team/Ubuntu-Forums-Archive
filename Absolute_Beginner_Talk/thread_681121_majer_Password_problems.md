---
title: "majer Password problems"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Bigadada_saba on 2008-01-28
I am working on a system that i installed about a yr  ago for a friend and he hasn't done upgrades for a long time because he changed the s.u. passwd an cant remember it. and he has the computer set to log on automatically how do i reset the su password. Need help Asap because he needs to travel to do a prsentation with the laptop and i have to in stall a program but can't without the su passwd.

---

### Post by bodhi.zazen on 2008-01-28
1. Use sudo, same password for both log in and admin

[uwiki]RootSudo[/uwiki]

2. boot to recovery mode and set a new root password with:

```
passwd root
```

---

### Post by anaconda on 2008-01-28
just boot to recovery mode and change the password with 
```
passwd username
```
in recovery mode you will have root rights..

wait a moment.. do you actualy mean "su" password and not sudo password? if you mean su password, that means that root acount is enabled, and even the recovery mode will ask for a password..

hmm. then the only change is to boot with a liveCD and delete or change roots password.. and then boot to recovery mode..

eg. boot with liveCD mount the harddisk, and backup and edit the file
/etc/shadow (from the hard disk not from the CD :)

the line from my shadow file is here:
```
anaconda:$1$EEm1hP2t$GaAhQ4ScJwZzaomwu9oQY1:13765:0:99999:7:::
```
and the encrypted password is after the username between two ":"s I dont remember if the $1$ is part of the password or not, but if you delete the right password pard then that user wont have a password anymore.. You can google and find out what part to leave on that line..

Or you could change the password to be same as here, which is "joooo" 
testi:$1$a7GW//Od$hlf36nn0aK16YMYzgn5HN.:13906:0:99999:7:::

so if you make sure that this part of the above line is exactly same than here, then that users password will be "joooo"
$1$a7GW//Od$hlf36nn0aK16YMYzgn5HN.

the above string is generated from joooo and the generation is done the same way with different installations of ubuntu so this solution will also work..

---

### Post by Bigadada_saba on 2008-01-29
Thanks got the problem solve with your advice
:guitar::guitar::guitar::guitar:

---

