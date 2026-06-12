---
title: "Kernel Update"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-27
I have Ubuntu 7.10 installed with 2.6.22.14 Kernel. I found a new Kernel(2.6.24) last week. I waited some time so that the new Kernel will be available in my Updates. But i didnt receive it. so should i upgrade my kernel and if so how to do it?

---

### Post by jeffus_il on 2008-02-27
Not unless you have a very good reason for upgrading, the changes in minor versions of the kernel are small and those in the repository are quite new. before you do anything read the release notes of the kernel so that you know what changes there are. I have just installed via upgrade a 24 kernel using hardy and had to drop back to the previous kernel because the restricted drivers package wasn't there and I had no madwifi network driver.

---

### Post by PmDematagoda on 2008-02-27
You will not get a normal kernel update to 2.6.24 since 2.6.22 is the kernel version that is deemed to be most stable for Gutsy(but you will get updates to newer versions of the 2.6.22 kernels if they are critical), kernel 2.6.24 is used in Ubuntu Hardy. 

It is not important to upgrade the kernel to 2.6.24, especially if you are concerned about stability and reliability since using a kernel that is incompatible with the currently installed software could cause that software to be affected.

---

### Post by indytim on 2008-02-27
My recommendation is to use the "Easy Button" and wait until the kernel update is streamed to the Repositories.

IndyTim

---

### Post by jordanmthomas on 2008-02-27
> **PmDematagoda said:**
> You will not get a normal kernel update to 2.6.24 since 2.6.22 is the kernel version that is deemed to be most stable for Gutsy(but you will get updates to newer versions of the 2.6.22 kernels if they are critical), kernel 2.6.24 is used in Ubuntu Hardy. 

It is not important to upgrade the kernel to 2.6.24, especially if you are concerned about stability and reliability since using a kernel that is incompatible with the currently installed software could cause that software to be affected.

I have a question that you seem you may be able to answer.  Since They're staying with 2.6.22, and it has that vulnerability where you can get a root shell by exploiting vmslice, do they still provide updates to 2.6.22 (and remove things like this vulnerability)?

It's not a big deal to me, since I'm not using Ubuntu anyway, but I have wondered about this...just not enough to look it up myself.

---

### Post by PmDematagoda on 2008-02-27
> **jordanmthomas said:**
> I have a question that you seem you may be able to answer.  Since They're staying with 2.6.22, and it has that vulnerability where you can get a root shell by exploiting vmslice, do they still provide updates to 2.6.22 (and remove things like this vulnerability)?

It's not a big deal to me, since I'm not using Ubuntu anyway, but I have wondered about this...just not enough to look it up myself.

According to the relevant bug report in Launchpad(I cannot really remember the link) and this [security bulletin]("http://www.ubuntu.com/usn/usn-577-1"), this bug has already been resolved and should have been fixed after you have done the latest kernel updates.

Edit:- I did mention the word "Critical" in my previous post jordanmthomas:).

---

### Post by jw5801 on 2008-02-27
> **jordanmthomas said:**
> I have a question that you seem you may be able to answer.  Since They're staying with 2.6.22, and it has that vulnerability where you can get a root shell by exploiting vmslice, do they still provide updates to 2.6.22 (and remove things like this vulnerability)?

It's not a big deal to me, since I'm not using Ubuntu anyway, but I have wondered about this...just not enough to look it up myself.

Yes, minor level updates will be passed down, ie. 2.6.22-13 to 2.6.22-14. These updates deal with security bugfixes like the one you mention above, which I believe was resolved as of 2.6.22-14, which is the kernel that was released with the final version of Gutsy. Things might not play nice if you implemented a more major update (ie. 2.6.22 to 2.6.24), ie. the newer kernel might want a newer version of glibc or bin-utils or something else that's rather important and isn't all that safe to update without a rebuild. I dunno, that's just speculation, I'm sure someone will correct me if I'm [wrong!](http://www.xkcd.com/386/)

---

