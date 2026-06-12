---
title: "Disabling root account"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by kenweill on 2006-01-02
Some or most say that it is discouraged to use the root account. That I should use "sudo" instead of using the root account.

Some say that root account is disabled by default in Ubuntu. It is only enabled after you assign a password for root.

Now, what if i have assigned a password for root, can I disable it back?

A user from another forum deleted the root account and can't run sudo command anymore. Advices from different users was to reinstall Ubuntu, since root account has been deleted.

What is the safest way to disable the root account?

---

### Post by Zelut on 2006-01-02
Root is only accessible in Ubuntu if you have set the root password (ie; sudo passwd root).  To disable this again use this command: sudo passwd -l root

---

### Post by kenweill on 2006-01-02
OK.
Thanks alot.

---

### Post by steve.horsley on 2006-01-03
There's a big difference between disabling the root account  - giving it an impossible password so you can't actually log in as root, and deleting the root account completely. Ubuntu installs with a disabled root account, but you can still run commands with root privilege by using the **sudo** (Super User DO) command. If you delete the root account, sudo is just trying to run things as a non-existent user which is doomed to failure.

If you like, you can set a a valid password to the root account with the command **sudo passwd root**, and disable it again with **sudo passwd -l root**.

---

### Post by sammydee on 2006-01-04
Why would you want to disaable the root account? Why is it such a security risk? Surely if the password is just a random collection fo letters and numbers that's pretty hard to guess. Also, if a user account can do whatever root can do through sudo, why would a root account be more risky anyway?

Sam

---

### Post by newuser111 on 2006-01-04
[QUOTE=sammydee]Why would you want to disaable the root account? Why is it such a security risk? Surely if the password is just a random collection fo letters and numbers that's pretty hard to guess. Also, if a user account can do whatever root can do through sudo, why would a root account be more risky anyway?

Sam[/QUOTE]

root is not a security risk in itself, its only if people decide to login to X as root, windows xp style

---

### Post by earobinson on 2006-01-04
also... if you have the root account enabled.... but you never use it... and your password is good. your system is just as secure as having it disabled.

this is what I do most of the time if im only doing one command now that my timer is set to 1 min ... (hope 23megs dont read this we always argue over su or sudo)

---

### Post by graham_hamblin on 2006-01-04
I just installed ubuntu 5.10 off the Linux Mag DVD and it's very impressive.   

I have read the foregoing but still have a problem signing in as root, I don't know the password, I can't set one using "sudo passwd root" and entering one.

Been using Slackware for around 12 years and would appreciate the answer to this one.    Thanks in anticipation.

---

### Post by hillbilly on 2006-01-04
hmm...thats funny it worked for me ! I just typed in the command entered the passed,was prompted to type the passwd one more time and then I could su to root.

---

### Post by graham_hamblin on 2006-01-04
Thanks hillbilly

I find it odd too as I have used sudo apt get and installed the whole of KDE online without problem.   I am delighted with ubuntu but could never live without a root log in to a console.

---

### Post by earobinson on 2006-01-04
check my sig for MY FAQ first question.... The answer is there.

---

### Post by steve.horsley on 2006-01-04
[QUOTE=graham_hamblin]I have read the foregoing but still have a problem signing in as root, I don't know the password, I can't set one using "sudo passwd root" and entering one.[/QUOTE]

Don't forget that when you go sudo passwd root that sudo will probably first ask for **your** password, and only then ask you for the new root password (twice).

Other ways are:
sudo bash
passwd 
or:
sudo su -
passwd
or:
sudo -s
passwd

---

### Post by graham_hamblin on 2006-01-05
For anyone as thick as I am the answer is:

sudo passwd root
enter your existing user passwd
enter a passwd for root
confirm the passwd for root
the root account is now active
Thanks to my mate Ted Wager

I can now sign in as root in a console in what I would consider the normal way and I am at a loss to understand why the root account is disabled in the first place.

Thanks for the above help folks.   I hadn't seen the replies before posting :-(

---

### Post by linus_torvalds_2006 on 2006-01-05
As I have read in several posts before coming to this one, the "root" account is disabled in Ubuntu by default, and you should almost never have to use it.  Now, of course, there are some programs in Ubuntu that can *only be run as "root,"* so, more than likely, you should almost always stay away from those programs.

Actually, I prefer to run the Ubuntu Live CD instead of installing the OS directly to the hard drive; it's much easier to use that way.  The only disadvantage is that, because the Live CD is read-only, you cannot save any of your settings anywhere.

On the other hand, *some* programs will run fine under your own user account, so I don't exactly see why you would even *need* the "root" password.

---

### Post by Madpilot on 2006-01-29
[QUOTE=linus_torvalds_2006]As I have read in several posts before coming to this one, the "root" account is disabled in Ubuntu by default, and you should almost never have to use it.  Now, of course, there are some programs in Ubuntu that can *only be run as "root,"* so, more than likely, you should almost always stay away from those programs.[/QUOTE]

You don't need to stay away from them, you just need to be aware that when you're using them you're deeper into your system than you usually are. Things like Synaptic and some of the other configuration tools can only be run with sudo/root, but there's no need to "stay away from them" - in fact, you'd be really crippling your use of Ubuntu if you did!

Also, I haven't see this posted to this thread, but have a look at [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) for the standard rundown of how Ubuntu handles sudo and/or root, and how to tweak that if you don't like it. (and why NOT to tweak it without good reason, even if you're used to how other distros handle things...)

---

