---
title: "Forgot root password"
date: 2005-05-31
forum: Absolute Beginner Talk
---

### Post by n0xyl on 2005-05-31
I forgot root password ](*,) , how can i change or remove it?

---

### Post by bored2k on 2005-05-31
[QUOTE=n0xyl]I forgot root password ](*,) , how can i change or remove it?[/QUOTE]

sudo passwd

When asked for passwd, use yours, then reset it.

---

### Post by ltmon on 2005-05-31
Would that be 

> sudo passwd root

instead?

Just checking, I might be wrong.

---

### Post by bored2k on 2005-05-31
[QUOTE=ltmon]Would that be 

> sudo passwd root

instead?

Just checking, I might be wrong.[/QUOTE]
 Yes and no.
sudo passwd will to the same effect.

If you are user John, and you type passwd, you will be changing John's passwd. In the case of sudo passwd, the command is being run by root.

---

### Post by n0xyl on 2005-05-31
[QUOTE=ltmon]Would that be 

> sudo passwd root

instead?

Just checking, I might be wrong.[/QUOTE]
 I fixed it using install-cd. Now when I use terminal I can root, but when i want to change some settings through Administration>>etc system requires password, i typed root, user password unsuccessfully. it says wrong password. which passwd i have to type?

---

### Post by Mez on 2005-05-31
ubuntu is set up to use suido rather than su via default.

This means you shouldnt really have a root password set.

if you're using any of the built in tools through the graphical environment, type your own password rther than the root password., as these commands use graphical versions of sudo

---

### Post by Lincx on 2005-06-24
Wow thanks alot this thread really helped me. Thanks to you all  :grin:

---

### Post by bored2k on 2005-06-24
[QUOTE=Lincx]Wow thanks alot this thread really helped me. Thanks to you all  :grin:[/QUOTE]
 Rock /on.

---

