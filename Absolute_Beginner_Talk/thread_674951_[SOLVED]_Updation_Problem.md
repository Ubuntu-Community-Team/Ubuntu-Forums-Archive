---
title: "[SOLVED] Updation Problem"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by srikrishnan on 2008-01-22
Hi all,

"There is 1 update available" message appears in the top right of my interface.

When I try to click the following message appears:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb)
  404 Not Found

Can anybody help me to solve this problem?

Thanks in Advance,
Srikrishnan

---

### Post by mikeyphi on 2008-01-22
Try a Synaptic search for the package:
xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb

It seems that it's not available from the site you used.........if synaptic continues to try to use that site you might have to edit your Sources.list to (#) out that site....

---

### Post by srikrishnan on 2008-01-24
Hi,

Thanks for your suggestion.

But without doing anything after one week at the last minute, it automatically gets updated.

I don't know how it is

Thanks,
Srikrishnan

---

### Post by PmDematagoda on 2008-01-24
Execute:-
```
sudo apt-get update
```
after that finishes your problem should be solved.

---

