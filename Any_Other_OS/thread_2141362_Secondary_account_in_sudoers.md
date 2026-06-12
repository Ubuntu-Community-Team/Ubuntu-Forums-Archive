---
title: "Secondary account in sudoers"
date: 2013-05-02
forum: Any Other OS
---

### Post by RockinsonM on 2013-05-02
Not sure where to put this exactly as my servers are CentOS currently but this is the only forum I have an account on and I'm too lazy to wait for a new account on another site lol

I usually just run as the root user but for other users I created a secondary account. Thing is I need the secondary account to basically do everything root would. I have it set up and added the account in the /etc/sudoers file but I want to configure it so that if you run a sudo command with that account it does not ask for the password. I know this is possible (I've done it before on CentOS 6.4) but I can't remember the syntax for it and I'm currently on the older CentOS 5.8.

Right now the line reads: Account2      ALL=(ALL)      ALL

I know there is a NOPASSWD option but I'm fuzzy on syntax to configure it to make it work properly.

Thanks

---

### Post by matt_symes on 2013-05-02
Thread moved to **Other OS / Distro Support.**

---

### Post by Lars Noodén on 2013-05-02
You can add access to a specific program by writing out that program including its path.

```

%group2 ALL=(ALL) NOPASSWD: /sbin/shutdown [-dfhknpr]* [a-zA-Z0-9 \:.]
%group2 ALL=(ALL) NOPASSWD: /usr/sbin/tcpdump

```

If you leave off any options after the program, then the user can launch it with any settings they feel like.

---

### Post by RockinsonM on 2013-05-02
So would 
```
Account2 ALL=(ALL) NOPASSWD: ALL
```
do what I want? Is that % needed at the beginning?

---

### Post by CharlesA on 2013-05-02
The % is because it is a group.

This might help too:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Lars Noodén on 2013-05-02
> **RockinsonM said:**
> So would 
```
Account2 ALL=(ALL) NOPASSWD: ALL
```
do what I want? Is that % needed at the beginning?

The way that is written, it would turn the account *account2* into a defacto root shell.  That might not be good.

The % at the beginning of a word at the beginning of a line means that it refers to a group.  It is easier to test and debug if privileges are granted and revoked at the group level.  Even if the group ends up having a single user, it is still a good practice to get into.

---

### Post by RockinsonM on 2013-05-02
A defacto root shell is basically what I was looking for. I have *maybe *3 people that would need root access but rather than have us all use root I wanted to create another account just for organizational purposes, but individual accounts aren't necessary.

Thanks

---

### Post by Lars Noodén on 2013-05-02
An advantage of having individual accounts is that there is a better history of who did what so that you know who to ask questions when something changes or stops working.

---

### Post by CharlesA on 2013-05-02
> **Lars Noodén said:**
> An advantage of having individual accounts is that there is a better history of who did what so that you know who to ask questions when something changes or stops working.

Agreed. I've got a script I use to run a command as a different user (Virtualbox is running as a different user) and I've thought about removing the password prompt, but I decided against it, even if the likelyhood of someone gaining access to my server is very slim. Better to have it there.

---

### Post by lykwydchykyn on 2013-05-02
> **RockinsonM said:**
> A defacto root shell is basically what I was looking for. I have *maybe *3 people that would need root access but rather than have us all use root I wanted to create another account just for organizational purposes, but individual accounts aren't necessary.

Thanks

Why not just use root then?  What's the point of a second account?

---

