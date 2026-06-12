---
title: "Problems with Synaptic"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2005-11-29
First and foremost being I don't really know what the hell I'm doing.  Anyone know a good howto on the topic?  Sorry to waste board space with mundane questions...

EDIT: My specific problem at the moment is as follows.  Sometimes I fail to connect altogether.  Sometimes I connect to some repositories, but not all.  Sometimes I connect to all repositories and get  errors trying to download, such as:
---
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2-common_1.2.10-17build1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2-common_1.2.10-17build1_all.deb)
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
---

Anyone seen this/solved this?


cheers from the icy north!
-pete

---

### Post by invalid on 2005-11-29
There have been some issues with people using the "us" repos. Try changing them from us.archive.ubuntu.com to just archive.ubuntu.com and see if it makes any difference.

Cb

---

### Post by somody on 2005-11-29
Or better yet, to ca.archive.ubuntu.com :)

---

### Post by TeeAhr1 on 2005-11-29
Wow, you guys are fast.  I was just coming back to say that it is definately the us repository that's giving me problems.

However, neither archive.ubuntu nor ca.archive.ubuntu seem to be any better.  I'm still getting this:

---
[http://ca.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://ca.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:) Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
---

Whaddaya think?


thx-
pete

---

### Post by somody on 2005-11-29
There must be a problem with your Internet connection then :(.

---

### Post by TeeAhr1 on 2005-11-29
I don't get it.  I'm connecting to security.ubuntu perfectly fine...

---

### Post by Kapre on 2005-11-29
[QUOTE=TeeAhr1]First and foremost being I don't really know what the hell I'm doing.  Anyone know a good howto on the topic?  Sorry to waste board space with mundane questions...

EDIT: My specific problem at the moment is as follows.  Sometimes I fail to connect altogether.  Sometimes I connect to some repositories, but not all.  Sometimes I connect to all repositories and get  errors trying to download, such as:
---
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2-common_1.2.10-17build1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2-common_1.2.10-17build1_all.deb)
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
---

Anyone seen this/solved this?


cheers from the icy north!
-pete[/QUOTE]


Teeahr - please update your sources.list to the one that is on this [site]("http://www.psychocats.net/linux/sources.php") (thanks to Aysiu)

K

---

### Post by TeeAhr1 on 2005-11-29
No dice, still timing out.  Now I'm timing out both on archives.ubuntu and security.ubuntu :/

---

### Post by TeeAhr1 on 2005-11-30
Hmm.  Funny.  When I went through apt-get, it didn't connect.  When I went through Synaptic, it connected right off and downloaded without a problem.  Thanks for the help, guys! :o)

---

### Post by somody on 2005-11-30
apt-get is faster, but sketchy, IMO :p

---

