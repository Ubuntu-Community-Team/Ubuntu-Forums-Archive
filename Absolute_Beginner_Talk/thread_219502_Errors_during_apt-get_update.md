---
title: "Errors during apt-get update"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-07-20
I added some more repositories to Synaptic and now when I apt-get update at the end I have these errors: ```
Reading package lists... Done
W: GPG error: http://people.ubuntu.com ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B0B7481B1F44842D
W: GPG error: http://ubuntu.geole.de dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6CBDA04570FF3753
W: GPG error: http://archive.ubuntu.com dapper-security Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com dapper-updates Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com dapper-backports Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com dapper Release: Unknown error executing gpgv
W: GPG error: http://users.lichtsnel.nl dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: http://www.beerorkid.com dapper Release: Unknown error executing gpgv
W: GPG error: http://archive.czessi.net dapper Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems

```
What's that gpgv?
If this would help - when I write the gpgv command in the terminal it says:
```
gpgv: keyblock resource `/home/fuzzy/.gnupg/trustedkeys.gpg': general error

```

---

### Post by risbac on 2006-07-20
GPG is a security system to authentify files (like emails, repos...). Your problem seems to be that apt-get can't make sure the file you are trying to download are safe. 

Did you sudo to apt? 
Also, when you add a new repo, usually you have to download the public key and add it to your authentified keys list. But that should not be a problem for repos like "http://archive.ubuntu.com dapper-updates"

So your gpgv binary is maybe corrupted. If sudoing apt is not any better, I would maybe try to reinstall gpgv.

---

### Post by FuzZy2006 on 2006-07-20
where can i find this gpgv? it's not on synaptic

---

### Post by risbac on 2006-07-20
Packet is called "gnupg"

---

### Post by FuzZy2006 on 2006-07-20
solved the problem by resetting the date ... lol

---

