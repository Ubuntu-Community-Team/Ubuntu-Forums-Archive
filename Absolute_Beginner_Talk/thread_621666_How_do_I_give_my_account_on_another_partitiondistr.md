---
title: "How do I give my account on another partition/distro full permission and control"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by EAL on 2007-11-23
How do I give my account on another partition/distro full permission and control of this partition and the files there?

I have Ubuntu on a large partition, then another distro - pclos - on a small partition. When I'm logged into pclos I want to be able to have full control over the files and disk space on my ubuntu partition where all my music and stuff is.  The accounts have different user names.

Thanks in advance.

---

### Post by dcstar on 2007-11-24
> **EAL said:**
> How do I give my account on another partition/distro full permission and control of this partition and the files there?

I have Ubuntu on a large partition, then another distro - pclos - on a small partition. When I'm logged into pclos I want to be able to have full control over the files and disk space on my ubuntu partition where all my music and stuff is.  The accounts have different user names.

Thanks in advance.

Each user account has a specific "UserID", you may be able to see what that is on each particular system, and then create a new user on the pclos system with the UserID of your Ubuntu account - then that may give you access to those files.

The other thing to try is to change the permissions to read/write for everyone.

---

### Post by EAL on 2007-11-24
Thanks.  I guess changing the permissions would be easiest.

---

