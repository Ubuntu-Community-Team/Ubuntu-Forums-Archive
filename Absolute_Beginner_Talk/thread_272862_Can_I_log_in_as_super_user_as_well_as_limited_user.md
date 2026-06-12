---
title: "Can I log in as super user as well as limited user?"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by kpfuser on 2006-10-07
Since it has been almost a year since an unsuccessful attempt to run ubuntu from a live CD, I thought it appropriate to collect up-to-date info regarding more recent developments. In addition, following a dubious experience with a small linux distro, I came to appreciate the need to clarify matters with respect to linux alternatives first before actually tinkering with them.

This brings up the following: I would like to be able to login as super user as well as limited user using a different password for each account. Furthermore I would prefer that this capability is already built into the basic distro because in a similar experience recently, although a limited user account was built in, its activation and 'normal' use was too involved and difficult for a beginner to handle.

So here is my question restated: Does ubuntu allow the user to login as either a super user or as a limited user simply by using a separate password for each account? If yes, is this capability available in the out-of-the-box installation?

---

### Post by 5-HT on 2006-10-07
> **kpfuser said:**
> So here is my question restated: Does ubuntu allow the user to login as either a super user or as a limited user simply by using a separate password for each account? If yes, is this capability available in the out-of-the-box installation?

No. Linux was designed to be a multiuser system from the get-go, but a user account is a user account--independent of separate passwords...
Easiest thing (apart from just utilizing Ubuntu's default use of 'sudo' to escalate privileges when needed) would be to use two accounts (limited and superuser) with the possibility of using symbolic links to share all needed files/directories. 

HTH.

---

### Post by kerry_s on 2006-10-07
Yes, you can.

No, not out of the box.

Ubuntu uses sudo so the root account is deactivated. From a security stand point this is a better feature than haveing a root account, most hackers will try root first, but if the root is not active they have to guess the user name and password, instead of just the root password.

---

### Post by 5-HT on 2006-10-07
> **kerry_s said:**
> Yes, you can.

No, not out of the box.

Ubuntu uses sudo so the root account is deactivated. From a security stand point this is a better feature than haveing a root account, most hackers will try root first, but if the root is not active they have to guess the user name and password, instead of just the root password.

But how could you have two separate accounts with the same username but separate passwords? Or am I mistaken about my understanding of the OP's question?

---

### Post by aysiu on 2006-10-07
Ubuntu disables a root login by default, but you *can* enable it by creating a password for root and then changing the login settings for the login screen to allow a root login, but... there's really no need for this.

Just create a launcher for the command ```
gksudo nautilus
``` When you click that launcher, you'll be prompted for your password, and you can browse as root *within* your otherwise limited account.

Any reason in particular to have two passwords? If you have two people (you and a friend or family member), have two passwords and make yours an administrator (not the same as root exactly). If you are the only person using your computer, and you're worried about security, just create one strong password--it's much better than having two weaker ones.

---

### Post by aysiu on 2006-10-07
> **5-HT said:**
> But how could you have two separate accounts with the same username but separate passwords? Or am I mistaken about my understanding of the OP's question?
As I understand it, the OP's question is how to have root log in as root with one password and the user log in as user with another password.

This is the standard procedure on most Linux distros, but it is not standard on Ubuntu or Mac OS X.

Ubuntu and Mac assume there's no reason to log in as root and be all-powerful for every task. Both make you user, but if you have administrative privileges, you can temporarily allow yourself root privileges for particular tasks.

---

### Post by 5-HT on 2006-10-07
> **aysiu said:**
> .  I guess I read too much into things when they're not explicitly stated. Thanks.

---

### Post by kpfuser on 2006-10-07
Thank you all for your replies. As I can see, some of you misinterpreted my questions to some extent. Likewise, I am a bit confused with some of the answers. There is probably a terminology issue somewhere, so let me try to clarify matters somewhat.

After I boot up my WinXP laptop, I am presented with a screen asking me to log in to one of two existing accounts. Both are mine (I am the sole user of my laptop) and each is protected by its own password. One account has administrator privileges. I use it when I want to install or uninstall programs, make changes to the registry, perform system maintenance, and the like. The other account is a limited account. I use it when I connect to the internet (for security reasons). This is what I would like to have in ubuntu and this thread was meant to find out if it is possible.

With this in mind, let me review some of the earlier replies.

5-HT

> Easiest thing (apart from just utilizing Ubuntu's default use of 'sudo' to escalate privileges when needed) would be to use two accounts (limited and superuser) with the possibility of using symbolic links to share all needed files/directories.

It seems that this meets my objectives. Can someone describe what privilege level is implied in ubuntu for 'limited', 'superuser', and 'root' (whether activated or not) accounts? Would it be reasonably easy (for a beginner) to set up the limited and superuser accounts following the initial installation?

aysiu

> As I understand it, the OP's question is how to have root log in as root with one password and the user log in as user with another password.

Yes, indeed! Also

> Ubuntu and Mac assume there's no reason to log in as root and be all-powerful for every task. Both make you user, but if you have administrative privileges, you can temporarily allow yourself root privileges for particular tasks.

The idea sounds workable to me but

> have two passwords and make yours an administrator (not the same as root exactly)

sounds closer to what I am looking for. So how does 'administrator' differ from 'root' and what does it take to set it up?

---

### Post by Sef on 2006-10-07
> 5-HT

Quote:
Easiest thing (apart from just utilizing Ubuntu's default use of 'sudo' to escalate privileges when needed) would be to use two accounts (limited and superuser) with the possibility of using symbolic links to share all needed files/directories.

It seems that this meets my objectives. Can someone describe what privilege level is implied in ubuntu for 'limited', 'superuser', and 'root' (whether activated or not) accounts? Would it be reasonably easy (for a beginner) to set up the limited and superuser accounts following the initial installation?


Limited is where you can only do certains things, e.g. internet, print, etc, but not be able install anything to the computer that uses sudo.

> 
Quote:
have two passwords and make yours an administrator (not the same as root exactly)

sounds closer to what I am looking for. So how does 'administrator' differ from 'root' and what does it take to set it up?

An administrator uses sudo to install programs, while not being in root itself.  For this you only need one password.  For a more detailed explantion of root/sudo, [click here.]("https://help.ubuntu.com/community/RootSudo")

---

### Post by kpfuser on 2006-10-07
Thanks Sef! Now let me see if I got things right. From reading the info in your link plus the previous replies, I am led to believe that

1. During installation I can set up two user accounts, one with administrator privileges and one limited, each with its own password.

2. Logging in as administrator would enable me to add and remove programs or perform other administration tasks that cannot be performed from the limited account.

3. Subsequently I can introduce a third (root) password to be used when I need to get temporary root privileges via the sudo tool.

Am I right?

---

