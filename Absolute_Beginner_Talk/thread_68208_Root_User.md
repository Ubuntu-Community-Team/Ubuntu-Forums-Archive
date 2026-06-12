---
title: "Root User"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by lavarock09 on 2005-09-22
Hey,

What is the password for the root user?

I assume the Username is root, so what is the password?

Thanks

Chris

---

### Post by papangul on 2005-09-22
I had made this mistake also when I first installed Ubuntu. :) 
There is no root password!
Whenever you are asked for password enter the password of the current user, but remember all users don't have admininstration rights.

---

### Post by PsyberOneZero on 2005-09-22
[Ubuntu - Root/Sudo](https://wiki.ubuntu.com/RootSudo) 
Ubuntu has root "disabled" by default, it's really best to use sudo if you need to do anything root-ish, and any desktop apps that need root privilages are already set up with gksudo.  I've been running Ubuntu for over a year now and I've never had to use the root account, or really wanted to.

---

### Post by KingBahamut on 2005-09-22
If you want to enable root user 

sudo passwd root

---

### Post by lavarock09 on 2005-09-22
Thanks guys, now I know.

A friend couldn't get into their account because they forgot their password and I wanted to  know how to get into the root account incase I forgot my password but I didn't know how, but now I do, :D

P.S. Oh, and ther friend got into their account in the end

---

### Post by Wolki on 2005-09-22
[QUOTE=lavarock09]A friend couldn't get into their account because they forgot their password and I wanted to  know how to get into the root account incase I forgot my password but I didn't know how, but now I do, :D[/QUOTE]

If such a thing happens, choose recovery in grub, It will boot into root, where you can set a new password for the user account. You don't need to set a root password for that.

---

### Post by dgrafix on 2005-09-22
[QUOTE=KingBahamut]If you want to enable root user 

sudo passwd root[/QUOTE]

I wanted to do this too, temporarily. How do i get the terminal back to normal again? as i just want to be able to do this when i have a lot of sudos to do. Ive tried logging out but terminal still drops to root (#) without asking for a password.

---

### Post by dgrafix on 2005-09-22
ok the login has timed out but how do i redisable su?

---

### Post by Mustard on 2005-09-22
[QUOTE=dgrafix]ok the login has timed out but how do i redisable su?[/QUOTE]
 

```
sudo passwd -l root
```

---

### Post by Wolki on 2005-09-22
[QUOTE=dgrafix]i just want to be able to do this when i have a lot of sudos to do.[/QUOTE]

Try "sudo su" :)

---

