---
title: "error with update"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by marcellus wallace on 2006-11-24
when I do the command sudo apt-get update this error comes up:

W: GPG error:
[http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466

how can i solve this?

using xubuntu, pentium 466 256 sdram

---

### Post by kenweill on 2006-11-24
open up /etc/apt/sources.lst
then add # sign on the lines with "http://mirror.ubuntulinux.nl dapper-seveas"

---

### Post by marcellus wallace on 2006-11-24
then it won't read the line anymore... and won't connect to the server

---

### Post by lordvolo on 2006-11-24
use:
sudo aptitude update
sudo aptitude install insertprogramhere

---

### Post by marcellus wallace on 2006-11-24
same problem:

W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466

---

### Post by konst88 on 2006-11-24
```
wget http://mirror.ubuntulinux.nl/1135D466.gpg -O- | sudo apt-key add -
```

---

### Post by kenweill on 2006-11-24
Then you'll have to disable it for a moment then reenable it later.
The problem is not in Ubuntu but its in the repository.

---

### Post by kenweill on 2006-11-24
> **konst88 said:**
> ```
wget http://mirror.ubuntulinux.nl/1135D466.gpg -O- | sudo apt-key add -
```

Owh yes. Try to download and install the gpg keys then install it.
I remember installing updates from Kubuntu. Where it wont work unless you download and install the gpg keys.

---

### Post by marcellus wallace on 2006-11-24
i think it works now, thank you all

---

