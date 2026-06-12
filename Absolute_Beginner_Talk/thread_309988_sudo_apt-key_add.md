---
title: "sudo apt-key add?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by robyholmes on 2006-11-30
hi i am trying to install berly, i am stuck on installing the headers for the drivers. so i tryed to install them and it won't update says some thing about a key? so: this is what i did after looking at some forum's>

shadowmodz@shadowmodz:~$ gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 31A5F97FED8A569E
gpg: requesting key ED8A569E from hkp server wwwkeys.eu.pgp.net
gpg --armor --export 1F41B907 > keyName.gpg
gpg: key ED8A569E: "Quinn Storm <livinglatexkali@gmail.com>" not changed
gpg: Total number processed: 1
gpg: unchanged: 1
shadowmodz@shadowmodz:~$ gpg --armor --export 1F41B907 > keyName.gpg
shadowmodz@shadowmodz:~$ sudo apt-key add keyName.gpg
gpg: no ultimately trusted keys found
OK
shadowmodz@shadowmodz:~$

and it didn't work, can anyone help? i am new to linux so i am not great at this? thanks a lot

---

### Post by jordanmthomas on 2006-11-30
It looked like it worked to me.  Does whatever you imprted the key for work?  ie, can you get the stuff you need from quinnstorm?

---

