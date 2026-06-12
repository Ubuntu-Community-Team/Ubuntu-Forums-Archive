---
title: "How do I get write access to other NTFS and Ext3 drives?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Svopp on 2008-02-27
Hey there,

I had been using win vista for a week but it sucked badly ... I decided to go back to XP, but now tried ubuntu, and i like it.

the single very most annoying thing in vista, though, was the administration rights ... even if i was the very very admin there are many things i couldnt do compared to being admin on win-XP.

Now ... I want to become the very master admin of my ubuntu 7.10 OS ... i wanna be able to have full control of my harddisks. currently they are set to "read only" and i cannot change that because i apparently do not have permission. if i wanna run games i gotta copy the game into my home/username directory

Is there any way to become the 'ultimate admin' ?

if not ... then how do i get most possible rights .. like adding myself to all usergroups...

if thats not possible either... then how do i get control of my harddisks from ubuntu?

1 week ubuntu user, first time poster.

Thanks in advance!

---

### Post by Rossross on 2008-02-27
You could log into root, but thats highly insecure to use constantly. What you can do is give more administrative rights to your current account.

---

### Post by taurus on 2008-02-27
Maybe this will explain it, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

---

### Post by SunnyRabbiera on 2008-02-27
well on ubuntu we use something called sudo, that sort of makes the default user the root user.
The default user can install new packages and such but it needs the default users password.
Sadly there is no real easy way to enable root user mode except the terminal, if you need to edit the things you speak about except by using the terminal.

---

### Post by Charcoal1981 on 2008-02-27
To gain administration rights, just use the command "sudo" before any command you use in the terminal, alternatively use the command gksudo to launch a GUI app. e.g.
```
gksudo nautilus
```
and you will run the app as root.

You should not attempt to run as root at all times as this is NOT secure (and it makes it easy to damage your installation).

You can use chmod, chown and chgrp commands to adjust the permissions/ownerships of files/folders. See [http://www.ss64.com/bash/](http://www.ss64.com/bash/) for more info on these commands and more.

---

### Post by aysiu on 2008-02-27
[This](http://www.psychocats.net/ubuntu/permissions) will help you out.

---

### Post by stchman on 2008-02-27
> **Svopp said:**
> Hey there,

I had been using win vista for a week but it sucked badly ... I decided to go back to XP, but now tried ubuntu, and i like it.

the single very most annoying thing in vista, though, was the administration rights ... even if i was the very very admin there are many things i couldnt do compared to being admin on win-XP.

Now ... I want to become the very master admin of my ubuntu 7.10 OS ... i wanna be able to have full control of my harddisks. currently they are set to "read only" and i cannot change that because i apparently do not have permission. if i wanna run games i gotta copy the game into my home/username directory

Is there any way to become the 'ultimate admin' ?

if not ... then how do i get most possible rights .. like adding myself to all usergroups...

if thats not possible either... then how do i get control of my harddisks from ubuntu?

1 week ubuntu user, first time poster.

Thanks in advance!

Use the sudo or gksudo command whenever you need to do an administrative task.

DO NOT log in as root as this is VERY insecure.  By default you cannot log in as root on Ubuntu you would have to go out of your way to do this.

---

### Post by Svopp on 2008-02-27
Very insecure ? ^^ sounds terrifitying ...

ok then ...  the main problem i have is that i cannot change "read only" to "read and write" on both my ntfs disk AND on my filesystem ext3...

ill check out some of the links given

awesome fast replies also, thank you all very much! :)

---

### Post by taurus on 2008-02-27
For ntfs filesystem, install ntfs-3g driver and use it to mount your ntfs partition if you want to write to it.

For ext3 filesystem, it depends on which directory (directories) you want to write to.  Don't just change the permissions or ownerships just because it's convenient for you.  Doing so in the wrong directories could crash your machine.  Then, we would have a bigger problem.

---

### Post by Iehova on 2008-02-27
Windows is awful at permissions, and it's terrifically bad that the default user on XP is the administrator. It's seriously one of Windows' biggest failings,so you wouldn't want to re-create that on ubuntu. ;)

Running games shouldn't necessitate copying them to your home directory, if you install your programs through Synaptic (which you should be doing unless you have a very particular reason :P), they'll all be accessible through the panel menu (ie. Applications > Games).

---

### Post by stchman on 2008-02-27
> **Svopp said:**
> Very insecure ? ^^ sounds terrifitying ...

ok then ...  the main problem i have is that i cannot change "read only" to "read and write" on both my ntfs disk AND on my filesystem ext3...

ill check out some of the links given

awesome fast replies also, thank you all very much! :)

If you are talking about anything other than your home directory you are not supposed to be able to write to it.  Linux permissions are part of the security of Linux.

In your / mount you should only be able to change permissions on the /home/<you name> folder.  If you have another partition formatted in EXT3 then it is OK to change permissions there.

I personally don't use my ~/ (short for home) for much.  I have another partition in the /media folder that I put all my personal stuff.  The ~/ folder is for apps to store configurations and such.  This technique allows me to do a fresh install of Ubuntu and not touch my personal data.

---

### Post by PeterJS on 2008-02-27
The biggest thing to understand about the different security models is the history that gave rise to them. Windows derives from DOS both operate on the assumption there there is only one user per machine, and anything run on that machine was done deliberately will a full understanding of the consequences by the user. Linux on the other hand derives from unix which was designed with multiple hostile users in mind from day one.

The windows model worked well before the internet when you needed physical access to the machine, if the user did something dumb they were well aware that it was their fault. But that doesn't hold anymore since the advent of the internet you can no longer assume that all access to a machine is authorized. The windows admin account has the keys to the castle because it's assumed they should have absolute control, because they have physical access. Well the requirement of physical access has gone out the door with the internet, but the security model derived from that (now faulty) assumption stands.

The linux security model isn't intuitive in a single user environment, doubly so if that user is used to being the unquestioned king of the castle, but imagine a shared machine with multiple users logged in at the same time. Further more assume they will behave hostilely towards each other, this is a much safer and realistic assumption than that they will behave civilly, as that requires both ethics and an understanding of the impact of their actions. So you've got two users, which one owns the system files? How do you prevent them from deleting, modifying, or reading documents they shouldn't? Linux was designed for a hostile environment from day 1, and the internet provides such an environment.

Consider a virus, if it gets loose on a windows machine it has complete unchallenged control of the system, that same virus if it got loose on a linux machine would have control over the account it compromised, that's it. Creating a fresh account and migrating documents and settings is a lot easier than hunting and killing a virus, or a full wipe.

Sure it's an inconvenience at first but once you learn how to work the system you get used to it. As abhorrent as it is to you not having total control, the idea of having total control frightens me, I'm pretty savvy, but that's just not safe.

The ubuntu security guide:
[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)

---

### Post by aysiu on 2008-02-27
Since the OP has given a few more details about the situation and the subject seems to have been derailed a bit to more theoretical discussions about security, I've changed the title of the thread to reflect the real support issue.

---

