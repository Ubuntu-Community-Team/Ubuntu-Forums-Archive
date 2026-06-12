---
title: "[SOLVED] allowing more than one user to use the root password."
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Het Irv on 2008-04-19
I have two users set up on my Ubuntu 7.10 install, one was created originally as a limited user the other was a normal account.  I then redid the permissions so that both users were normal.

My problem now is that gksudo only works for one user, even though I am using the same password.  Shouldn't the root password be the same for both users?

---

### Post by lswest on 2008-04-19
gksudo requires the user's password, not roots, gksu and su would require the root password.  sudo and gksudo require the input of the user's password, as long as they are both in the sudoers file.

---

### Post by Het Irv on 2008-04-19
mmk, thanks.  I'm gonnna figure out how to use this OS yet.

---

### Post by meborc on 2008-04-19
there is more info how to allow more people use sudo (as well as general info on sudo) here - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Archmage on 2008-04-19
Don't you need to allow the user to become root first? Or else everybody could get root access.

---

### Post by Het Irv on 2008-04-19
I did that step already, but I was trying to use the wrong password.

---

### Post by lswest on 2008-04-19
no problem, took me a while to realize that too when i first started ;) glad i could help.  Thanks for the thanks too :) and yeah, you know where to find me if you've got a specific question ;) (sure, i might not be able to help, but the offer is there)

---

### Post by bodhi.zazen on 2008-04-19
> **Archmage said:**
> Don't you need to allow the user to become root first? Or else everybody could get root access.

No, Ubuntu uses sudo. sudo is configured such that any user in the admin group has root access via sudo entering his or her log in password.

See the link meborc gave you.

You can configure sudo via visudo

[http://www.gratisoft.us/sudo/man/visudo.html](http://www.gratisoft.us/sudo/man/visudo.html)

By default the root account is locked in Ubuntu.

---

