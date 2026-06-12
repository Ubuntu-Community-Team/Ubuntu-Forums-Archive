---
title: "Kubuntu &quot;Can't be verified&quot; GPG import please"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Frak on 2006-11-17
Hello, I've installed Kubuntu on my desktop and I run off of a wireless network, Kubuntu can't connect desktops in Live mode, but anyway, after I messed with the sources list, I reopened the software channels, but now it says it can't be verified
```
W: GPG error: http://kubuntu.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: http://kubuntu.org dapper Release: The following signatures couldn                                                           't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D50                                                            88

```
does anybody know where or how I can get rid of this.](*,) 

Thanks

---

### Post by wieman01 on 2006-11-17
Run this from command line:
> sudo gpg --keyserver subkeys.pgp.net --recv [COLOR="Red"]A506E6D4DD4D5088[/COLOR]
sudo gpg --export --armor [COLOR="Red"]A506E6D4DD4D5088[/COLOR] | sudo apt-key add -
Generally this error message will not be much of a problem. The package will install anyway, it's a simple warning message. The system simply asks for the public key for authentication of the packages.

---

### Post by Frak on 2006-11-17
Thank you very much!

---

