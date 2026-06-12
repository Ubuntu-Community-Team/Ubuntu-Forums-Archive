---
title: "HELP!! &quot;sudo&quot; not accepting password."
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by doodsangel on 2006-08-25
Finally got Ubuntu 5.10 to install to my computer and it seemed to be without any glitches except for 1.

**Does "sudo" use a different password than root? **

The reason I'm asking is, when I try to run any of the system apps, it asks me a password, and when I type my root password, it tells me the password is incorrect.

Now I am 100% sure that I am using the correct password, because when I open a terminal, **I can do a "su" and then type *root password *and it works 100%**. While in **"su #" **mode, I can also change the root password and the like, but as soon as I try to do a **"sudo"** command, I'm  met by a brickwall. Even **sudo passwd root **fails asking me a password and then not accepting it. :confused: .

Does anybody have any ideas?

---

### Post by amo-ej1 on 2006-08-25
with su you have to enter the password of the user you wish to change to
with sudo you have to setup /etc/sudoers first and if you set it to prompt for a password (which is recommended) you have to enter YOUR OWN password, not that of the user you are changing to.

---

### Post by doodsangel on 2006-08-25
Cool. Thanks.:p

---

### Post by drtvasudevan on 2006-08-25
by default there is no root setting in ubuntu.
unless you setup a root specifically there will be no root.
su is actually set user. not super user etc imagining root.

most of the root functions are done through prepending sudo to commands.
it will ask for the password only if it is a root function.

---

### Post by doodsangel on 2006-08-25
Well, when I do an action eg. "Disks", it asks for a password... I'm sure I have tried the password of the user I'm logging in with as well. That also failed.... But I will try again tonight.

When I installed, I set a root password as well as created an account for myself to use....

---

