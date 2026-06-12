---
title: "Easy ubuntu GPG error"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by El_Quintron on 2007-05-21
Hi guys, I'm just full of requests for you helpful people today.

When I run sudo apt-get update after installing easy ubuntu I get this:

[I]"W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems"[/I]

Once again any suggestions are appreciated.

---

### Post by Happy_Man on 2007-05-21
Did you run ```
sudo apt-get update
``` like the good little terminal recommended?

---

### Post by El_Quintron on 2007-05-21
Yessir!

that's what happens when I run sudo apt-get update, I've tried it a couple of times and all I get is a bunch of updating and that.

---

### Post by Happy_Man on 2007-05-21
Well, then, that means it's a problem on the other end.... perhaps a server is down or something?

---

### Post by El_Quintron on 2007-05-21
K well today is a holiday so I may wait a little while and see if it works tomorrow morning.

Thanks!

---

### Post by zvacet on 2007-05-21
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]

in your case 

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
 gpg --export --armor  2EBC26B60C5A2783 | sudo apt-key add -

---

### Post by El_Quintron on 2007-05-21
Thanks for the advice,

Should I run it as root? 
[I]~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server subkeys.pgp.net
?: localhost: Connection refused
gpgkeys: HTTP fetch error 7: couldn't connect: Connection refused
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
[/I]

---

### Post by Happy_Man on 2007-05-22
Put sudo in front....

---

