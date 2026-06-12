---
title: "Is source (211.74.198.129) available to download update now?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by livefordirty on 2006-08-19
Is source (211.74.198.129) available to download update now?

Why apt-get & synaptic package manager could not download update and files now?

---

### Post by Klaidas on 2006-08-19
Well, umm, I don't know which source that is, but if it's Ubuntu's resposition I guess the server was down

---

### Post by livefordirty on 2006-08-19
Yeah, i meant repository of ubutun!-
but how could the repository- source be down for days?

---

### Post by matthew on 2006-08-19
I don't know anything about the address you mention, but this site is up and works fine for browsing.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

And the main repos are also working well.
```
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu commercial packages
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

---

### Post by Klaidas on 2006-08-19
Ubuntu commersial? huh?
Since when is that availible, I didn't know anything about that :-k

---

### Post by matthew on 2006-08-19
> **Klaidas said:**
> Ubuntu commersial? huh?
Since when is that availible, I didn't know anything about that :-k[http://www.ubuntuforums.org/showthread.php?t=211699](http://www.ubuntuforums.org/showthread.php?t=211699)

---

### Post by livefordirty on 2006-08-19
The address is from the synaptic package manager when i tried to download the latest update and pacakge !

Here is one of the message :
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5-0.6ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5-0.6ubuntu0.1_i386.deb)
Could not connect to 211.74.198.129:8080 (211.74.198.129), connection timed out

What's the problem? ( my internet conection or the repository server?)

---

### Post by matthew on 2006-08-19
> **livefordirty said:**
> The address is from the synaptic package manager when i tried to download the latest update and pacakge !

Here is one of the message :
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5-0.6ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5-0.6ubuntu0.1_i386.deb)
Could not connect to 211.74.198.129:8080 (211.74.198.129), connection timed out

What's the problem? ( my internet conection or the repository server?)I did some checking and the site works fine for me. All I can think is that the problem must be with your internet connection somewhere or between your service provider and the repositories. My suggestion is to wait a day or two and try again.

---

### Post by livefordirty on 2006-08-21
The problem's been lasting for weeks.
It works fine before.

What could "service provider" do to cause this problem ?

is there anyway to solve it?

---

### Post by matthew on 2006-08-21
> **livefordirty said:**
> The problem's been lasting for weeks.
It works fine before.

What could "service provider" do to cause this problem ?

is there anyway to solve it?Odd. Perhaps there is a problem with how your sources.list is set up?? Take a look at this page and compare what you have with what is written here. If there's a difference, follow the directions on the page to set up a new sources.list and then try again.
**[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)**

---

### Post by livefordirty on 2006-08-21
i checked that page, and followed that direction to setup new source.list.

but problem is still when i "sudo aptitude update"

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to 211.74.198.129:8080 (211.74.198.129), connection timed out


please help check what's wrong with this?

---

### Post by livefordirty on 2006-08-21
rr [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to 211.74.198.129:8080 (211.74.198.129), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Could not connect to 211.74.198.129:8080 (211.74.198.129), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to 211.74.198.129:8080 (211.74.198.129), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Could not connect to 211.74.198.129:8080 (211.74.198.129), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to 211.74.198.129:8080 (211.74.198.129), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to 211.74.198.129:8080 (211.74.198.129), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to 211.74.198.129:8080 (211.74.198.129), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed

---

### Post by livefordirty on 2006-08-21
is there any backup server of repository to download update and packages?
( another server with different ip address)

---

