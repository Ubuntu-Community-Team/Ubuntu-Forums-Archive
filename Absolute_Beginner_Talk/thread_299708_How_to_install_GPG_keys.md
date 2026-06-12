---
title: "How to: install GPG keys"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-11-14
How do I command apt-get to update the GPG keys?

How do I get apt-get to dump (to the screen) it's configuration?

---

### Post by harlan on 2006-11-14
To add a gpg key (change KEY for the requested key)
$ gpg --keyserver subkeys.pgp.net --recv KEY
$ gpg --export --armor KEY | sudo apt-key add -

After that
$sudo apt-get update

To update your gpg keys
$ sudo apt-key update

To list your keys
$sudo apt-key list
 
More options 
$ man apt-key

---

