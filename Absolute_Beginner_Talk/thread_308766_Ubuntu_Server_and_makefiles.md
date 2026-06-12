---
title: "Ubuntu Server and makefiles"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by coke on 2006-11-28
I installed Ubuntu server on one of my Linux boxes and I was suprised to see it didn't have automake/autoconf/makefile support. 

Im looking to be able to set up the qmail server outlined in qmailrocks.org, though they don't offer an installation guide for Ubuntu. Only debian. I understand that Ubuntu is a debian flavor of linux.


Is there anything else other than autoconf/automake/makefile support I would have to add? If I added these, could I then proceed as outlined in the Debian installation guide for Qmailrocks.org?

---

### Post by bodhi.zazen on 2006-11-28
> **coke said:**
> I installed Ubuntu server on one of my Linux boxes and I was suprised to see it didn't have automake/autoconf/makefile support.

I suggest you install build-essential and [checkinstall](http://www.howtoforge.com/howto_linux_debian_deb_checkinstall)```
sudo aptitude install build-essential checkinstall
```

./configure && make && sudo checkinstall

---

