---
title: "Error when updating"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by tL0z on 2007-06-09
Hello,

I got an error when updating my Ubuntu. Here it is:

> W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-amd64_Packages)


What shall I do?

Thanks!

---

### Post by matthewboh on 2007-06-09
Go into /etc/apt/sources.list and make sure you don't have any duplicates in the list.

---

### Post by tL0z on 2007-06-09
Hm, are those the same ones:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

I mean, doesn't the "universe multiverse" make the second one different?

---

### Post by matthewboh on 2007-06-09
> **tL0z said:**
> Hm, are those the same ones:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

I mean, doesn't the "universe multiverse" make the second one different?

The second line says to add four different types of source files, but it contains two that are already included in the first line.  You can either delete the first line or delete "main restricted" in the second line.

---

### Post by tL0z on 2007-06-09
Ah, ok! Now I understand how it works. Thanks! :)

---

