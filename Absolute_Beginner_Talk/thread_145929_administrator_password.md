---
title: "administrator password"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by urbaneezer on 2006-03-17
Ah...does anyone know how to reset your administrator password?

I'm trying to run setup and installation for some HP drivers and when I open a terminal window and attempt to run the instructions from sourceforge, I keep getting the following:

username@computername:~$ su
Password:
su: Authentication failure
Sorry.
username@computername:~$

Obviously, where it says username@computername that is actually my username and the name of my machine. And the password that I've always entered here is the same as the password I use when logging onto my machine (with my username).

This has never happened before. The only thing that I can think of is that I downloaded Easy Ubuntu since the last time I ran anything in Terminal.

Any ideas guys & gals?

---

### Post by halfvolle melk on 2006-03-17
Hi,
You can also log in as root like this:
```
sudo su
```
Then change your password with:
```
passwd
```

---

### Post by derelict on 2006-03-17
Can't you sudo the commands ordered by the instructions?

---

### Post by IcyEars on 2006-03-17
I'm pretty new to all this myself and I had the same problem.  When I installed Ubuntu, I didn't get asked to set a Root password at install time, so I guess it doesn't have one (hence the need to set it if you want to login as root).  In all the tutorials I've seen, when you need to do anything as Root, you have to use the SUDO command (and I'm not a big fan of this).  So I set the root password as follows:

1) Open a terminal and type sudo passwd root.

2) It asks you for your password, type in your normal user password.

3) It then asks you for the new root password - type this in.

4) It verifies it.

5) Done.

You can now type SU, enter the new password and your in as root.

Hope this helps.

---

### Post by WoodyMahan on 2006-03-17
When I changed the password on my system, I found that things like Synaptic started failing.  I had to reset the password before those things started working again.  I find that the sudo prompt let's me do anything I need to with my own user password.

---

### Post by meborc on 2006-03-17
STOP don't confuse your user password with su password... they are totally different things...

read: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

