---
title: "[B]SU root question[/B]"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by chemicalgr on 2007-06-05
I'm running ububtu feisty and i want to su root but authedication fails,what i should do about that?

---

### Post by taurus on 2007-06-05
Just use sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by starcraft.man on 2007-06-05
> **chemicalgr said:**
> I'm running ububtu feisty and i want to su root but authedication fails,what i should do about that?

Ummmm, whats wrong with using Sudo? Thats what Ubuntu is meant to use. Explanation of why and how is [here]("https://help.ubuntu.com/community/RootSudo"). Far as I know, su doesn't work unless you turn it on yourself after installing Ubuntu.

Edit: HA! taurus posting right before me with same link, MIND READER!!!

---

### Post by chemicalgr on 2007-06-05
Actually let me know this,the root passwd is different from my first(by installation) user passwd?or it's auto-generated after the installaton

---

### Post by taurus on 2007-06-05
What are you trying to install?

p.s.  Hi there,  starcraft.man...

---

### Post by chemicalgr on 2007-06-05
nothing now,i just  want a full access on my system on any time
..."It's a Zerg Leister...!"

---

### Post by starcraft.man on 2007-06-05
> **chemicalgr said:**
> ok then how can i become a root then

Well, you don't really become root. Ya just use sudo whenever you want to execute a terminal command with temporary root powers.

```
sudo <command> 
```

thats it (no <> just the command name, like lspci). If its a graphical app your launching from terminal, you use:

```
gksudo <command>
```

and if you are planning on a very long session with the terminal (I've had a few of those...)

```
sudo bash
```

that will force you to root priveledges for the duration of the terminal session. Not really recommended, I only do it the odd time...

Thats about all ya need to know I suppose, if theres something in particular ya need to install I'd direct ya at [ubuntuguide.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

Edit:
 > **chemicalgr said:**
> nothing now,i just  want a full access on my system on any time
..."It's a Zerg Leister...!"

Well, the point of sudo is so that you never do have complete access to your system.... its meant to be a security limitation.

---

### Post by taurus on 2007-06-05
Just use the sudo command if you need to install something or modify something and use the same password that you use to log in with.  Otherwise, use your regular account.

---

### Post by CREEPING DEATH on 2007-06-05
There is no root accout by default, most commands can be done by:
```
~$ sudo COMMAND
```
If you need to run something as root, I just use:
```
~$ sudo bash
```

CD

---

### Post by chemicalgr on 2007-06-05
You are cool and measured...! (greek expression)
hehe
thanks.

---

### Post by Nekiruhs on 2007-06-05
Umm, you could use 
```
sudo su
```
if you must.
It always fails authentication if you dont sudo su

---

