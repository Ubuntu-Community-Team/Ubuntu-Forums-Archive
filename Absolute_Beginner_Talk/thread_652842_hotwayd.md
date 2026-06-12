---
title: "hotwayd"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by gleble on 2007-12-29
Hi
 I am trying to install hotwayd but when I come to the smtp bit, I get
this message:
'Building hotsmtpd:                      no
    You are missing cyrus-sasl v2 required by hotsmtpd to authenticate.
    Hotsmtpd will not be compiled unless you install this library
    and re-run configure.'
So I download cyrus-sasl and configure, which seems to be OK but when I
make I get loads of errors:
'digestmd5.c:279: warning: pointer targets in initialization differ in
signedness'

What am I doing wrong?

---

### Post by rkd on 2007-12-29
I know nothing about hotwayd, so I'm just making a wild guess here: Perhaps you got the wrong version of cyrus-sasl. I'm guessing that there are versions for different environments -- perhaps different versions for 32 bits and 64 bits, perhaps different versions for Linux, Solaris, BSD, etc., perhaps different versions for various releases, could be other reasons, too. 

Look to see whether there are different versions and be sure you got the right one.

---

