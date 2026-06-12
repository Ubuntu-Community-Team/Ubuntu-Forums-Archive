---
title: "Opera Apt Problem"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by xunshirine on 2006-11-17
**deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free** repository is in source list but when executing **apt-get update** I got the following error message.

W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791

The repository of Opera changed or sth else there? Thanks.

---

### Post by Bachstelze on 2006-11-17
Maybe it would be a good idea to read the instructions on the repo's homepage, which is located at the link you posted twice ;)

---

### Post by skymt on 2006-11-17
Run this code in a terminal to update your Opera GPG key (from deb.opera.com):```
sudo gpg --keyserver subkeys.pgp.net --recv-key 6A423791
sudo gpg --fingerprint 6A423791
sudo gpg --armor --export  6A423791| sudo apt-key add -
```

---

### Post by xunshirine on 2006-11-17
> **HymnToLife said:**
> Maybe it would be a good idea to read the instructions on the repo's homepage, which is located at the link you posted twice ;)
Could you post the instruction page of Opera repo homepage,please. I couldn't find. Also, Thanks skymt.I will try

---

### Post by Bachstelze on 2006-11-17
You posted the link twice in your own message ;) It's [http://deb.opera.com/](http://deb.opera.com/)

---

### Post by xunshirine on 2006-11-17
> **HymnToLife said:**
> You posted the link twice in your own message ;) It's [http://deb.opera.com/](http://deb.opera.com/)
Yea I know I posted it twice but where is the instructions that might help to solve my question , as you indicated?

---

### Post by Bachstelze on 2006-11-17
> To install the key on your host, do some thing like this

(...)

Ubuntu users

sudo gpg --keyserver subkeys.pgp.net --recv-key 6A423791
sudo gpg --fingerprint 6A423791
sudo gpg --armor --export  6A423791| sudo apt-key add -

(which is what skymt mentioned above)

---

### Post by xunshirine on 2006-11-17
> **HymnToLife said:**
> (which is what skymt mentioned above)
Thanks @HymnToLife, but as you know I am absolute beginner and it is impossible to help a beginner just giving an url. :(

---

