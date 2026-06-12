---
title: "when an application can't do sudo"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by icantsee on 2006-01-30
Hi,

I have an application on a Windows computer that can send a job to a Linux server. When that program sends the job, it does not use the sudo command. (I think it was  designed for distros like RedHat.) Unfortunately, I cannot edit the program to send a sudo command. The program simply makes me fill out the computer IP address, user name, password, and directory on the Linux computer. I guess the program puts the info together into one command and sends it to the server.

Anyway, since my Ubuntu computer requires that I type sudo before almost every command that launches a program, what can I do to remedy this?

Thanks in advance
-R

---

### Post by super on 2006-01-30
don't know if this is the kind of solution you want, but i think the simplest thing to do would be to enable the root account in ubuntu. it's easy.
just type:

[FONT="Courier New"]sudo passwd root[/FONT]

and enter a password for the root account.

---

### Post by towsonu2003 on 2006-01-30
[QUOTE=super]don't know if this is the kind of solution you want, but i think the simplest thing to do would be to enable the root account in ubuntu. it's easy.
just type:

[FONT="Courier New"]sudo passwd root[/FONT]

and enter a password for the root account.[/QUOTE]
I heard a couple of times (especially in automatix discussions) that this may break applications in ubuntu, which means the OP will need to do some forum searching and some reading about enabling root in ubuntu ;)

---

### Post by Ocxic on 2006-01-31
how about writing a script that will run the program using sudo for you, then have the windows machien run that script instead of the program directly.

---

