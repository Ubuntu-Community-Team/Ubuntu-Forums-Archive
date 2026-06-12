---
title: "Weird Sources.list problem! HELP PLZ!"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by chonzy on 2006-06-28
I typed this into my sources.list file, ok, till here everything is fine, but whenever i try to "apt-get updates" it tells me that line 19 is badly formed, and i just can't figure out whats wrong! thx to anyone that can help me out


# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file

# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb 
[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb 
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas)
 dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# Penguin Liberation Front (packages)

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

---

### Post by Stolie on 2006-06-28
It looks as though the problem would be with the "Seveas' Packages". you probably need to put the "dapper-seveas all" after the link line, instead of on a different line...

---

### Post by aysiu on 2006-06-28
Try this instead: ```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file

# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)

deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted

deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb http://seveas.theplayboymansion.net/seveas dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# Penguin Liberation Front (packages)

deb ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/ dapper free non-free
``` If that doesn't work, use these instructions. I **know** these work. [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by chonzy on 2006-06-28
Thx!


Fixed!!

---

### Post by catlett on 2006-06-28
Just for your information. This was the issue 
> [COLOR="Red"]deb[/COLOR]
[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
The line was written wrong. You have a couple written wrong but the computer will stop at the first eror and won't look further. The line needed to be this 
> [COLOR="Red"]deb[/COLOR] [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse This was just for the sake of knowing. Keep the one Aysiu gave you, it has everything you will need for your system.

---

### Post by ubuntu_demon on 2006-06-29
More information about Seveas packages is right here : [https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages)

chonzy you probably don't need the Seveas repository. Based on your post count I think you are a new user. Most average desktop users don't need seveas' packages and I don't think he and his mirrors have much bandwith.

aysiu I think it's great that you help so much users. I think you are really valuable to the forums! IMHO it's better not to advice people to add the Seveas repository uncommented repository to their sources.list.

IMHO it's better to refer people here :
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
or here :
My recommended Dapper sources.list
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by aysiu on 2006-06-29
[QUOTE=ubuntu_demon]
aysiu I think it's great that you help so much users. I think you are really valuable to the forums! IMHO it's better not to advice people to add the Seveas repository uncommented repository to their sources.list.[/QUOTE] I wasn't so much advising use of the seveas repository as just fixing the OP's sources.list (which happened to include that repository). I have no idea what that repository is.

---

