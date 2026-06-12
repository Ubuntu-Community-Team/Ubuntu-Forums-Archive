---
title: "libpcre3 (&gt;= 4.5)"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-06-25
Tried to install the Dapper Kubuntu-desktop and it failed, too many errors. I already have Dapper/Gnome.

While trying to solve that problem, I discovered that some programs (like kdelibs4c2a) will not be installed because they need libpcre3 (>= 4.5) but it's not going to be installed. I've tried googling to discover what libpcre3 (>= 4.5) and why I need it, but no joy.

Can anyone enlighten me? Thanks in advance.

---

### Post by gingermark on 2006-06-25
[http://packages.ubuntu.com/dapper/libs/libpcre3](http://packages.ubuntu.com/dapper/libs/libpcre3)

([http://packages.ubuntu.com](http://packages.ubuntu.com)) is your friend.

Could you post the contents of your sources.list file please (located in /etc/apt)

---

### Post by editrix on 2006-06-25
[QUOTE=gingermark][http://packages.ubuntu.com/dapper/libs/libpcre3](http://packages.ubuntu.com/dapper/libs/libpcre3)

([http://packages.ubuntu.com](http://packages.ubuntu.com)) is your friend.

Could you post the contents of your sources.list file please (located in /etc/apt)[/QUOTE]

Thanks for that package url. It's something I'm really going to explore once I get the new system going. BTW, I tried the ftp.cs.umn.edu/pub/ubuntu (it's in Canada, I think, where I am) and got a 404 error. I wonder if the ca. in the sources list is the same place.

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

---

### Post by gingermark on 2006-06-25
I have no idea why it woukd require a version of libpcre3 more than 4.5. I am a kubuntu user, using KDE 3.5.3 and I only have version 4.1 of libpcre3 installed.

I thought maybe your sources.list might contain a clue of some dodgy dependencies somewhere, but it seems ok to me. Sorry, I'm stumped :(

---

