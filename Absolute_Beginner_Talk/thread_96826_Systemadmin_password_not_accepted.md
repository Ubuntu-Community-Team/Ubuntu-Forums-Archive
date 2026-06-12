---
title: "Systemadmin password not accepted"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by RedKing on 2005-11-29
Hi 

I am trying to access synaptic, I enter my password and then nothing.

i have tried both my user password and the root password but to no avail.

Any ideas, This is probably a no brainer so apologies if it is.

Thanks
RedKing

---

### Post by linbetwin on 2005-11-29
Ubuntu doesn't use a root passwd unless you create it. Did you?
If not, you need your user account to become root.

---

### Post by RedKing on 2005-11-29
[QUOTE=linbetwin]Ubuntu doesn't use a root passwd unless you create it. Did you?
If not, you need your user account to become root.[/QUOTE]

I did create a root password, neither password is accepted.
I can become root from the cmd line using su !

---

### Post by hashimoto on 2005-11-30
You probably can't start the admin programs since your user name is not in the sudoers list. To fix, open terminal, then

su
visudo

Add your username to the end of the file, with the same rights as the previous line has (something like ALL (ALL) ALL ) save and quit. You should now be able to run any admin porgrams.

In another thread somewhere somebody suggested that you should add your username to the admin group or something (if I recall this was the correct way to fix...). Do a search if you want to find out more.

---

### Post by RedKing on 2005-12-01
To hashimoto

Thanks for your help.
i edited the sudo file to add my username  with ALL (ALL) ALL permissions and that did the trick.

Thanks again

---

### Post by hashimoto on 2005-12-02
Glad I could help!

---

