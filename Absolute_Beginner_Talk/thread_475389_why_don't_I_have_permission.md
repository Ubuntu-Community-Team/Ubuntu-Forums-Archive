---
title: "why don't I have permission?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by kevmore on 2007-06-16
I am the only one that is ever going to use this computer, so I don't want to be told that I don't have permission.  Does anybody know how to make me master over my computer?

---

### Post by 5-HT on 2007-06-16
If you [really want to do that]("https://help.ubuntu.com/community/RootSudo"), you can edit /etc/sudoers accordingly to not require a password for anything. Please refer to 'man 5 sudoers' for information on how to do that. There are other ways to achieve what you want that have been covered many times in the forums that a simple search can reveal.

cheers,

---

### Post by Jimmyfj on 2007-06-16
For each administrative task you'll need the sudo su command in your terminal - That's for security reasons

---

### Post by freesitebuilder on 2007-06-16
The second bullet point on this page has some info on why Linux works the way it does:
[http://www.whylinuxisbetter.net/items/viruses/index.php](http://www.whylinuxisbetter.net/items/viruses/index.php)

The other pages are worth reading too, when you have a moment.

---

### Post by ramjet_1953 on 2007-06-16
The whole idea of why you are have to log in and use the sudo command is to protect your system from Internet hackers and from yourself.

If you have just come from a Windows environment, you will be only too aware of the nightmare of virus infection, trojans, keyloggers and the like.

If you want to escape from this, accept that your Linux system is secure from all of this and you need to only use root privileges when absolutely necessary.

A small price to pay for peace of mind, wouldn't you agree?

regards,
Roger :cool:

---

### Post by kevmore on 2007-06-18
Save me from myself!!!  Yes maybe it's better to leave it alone then.  Thanks for the replies.

---