### Post by robyholmes on 2006-11-30
not this is what it said..
shadowmodz@shadowmodz:~$ sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Get: 4 [http://www.beerorkid.com](http://www.beerorkid.com) edgy Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) edgy Release
Errhttp://www.beerorkid.com edgy Release

Get: 5 [http://www.beerorkid.com](http://www.beerorkid.com) edgy Release [5755B]
Ign [http://www.beerorkid.com](http://www.beerorkid.com) edgy Release
Ign [http://www.beerorkid.com](http://www.beerorkid.com) edgy/main-edgy Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) edgy/main-edgy Packages
Fetched 5947B in 4s (1410B/s)
Reading package lists... Done
W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems
shadowmodz@shadowmodz:~$

so it isn't getting that file?

---

### Post by jordanmthomas on 2006-11-30
```
KEY=31A5F97FED8A569E
gpg --keyserver subkeys.pgp.net --recv $KEY
gpg --export --armor $KEY | sudo apt-key add -
```

Try that.  If it doesn't work, I'm not sure what to do.

---

### Post by robyholmes on 2006-11-30
i did this...

shadowmodz@shadowmodz:~$ KEY=31A5F97FED8A569E
shadowmodz@shadowmodz:~$ gpg --keyserver subkeys.pgp.net --recv $KEY
gpg: requesting key ED8A569E from hkp server subkeys.pgp.net
gpg --export --armor $KEY
gpg: key ED8A569E: "Quinn Storm <livinglatexkali@gmail.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
shadowmodz@shadowmodz:~$ gpg --export --armor $KEY
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

mQGiBEOc7TcRBADNBma+iSVGzw27+eHgPWlOCls8kypyVl2/OMdaqMvD0So26G6C
n0UpKSK3QGurvE73XfwtkmX4wTCr3hxAUgjncbef+k2Y7aohwMNOLAUAnS1GH0J0
W1KYqfLo2LtN3oHAO1d3lQ32WUQ9Y21Y1ONg1hAzEsYobe8WX6MYJ9TP2wCgg4ai
DWi6Wwn54EeGD4ms0iojH6ED/iVaM9H8hl2CljtuZIQmzruCOhz5RF06niVdayl2
A0uJr3kjzzkaq0zH8LUbC2Ygs707uNTwUVzvslqch/4TnxZUa/pyHQNrWfBWK0h3
wz9HkscEzUWrhwj2cCBK4T4h1urdv/ONotQWJ923KZMgjCStlr4+NdjvtIm4v15G
aQ3ZA/sGtaMSu0T2OkZYFbznw3hXFVwMHFPfJALZK7wreF3JjfthGZkP6WcJSxGA
c2ycNpkP6wMZpw1urgqZ/zXJFHu8jbZQ0F49K+J9xi0PtM078wPxJTR5SFkjwiCr
n7aUtUliE7nBKgs4pXIhK51Qv9tVQdVOfGx1CoyxVeR9NW5oPrQnUXVpbm4gU3Rv
cm0gPGxpdmluZ2xhdGV4a2FsaUBnbWFpbC5jb20+iGAEExECACAFAkOc7TcCGwMG
CwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRAxpfl/7YpWnkIYAJ9p3DhaDzRUH8cc
TOn+0YUaPfWs8QCffTr5ddzRXaV4G0uCeQHqusbujdKIRgQQEQIABgUCRGMSDAAK
CRCVWUT5VSc9RvF7AJ0Y5ejx3MsdCvOygDUzOjPHfU3+DgCfcpseiDhb/kWtEDLp
8Zf9HbN6eziInAQQAQIABgUCRPylTQAKCRCDTcXN9nDgIlJ8A/0fduaP/0vzbmmK
m3Fv1+YXh3pQE4a7yWdhawxpYRpz03evGjKsvVf1h6pC6Hb2RR4DD1rmvtxB7Nrx
loGZJEN5n2N+DzVLzvHPg8CLoVCvTkp28E70Wxsvz7U0qMw+vPB/VbTSx31bVQn6
GIgxvsV2a+HgIyXLLaOTEgdPb3nyLIhGBBARAgAGBQJFOzOwAAoJEB41yzXPAuYo
dvIAn0IQREOkw/2vcUsXMRA8wW6gQ4XgAKDSOLuYhnAmv3KcM81VML0qK1DdVLkC
DQRDnO1MEAgAilfXvUNF+AMtGQwbrNjZ7lk5Ga9wVrAYfTbl+biINVHBChKF+GaX
exsxrgssQC/CUcKwZ0snUjOJ16wQkU6WLLnIkHdSO3W3VrIurRGUDiClG7bTv8ES
wOiMYp+iTLKo7nI5mxHuEYNUjVGTggn3JAr05tastPRaN2Rcj5WpdjyV0U6jB4XM
/O+IFh29BgKdYJQ12L7/Wp6+Y/vZkUNrkSN/UU5osrAECz0byMZZQhVHQ8hymGCG
W5V+pQ9GsPNanZN/KuebOsm7Nc2nC6HkY2UcVunj/qMaVR7qFVW1JDjX3ZjWSKah
vozfIMZY1Ize3P1dS5IPwOcgy362wzYv1wADBQf+MLuPTjrEs8KdOtXxyQK2qbhk
6qIhPu9vHu9IYtS5zaKyQ+T0UMA2r2fNQ8B0i123uv1yeFnmTeieUocGmC808nMh
vxVTldb00ogIyS7+0W1DkT7MACVe5XUASmUH9Uqp4ll6qw61LocQDEzx5m0C8L7D
V8hNkC9QBaEUDyeSZ22g8Vvt/Z2+O6ByTxnZO1EpTqIqxuDbD7og/nQZlID5vf8N
jueumDVe0W550YNIsUTqaarQjzcHp5ZeFa4XYJ7lQQAZEsMF6EozjfBXJSsClzdE
61YwCPqprCtWyaX70fLhOcyMBO3ei8dnauMuaoWbyjfvJaQdvqQF4A7V1ERKPohJ
BBgRAgAJBQJDnO1MAhsMAAoJEDGl+X/tilaeN1QAniYP6aAHIe7dYFGzu4vcJNuU
ITtKAJ9t9lUgNIs/kXy/3vyatPt+Gn/I5w==
=lUfo
-----END PGP PUBLIC KEY BLOCK-----
shadowmodz@shadowmodz:~$ sudo apt-key add
gpg: can't open `': No such file or directory
shadowmodz@shadowmodz:~$

that not right is it! lol

---

### Post by jordanmthomas on 2006-11-30
try it this way instead then
```
gpg --keyserver subkeys.pgp.net --recv 31A5F97FED8A569E
gpg --export --armor 31A5F97FED8A569E | sudo apt-key add -
```
I was lazy earlier and didn't feel like putting the number in both places.
This is how I always imported keys, and it would always work.  I'm not sure what your problem could be.

--and as a side note, you should still be able to download and install stuff, it just won't be authenticated.

---

### Post by robyholmes on 2006-11-30
i really don't get how you put that code in? i keep trying but it says the same as above, looks different, i am trying to install berly, and for that i need nvidia drivers and for that i need these headers? i judt don't get it? at all!

---

### Post by jordanmthomas on 2006-11-30
Well, what happens if you try to download the drivers anyway.  I had a key for e17 I couldn't get but I was still able to download everything from the repos.

It seems like you are getting the key fine, but it is either already imported or just won't import for some reason.  You can look at your imported keys somewhere in synaptic (don't know where as I don't use Ubuntu or synaptic)

---

### Post by pjmrider on 2008-04-30
This worked for me adding wxWidgets for authorization:

curl [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) | sudo apt-key add -

---

