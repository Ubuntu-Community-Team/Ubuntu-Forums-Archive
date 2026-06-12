---
title: "HELP!! Need an Ubuntu 10.10 server+mac.iso (not desktop)"
date: 2010-10-28
forum: Apple Hardware Users
---

### Post by damang111 on 2010-10-28
We run our MacPRO's as servers.
I need the latest bootable Ubuntu SERVER edition.

I tried creating my own with mkisofs ([http://ubuntuforums.org/archive/index.php/t-19428.html](http://ubuntuforums.org/archive/index.php/t-19428.html))
the CD was bootable but the error "cd-rom drive contains a cd which is not recognized.." when installing.  Not sure how I made sure I copied the entire contents with rsync and used mkisofs... but anyway,

Can someone point me to a Mac Bootable Maverick 64 bit SERVER version ?

thanks.

---

### Post by ryanczak on 2010-10-28
Why not get the daily ISO from here:

[http://cdimage.ubuntu.com/ubuntu-server/daily/current/](http://cdimage.ubuntu.com/ubuntu-server/daily/current/)

---

### Post by damang111 on 2010-10-28
> **ryanczak said:**
> Why not get the daily ISO from here:

[http://cdimage.ubuntu.com/ubuntu-server/daily/current/](http://cdimage.ubuntu.com/ubuntu-server/daily/current/)

thanks for the reply.
what is the difference between the iso (64 bit version) in the above link and the 64 bit server on the main page?

It's a known issue that the 64bit maverick version will not boot on MacPro's.

tia.

---

### Post by ryanczak on 2010-10-29
The version in the link I posted above is the daily build of the Maverick server ISO. If the issue that is affecting the ability to boot on a mac pro has been addressed in a more recent version of maverick (or one of maverick's components) the daily ISO might work for you.

---

### Post by damang111 on 2010-10-29
> **ryanczak said:**
> The version in the link I posted above is the daily build of the Maverick server ISO. If the issue that is affecting the ability to boot on a mac pro has been addressed in a more recent version of maverick (or one of maverick's components) the daily ISO might work for you.

nope no good still.

I wonder what's taking them so long to fix it.

---

### Post by ryanczak on 2010-10-29
How does the CD install fail? Have you opened a bug report?

---

### Post by damang111 on 2010-11-02
> **ryanczak said:**
> How does the CD install fail? Have you opened a bug report?

It's a known issue the 64 bit 10.10 does not boot on mac.

---

### Post by ryanczak on 2010-11-02
I installed 10.10 on my MBP 7,1 with out any problems. Stock CD ISO boots just fine.

---

### Post by damang111 on 2010-11-03
> **ryanczak said:**
> I installed 10.10 on my MBP 7,1 with out any problems. Stock CD ISO boots just fine.

The 64-bit version?
other people are having issues installing the stock SERVER 64-bit 10.10.
see:
[http://ubuntuforums.org/showthread.php?t=1607177](http://ubuntuforums.org/showthread.php?t=1607177)
there's a few more on the web.
I have about 6-7 MacPro's Xeon 64-bit that refuses to boot off the CD and just hangs.

---

