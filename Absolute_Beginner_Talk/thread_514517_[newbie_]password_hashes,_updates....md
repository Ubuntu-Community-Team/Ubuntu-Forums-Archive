---
title: "[newbie ]password hashes, updates..."
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by damatta on 2007-07-31
Hiya,
I was wondering what algorithm is used to protect passwords in Kubuntu and if it's possible to change it (i.e to blowfish).
When a new version of Ubuntu/Kubuntu is released, is there a way to upgrade your system to that? IF not, what is advisible?
I'm a real newbie to linux and had a hard time making nvidia driver to work, adding codecs among other things. I did install that "restricted" package but still had to manually add some codecs. After opening an mp3 file I was prompted to download the bloody codec! Would you happen to know a very easy way of installing codecs that would play most formats?

---

### Post by nitro_n2o on 2007-07-31
here is how you play all restricted formats [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and it's easy don't worry about that 
for hashing i guess *not sure* it's md5

---

### Post by Pragmatist on 2007-07-31
There is a package called **kde-pwmanager **that is in the repositories (I found it using synaptic).  You might also want to use the search feature of a package manager program like synaptic.  Then you can read the descriptions of different software packages and see if they interest you.

---

### Post by damatta on 2007-08-01
Thank you for the your attentiveness.
Regarding the passwords, i was thinking of configuring Kubuntu's native encryption so that it uses blowfish instead of md5. For instance: in freebsd you can do it by editing /etc/login.conf .
Thanks in advance

---

### Post by Pragmatist on 2007-08-01
Edit: I believe /etc/login.defs  is Ubuntu's version of BSD's login.conf

```
man login.defs
```

Notice that the login.defs man page states that PAM is mostly in charge now.

PAM is a good starting point:

```
man 7 pam
```

---

