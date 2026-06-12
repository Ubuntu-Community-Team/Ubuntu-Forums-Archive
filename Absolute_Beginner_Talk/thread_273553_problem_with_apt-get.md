---
title: "problem with apt-get"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by unisol on 2006-10-08
when i run sudo apt-get update i get the follo0wing error messages:W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following sign atures couldn't be verified because the public key is not available: NO_PUBKEY F 120156012B83718
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following sign atures couldn't be verified because the public key is not available: NO_PUBKEY F 120156012B83718
W: You may want to run apt-get update to correct these problems

what can i do to correct these problems im using ubuntu dapper 606

---

### Post by mitch.c on 2006-10-08
> **unisol said:**
> when i run sudo apt-get update i get the follo0wing error messages:W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following sign atures couldn't be verified because the public key is not available: NO_PUBKEY F 120156012B83718
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following sign atures couldn't be verified because the public key is not available: NO_PUBKEY F 120156012B83718
W: You may want to run apt-get update to correct these problems

what can i do to correct these problems im using ubuntu dapper 606
The problem is, you need the GPG key that goes with the repository. The key is used to verify the authenticity of the packages you install. You need to find out if there is a key available, and if so, follow the directions here: [https://help.ubuntu.com/community/Repositories/Ubuntu#head-589d9639c60888f17e3d660b375340777b436077](https://help.ubuntu.com/community/Repositories/Ubuntu#head-589d9639c60888f17e3d660b375340777b436077)

If not, I think you should be able to install software anyway, you are just going to be warned like this each time.

---

### Post by meng on 2006-10-08
Yup, as the above post says, it's not an apt-get problem, it's just that apt-get will warn you that these packages are "unauthenticated" unless you supply the GPG key. You can still install everything, you just need to acknowledge that they are "unauthenticated"
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
there's a section here on managing keys.
However, my preliminary google search did not unearth the key for that repository.

---

