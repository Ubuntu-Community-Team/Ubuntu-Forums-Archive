---
title: "Network - not able to access other sites"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-07-18
I'm trying to use the "Places->Connect to server" functionality.

It finds my home network, and displays both PCs (I know, not a massive network!). When I try and click on the other one, I get this message:

Sorry, couldn't display all the contents of "Windows Network: <other computer name>".

Any idea how I can resolve this please?

Thanks!

---

### Post by MythicalVax on 2007-07-18
Well, I think it should be a Windows side problem. You should investigate on your Windows box and check your guest access (anonymous browsing)...
But I would not spend so much time about it... I would simply invest on my /etc/fstab entries in order to have them correctly inserted.[INDENT]Sample line for /etc/fstab:
[/INDENT][INDENT]**//windoze_computer/share_name**    /**mnt/share_name**    smbfs noauto,rw,username=**windoze_user**,password=**password**,fmask=777 0 0
[/INDENT]I would leave browsing facilities to uninformed and untrained Windows users. Ubuntu and - in general - Linux are so good at networking that you do not need to get in trouble with Windows specific matters: just keep the necessary Windows features and forget about the rest. :)
You are already evaluating an alternate method of doing the same things... Just keep going and don't look backwards!

---

### Post by qprfact on 2007-07-18
Thanks! Will give it a try!

---

### Post by qprfact on 2007-07-18
I'm a bit unclear on something - what if the user doesn't have a password on the windows pc? How do I specify that?

---

### Post by MythicalVax on 2007-07-19
Generally it is considered a very bad practice not having set a password because anyone might simply guess your username and then easily try
[INDENT]*net use \\your_ip\c$ /user:username*
[/INDENT]to gain full access to your Windows computer.

So, it is **very very very bad.**
It is so bad that the latest Windows versions - at last! - do not allow administrators accounts do this.
(If you are the computer owner, you are running an administrator account for sure and network logins should be disabled by default.)

On Windows, press *Ctr+Alt+Del* to get to the change password option and set it immediately.
On Ubuntu, run a terminal and type *passwd*.

---

### Post by qprfact on 2007-07-19
It's OK, it's not quite as bad as that! There are three accounts on the "other" PC, two of which have administrator rights and are password protected. The third (which doesn't currently have a password) is limited access only. Is that still as bad?

---

