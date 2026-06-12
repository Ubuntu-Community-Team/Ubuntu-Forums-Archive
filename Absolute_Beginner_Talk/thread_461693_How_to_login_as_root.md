---
title: "How to login as root?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by jingdejun on 2007-06-02
I tried to login as 'root' on login screen, but was told administrator is not allowed to login using this screen. What happen?

During installation of Ububtu Feisty, I remember did not set acount for administrator, root.

---

### Post by drowner on 2007-06-02
You don't need to login in as root.

The root password is randomly set.

You can do all the admin tasks using the 'sudo' command.
The first account created during install is the superuser, and has these privileges
May I ask why you wish to log in as root?

---

### Post by jonward0690 on 2007-06-02
Well first you need to type in"sudo passwd" to set your root password then you need to go to system,preferences,then to login windows the you need to go to security and click allow local system admins to graphically   login.

---

### Post by drowner on 2007-06-02
I know there are no 'rules' on this forum

But I don't agree with teaching what appears to be a new user how to enable root login, unless they have a damn good reason to need to root login, and I can't think of one.

We should be encouraging sudo use.

But thats just my opinion.

---

### Post by jonward0690 on 2007-06-02
> **drowner said:**
> I know there are no 'rules' on this forum

But I don't agree with teaching what appears to be a new user how to enable root login, unless they have a damn good reason to need to root login, and I can't think of one.

We should be encouraging sudo use.

But thats just my opinion.

Well I new how to login to root the first week when I had Ubuntu and I never broke it from loging to root every now and then.

---

### Post by Death_Sargent on 2007-06-02
> **jonward0690 said:**
> Well I new how to login to root the first week when I had Ubuntu and I never broke it from loging to root every now and then.

that maybe true but as root you are susceptible to viruses and even hackers.

The only reason to graphically login as root is to fix stuff while preferably offline

---

### Post by drowner on 2007-06-02
> **jonward0690 said:**
> Well I new how to login to root the first week when I had Ubuntu and I never broke it from loging to root every now and then.

Well, good for you.

I have never logged in as root, and I have never needed to.

---

### Post by jonward0690 on 2007-06-02
> **drowner said:**
> Well, good for you.

I have never logged in as root, and I have never needed to.

Being able to log in as root has saved me a few times because I messed the system up from doing othere things to it.Not being mean cause you are rite that beginners should not know how to do that.Sorry if I offended you.

---

### Post by drowner on 2007-06-02
They can KNOW how to do it, they just need to be instructed that it is a risky thing to do, and as such, I always ask why they want to do it, because, i can guarantee you, there is a sudo command for whatever they are trying to do.

---

### Post by jonward0690 on 2007-06-02
> **drowner said:**
> They can KNOW how to do it, they just need to be instructed that it is a risky thing to do, and as such, I always ask why they want to do it, because, i can guarantee you, there is a sudo command for whatever they are trying to do.

Well the only reason I enable the root graphical login is because I broke sudo once and you can fix it if you can login to root,it was my fault I tried to make firestarter run without a password

---

### Post by drowner on 2007-06-02
Ok, fine, whatever.

I'm not sure how you could break sudo, but thats fine.

If this fella has broken sudo, then we can fix it, but he has probably (as is often the case when someone wants to log in as root) just 'heard' about it, or got some advice that pertains to a non-sudo distro of linux.

---

### Post by jonward0690 on 2007-06-02
> **drowner said:**
> Ok, fine, whatever.

I'm not sure how you could break sudo, but thats fine.

If this fella has broken sudo, then we can fix it, but he has probably (as is often the case when someone wants to log in as root) just 'heard' about it, or got some advice that pertains to a non-sudo distro of linux.

It is not hard to break sudo,to mess with sudo just type this in"export EDITOR=gedit"then this"sudo visudo" then mess with the file and if you mess with it like I did every time you try to sudo you will get a error.

---

### Post by drowner on 2007-06-02
Well, OK.

Why you needed to do that to set up a firewall is beyond my comprehension, but it doesn't matter, we are bumping a thread for no good reason.

---

