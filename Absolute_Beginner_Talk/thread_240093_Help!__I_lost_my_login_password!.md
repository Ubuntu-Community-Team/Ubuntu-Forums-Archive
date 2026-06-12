---
title: "Help!  I lost my login password!"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by jgould on 2006-08-20
Hi everyone.

Let me preface this with saying that I am an absolute beginner at Linux/Unix.  So of you help me, please lead me step by step.

I remember my login name into the Ubuntu operating system, but I cannot remember my password for the life of me.

Is there any way at all, even hacks, to try and recover it?  Or am I screwed and looking at a complete reinstall?

Please help?
Thank you,
John

---

### Post by b_martinez on 2006-08-20
try booting into the rescue mode. Log in as root and type this 

passwd "yourUSERname"

follow the prompts.
If you are the original installer/owner of the computer, you should remember the root password.If you are trying to hack your siblings computer, you are out of luck. LOL [http://ubuntuforums.org/images/smilies/icon_mrgreen.gif](http://ubuntuforums.org/images/smilies/icon_mrgreen.gif)
Bill

p.s. this will allow you to generate a new password for your account
B

---

### Post by ajgreeny on 2006-08-20
I think when you start up in recovery mode (not rescue mode) you are already in root and can then go as suggested by b_martinez.  There is no root password by default in ubuntu, so don't bother trying to remember it or looking for it as your own pw is the only one set up at install.

---

### Post by b_martinez on 2006-08-20
> **ajgreeny said:**
> I think when you start up in recovery mode (not rescue mode) you are already in root and can then go as suggested by b_martinez.  There is no root password by default in ubuntu, so don't bother trying to remember it or looking for it as your own pw is the only one set up at install.

Sorry, I forgot I had created a password for root in my system.
Bill

---

### Post by ajgreeny on 2006-08-20
Just out of interest, why did you decide to set up a root password instead of using the sudo system in ubuntu?  I've used both systems in different distros of linux and find sudo so much easier than a separate login once you are used to it.  Next time I suggest you try sticking with the system default of sudo and no root account and see how you get on.

I don't know how you can deal with the loss of root password, unfortunately, unless using the live CD and mounting your ubuntu install will allow you to reset the root password.  No doubt someone else will know if it is possible. 
Best of luck!

---

### Post by b_martinez on 2006-08-20
Primarily, it is a habit. 99% of the tme, I use sudo. But, I tweak things a lot. When I hose a system, I find it easiest to log in as root, and fix my mistakes. Day before yesterday, I hosed my X system, and had it back up in about 5 minutes.[ I was learning aptitude and adept, still am.[http://ubuntuforums.org/images/smilies/icon_mrgreen.gif](http://ubuntuforums.org/images/smilies/icon_mrgreen.gif) ] 
If I was just starting out in GNU/Linux I wouldn't be doing this, but I have FC5,Vector Linux,X-K-Ubuntu on this box, and am installing Debian on an old Gateway 433c as I type this. 
 "Anything worth doing is worth overdoing!" to quote Lazarus Long.
Bill

---

### Post by b_martinez on 2006-08-20
> **b_martinez said:**
> Primarily, it is a habit. 99% of the tme, I use sudo. But, I tweak things a lot. When I hose a system, I find it easiest to log in as root, and fix my mistakes. Day before yesterday, I hosed my X system, and had it back up in about 5 minutes.[ I was learning aptitude and adept, still am.[http://ubuntuforums.org/images/smilies/icon_mrgreen.gif](http://ubuntuforums.org/images/smilies/icon_mrgreen.gif) ] 
If I was just starting out in GNU/Linux I wouldn't be doing this, but I have FC5,Vector Linux,X-K-Ubuntu on this box, and am installing Debian on an old Gateway 433c as I type this. 
 "Anything worth doing is worth overdoing!" to quote Lazarus Long.
Bill

As for losing the root password, Knoppix may be an option, but I have the feeling that you need the OS root password to chroot for it.
B

---

### Post by af4k on 2006-08-31
root log-in, chroot, sudo, all these terms confuse me!
I see all of these answers as being guys showing oiff their knowledge rather than trying to help someone who is stuck.
I am arank beginner, and no one haswritten anything that gives me a clue on how to proceed.
I have a knoppix CD.
WIll that help?

---

