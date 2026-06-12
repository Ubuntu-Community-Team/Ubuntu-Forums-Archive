---
title: "GPG question"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-08-09
Every time I try to update/download something for Kubuntu 6.06 (which I'm using) I get the gpg error message.

So I tried this: (DD4D5088 is the key number in source-o-matic)

~$ gpg --keyserver subkeys.pgp.net --recv DD4D5088
gpg: requesting key DD4D5088 from hkp server subkeys.pgp.net
gpg: key DD4D5088: public key "Jonathan Riddell <jriddell@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

So, Kubuntu isn't trusted? Or did I do something wrong?

---

### Post by davebgimp on 2006-08-09
You should be fine. Users can manually set trust levels and GPG is just telling you that no trust level is set - which shouldn't generate problems for you I believe.

Don't forget the second step:

**gpg --export --armor KEY | sudo apt-key add -**

---

### Post by editrix on 2006-08-10
> **davebgimp said:**
> You should be fine. Users can manually set trust levels and GPG is just telling you that no trust level is set - which shouldn't generate problems for you I believe.

Don't forget the second step:

**gpg --export --armor KEY | sudo apt-key add -**

Thanks for replying. Is the above one command or 2? I tried it both ways, and got:

gpg: WARNING: nothing exported

both times.

---

### Post by davebgimp on 2006-08-10
> **editrix said:**
> Thanks for replying. Is the above one command or 2? I tried it both ways, and got:

gpg: WARNING: nothing exported

both times.


Open a terminal and type this all on one line:

**gpg --keyserver subkeys.pgp.net --recv KEY**
      
and the next command, type this...all one line

**gpg --export --armor KEY | sudo apt-key add -**

Where it says **KEY**, substitute with the appropriate number. In your case, that's DD4D5088

---

### Post by editrix on 2006-08-10
> **davebgimp said:**
> Open a terminal and type this all on one line:

**gpg --keyserver subkeys.pgp.net --recv KEY**
      
and the next command, type this...all one line

**gpg --export --armor KEY | sudo apt-key add -**

Where it says **KEY**, substitute with the appropriate number. In your case, that's DD4D5088

Well, at least it didn't barf lots of code at me :-)

1st command went okay, but when I did gpg --export --armor KEY | sudo apt-key add -

I got

gpg: no ultimately trusted keys found
OK

Hmmm ...

---

### Post by davebgimp on 2006-08-10
That's not an error. As I said a few posts ago. GPG is just telling you that the trust level is not set on the key. Not a big deal.

---

### Post by editrix on 2006-08-10
> **davebgimp said:**
> GPG is just telling you that the trust level is not set on the key. Not a big deal.

Okay, thanks. PS: Just visited your site. Cool wallpaper. I never even tried to quit :-)

---