### Post by FuriousLettuce on 2006-08-25
We'll start by making sure you're part of the admin group. Log in as root [if you can't log in as root (i.e. you haven't set it up / don't have the password), press escape when GRUB gives you the option (when booting up) and choose recovery mode. That will log you in as root.]

Once you're logged in as root, do

```
usermod -g admin username
```

where username is your username.

If that doesn't work, check the /etc/sudoers file:

```
nano /etc/sudoers
```

there should be a line similar to this:

```
%admin ALL=(ALL) ALL
```

if not, add it. [I think that code's right, I'm not sat at my ubuntu box - if it doesn't work, just google /etc/sudoers to make sure the syntax is correct.]

---

### Post by doodsangel on 2006-08-25
Cool... I'm going to try that tonite.

I really need to get this right so that I can configure my sierra aircard, otherwise no internet for me. ::neutral:

---

### Post by hotbrainz on 2006-08-25
If all else fails just do this:

sudo passwd root

it will ask you to enter your new linux password... so enter your new password. 
There we go, its done

Cheers

---

### Post by FuriousLettuce on 2006-08-25
*NB: The above fix will have you running as root all the time, which is a great security risk*

---

### Post by doodsangel on 2006-08-25
> **hotbrainz said:**
> If all else fails just do this:

sudo passwd root

it will ask you to enter your new linux password... so enter your new password. 
There we go, its done

Cheers

**sudo passwd root** <-already tried this. It asks me for a password, which is not accepted when I type either my username password or root password.

---

### Post by hotbrainz on 2006-08-25
Then try

> su passwd root

have you tried this too :>

---

### Post by doodsangel on 2006-08-25
:) No,  but I will tonight.

---

### Post by harisund on 2006-08-25
Let me see if I can get everything correctly here. 

(1)'root':
the traditional name given to the one user on *nix machines who can potentially do everything, including the famed 'rm -rf /' . Unlike all other users whose home directories are in /home/ this guy's home directory is /root. For most practical purposes, this person is just another user. Meaning he can be put in groups and all that... but remember, this user is extremely powerful. 

So powerful that Ubuntu by default comes with this user disabled. 

(2)regular user
Anybody who can log in to the machine. The user is given a directory to store data in (/home/username) and a password for himself. On some machines (you can set it up on Ubuntu as well) the user has an upper limit on how much space he can occupy.

Each user can be in multiple groups. The concept and necessity of groups is explained next. 

Now, all files created by the user by default are modifiable by the user (and root of course.) and by no others. However for certain purposes, there might be a bunch of users needing access to modify files. In such a case, they are all put in a 'group' and that file is given the permission to be modified by the group. It might by owned by that 'user' but can be modified by everyone in the 'group'. 

executing 'groups username' lists all the groups that the username is a part of on the system. By default on my Ubuntu system I a part of
```
harisund adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
```

For further information I encourage you to look the man pages of commands like newgrp and id -g

(3) passwd {username}
If entered with no {username} you can change your own password, and if entered with {username} you will be changing the username's password. 

Naturally, only the root can change someone else's password. If you are not root you can't change other's passwords. 

(4) su (and su -, and su - username)
Typically means becomes su, or super user. When executed as is, it means you want to become root, which means you will need to enter root's password. Note that this will not work by default in Ubuntu, since there is no root password in Ubuntu. 

The - is a better way to do it, since it will automatically change the environment variables. If you don't understand what that means, just know it is better to do su - than su. 

Also, su - username literally means "become that username." Think of "su -" as being equivalent to "su - root" 

Therefore, if I give you the password to my account on a system, you can log in with your account, enter "su - harisund" and become harisund. 

(5)sudo -- the ultimate beauty
sudo literally means "do as su" or "do as super user". 

Remember I said there is no root password on Ubuntu? Here's what I am talking about. By default the root password on Ubuntu has been scrambled, meaning root CAN NOT log in or run commands. 

So what do you if you need to modify system files which you can't do as a regular user? If there was a root password you could have done "su -" or "su - root". But because there isn't you use sudo. 

Now here's the part that confuses most people. When you ask for sudo, it asks a password. Now I just told you Ubuntu comes with no root password. So whose password does it ask for? Your very own !

Ubuntu misses one feature that appears on other machines with sudo. The first time you run sudo on non Ubuntu machines you receive a message that goes like this: 

> You have been giving root previleges on this machine. Remember, it is a previlige, not a right (or something like that). Please do not misuse it and respect the other users on the system. 

You get the picture, right? 

So who can run sudo? If everybody can run sudo, then everybody can potentially become root right? 

Yes. The /etc/sudoers file determines who have the capability to call 'sudo'. Initially it is set so that "all users who are a part of the admin group can call sudo". Do you remember the groups command I mentioned earlier? Invoke that, and you will see you belong to the admin groups. One of the earlier posts asked you to do just that. Add yourself to the admin group. By default, Ubuntu adds the first user to the admin group, so that he can call sudo. 

Now, as further examples, let's break down the various commands seen here and why they didn't work, or when they will work. 

(.) sudo any-command
By default this will work. The only caveat, you have to enter *your* password, meaning the password of the username under whih you are working. Remember, this has nothing to do with whether or not the root account has a password or not. This just uses *your* password to ensure you are who you claim to be. So if you were to leave your machine for a quick coffee break, and I happen to stroll by, I can't invoke sudo. 

(.) su / su -
By default this will not work. Because you attempt to login as root (remember, this is equivalent to su root or su - root) and by default root has no password (there is a root account. Just that it has no password.) So you can practically keep typing all day and you will never be able to log in. 

(.) sudo passwd root
You are running a command as sudo, or as root. What command are you running? basically just 'passwd root' which is equivalent to 'passwd username'. Remember what I said earlier? You can only change someone's password if you are root? sudo here makes you root for that command. 

So technically, if you look at it, if you were to do 'passwd' it is equivalent to 'passwd myusername'. Similarly, if you were to do just 'sudo passwd' it is equivalent to 'sudo passwd root'. Get it? 

(.) sudo su -
Let's break it down into "sudo" and "su -". The first sudo tells the system to run the next command as root and asks your password first. What does it run? "Log in as root". So basically you are telling your system "As root, log in as root" or in other words "as root, log in" which will give you a root terminal. 

That is, these are equivalent:
---- sudo su - (run as root, and log me as root. Password - my own)
---- sudo -i (log me as root. Password - my own)
---- su - (log me as super user. Password - root's)
---- su - root (log me as root. Password - root's)

The difference, the first two ask for your password and throw you in a root shell. The second two ask you for the root password and then throw you in a root shell. 

So the first two will work by default in Ubuntu (since your password exists) and the second two will not work by default in Ubuntu (since root password doesn't exist). To make the second two work in Ubuntu, the root needs to be given a password. This can be done using

sudo passwd (as root, give password to myself (root) )
sudo passwd root (as root, give password to root) 

(.) su passwd root
This is completely wrong. First, it will look at su passwd, and attempt to log you as the user called 'passwd'. Obviously none exists, and it will complain. Understand what su does? Changes you to that user, after asking the password of *that* user. If you know the password of *that* user, great. Else bad luck.

Now, coming to one problem. Do a simple 'sudo ls' meaning list the files as a root user. Of course, this is no different from regular ls, because the listing is going to be the same. However, it should ask you for a password, and enter *your* password. 

If it doesn't accept it should spit one of two errors. One, "you don't have sudo permission", two "wrong password". What does it say?

---

### Post by doodsangel on 2006-08-25
Thank you for all the time you took in typing up this post. I REALLY REALLY appreciate it. :KS 

1. I did expert install, due to the fact that partition editor for Breezy did not allow me to edit my partition. Only gave me option to trash all 120GB of HDD and start over, and with my wife doing her Thesis for her MBA on WinXP, that was not an option. 
Meaning, I ended up with a root account as well as a user account.... **Check/Uncheck/Maybe an oops.**
2. I do have a regular user account. **Check**
3,4 Thank you. I have a cery good understanding of this now. **Check**
5. Thank you very much for explaining this to me as well... It is a lot clearer now, and it makes me think that I should do the passwd scramble on root again. I think the command it **sudo passwd -l root**

> *If it doesn't accept it should spit one of two errors. One, "you don't have sudo permission", two "wrong password". What does it say?* - ** It says that the password is incorrect.** But i cannot confirm that at the moment as the machine is at my house, and myself @ work. I doubt that it is "you don't have sudo permission", but I'm not sure. :-# 

So I think that my first plan of action tonight should be.
1. **groups doodsangel** from this make sure that doodsangel is part of the admin group.
1.5 **if (doodsangel <> admin)** <- if I get this, should I then do this: **usermod -Gadmin doodsangel**
2. **vi /etc/sudoers** and confirm that the admin group may do sudo.
3. I should be fine now, so after testing that I can **sudo**, i should issue: **sudo passwd -l root**

Is that more or less it?

Once again I thank you for your time in explaining everything.

---

### Post by FuriousLettuce on 2006-08-25
//ignore

---

### Post by harisund on 2006-08-25
Looks like you are all good to go!

---

### Post by Metacarpal on 2006-08-25
The answer to this was MUCH simpler than you guys think...

When you're using SUDO, you don't enter the root password.  You enter the password for whatever username you're logged in under.  Your sudo password is the same as your login password.

---

### Post by harisund on 2006-08-25
That's right metacarpal, but apparently the parent poster's user was not a part of the admin group. Consequently there was a root account with a root password, he couldn't use sudo, and logging backing with root and making sure he adds himself to the sudo-capable group was the only option.

---

### Post by Metacarpal on 2006-08-25
> **harisund said:**
> That's right metacarpal, but apparently the parent poster's user was not a part of the admin group. Consequently there was a root account with a root password, he couldn't use sudo, and logging backing with root and making sure he adds himself to the sudo-capable group was the only option.

Ah.  I was just looking at his first post where he specified that he was trying to use the root password and asked if sudo used a different password than root's.

---

### Post by harisund on 2006-08-25
Indeed... that was my initial impulse as well.. as well another posters :)

---

### Post by drtvasudevan on 2006-08-25
wow harisund!
what a detailed explanation.
much obliged!

---

### Post by harisund on 2006-08-25
Thanks a lot for those kind words drtvasudevan

---

