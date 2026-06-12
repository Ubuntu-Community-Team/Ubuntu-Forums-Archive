---
title: "Having problem with installing &quot;git-core&quot;"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by imsangha on 2007-08-17
I just installed ubuntu 7.04 yesterday, and I absolutely know nothing.

I went to terminal and typed "sudo get-apt install git-core," and i get the following error message.

[COLOR="DarkOrange"]
sangha@sangha-linux:~$ sudo apt-get install git-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcurl3-gnutls libdigest-sha1-perl liberror-perl rcs
Suggested packages:
  git-arch git-cvs git-svn git-email git-daemon-run gitk gitweb cogito
Recommended packages:
  git-doc curl
The following NEW packages will be installed:
  git-core libcurl3-gnutls libdigest-sha1-perl liberror-perl rcs
0 upgraded, 5 newly installed, 0 to remove and 3 not upgraded.
E: The package index files are corrupted. No Filename: field for package rcs.[/COLOR]

I have no clue what to do, and I've been trying googling and did not get an answer. "git-clone" is what I'm trying to get, but I guess it is not installed yet. Any help will be greatly appreciated. Thank you for reading this post, and have a great day!

---

### Post by mysticmatrix on 2007-08-24
Try this

```
sudo apt-get update
sudo apt-get upgrade
```

and then 
```
sudo apt-get install git-core
```

If this doesn't works, post output of following command
```

cat /etc/apt/sources.list
```

---

