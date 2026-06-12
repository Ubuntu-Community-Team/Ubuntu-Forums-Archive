---
title: "Can't run 7.10"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by cybrough on 2008-01-14
I'm using 7.04 on a Kohjinsh SA-1 with a AMD Geode processor, 500Mhz, 1GB memory. It runs very well with 7.04 but when I upgrade to 7.10 I get a black screen after boot.  I must cnl-alt-del to reboot to 7.04.  This may be a problem with xorg.conf.  I'm wondering if I can copy the 7.04 xorg.conf to a thumb drive and the  install 7.10 in text mode and then copy xorg.conf back into 7.10.

Cy

---

### Post by nikoPSK on 2008-01-14
> **cybrough said:**
> I'm using 7.04 on a Kohjinsh SA-1 with a AMD Geode processor, 500Mhz, 1GB memory. It runs very well with 7.04 but when I upgrade to 7.10 I get a black screen after boot.  I must cnl-alt-del to reboot to 7.04.  This may be a problem with xorg.conf.  I'm wondering if I can copy the 7.04 xorg.conf to a thumb drive and the  install 7.10 in text mode and then copy xorg.conf back into 7.10.

Cy

If you want to try this, though I don't think (It might :D) wirk, just reconfigure xorg. 
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

nikoPSK

---

### Post by stoodleysnow on 2008-01-14
Kohjinsh?
Who the heck are they? o_0

---

### Post by nikoPSK on 2008-01-14
> **stoodleysnow said:**
> Kohjinsh?
Who the heck are they? o_0

maybe a typo :shock:

---

### Post by cybrough on 2008-01-15
It's Kohjinsha, I miss spelled it in my original post.  It is a UMPC with a 7" screen, 40gig hd.  I tried dpkg-reconfigure xserver-xorg with no improvement.

---

### Post by nikoPSK on 2008-01-15
> **cybrough said:**
> It's Kohjinsha, I miss spelled it in my original post. It is a UMPC with a 7" screen, 40gig hd. I tried dpkg-reconfigure xserver-xorg with no improvement.
 
hrm, well it's not your specs...

---

### Post by WhiteGollum on 2008-03-09
I own a Koji too
it seems that you have two problems, I have been able to solve only one.

1: The Xorg version have a bug that do not permit to switch to another terminal. You have to patch the xorg source or install a pre-patched xorg from anothe PPA:
[https://launchpad.net/q-funk/+archive](https://launchpad.net/q-funk/+archive)

2: Xorg amd driver seems to fail. I also suffer the same error, and have no idea to solve it.

Sorry men

---

### Post by barrybingham on 2008-03-23
I think this issue affects everything with an AMD geode, including my Koolu. Koolu promised to solve this months ago but they've taken down their web page cautioning against gutsy upgrades without posting a promised solution:(. I've tried the Hardy beta too via livecd and this also gives a blank screen with no access to console. I think we geode users may be running Feisty for a l o n g time before there's a repo-based solution to this issue. It is an Xorg issue, not an unbuntu/debian issue, and I suspect that no other current distros with later Xorg setups will work with X on the koolu - I can confirm that this applies to Fedora 8.

---

### Post by bhavi on 2008-03-23
> **barrybingham said:**
> I think this issue affects everything with an AMD geode, including my Koolu. Koolu promised to solve this months ago but they've taken down their web page cautioning against gutsy upgrades without posting a promised solution:(. I've tried the Hardy beta too via livecd and this also gives a blank screen with no access to console. I think we geode users may be running Feisty for a l o n g time before there's a repo-based solution to this issue. It is an Xorg issue, not an unbuntu/debian issue, and I suspect that no other current distros with later Xorg setups will work with X on the koolu - I can confirm that this applies to Fedora 8.
Hmm well reconfiguring xserver also wont help.... ?

Have you tried xubuntu a lighter version of ubuntu?

---

### Post by barrybingham on 2008-03-23
> **bhavi said:**
> Hmm well reconfiguring xserver also wont help.... ?

Have you tried xubuntu a lighter version of ubuntu?

Reconfiguring won't help. Nor will lighter versions of ubuntu. It is X itself which will not function: in fact it causes a hardware freeze!

Have found this though, which suggests that a solution exists (although it seems not to have made it into the latest Hardy beta):
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-amd/+bug/140051](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-amd/+bug/140051)

---

