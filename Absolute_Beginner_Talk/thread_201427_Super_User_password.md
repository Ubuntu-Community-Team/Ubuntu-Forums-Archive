---
title: "Super User password"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by rtcary on 2006-06-21
I just installed 5.10 and during the install I was not to my knowledge asked to set a password for root; just to establish a user.  Did I miss something?

Thank you.....

---

### Post by b1g4L on 2006-06-21
Go to users, and set the password for root.

---

### Post by Brunellus on 2006-06-21
Ubuntu doesn't enable the root account by default, opting instead to give the first user "sudo" access.  This is explained at length in the wiki:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In essence, it means that to do anything that needs root permissions, you prefix the command with "sudo."  You will then be prompted for a password, which is the USER password.

Sudo is a perfectly good way of doing things.

---

### Post by rtcary on 2006-06-21
[QUOTE=Brunellus]Ubuntu doesn't enable the root account by default, opting instead to give the first user "sudo" access.  This is explained at length in the wiki:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In essence, it means that to do anything that needs root permissions, you prefix the command with "sudo."  You will then be prompted for a password, which is the USER password.

Sudo is a perfectly good way of doing things.[/QUOTE]

When I try to bring up users & Groups, Gnome tries to load it and then times out.  Any suggestions?

Todd

---

### Post by Brunellus on 2006-06-21
[QUOTE=rtcary]When I try to bring up users & Groups, Gnome tries to load it and then times out.  Any suggestions?

Todd[/QUOTE]
it doesn't even prompt you for a password?

---

### Post by rtcary on 2006-06-21
[QUOTE=Brunellus]it doesn't even prompt you for a password?[/QUOTE]

Correct!  I do have Red hat Linux on a server and when I access the same item, it does ask for a password.

However, I may have stacked the deck against myself: I am trying to install Ubuntu on a Toshiba notebook that does not have an Ether net connector.  Under Win 2K I can use a wireless card.

Todd

---

### Post by newbie_buntu on 2006-06-21
Todd - I would suggest installing ubuntu 6.06 (dapper drake).  The built in configuration has a wireless adaptor and might help with your wireless on your Toshiba.  Why were you going with 5.10 in the first place? 

j

---

### Post by rtcary on 2006-06-21
I had downloaded it some time ago and found the CD the other day.  Then when I went to the Ubuntu site I discovered there is a much newer one (Daper Drake).

It is on a partition on the notebook as an experiment.  Should I somehow remove the partition?

Todd

[QUOTE=newbie_buntu]Todd - I would suggest installing ubuntu 6.06 (dapper drake).  The built in configuration has a wireless adaptor and might help with your wireless on your Toshiba.  Why were you going with 5.10 in the first place? 

j[/QUOTE]

---

