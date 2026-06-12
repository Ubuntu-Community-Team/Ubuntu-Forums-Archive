---
title: "Disable mouse while writing"
date: 2009-05-09
forum: Apple Hardware Users
---

### Post by tiam87 on 2009-05-09
hi,
i want disable mouse while writing in order to avoid casual touching .i searched into the forum  but i didn't found any post helpful.
 i've a macbook 3,1 with ubunty jaunty.this is my xorg.conf (attached).
Before jaunty i used syndaemon command but now i have this error:

```

X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```
Thanks

---

### Post by mwae on 2009-05-11
Hi tiam87,

this is a known bug for amd64 systems (intrepid and jaunty), see 
[http://ubuntuforums.org/showthread.php?t=948250]("http://ubuntuforums.org/showthread.php?t=948250")
and
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/295236]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/295236")

It is solved (for the mentioned systems, including mine :-)) by adding the repo of wgrant and "downgrading" xserver-xorg-input-synaptics to wgrant's version. Unfortunately, the package management continues to advertise the broken version as an upgrade. Also unfortunately, the forum discussion is closed, because it was considered as an intrepid testing issue.

Good luck,
Matthias

---

### Post by tiam87 on 2009-05-11
Thanks Matthias.
i'tried but adding this line   
deb [http://ppa.launchpad.net/wgrant/ubuntu](http://ppa.launchpad.net/wgrant/ubuntu) intrepid main
i 've this error after apt-get update : 
 GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A7CEB1D8A626B42
Any ideas?

---

