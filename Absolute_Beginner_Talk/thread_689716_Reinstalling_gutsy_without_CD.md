---
title: "Reinstalling gutsy without CD"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by ssharps711 on 2008-02-06
I only have the cd for edgy. Any way to do a clean reinstall gutsy without a cd? I still have Fesity installed, I'm thinking I can just wipe Gutsy and reinstall from feisty? I don't want to burn to a cd either.

I just want to be able to open feisty's update manager and reinstall gutsy from there. Any possible way to do this?

---

### Post by wolfen69 on 2008-02-06
there's always this: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by ssharps711 on 2008-02-06
Ah, that's a possibility. I think I'm just going to do a clean install of edgy then upgrade normally with update manager or whatever it's called. 

Thanks

---

### Post by bodhi.zazen on 2008-02-06
You can use debbootstrap, install gutsty in a chroot, then apt-get install ubuntu-desktop.

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

---

