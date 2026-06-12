---
title: "can't access Synaptic Package Manager"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by RedKing on 2005-11-29
Hi

When i try to access the Synaptic Package Manager, it asks for a password.
I type in my password (user pwd) and nothing happens. I have also tried entering the root password (which is created---from a previous post) but i still can not get access.

Any ideas as i am really new to this.

---

### Post by Kapre on 2005-11-29
[QUOTE=RedKing]Hi

When i try to access the Synaptic Package Manager, it asks for a password.
I type in my password (user pwd) and nothing happens. I have also tried entering the root password (which is created---from a previous post) but i still can not get access.

Any ideas as i am really new to this.[/QUOTE]

Redking - root password is different from the admin password that SPM is asking for.  If you know your root password, can you try logging in as root and then modify the rights (on System---Administartion----Users and Groups) of your login name and you may also change the password.

K

---

### Post by Anomaly on 2005-11-29
The password it asks is the admin password, i'm assuming that you have root access so it would be the same password as your login.

    hope this helps

---

### Post by Xian on 2005-11-29
If you have a root passwd then you can open Synaptic w/this command:
$ gksu synaptic

I would also inspect your sudoers file for corruption.
It should be run as root w/this command:

$ visudo

---

### Post by Books on 2005-11-29
[QUOTE=RedKing]Hi

When i try to access the Synaptic Package Manager, it asks for a password.
I type in my password (user pwd) and nothing happens. I have also tried entering the root password (which is created---from a previous post) but i still can not get access.

Any ideas as i am really new to this.[/QUOTE]

Hi, RedKing

Same here. I just installed Kubuntu last night and today I installed Synaptic. I had heard that Synaptic has fewer problems than Kynaptic so I used apt-get to grab it. It appears in the Applications > System menu but when I select it the little hourglass just turns and turns, then nothing. No program. I then noticed that Kubuntu came with a *different* package manager, Adept. Adept seems to be working, but I wish I knew if I should be using Synaptic instead.

If you're using Ubuntu maybe your problem isn't the same as mine, or maybe it is?

Good luck!

Books

---

### Post by RedKing on 2005-12-01
Thanks for the help

I edited the sudoers file, adding my username and giving me the same privileges as root.

Shes a hummin now.

---

