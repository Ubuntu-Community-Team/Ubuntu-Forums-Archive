---
title: "updates failing."
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by modulistic_terror on 2007-11-16
i am using update manager which is telling me to install 3 updates when i click on install this is what is written in the error message.
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden

any help would be much appreciated.

---

### Post by taurus on 2007-11-16
Yes, it has been a problem since early this afternoon.

[http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)
[http://ubuntuforums.org/showthread.php?t=463944](http://ubuntuforums.org/showthread.php?t=463944)

---

### Post by modulistic_terror on 2007-11-16
The problem will be resolved on the other end of the signal then?

---

### Post by blackhole54 on 2007-11-17
> **modulistic_terror said:**
> The problem will be resolved on the other end of the signal then?

Quote from [this post]("http://ubuntuforums.org/showpost.php?p=3783704&postcount=4") on the sticky thread *taurus* referred to:

> 
A bug was identified in the update associated with USN-544-1 [http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)

As a result, the update was disabled to prevent users from inadvertently upgrading to this defective release.

**When the problem is resolved, the permissions will be restored to normal. **Thanks for everyone's patience and understanding. (emphasis added)


This is referring to the three updates that failed for you,which have to do with SAMBA.  So the instructions are just to wait until it starts working :)

---

### Post by ecionci on 2007-11-17
Thanks for the quick info. It's what makes Linux great. In windows we would
have to maybe wait for the next update.:-)

---

