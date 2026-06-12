---
title: "GPG Key - what's this all about?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Optiker on 2006-08-10
About the time I figured out and got a little bit accustomed to repositories and using Adept to install packages, along comes something that mentions GPG keys. Can somebody tell me in simple terms what that's all about and under what circumstances it is necessary? I presume it's a security thing? From what I see, for repositories entered by default at Kubuntu installation, keys aren't necessary...or am I mistaken?

Thanks!
Optiker

---

### Post by davebgimp on 2006-08-10
> **Optiker said:**
> About the time I figured out and got a little bit accustomed to repositories and using Adept to install packages, along comes something that mentions GPG keys. Can somebody tell me in simple terms what that's all about and under what circumstances it is necessary? I presume it's a security thing? From what I see, for repositories entered by default at Kubuntu installation, keys aren't necessary...or am I mistaken?

Thanks!
Optiker

GPG is short for the Gnu Privacy Guard.

[http://www.gnupg.org/](http://www.gnupg.org/)

From the site:
> GnuPG is the GNU project's complete and free implementation of the OpenPGP standard as defined by RFC2440 . GnuPG allows to encrypt and sign your data and communication, features a versatile key managment system as well as access modules for all kind of public key directories. GnuPG, also known as GPG, is a command line tool with features for easy integration with other applications. A wealth of frontend applications  and libraries  are available.

It is used for a variety of reasons. Encrypting files, emails etc... but also to authenticate people and things.

Ubuntu uses the GPG keys to make use that the repositories you connect to have not been compromised and are in fact the real deal. It's a good thing.

---

### Post by Optiker on 2006-08-10
Dave...Thanks! Very clear answer. I suspected it had something to do with PGP, and would aqgree it's a good thing...just another thing to learn how to work with.

Optiker

---

