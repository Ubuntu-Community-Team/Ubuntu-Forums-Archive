---
title: "Ack!  Install problems"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by msharelick on 2007-05-04
Hi:

I installed the desktop 7.04 version on my Dell 700 M laptop.  I used the guided partitioning method.  

Now, the following situation exists:

1)  The install did not give me the opportunity to set my root password. 

2)  It did not set up a dual boot situation so I can't get my Windows XP partition back!

How do I fix these two problems?

Thank You

Matthew Harelick

---

### Post by MST3Kakalina on 2007-05-04
I don't know how to fix your dual boot problem, but Ubuntu doesn't create a root account; it uses sudo instead.  So to get root access for a command, you type **sudo *command*** and then give your account password at the prompt.  Or do you mean you were never prompted to make ANY kind of account....?

---

### Post by Sef on 2007-05-04
> ) The install did not give me the opportunity to set my root password. [QUOTE]

Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo").

[QUOTE]2) It did not set up a dual boot situation so I can't get my Windows XP partition back!


Open the Terminal (Applications > Accessories > Terminal)

then type this command:

```
sudo fdisk -l
```

and paste the results from it in a new post here.

---

### Post by msharelick on 2007-05-05
I looked at my disk with fdisk and confirmed that in fact the installation wiped out my windows partition.  This is really annoying.  I would think that the "Guided Install" would be safer than this.  Both SUSE and RedHat have a guided install that is safer than this. 

Matthew

---

