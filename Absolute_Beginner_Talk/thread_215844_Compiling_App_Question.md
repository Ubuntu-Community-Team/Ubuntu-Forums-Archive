---
title: "Compiling App Question"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Tom Fury on 2006-07-14
I'm trying to compile wireshark-0.99.2pre1.  This is my first attempt at compiling an application from source code.  I did all my reading and installed everything I needed to get the ./configure to work.  I ran make and it looks like there are no errors at the end.  However, I cannot find the wireshark binary.  Shouldn't it be in the same directory that I'm compiling in?

This is actually my second attempt at it.  I originally did:

sudo auto-apt run ./configure
sudo make
sudo checkinstall

It made and installed the package but again I couldn't find the wireshark binary so I uninstalled it and went back to basics by not using auto-apt and checkinstall.

---

### Post by Sonofmoog on 2006-07-14
Do

```
locate wireshark
```

If you have too many hits, do

```
locate wireshark | grep bin 
```

If you get no hits, make sure the locate database is current by typing

```
updatedb
```

HTH

---

### Post by Tom Fury on 2006-07-14
Thanks for the reply.  Here is what I found.

```
xxx@puffy:~/wireshark/wireshark-0.99.2pre1$ locate wireshark | grep bin
/home/xxx/wireshark/wireshark-0.99.2pre1/epan/dissectors/packet-dcerpc-rs_bind.c
/home/xxx/wireshark/wireshark-0.99.2pre1/epan/dissectors/packet-ypbind.c
/home/xxx/wireshark/wireshark-0.99.2pre1/epan/dissectors/packet-ypbind.h
/home/xxx/wireshark/wireshark-0.99.2pre1/epan/dissectors/.deps/packet-dcerpc-rs_bind.Plo
/home/xxx/wireshark/wireshark-0.99.2pre1/epan/dissectors/.deps/packet-ypbind.Plo
/home/xxx/wireshark/wireshark-0.99.2pre1/epan/dissectors/.libs/packet-dcerpc-rs_bind.o
/home/xxx/wireshark/wireshark-0.99.2pre1/epan/dissectors/.libs/packet-ypbind.o
/home/xxx/wireshark/wireshark-0.99.2pre1/epan/dissectors/packet-dcerpc-rs_bind.lo
/home/xxx/wireshark/wireshark-0.99.2pre1/epan/dissectors/packet-ypbind.lo
/home/xxx/wireshark/wireshark-0.99.2pre1/radius/dictionary.bintec
```

So, it looks to me that the make is not working to create the binary.  Here is the last part of the make terminal.

```
make[3]: Leaving directory `/home/xxx/wireshark/wireshark-0.99.2pre1/doc'
/usr/bin/perl ./make-version.pl .
Version configuration file version.conf not found.  Using defaults.
This is not a SVN build.
svnversion.h is up-to-date.
make[2]: Leaving directory `/home/xxx/wireshark/wireshark-0.99.2pre1'
make[1]: Leaving directory `/home/xxx/wireshark/wireshark-0.99.2pre1'
```

Am I missing something when doing the make??  Is there something I'm doing wrong?

---

### Post by Sonofmoog on 2006-07-15
> **Tom Fury said:**
> Thanks for the reply. Am I missing something when doing the make??  Is there something I'm doing wrong?

Yes.  It's been awhile since I've built anything from a tarball, but I remember enough to know that .. leaving directory .. is not the last message you receive.  There's usually some sort of exit message, or an exit code, that you can check.  I am no expert in these matters, so the only recommendation I can make to you of any merit is to try to re-download the tarball - perhaps from a different mirror - and try again ..

---

### Post by Tom Fury on 2006-07-18
I saw that wireshark moved from their prerelease to the formal one.  I redownloaded it and tried to compile it again.  Same problem as above.  I also tried it by enabling and using the root account.  Same exact problem.

Is there a log or something that is created when compiling an app that I can look in to try and figure out why this won't compile under Ubuntu?

---

