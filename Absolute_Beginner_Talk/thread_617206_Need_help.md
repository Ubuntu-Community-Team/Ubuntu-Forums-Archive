---
title: "Need help"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by planet-reptile on 2007-11-19
Okay. I have tryed to get help, but with no success at the moment.

The problem is that whenever i do an update it won't accept my key
An error accured
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: folowing signatures could not be viryfied because public key is not available: NO_PUBKEY 2EBC26B60C5A2783 
(Translated)

Then i tryed to type in the terminal:
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add - 
That did not solved the problem.
Then i tryed:
sudo aptitude update and that did not solve the problem.

Can someone please help? :)

---

### Post by hyper_ch on 2007-11-19
You have to replace "KEY" with the actual provided key!

---

### Post by planet-reptile on 2007-11-19
LOL I should have known that

---

### Post by planet-reptile on 2007-11-19
>My computer name<:~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server subkeys.pgp.net
gpg: /home/kim/.gnupg/trustdb.gpg: trustdb created
gpg: key 0C5A2783: public key "Medibuntu Packaging Team <admin@lists.medibuntu.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
>My computer name<:~$ gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add - 

Does that look right?

---

### Post by planet-reptile on 2007-11-19
It's doing it all over again. Tryed to click on check in update, but the same warning came up as i started posting.

---

### Post by hyper_ch on 2007-11-19
I think it should be:

```

gpg --export --armor 0C5A2783 | sudo apt-key add -

```

---

### Post by planet-reptile on 2007-11-19
This is how it looks now.

>My computer name<:~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server subkeys.pgp.net
gpg: key 0C5A2783: "Medibuntu Packaging Team <admin@lists.medibuntu.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
>My computer name<:~$ gpg --export --armor 0C5A2783 | sudo apt-key add -

Does it look right?

---

### Post by planet-reptile on 2007-11-19
Man it keeps on doing the same thing.
But is it important that it works?

---

### Post by hyper_ch on 2007-11-19
it's not important but it helps preventing malicious stuff... e.g. dns poisoning...

---

### Post by planet-reptile on 2007-11-19
WUHU, it works now :guitar:
Thanks for the help.=D>

---

### Post by hyper_ch on 2007-11-19
what helped now?

---

