---
title: "update problems"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-04-22
every time I try to check for updates I bump into this error:
```
W: GPG error: http://medibuntu.sos-sts.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

what is this and how do I prevent it?

---

### Post by Gmbrdilos on 2007-04-22
anyone?

---

### Post by Gmbrdilos on 2007-04-22
some help would be ince...

---

### Post by zvacet on 2007-04-22
Try with this command first 
  
```
sudo aptitude update && sudo aptitude upgrade
```

and if is no luck  

[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]

and un your case 

gpg --keyserver hkp://subkeys.pgp.net --recv-keys  2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783  | sudo apt-key add -

---

### Post by Seisen on 2007-04-22
Here's how to fix it, copy it into the terminal.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

``` then

```
sudo aptitude update

``` if it doesn't work keep trying sometimes it doesn't want to.

---

