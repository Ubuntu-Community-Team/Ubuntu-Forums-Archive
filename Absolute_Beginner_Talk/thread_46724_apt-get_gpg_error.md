---
title: "apt-get gpg error"
date: 2005-07-05
forum: Absolute Beginner Talk
---

### Post by s0lid on 2005-07-05
how do i correct this?



Fetched 1165kB in 26s (44.6kB/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=s0lid]how do i correct this?



Fetched 1165kB in 26s (44.6kB/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems[/QUOTE]

Well...there isn't really a way to fix the key thing. Its a brand new thing that they are trying to do to make sure that spyware doesn't come. The eventual point is to make it so that software only installs from trusted sources. Problem is that a few of the trusted sources lack keys now. More work is done to fix this in try 2...but take heart in the fact that we don't have ANY spyware yet and it would be nice to get this hammered out so that it might never come.

In short...ignore.

---

### Post by s0lid on 2005-07-06
actually its a gpg key error but what i want to know is where can i get the repo's gpg key.

you can't ignore it it's too annoying

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=s0lid]actually its a gpg key error but what i want to know is where can i get the repo's gpg key.
[/QUOTE]

Its not that easy. Each package has to have the key I think. And the developer has to do that when making the package.

Does it interfere with installing things?

---

