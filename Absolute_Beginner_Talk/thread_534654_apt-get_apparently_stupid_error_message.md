---
title: "apt-get: apparently stupid error message"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by wog on 2007-08-25
Why is it when I run "apt-get update" it tells me at the end of the error message:

W: You may want to run apt-get update to correct these problems

Didn't I just run apt-get update? Can't it tell I just ran apt-get update?

---

### Post by Majorix on 2007-08-25
Its not that stupid. Apparently there is a problem with your sources.list and apt-get can't fix it.

Mind sending /etc/apt/sources.list?

---

### Post by asmoore82 on 2007-08-25
are you running with proper permissions ... I.E. as **root** or with **sudo**

---

### Post by wog on 2007-08-25
> **asmoore82 said:**
> are you running with proper permissions ... I.E. as **root** or with **sudo**

I was running it with sudo.

I can't find my handy list of Linux notes. I may have to reconstruct them, but until I do I'm almost back to square one. bleah.

---

### Post by asmoore82 on 2007-08-25
maybe you should post the entire output of 'sudo apt-get update'

---

### Post by jordanmthomas on 2007-08-25
It probably tells you what the real problems are before it says to run apt-get update again.  Read the lines above it and scope out any errors.  Then, edit your /etc/apt/sources.list to fix the problems it describes and run apt-get update again.

---

### Post by wog on 2007-08-25
> **Majorix said:**
> Its not that stupid. Apparently there is a problem with your sources.list and apt-get can't fix it.

Mind sending /etc/apt/sources.list?

I guess it just *sounds* stupid.

The precise error message is this: 
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I just don't see where in sources.list it refers to that. Maybe you'll have better luck.
Here you go:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://people.ubuntu.com/~pitti/ddebs](http://people.ubuntu.com/~pitti/ddebs) feisty main universe 
deb [http://people.ubuntu.com/~pitti/ddebs](http://people.ubuntu.com/~pitti/ddebs) feisty-updates main universe
deb [http://people.ubuntu.com/~pitti/ddebs](http://people.ubuntu.com/~pitti/ddebs) feisty-proposed main universe
deb [http://people.ubuntu.com/~pitti/ddebs](http://people.ubuntu.com/~pitti/ddebs) feisty-security main universe

---

### Post by jordanmthomas on 2007-08-25
Try this:
```

KEY=58403026387EE263
gpg --keyserver subkeys.pgp.net --recv $KEY
gpg --export --armor $KEY | sudo apt-key add -

```

Then, run apt-get update and see if that helps.

**edit** by the way, everything should still work even though that error is there
**edit2** I also don't know which repo is causing that one.  I would assume it's whichever one has wine in it.

---

### Post by wog on 2007-08-25
> **jordanmthomas said:**
> Try this:
```

KEY=58403026387EE263
gpg --keyserver subkeys.pgp.net --recv $KEY
gpg --export --armor $KEY | sudo apt-key add -

```

Then, run apt-get update and see if that helps.

**edit** by the way, everything should still work even though that error is there
**edit2** I also don't know which repo is causing that one.  I would assume it's whichever one has wine in it.

The second line gave me this:
james@linux-box:~$ gpg --keyserver subkeys.pgp.net --recv $KEY
gpg: directory `/home/james/.gnupg' created
gpg: can't open `/gnupg/options.skel': No such file or directory
gpg: keyring `/home/james/.gnupg/secring.gpg' created
gpg: keyring `/home/james/.gnupg/pubring.gpg' created
gpg: requesting key 387EE263 from hkp server subkeys.pgp.net
gpg: no valid OpenPGP data found.
gpg: premature eof while reading hashed signature data
gpg: /home/james/.gnupg/trustdb.gpg: trustdb created
gpg: key 387EE263: public key "Scott Ritchie <scott@tuzakey.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

is that good, or do I need to do something else before entering the last line?

---

### Post by jordanmthomas on 2007-08-25
It looks like it's ok.  If it's not it won't hurt to do the last line.

---

### Post by wog on 2007-08-25
Thank you, Jordan, that seems to have fixed it. No more error. :)

---

