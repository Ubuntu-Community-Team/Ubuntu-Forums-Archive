---
title: "java for firefox"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by jrev on 2005-08-18
Hi,
I thought I had installed java environment on firefox with the ubbuntuaddon.zip file, but when I type 
about:plugins I found only shockwave Flash and futureSplash player installed 

How can I install the java on firefox ?
Thanks

---

### Post by bored2k on 2005-08-18
Execute the commands in Terminal mode (Applications -> System Tools -> Terminal)

1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
3. sudo apt-get install sun-j2re1.5

Restart Firefox.

---

### Post by jrev on 2005-08-18
thanks for that quick answer 
It worked fine and I transfered the .deb package to install it on another laptop cause
I only have a slow modem connection

---

