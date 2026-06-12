---
title: "problem with updates"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2008-01-19
I am using Ubuntu 7.10 on a Dell desktop. When I logged on, I saw that I had an update waiting to be downloaded and installed: xserver-xorg-core.

When I went ahead with it I got the following error message:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  403 Forbidden

Can someone suggest what needs to be done?

Aam-aadmi

---

### Post by smartboyathome on 2008-01-19
Try changing your sources to another site (via System > Administration > Software Sources > Download from dropdown > Other > Select best site). This may help.

---

### Post by xeth_delta on 2008-01-19
I would say the server from which you are retrieving the sources is either down or is having some technical problems. You might need to change (at least temporarily) the server rom which you get packages.

Can you post the contents of the file "/etc/apt/sources.list"?

---

### Post by xeth_delta on 2008-01-19
> **smartboyathome said:**
> Try changing your sources to another site (via System > Administration > Software Sources > Download from dropdown > Other > Select best site). This may help.

Agree, that should work well.

---

### Post by thelatinist on 2008-01-19
Just right-click on the update manager notification icon and choose "Check for Updates."  This was caused by a bad package being replaced by a new one with a different name.  Since the update manager only retrieves the list periodically, it doesn't yet know the new name.

There are several threads on this exact same topic, one of them on the first page of this very thread and marked [Solved].  Please take the time to search and read before you post. :-)

---

### Post by acridfusion on 2008-01-19
yeah it was doing that to me yesterday... forbidden 443 or something so i just waited til today. updated fine

---

### Post by aam-aadmi on 2008-01-20
Thanks all. It worked fine today.

---

