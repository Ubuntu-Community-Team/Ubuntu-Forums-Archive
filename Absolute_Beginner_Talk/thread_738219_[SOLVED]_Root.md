---
title: "[SOLVED] Root ?"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by eaglehorse on 2008-03-28
How do you change to a root user in dapper?This is confusing me.

---

### Post by DBrocks on 2008-03-28
All commands in the terminal:


For permanant root login:
```
sudo su
```

for temporary root access:
```
sudo COMMAND
```

for root access in the GUI,
```
gksudo
```

Good luck!

~Dan

---

### Post by eaglehorse on 2008-03-28
[LEFT]thank you
8)
[/LEFT]

---

### Post by Jimmy Johnson on 2008-03-28
Buntu don't come with user root, to get root/SuperUser you need to open a console and type: sudo passwd root

After you do that you will have a root user account and be able to use SuperUser/su.

---

### Post by adelahunty on 2008-03-28
Another option - and a bit risky, as with all root things - is simply:

```
sudo bash
```

...or whatever your shell of choice is.  Lets you type things until you utterly destroy your setup... ;)

---

### Post by DBrocks on 2008-03-28
> **eaglehorse said:**
> [LEFT]thank you
8)
[/LEFT]


No prob. There* is *a thank-you feature.
nah, I'm just being vain. :lolflag:

and also, mark this thread as solved. It makes the people helping others lives easier, and it makes the lives easier of people looking for a solution.

---

### Post by mrsudo on 2008-03-28
DBrocks pretty much nailed it

---

### Post by ruibernardo on 2008-03-28
Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo). It's very important!

If you have to many comands to be executed with sudo, change to a «root» prompt:
```
$ sudo -i
#

```
Type "exit" to return to your normal and unprivileged user prompt.

---

### Post by DBrocks on 2008-03-28
> **epimeteo said:**
> Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo). It's very important!

If you have to many comands to be executed with sudo, change to a «root» prompt:
```
$ sudo -i
#

```Type "exit" to return to your normal and unprivileged user prompt.

I explained that. 
```
sudo su
```
does the same thing :)

---

### Post by Oldsoldier2003 on 2008-03-28
> **Jimmy Johnson said:**
> Buntu don't come with user root, to get root/SuperUser you need to open a console and type: sudo passwd root

After you do that you will have a root user account and be able to use SuperUser/su.

no. that is incorrect. you do NOT have to enable the root account in order to use sudo. Please do not give false information that can cause a new user to unintentionally create a breach of the debian security model.

---

### Post by DBrocks on 2008-03-28
PEOPLE: Stop posting suggestions on a [solved] thread! Thanks!

---

### Post by Duck2006 on 2008-03-28
>  Originally Posted by Jimmy Johnson  View Post
Buntu don't come with user root, to get root/SuperUser you need to open a console and type: sudo passwd root

After you do that you will have a root user account and be able to use SuperUser/su.

You can do this to log in as root ie at log in

user name root
passwork (root password)

and you login as root user.

Not sure if you can still do this, i know it's not a good idea to for security  reason.

---

### Post by ruibernardo on 2008-03-28
Jimmy Johnson, please read the link I [posted earlier]("https://help.ubuntu.com/community/RootSudo") and also this: [New forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201"). 

There is a difference in creating a root password or accessing to root privileges without a root password. Creating a root password is a security risk that must be taken only if you really know what your doing. I don't think it's the case here. You simply told to create a root password.

Again my suggestion is this:
```
$ sudo -i
#
# exit
$
```

---

### Post by ruibernardo on 2008-03-28
Sorry DBrocks about pointing you. It was Jimmy Johnson the told to create a root password.  I'll edit my previous post.

You can do what you said, but it's not the ideal way of doing it. "sudo -i" is the best one, imo.

---

### Post by DBrocks on 2008-03-28
> **epimeteo said:**
> Sorry DBrocks about pointing you. It was Jimmy Johnson the told to create a root password.  I'll edit my previous post.

You can do what you said, but it's not the ideal way of doing it. "sudo -i" is the best one, imo.

Lol, its okay. I was like WTH? lol. I prefer sudo su. It takes me too long to find "-" lol.

---

### Post by Jimmy Johnson on 2008-03-28
> **epimeteo said:**
> Jimmy Johnson, please read the link I [posted earlier]("https://help.ubuntu.com/community/RootSudo") and also this: [New forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201"). 

There is a difference in creating a root password or accessing to root privileges without a root password. Creating a root password is a security risk that must be taken only if you really know what your doing. I don't think it's the case here. You simply told to create a root password.

Yes, that is correct, what I posted only creates a root password so a person can use su/SuperUser, they will still not be able to login as root, as I posted above I do not advocate logging in as root, it is simply not needed.

But I think you for your warning and will simply not reply to such post in the future. :)

---

### Post by Jimmy Johnson on 2008-03-28
> **Oldsoldier2003 said:**
> no. that is incorrect. you do NOT have to enable the root account in order to use sudo. Please do not give false information that can cause a new user to unintentionally create a breach of the debian security model.

Actually you are getting your Ubuntu security mixed up and calling it Debian security, Debian don't use sudo and I don't know of any other distro outside of buntu that uses sudo and unless you know how to manage the time you are logging in while using sudo it is actually more of a security risk than using su.

Don't get me wrong, I'm not advocating logging in as root, there is no need to, on the other hand if you have not used su or SuperUser File Manager you don't know what you are missing and the poster asked about "root" and I told the poster about "root".

---

