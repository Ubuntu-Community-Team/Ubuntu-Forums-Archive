---
title: "App download problems"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by foxjwill on 2006-07-22
When I try to download some programs with Add/Remove Applications, it pops up the following error:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/i/imlib/imlib-base_1.9.14-29ubuntu1_all.deb
  


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libu/libungif4/libungif4g_4.1.4-1_i386.deb
  


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/i/imlib/imlib11_1.9.14-29ubuntu1_i386.deb
  


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1_i386.deb
  


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sox/sox_12.17.9-1_i386.deb
  


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/d/docker/docker_1.4-3_i386.deb
  


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openssl097/libssl0.9.7_0.9.7g-5ubuntu1_i386.deb
  


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcltls_1.5.0-2_i386.deb
  


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.95-1_i386.deb
  


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/galeon/galeon-common_2.0.1-1ubuntu2_all.deb

```

---

### Post by taurus on 2006-07-22
Because us.archive.ubuntu.com is down.  Try again later or remove "us" from all the lines in /etc/apt/sources.list...

---

