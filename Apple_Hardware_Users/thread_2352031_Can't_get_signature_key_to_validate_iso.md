---
title: "Can't get signature key to validate iso"
date: 2017-02-08
forum: Apple Hardware Users
---

### Post by pwilson2008 on 2017-02-08
I am trying to verify the ubuntu.iso download. However I am not getting the same results as the verify page suggests. I already have the .iso file. I download the SHA256 files to the same directory. I am using Terminal in Mac OS X.


[https://www.ubuntu.com/download/how-to-verify](https://www.ubuntu.com/download/how-to-verify)


To get the SHA256 files, I enter in terminal


```
curl -O  http://releases.ubuntu.com/16.04/SHA256SUMS
curl -O  http://releases.ubuntu.com/16.04/SHA256SUMS.gpg
```



To get the signature key I enter
```
gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys "8439 38DF 228D 22F7 B374 2BC0 D94A A3F0 EFE2 1092" "C598 6B4F 1257 FFA8 6632 CBA7 4618 1433 FBB7 5451"
```

I get
```

gpg: "8439 38DF 228D 22F7 B374 2BC0 D94A A3F0 EFE2 1092" not a key ID: skipping
gpg: "C598 6B4F 1257 FFA8 6632 CBA7 4618 1433 FBB7 5451" not a key ID: skipping
```

OK. lets see if I can do anything else


I enter
```
gpg --list-keys --with-fingerprint 0xFBB75451 0xEFE21092
```

I get  

```
pub   1024D/FBB75451 2004-12-30
      Key fingerprint = C598 6B4F 1257 FFA8 6632  CBA7 4618 1433 FBB7 5451
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>


pub   4096R/EFE21092 2012-05-11
      Key fingerprint = 8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>
```
 
WOOT! Just like the page says I should.


I then enter


```
gpg --verify SHA256SUMS.gpg SHA256SUMS
```

I get the results the page says I should, except the creation date of the signature is different.




Finally I enter


```
shasum -a 256 -c SHA256SUMS 2>&1 | grep OK
```

I get 


```
Ambiguous output redirect.
```

I am sure it is something stupid I did or missed. Any guidance is greatly appreciated.

---

### Post by howefield on 2017-02-09
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by pwilson2008 on 2017-02-20
I don't see how this is an apple hardware issue.

---

### Post by howefield on 2017-02-21
> **pwilson2008 said:**
> I don't see how this is an apple hardware issue.

No I don't believe it a hardware issue either, but given that validating the iso has specific instructions for macOS, then it's reasonable to think who better to help you than other macOS users.

---

