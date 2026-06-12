---
title: "What's the point on having both Root and Normal user?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by lonrot on 2007-10-12
I would like to use only one account and do everything with that, it's also a pain being asked with password everytime I install something, etc.

I'm migrating from windows, so there are some things I'm really not used to.

There's also something that bugs me, if I browse the folders, root folders cannot be seen, but only if I log as root. So for me one account should be sufficient, or at least being always logged as root without being asked with passwords.

---

### Post by leg on 2007-10-12
Your account (the first one created when installed) can do all the super user things but you need to use the command su in front of it.

---

### Post by John.Michael.Kane on 2007-10-12
> **lonrot said:**
> I would like to use only one account and do everything with that, it's also a pain being asked with password everytime I install something, etc.

I'm migrating from windows, so there are some things I'm really not used to.

There's also something that bugs me, if I browse the folders, root folders cannot be seen, but only if I log as root. So for me one account should be sufficient, or at least being always logged as root without being asked with passwords.

Things are done differently in Linux/Ubuntu, however. If you are still bent on running as root 24/7 read below.

[COLOR="DarkRed"]Enabling the root account is neither supported nor necessary. To do so is at ones own risk[/COLOR]
To enable the root account (i.e. set a password), use:
Run:
```
sudo passwd root
```
Then enter your existing password, enter the password for root, and confirm the password for root.

---

### Post by RCC2k7 on 2007-10-12
Those of us who have had to use Vista know the "party" of doing everything as an administrator is over.

I do find the Linux approach, (entering a password as if I were on some sort of corporate computer, while I'm working with MY OWN computer at home), a bit idiotic. I hope that at some point Linux adopts a less bureaucratic approach (UAC-style) to confirm administrative tasks without having to type a password (Continue or Cancel). I don't expect it  to be the standard approach but at least give it as an option for those of us who really hate the extra bureaucracy of the Password prompts.

---

### Post by rsambuca on 2007-10-12
> **RCC2k7 said:**
> Those of us who have had to use Vista know the "party" of doing everything as an administrator is over.

I do find the Linux approach, (entering a password as if I were on some sort of corporate computer, while I'm working with MY OWN computer at home), a bit idiotic. I hope that at some point Linux adopts a less bureaucratic approach (UAC-style) to confirm administrative tasks without having to type a password (Continue or Cancel). I don't expect it  to be the standard approach but at least give it as an option for those of us who really hate the extra bureaucracy of the Password prompts.The point of a limited user account is not only for protection from people at your desk.  It is also significant in protecting you from outside attacks via the net, viruses, etc.  If a hacker were to gain access to your computer via your internet connection, they would only have the same access as the user.  If you ran as root, they could do anything they wanted with your system.

---

### Post by Ubris on 2007-10-12
In a word, [security]("https://help.ubuntu.com/7.04/administrative/C/") &#8211; from yourself and from the bad internet.

I'm sorry, but I have to point this out: I don't see this as an accessibility issue. Usability, yes. Perhaps you are getting them confused? :)

Hope this doesn't stop you enjoying *buntu &#8211; think of the peace of mind you're getting back in return.

---

### Post by frafu on 2007-10-13
Hello, 

There is nothing in this thread that relates directly to software for disabled people. 

Consequently, I will move it to the Absolute Beginner Talk forum, where it is more appropriate. 

Have a nice day. 

Francesco

---

