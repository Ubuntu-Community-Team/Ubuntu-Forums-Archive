---
title: "Root password"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by Apple 101 on 2006-06-23
I need to get access to admin options, but it asks for a root user password.  I never set a root user password, so how can I know what it is?

---

### Post by x64Jimbo on 2006-06-23
There is no root password. It's your user password. All root-level actions in Ubuntu are done through sudo.

---

### Post by oldmanstan on 2006-06-23
the password you set during the installation is the root password, try your normal password that you login with

EDIT: jimbo beat me to the punch by seconds

---

### Post by falcon15500 on 2006-06-23
Root access is disabled by default.  Generally in Ubuntu if you need to use root privs, you use the sudo, or gksudo commands.  If the password dialog box you are referring to is from within X - use your own password, as this is a gksudo prompt.

falc

---

### Post by Apple 101 on 2006-06-23
Thanks for your help everyone.  My password works fine - and yes, it was the dialog box from X.

---

### Post by frodon on 2006-06-23
This is a useful link which will learn you all you need to know : 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Apple 101 on 2006-06-23
Thankyou for that link frodon.  It was really useful.

---

### Post by WebDrake on 2006-06-23
[QUOTE=frodon]This is a useful link which will learn you all you need to know : 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)[/QUOTE]
One thing I've never understood, and which I don't think is clear from that article, is this:

What I want to do is to maintain the use of sudo, and keep root disabled.

*BUT*---I want to have to enter a different password to my own normal login when prompted after a sudo command.  It strikes me that's the most secure option on a system.

Is that possible?

---

### Post by karlsson88 on 2006-06-23
you can create 2 accounts?

---

### Post by WebDrake on 2006-06-23
[QUOTE=karlsson88]you can create 2 accounts?[/QUOTE]
Sure, you can create a second account without administrator privileges, and so can't use the sudo command.  But that seems a kind of inefficient solution for my own machine, which is used by just me.

---

### Post by aysiu on 2006-06-23
Actually, the most secure option is to create a good, strong password.

---

### Post by WebDrake on 2006-06-26
[QUOTE=aysiu]Actually, the most secure option is to create a good, strong password.[/QUOTE]
Absolutely :)

Perhaps you could clarify on one point.  My assumption was that if someone could compromise your individual account, they would know---or easily be able to work out---your password, but having a different administrative password would make it more difficult (though not impossible) for them to compromise the whole system.

... but my guess is, if you're working with a single-user machine as I am, then, different administrator password or no, if your user account is compromised, you're probably buggered anyway, and the relevance of administrator privileges is more a safeguard to make you *think* when you're installing stuff, and to prevent you doing important stuff by accident.

Having done a bit more background reading I realised that what Ubuntu has in mind with its model is that individual users can be granted varying degrees of administrator privilege, and the way Ubuntu uses sudo allows this to be done very easily without the complication of shared or multiple passwords.  I can see that in this case the absence of root would add to security, both by disguising the administrator account(s) and by putting in safety checks (the need to use sudo + password) which root does not have.

---

### Post by aysiu on 2006-06-26
Well, one way to look at it is:

If you have a username and someone compromises that username, the cracker has no idea whether that username has *sudo* privileges or not.

The cracker does know right off the bat, though, that most Linux and Unix systems have a user named root who has full access to the system. Username known. Privilege known. Only thing to guess is the password.

On the other hand, as LordHunter has pointed out numerous times, if someone compromises any account on your computer... it's only a matter of time before the entire system is breached.

It's much better to have one account with sudo privileges and a very difficult-to-guess password than a user account and a root account, each with an easy-to-guess password.

---

### Post by Apple 101 on 2006-06-27
Yes, that's true.  A hard-to-guess password is a real security item.

---

