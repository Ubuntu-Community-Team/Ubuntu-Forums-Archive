---
title: "sudo apt-get update"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-05-15
When I run sudo apt-get update, I get this error message:
[B]W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3
W: You may want to run apt-get update to correct these problems[/B]
What does this mean?:(

---

### Post by ProjectGod on 2006-05-15
hmmm... havent seen that one... one question. have you added the extra repositories by editing the "sources.list" file?

---

### Post by aysiu on 2006-05-15
What's cyberfunk...?

---

### Post by ProjectGod on 2006-05-15
haha! we have no idea. :mrgreen:

---

### Post by NeoGreen on 2006-05-15
Well I do remember having done something with the Repositories to get my wireless card working on my laptop (I think).  :confused:

---

### Post by uzi09 on 2006-05-15
[QUOTE=aysiu]What's cyberfunk...?[/QUOTE]

CIPHERfunk :D


looks like u added an extra repository which isn't validated by any sort of 'signature' so apt-get's just warning yah. if you want to get rid of it, the only way i know is to remove the entry for cipherfunk.org from your /etc/apt/sources.list

---

### Post by Sef on 2006-05-15
Cipherfunk.org is a blog for hacking linux. 

[http://cipherfunk.org/diary/index.html]("http://cipherfunk.org/diary/index.html")

I would get rid of that one.

---

### Post by nanotube on 2006-05-15
well, there is also another way (and a better way, i might add). that is to import the gpg key for the repository. check the cipherpunk website and see if they provide a signing key for their repository. 

hmm, i just checked, and the guy doesnt provide his gpg key - but you could email and ask yourself:  [email]pd@cipherfunk.org[/email]

---

### Post by Tamihania on 2006-05-15
Hi,

1.go to the website:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

and find the sources.list and KEY for Breezy (I am using Dapper and cannot give you my KEY :( )

2. open terminal and:

# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

replacing KEY with the code you get in the sources list for cipherfunk.

Have a nice day,

Tami

---

