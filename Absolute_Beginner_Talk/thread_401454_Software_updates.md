---
title: "Software updates"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by cypherzero on 2007-04-04
I've suddenly started getting this error when I try download packages or update software:

[FONT="Courier New"]W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>[/FONT]

I get a further warning about compromising security using unrecognized signatures when I try to install or update anything.

Any ideas would be much appreciated!

---

### Post by mikeyphi on 2007-04-04
Open a terminal and type:

apt-get update

---

### Post by Punker on 2007-04-04
did you have automatix?

---

### Post by cypherzero on 2007-04-04
'apt-get update' gives the same error as the Synaptic Package Manager I'm using.
I've no idea what Automatix is.

---

### Post by Maestro23 on 2007-04-04
> **cypherzero said:**
> 'apt-get update' gives the same error as the Synaptic Package Manager I'm using.
I've no idea what Automatix is.

Automatix: [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by cypherzero on 2007-04-04
In which case no, I'm not using that :rolleyes:

---

### Post by cypherzero on 2007-04-04
Thinking my signature keys that came on the CD might be wrong. Anyone know where to get the valid keys from?

---

### Post by Maestro23 on 2007-04-04
> **cypherzero said:**
> In which case no, I'm not using that :rolleyes:

Good man.:popcorn:

---

### Post by karamba_kid on 2007-04-04
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>


That's the output I get with :

sudo apt-key list

You can download those keys from a keyserver.   Read/skim the manual for gpg (man gpg) to see how.

---

### Post by cypherzero on 2007-04-06
Okay, nothing seemed to work but the problem has gone away as mysteriously as it appeared. How odd. :-s

---

