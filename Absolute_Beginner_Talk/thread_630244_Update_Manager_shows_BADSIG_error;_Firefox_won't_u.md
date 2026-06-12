---
title: "Update Manager shows BADSIG error; Firefox won't upgrade"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by TristanDee on 2007-12-03
Both Update-Manager and [COLOR="Blue"]sudo apt-get update[/COLOR] shows the following errors.

> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) gutsy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

> W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) gutsy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

One thing I understood: the Ubuntu server here in Bangladesh has got something to do with the error, but changing software sources to main server also yields a similar error message in the terminal:

> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) gutsy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

However, running the apt-get update doesn't correct the problems.

Then Firefox 2.0.0.8 won't upgrade. I downloaded a firefox-2.0.0.9.tar.gz file but can't install it. I've forgotten how I downloaded it, most probably through the browser's "check for updates" option.

Too many queries? Sorry for that, but I'm a little scared as I know very little about Linux/Ubuntu.
Thanks in advance.

---

### Post by Partyboi2 on 2007-12-03
have you tried to set the Authentication keys back to defaults System>Admin>Software Sources under the Authentication tab you can choose to restore to default.

---

### Post by TristanDee on 2007-12-03
Just did it. There are 2 options in the Authentication field: "437D05B5 2004-09-12 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" and "FBB75451 2004-12-30 Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>".

After that still getting the same error message.

---

### Post by Partyboi2 on 2007-12-03
Just looking at  bug reports and the solution that they used was to try
```
apt-get update -o Acquire::http::No-Cache=True
```
 which set the cache-control headers to turn caching off
you can read more about it here:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/33505](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/33505)
another bug suggests force apt-get to re get the signature file each time.
Here is the link to that bug report
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/14486](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/14486)

---

### Post by TristanDee on 2007-12-03
Thanks Partyboi2, ran the code and I believe it worked. The update couldn't fetch some index files though.
And as I write this I can see a yellow baloon overhead showing some updates.
So, let me check. Thanks again.

---

### Post by TristanDee on 2007-12-03
Oh yeah, they *are* downloading. And the Firefox too.
Thanks Partyboi2.

---

### Post by MoHamm on 2008-01-06
Tried it and it worked for me too


> Just looking at bug reports and the solution that they used was to try
Code:

apt-get update -o Acquire::http::No-Cache=True



cheers

---

### Post by pkid on 2008-01-06
Helped me too.  Thanks!

---

### Post by StefanPieter on 2008-05-14
It worked for me too.
Thanks

---

