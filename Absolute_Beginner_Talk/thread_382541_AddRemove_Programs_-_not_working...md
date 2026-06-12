---
title: "Add/Remove Programs - not working.."
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by jezebel on 2007-03-12
Hi.

I've been experimenting with Ubuntu (and liking it!); I don't know what I did (after messing around with my NVidia driver and resolution...) but now when I try to add a program through the Add/Remove programs in the Applications menu, I can't get anything. It looks like Ubuntu is trying to get the apps from Japan (where I'm based)

Here's what I get when trying to add, for example, a game:

W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/pool/universe/a/armagetron/armagetron-common_0.2.7.0-1.1ubuntu2_all.deb](http://jp.archive.ubuntu.com/ubuntu/pool/universe/a/armagetron/armagetron-common_0.2.7.0-1.1ubuntu2_all.deb)
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)


W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/pool/universe/a/armagetron/armagetron_0.2.7.0-1.1ubuntu2_i386.deb](http://jp.archive.ubuntu.com/ubuntu/pool/universe/a/armagetron/armagetron_0.2.7.0-1.1ubuntu2_i386.deb)
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)


On the other hand, when I tried to install Adobe Reader, no problem. I'm figuring it's because it's a pretty international app...

Can anyone tell me how to fix this??

OH - also, my Automatix2 won't fully launch, either - it starts up, I accept the terms, then - it disappears...

Thanks!

J.

---

### Post by chewearn on 2007-03-12
System -> Administration -> Software Sources

You can change the "Download from" to another.

---

### Post by jezebel on 2007-03-12
Erg. That should have been SO obvious, but somehow I couldn't get it:)  Thanks very much - I did what you said and everything is great.

---

