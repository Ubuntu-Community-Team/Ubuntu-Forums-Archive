---
title: "problem with ubuntu."
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by OrAtE! on 2005-12-06
i just installed ubuntu v5.04 for intel x86, and i have a little problem...   "root" access cannot be achieved on the main ubuntu login screen, i mean i can log in to ubuntu as "root", that i need to because of the write privileges...  i need to "VI" some root ownered files and need to paste some stuff on it.

BTW the instalation process never asked me for "root" credentials...   i could change the pass of "root" by the the user manager, but kinda weird that the most important user on the system is left in that unimportance.

---

### Post by jwd45244 on 2005-12-06
1) login as your normal user
2) start a terminal window
3) sudo ... (whatever command you were going to use as 'root')
4) it will prompt for your password (this is the one for your normal user)

sudo basically let's you be "root" for the duration of the command

---

### Post by Joe_CoT on 2005-12-06
One of the biggest differences between ubuntu and other distros of linux is that ubuntu, for all intents and purposes, doesn't have a root account. this makes it more secure in many ways, and because it means users won't be tempted to run as root, it's less likely for someone to mess up their system inadvertantly.

precede commands you want to run as root with the sudo command. the first time you run sudo in a terminal, it'll ask for your password (your user password). after that it'll let you use sudo for as long as that terminal is open. A bit of a pain compared to logging in or su-ing as root for configuring stuff, but not that big a deal.

---

### Post by OrAtE! on 2005-12-06
i used "sudo" and it ask me for my user pass.... not root pass :???:...

but i was able to write in the file this time with "vi", why was that? the file was tagged as "root property" and i dont identified as root :???:

---

### Post by OrAtE! on 2005-12-06
ahh...   this was my command:

sudo -u root vi profile

---

### Post by Joe_CoT on 2005-12-06
you didn't need to do that. all you needed to do was use:
sudo vi profile

the sudo command runs things with root privileges. that's it.

---

### Post by OrAtE! on 2005-12-06
ok. thanks... ill be trying.

---

### Post by aysiu on 2005-12-06
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by lreyes6 on 2005-12-06
if you want to change or set a root password you just do 
```
su root
``` then wil ask for the root pass and confirmation... 
but with sudo any root command goes fine

---

