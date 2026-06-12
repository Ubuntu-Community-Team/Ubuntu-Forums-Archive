---
title: "[SOLVED] setting up a PGP key for Launchpad"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by univremonster on 2007-07-20
On the page [https://launchpad.net/~bruzzone/+editpgpkeys](https://launchpad.net/~bruzzone/+editpgpkeys)

I see

A message has been sent to [email]bruzzone@physics.umn.edu[/email], encrypted with the key ####X/###X#XX#. To confirm the key is yours, decrypt the message and follow the link inside.

I got the message and downloaded it to my computer.   However this is what happens in the command line

remonster@remonster-desktop:~$ cd Desktop/

remonster@remonster-desktop:~/Desktop$ ls

                                  Launchpad_ Confirm your OpenPGP Key.txt

remonster@remonster-desktop:~/Desktop$ gpg -d Launchpad_\ Confirm\ your\ OpenPGP\ Key.txt 



You need a passphrase to unlock the secret key for

user: "Daniel Bruzzone <bruzzone@physics.umn.edu>"

1024-bit ELG-E key, ID 39149EEF, created 2007-07-20 (main key ID 267F0EF7)



gpg: Invalid passphrase; please try again ...


This is after copy+pasting the passphrase I have above (except obviously they aren't all xs and #s).  What am I doing wrong?

---

### Post by Foxmike on 2007-07-24
The passphrase is a password you putted to decrypt the key.  You have setted it up when you firstly built the key to send it to Launchpad.  It will/should not appear anywhere in clear text.  If you do not remermer it, you should build another key, remember the passphrase you put on it, and then send it back to launchpad.

---

### Post by univremonster on 2007-07-24
Ah... THAT password... well don't I feel silly.  Thanks for the help.

---

### Post by Foxmike on 2007-07-24
You're very welcome!;)

---

