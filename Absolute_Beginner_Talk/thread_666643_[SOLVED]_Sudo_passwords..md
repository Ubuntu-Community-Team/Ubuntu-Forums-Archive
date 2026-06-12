---
title: "[SOLVED] Sudo passwords."
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-01-13
i dont want the sudo password to be my account password.
for obvious security reasons.

when i sudo i would like it to ask for a different password other than my login.

just like PCLinuxOS.

is this possible?

my friend told me to create a root password and ```
sudo su
``` wheneve ri want higher privs.
i dont want to do that.

is there a way to get it to ask the 'root' password on my account?
so when i 'sudo' it will ask for the root sudo password rather than mine?

sorry if its a bit confusing, as i said PCLinux is a perfect example of what im after.

to me, security is very important in a system.
and how Ubuntu is at the moment is well, useless if you are indeed hacked.

---

### Post by PetePete on 2008-01-13
you need to enable the root account to do this.
sudo passwd root

then after that, i think you can just run su and type in root password, although i've not tried this on ubuntu

the ubuntu method is tried and tested and IS secure, even if you are hacked the attacker can not gain access to your password (unless you store in a file, or keylogger i suppose, but these would be the same as a normal root password problems.)

---

### Post by p_quarles on 2008-01-13
From a security standpoint, using sudo vs. using a separate root password are completely equal. Unless you are giving out your sudoer password to strangers, having a separate root password won't make a bit of difference in terms of system hardening.

It is a good idea, though, in many cases to use a non-privileged account for your normal activities. If that's what you're after, that's super easy: just create a new user without sudoer privileges.

If you would rather keep your current user name and give the new account administrative privileges, that's also easy:
```
sudo useradd -G admin administrator
```Then remove the old user from the admin group (the group that has full sudoer privileges in Ubuntu):
```
sudo deluser skymera admin
```And of course you'll need to log out before that last change takes effect.

EDIT: It just occurred to me that you'll probably want to set a password on the sudoer account before removing sudo privileges from the normal user:
```
sudo passwd administrator
```
Otherwise, you'd need to bother with recovery mode. /EDIT

---

### Post by Steveway on 2008-01-13
Using sudo is actually more secure.
Why? Because someone breaking in does also have to guess your username and your password.
With a root account he only has to guess the password.

---

### Post by asmoore82 on 2008-01-13
> **Steveway said:**
> Using sudo is actually more secure.
Why? Because someone breaking in does also have to guess your username and your password.
With a root account he only has to guess the password.

EXACTLY RIGHT!

with a sudo style system:
if you never setup a root password,
you can check through the logs of people trying to crack the root password via SSH, and just laugh and laugh

They would have to know your username before they could realistically even begin to guess a passwd.

---

### Post by p_quarles on 2008-01-13
Any cracker who has the tiniest chance of discovering a good password would be able to get the system's user names in about two minutes. An account name is not a security measure, and that's not a particularly good reason for using sudo. 

But: let's not rehash the sudo vs. root debate here. The OP's question has been, in my opinion, answered. If anyone has a better way of accomplishing the task, please post it.

---

### Post by aysiu on 2008-01-13
This thread contains some more solutions:
[Different login and sudo passwords](http://ubuntuforums.org/showthread.php?t=181877)

I hope that helps.

But, no, having a separate root account is *not* inherently more secure than Ubuntu's default *sudo* model.

For more information, including pros and cons for both sides, read this link:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by daimaru on 2008-01-13
um i enabled my root account a while back with sudo passwd,
is there a way to undo that? get rid of the root account again?

thx

---

### Post by p_quarles on 2008-01-13
> **daimaru said:**
> um i enabled my root account a while back with sudo passwd,
is there a way to undo that? get rid of the root account again?

thx
You don't get rid of it, you just lock it:
```
sudo passwd -l root
```

---

### Post by daimaru on 2008-01-13
> **p_quarles said:**
> You don't get rid of it, you just lock it:
thx p_quarles

---

### Post by asmoore82 on 2008-01-14
> **p_quarles said:**
> Any cracker who has the tiniest chance of discovering a good password would be able to get the system's user names in about two minutes.

[SIZE="3"]yeah, How?[/SIZE]

---

### Post by p_quarles on 2008-01-14
> **asmoore82 said:**
> [SIZE="3"]yeah, How?[/SIZE]
How would they get the password? Same way. Your username is very unlikely to be an encrypted, semi-random string of 10+ characters, however.

---

### Post by skymera on 2008-01-14
> **aysiu said:**
> This thread contains some more solutions:
[Different login and sudo passwords](http://ubuntuforums.org/showthread.php?t=181877)

I hope that helps.

But, no, having a separate root account is *not* inherently more secure than Ubuntu's default *sudo* model.

For more information, including pros and cons for both sides, read this link:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

but if your account is hacked, threy know your password.
which is your sudo password.

so in the event of hacking sudo is infact useless in that situation

i think it protects yourself from yourself.

i check the links

---

### Post by p_quarles on 2008-01-14
> **skymera said:**
> but if your account is hacked, threy know your password.
which is your sudo password.

so in the event of hacking sudo is infact useless in that situation

i think it protects yourself from yourself.

i check the links
I would do some research into how Linux protects passwords before jumping to that conclusion. In fact, your password isn't stored anywhere on the system: it simply matches a hash that's stored in /etc/shadow. Much the same as with a public key pair or an MD5 hash, the hash itself provides no clue as to what the matching password is. Extracting the matching password is a long, CPU-intensive process involving brute force. The better your password, the more likely that you'll need BlueGene to crack it. 

What's more: the /etc/shadow file is only readable by root. Gaining access to this file would require that the attacker *already know* your sudoer password, or have found a backdoor to root access. In either case you'd be hosed anyway.

---

### Post by skymera on 2008-01-14
hmmm.

ok, that. you even

has made that clear.
i have recently changed my password which now contains capiltals, symboles, numbers and letters.

[quote=p_quarles] What's more: the /etc/shadow file is only readable by root. Gaining access to this file would require that the attacker already know your sudoer password, or have found a backdoor to root access. In either case you'd be hosed anyway.[/quote]

Seems like it would require uber time to crack. =|

and your right, i dont virutally no reserach on the passwords, never crossed my mind actually.
i reserached other things.

so after all this, i think im going to leave the pass how it is, or strengthen it more.

Thanks

---

### Post by asmoore82 on 2008-01-14
I'm talking specifically about remote attacks on my SSH server.

On a non-sudo system, they already know that root is the admin account,
so they can skip to the password guessing stage.
(And I used to check my logs and ban IPs with more that 30 or so guesses.)

On Ubuntu with sudo, however, they assume root is a viable account and
skip to the password guessing stage, but they will NEVER get in that way.
There is no way for the would-be attacker/cracker to even know what
username to try to break in with unless they know me from other sources
AND can somehow match me to my IP.

In this particular case, just the mere presence and setup of sudo has enhanced my security.

---

