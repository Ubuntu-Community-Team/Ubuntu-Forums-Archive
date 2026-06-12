---
title: "I forgot my username and password"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by intensedaz on 2006-10-11
Oops, forgoten username and password,help

---

### Post by whizbaby on 2006-10-11
Start from liveCD

Let's assume your HD-system is mounted on /media/hda2 (replace by appropriate) and that your future password will be *one_two* (not recommended, replace) . Open a terminal and type
**openssl passwd one_two**
you'll get an answer **similar** (not equal) to

**MOOMoyfSTokjA**

then do (remember to replace the mount point by the correct one)

sudo nano /media/hda2/etc/shadow

and go to the line with your username and replace the key between the first two colons by the key you created, like I did for my dummy


dummy:**MOOMoyfSTokjA**:13777:0:99999:7::: 

now you have set a new password

EDIT:
I recommend that after rebooting and logging in you do (terminal)

passwd

to change your password again, somehow this seems to produce a more encrypted key.

---

### Post by Tamil on 2006-10-11
[http://www.ubuntuforums.org/showthread.php?t=264535](http://www.ubuntuforums.org/showthread.php?t=264535)

---

### Post by aysiu on 2006-10-11
Boot into recovery mode.

Type ```
cd /home
ls
``` This will tell you what your username is, which I'll call *username* for the sake of these instructions. ```
passwd *username*
``` will reset your password to one you like (and can remember) ```
reboot
``` to reboot into regular (not recovery) mode.

---

### Post by soutSA on 2006-10-11
reboot you machine..

during boot up, at the grub loading screen press ECS. You will get option to load different kernels. Choose the one that states recovery next to it.

This will boot you up in a terminal and into single user mode.

At the prompt type in the following:

#passwd username

where username is your own username. Then it will give you the option to change your password. After changing you password just type:

#exit

This will boot ubuntu to the login screen. Type in your username and new password. BAM!!!!!

Your in..

Hope that helps

---

### Post by dannyboy79 on 2006-10-11
> **soutSA said:**
> reboot you machine..

during boot up, at the grub loading screen press ECS. You will get option to load different kernels. Choose the one that states recovery next to it.

This will boot you up in a terminal and into single user mode.

At the prompt type in the following:

#passwd username

where username is your own username. 

He doesn't know his username, how in the world are your instructions going to help him?

---

### Post by soutSA on 2006-10-11
sorry my bad!!

Booting into single usermode will also give him root access. Then you can change you root password to something you remember by doing:

#passwd root

and change to password to what he wants. Boot the machine, log in as root. Then go and lookup his users by going to:

System>administration>users and groups

just my 2 pence:)

:-D :-D :-D

---

