---
title: "Online as root"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by jonpon on 2007-09-24
Can anyone tell me if I'm being silly by going online as root? I'm the only user on my machine and it's just practical for me. Am I taking unnecessary  risks?

---

### Post by master_kernel on 2007-09-24
I can't think of any except that you could screw your system if you accidentally change a setting or delete a file.

---

### Post by Shazaam on 2007-09-24
-dons flameproof firesuit once again-
Yes you are. Just like with Windows admin accounts. Direct access to your file system.
Practical? How? I can surf the net just fine without being root.

---

### Post by Dr Small on 2007-09-24
> **Shazaam said:**
> -dons flameproof firesuit once again-
Yes you are. Just like with Windows admin accounts. Direct access to your file system.
Practical? How? I can surf the net just fine without being root.
But really, there is no potential security risk, and since he is the only user on the machine, as long as he is responsible enough, I see no huge risk at browsing the internet as root... :|

Dr Small

---

### Post by mysticmatrix on 2007-09-24
> **master_kernel said:**
> I can't think of any except that you could screw your system if you accidentally change a setting or delete a file.

Havn't faced one of 100 odd linux virus yet? :)
Or better some Windoze virus in Wine?

That what happens when you run in root account.

---

### Post by ThrobbingBrain66 on 2007-09-24
What is so troublesome about going online as a normal user?  Doing anything as root is taking an unecessary risk.  That's basically what you do in Windows XP (unless you've been setup as a limited user) as look what kind of trouble that can get you into.  Any program/script/whatever can do whatever it wants without approval.

---

### Post by ThrobbingBrain66 on 2007-09-24
> **Dr Small said:**
> But really, there is no potential security risk, and since he is the only user on the machine, as long as he is responsible enough, I see no huge risk at browsing the internet as root... :|

Dr Small

Surely you can see the problem with your statement.  I trust myself well enough to run everything as root, but I still don't.  The problem is I don't necessarily trust everyone around me.  They don't necesarily have my best interests in mind.  I'd rather have the peace of mind running as a normal user.

---

### Post by Dr Small on 2007-09-24
> **ThrobbingBrain66 said:**
> Surely you can see the problem with your statement.  I trust myself well enough to run everything as root, but I still don't.  The problem is I don't necessarily trust everyone around me.  They don't necesarily have my best interests in mind.  I'd rather have the peace of mind running as a normal user.
Of course. It all depends upon how every person is responsible.
It is safer to assume that Running as a regular user is safe, and recommend it to new users, but we can not state that it is unsafe to run as root, and have proof to back it up.

I myself, occasionally, run another X display as root, just for quick administratoring, and not having to enter passwords at every prompt, but that I would not recommend to new users, as it in itself is more of a risk at data loss than security.

Dr Small

---

### Post by RomeReactor on 2007-09-24
Hi. I would suggest you **don't** log in as root, particularly if your system has internet connection; there *are* vulnerabilities in the browsers, and someone *could* take control of your system through a vulnerability. Being logged in as root, you don't need to input passwords to alter system files, so neither would an attacker...

There are no benefits to run as root other than the convenience of not having to enter your password for administrative tasks, and the risks **far outweigh** the benefits.

Maybe this is an incorrect way to phrase it, but hopefully you get the idea.

---

### Post by Adramelech on 2007-09-24
Of course there are examples software is full of bugs just look the new pdf exploit.

root + bug = rootkit

and... if linux users start running the system as root, we are going to see more people focusing on making virus for linux, lets just keep the good practices =).

---

