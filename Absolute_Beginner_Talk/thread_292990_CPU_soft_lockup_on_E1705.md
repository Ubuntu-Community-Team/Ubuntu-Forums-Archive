---
title: "CPU soft lockup on E1705"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by chrisknight on 2006-11-04
I dont want to sound like im bashing here because im not.  I am a Fedora user.  ...and Red Hat user from 1998 forward.  I am no newbie to Linux.  I have to say that I "switched" to Ubuntu because in the community, is has great respect and Intel's driver release for the ipw3945abg is hardy user friendly.  So in an attempt to simplify the wireless install, I thought Id give Edgy a go.  I have had my Dell E1705 for about 3 months now, and still have yet to get my wireless (wpa enc) to run under linux. (Fedora, Ubuntu, solaris i386, mandrake) I thought Ubuntu would change that.  I have never had a system refuse to boot until I tried to use Ubuntu today (edgy 6.10).  It errors while loading drivers for ipw3945 in recovery mode (i think thats what its called).

Any one else have this?
Has Ubuntu released a fix?

Thanks,
Chris

---

### Post by mcglnx on 2006-11-04
Hi,

I got exactly the same issue. I removed the script ipw3945 in /etc/<somewhere>. After that I was able to boot. 
This is a nasty trick for an 'end user' platform, but it works.

BTW, I was not able to have a wireless network working w/ Edgy. It worked with 6.6 however.

Cheers,
M

---

