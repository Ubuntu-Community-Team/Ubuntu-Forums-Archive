---
title: "Error with a package being detected"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by Cath0de on 2006-07-26
Okay, so I'm trying to install wireshark, formerly known as ethereal (which is being a total pain in the ***, I've been screwing around for 2 days trying to pin down all the dependencies and feel like I'm getting close), and whenever I ./configure, I come up with a libpcap error:

```
checking for pcap.h... yes
checking for pcap_open_live in -lpcap... no
checking for pcap_open_live in -lpcap with -lcfg -lodm... no
checking for pcap_open_live in -lpcap with -lpfring... no
configure: error: Can't link with library libpcap.

```

I've installed libpcap, libpcap-dev, libpcap, libpcap0.8, libpcap0.8-dev, and then searched through the forums and came up with this command I didn't understand, but used it in /usr/lib:

```
root@ubuntulaptop1:/usr/lib# ln -s libpcap.so.0.8.3 libpcap.so.0

```

I still get that message. Help!

](*,)

---

### Post by mlind on 2006-07-26
Why not to use ethereal package on Ubuntu **universe** repository?

---

### Post by Cath0de on 2006-07-26
you think outside of the box...I like it...

---

### Post by abowman on 2006-07-26
Keep it simple

---

### Post by Tom Fury on 2006-07-31
The problem for me is that that version of Ethereal has a major bug in it that showed up after I upgraded to Dapper.  I've been trying to compile wireshark since the pre-release with no success.

---

### Post by mlind on 2006-07-31
> **Tom Fury said:**
> The problem for me is that that version of Ethereal has a major bug in it that showed up after I upgraded to Dapper.  I've been trying to compile wireshark since the pre-release with no success.

You can compile wireshark from debian experimental repository. It doesn't require any changes to packaging information to get it build on Dapper.
If you fail to get it work, I can put the packages on my repository.

I just tested and it builds cleanly.

---

### Post by Tom Fury on 2006-08-01
Thanks for the offer.  I got my missing piece of information from the wireshark users list and got it to compile and install.  Isn't it funny that when you give it what it needs it seems to work better ;)

---

