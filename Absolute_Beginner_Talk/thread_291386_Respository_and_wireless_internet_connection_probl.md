---
title: "Respository and wireless internet connection problem"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-11-02
So I just reinstalled Dapper after a disasterous attempt at upgrading to Edgy, and I currently cannot install any upgrades, the upgrade program wants to to update. Please note that I CAN (and currently am) connected to the internet. Here is my respository list

```

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

```

My second problem is that my NIC (SMC2635W) rarely connects to my wireless internet after turning on my laptop. I have set my DNS server as my router IP address,  my internet settings is configured via DHCP, and I use wireless encryption. Has anyone had similar problems, and if so, how did you fix it?

Thanks :)

---

### Post by spamzilla on 2006-11-02
Anyone?

I have ried several respository lists and still no luck :(

---

### Post by dillbertdabomb on 2006-11-02
wireless support in linux is pretty bad...

get wired or go back to winblows...](*,)

opps: forgot; you can go to packages.ubuntu.com to get stuff...

just a little harder

---

### Post by Roobert on 2006-11-02
Can you post the output from 

```
sudo apt-get update
```

---

### Post by spamzilla on 2006-11-02
dillbertdabomb, my NIC worked fine before the upgrade, and after making a few changes and restarting my laptop a few times, my internet connection at bootup seems to be connecting fine now!

Roobert, here's the output of sudo apt-get update

```

matt@matt-laptop:~$ sudo apt-get update
Password:
Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://gb.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outReading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

I am not using any proxies btw.

---

### Post by Roobert on 2006-11-02
I would first try hitting other repositories, like us.archive.ubuntu.com, or ca.archive.ubuntu.com. I'm updating from the Canadian repo now with no troubles. If you still get time-out errors, try this, it worked for me:

```
sudo cp /etc/apt/apt.conf /etc/apt/apt.conf_backup

```

Check /etc/apt/apt.conf for a line like ```
Acquire::http::Proxy "false";
``` Try removing this line from the file, and then run apt-get again. If this doesn't work, you can always revert back to your original /etc/apt/apt.conf.

---

### Post by spamzilla on 2006-11-02
None of that worked Roobert :( DO you have any other suggestions?

---

### Post by Roobert on 2006-11-02
No, sorry...I don't have any other ideas...maybe try checking out [this thread]("http://www.ubuntuforums.org/showthread.php?t=289195"); dbott67 gave me a lot of things to check for in terms of connectivity, DNS, etc. Probably worth reading through his posts and checking the same things for yourself.

Hope this helps.

---

### Post by spamzilla on 2006-11-02
Ahhh excellent! Thanks for pointing me in the direction of that thread, and many thanks for the help. As you may have guessed, I fixed the problem :D

---

