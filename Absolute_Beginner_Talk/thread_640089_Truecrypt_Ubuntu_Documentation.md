---
title: "Truecrypt Ubuntu Documentation"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-12-13
I swear I saw a huge write up of Truecrypt in the Ubuntu Documentation.
Can anyone help me find it.... I used it to install it on my last machine
but now I can't seem to fine it.

---

### Post by Rocket2DMn on 2007-12-13
Is this what you're looking for? - [https://help.ubuntu.com/community/TruecryptHiddenVolume](https://help.ubuntu.com/community/TruecryptHiddenVolume)

---

### Post by Orbital75 on 2007-12-13
Now, it sure isn't...... It didn't talk about hidden volumes just how to
add the the pgp signature to the repositories and then how to install
it.  I can't find it for the life of me.

---

### Post by Rocket2DMn on 2007-12-13
You didn't say anything about repositories or sources.list
Are you looking for [https://help.ubuntu.com/community/Repositories/Ubuntu#head-589d9639c60888f17e3d660b375340777b436077](https://help.ubuntu.com/community/Repositories/Ubuntu#head-589d9639c60888f17e3d660b375340777b436077)

---

### Post by Orbital75 on 2007-12-13
Rocket2DMn 
Thanks for your responses but that wouldn't be it either.
Thats the thing, there are a few things that pop up when
you search for it in the documentation but non of them
are the one I read.  This included the address of truecrypt
to add to your repositories and how to install the program.
It also showed you how to add some other program that randomizes 
the encryption stream which you had to install before the actual program.
It was very detailed and a great resource. I should have book marked
it.....  :(

---

### Post by niteshifter on 2007-12-14
Hi 

For what it's worth that part about adding a randomizing program sounds like maybe for an earlier version of truecrypt? Current version (4.3a) will build entropy via mouse or keyboard.

It's not difficult to install Truecrypt. The problem I encountered (with Edgy) was a missing program: dmsetup
See if you have dmsetup:
```
locate dmsetup
```

Should show something like this if it's installed:
```
foo@bar:~$ locate dmsetup
/var/lib/dpkg/info/dmsetup.md5sums
/var/lib/dpkg/info/dmsetup.list
/usr/sbin/gdmsetup
/usr/share/applications/gdmsetup.desktop
/usr/share/doc/dmsetup
/usr/share/doc/dmsetup/changelog.Debian.gz
/usr/share/doc/dmsetup/changelog.gz
/usr/share/doc/dmsetup/INTRO
/usr/share/doc/dmsetup/copyright
/usr/share/gdm/gdmsetup.glade
/usr/share/man/man1/gdmsetup.1.gz
/usr/share/man/man8/dmsetup.8.gz
/sbin/dmsetup

```
Not there? Download dmsetup with Synaptic or apt-get
```
apt-get install dmsetup
```

Once I installed that installation went smooth.

I assume you have downloaded truecrypt-4.3a-ubuntu-7.10-x86.tar.gz from [www.truecrypt.org](www.truecrypt.org) and that the file is in your home folder. I say this because there is no mention of a Debian-style repository anywhere on [www.truecrypt.org](www.truecrypt.org) - just a downloads page: [http://www.truecrypt.org/downloads.php]("http://www.truecrypt.org/downloads.php")

1.a. Use Archive Manager (aka file-roller) to unpack the archive. In the Extract dialog you want to re-create folders (under Actions). When it's done you should have a new folder named truecrypt-4.3a in your home folder. 

1.b OR you can unpack via command line:
```
tar xvzf truecrypt-4.3a-ubuntu-7.10-x86.tar.gz
```

2. Switch to that folder.
```
cd truecrypt-4.3a
```

3. Install truecrypt with dpkg:
```
sudo dpkg -i truecrypt_4.3a-0_i386.deb
```

The rest is just clean-up. Use the GUI and goto your home folder and delete the folder truecrypt-4.3a OR via the command line:

1. Change to your home directory
```
cd ~
```

2. Delete the installation folder - type carefully here
```
rm -rf truecrypt-4.3a
```

HTH

---

### Post by Orbital75 on 2007-12-14
Thanks I'll look into that and give it a try.....
I really appreciate the help :)

---

