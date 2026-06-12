---
title: "GPG Error"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by spinflick on 2006-11-16
Can anyone tell mr why I get this error I tried last night and this morning but still the same. Bet it's something really dumb I havnt done ;) 

W: GPG error: [http://media.blutkind.org](http://media.blutkind.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems
spinflick@Alpha0010:~$

---

### Post by wieman01 on 2006-11-16
Run this from command line:
> sudo gpg --keyserver subkeys.pgp.net --recv [COLOR="Red"]31A5F97FED8A569E[/COLOR]
sudo gpg --export --armor [COLOR="Red"]31A5F97FED8A569E[/COLOR] | sudo apt-key add -
Generally this error message will not be much of a problem. The package will install anyway, it's a simple warning message. The system simply asks for the public key for authentication of the packages.

---

### Post by wieman01 on 2006-11-16
Deleted...

---

### Post by spinflick on 2006-11-16
I just found out that Beryl is no longer supporting Dapper :( so it will have to wait.

---

