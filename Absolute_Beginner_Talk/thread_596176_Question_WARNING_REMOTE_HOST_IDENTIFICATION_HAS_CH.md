---
title: "Question: WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by aspen_dv on 2007-10-29
I trying to ssh to a machine and I got the offending key warning message
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
e4:43:27:5d:ad:8f:e8:fb:e7:af:5e:a0:26:6d:a1:dd.
Please contact your system administrator.
Add correct host key in /home/vietp/.ssh/known_hosts to get rid of this message.
Offending key in /home/vietp/.ssh/known_hosts:24
RSA host key for 72.43.222.229 has changed and you have requested strict checking.
Host key verification failed.

I found one solution which is to delete everything in the .ssh/known_hosts file. But this is not a "real" solution as I've been told. Can someone tell me which line to delete in the file? I can't locate any line that associated with the IP address. Thanks

---

### Post by p_quarles on 2007-10-29
Well, if you are sure you know which entry in the known_hosts file corresponds to the computer you failed to login to, you can delete that. known_hosts isn't really meant to be a human-readable file, though, so it's not going to be obvious. 

If you don't want messages like this, you can always edit /etc/ssh/ssh_config and turn off strict checking. 

Since you didn't ask about the warning itself, I'm assuming you know why the hostkey changed, and are sure that it's safe.

---

### Post by lrhogusa on 2007-11-09
In 7.10 version, I see that /home/<user>/.ssh/known_hosts is hashed so you can't tell what line of data to delete that is related to box you are trying to connect to. Solution:

Edit /etc/ssh/ssh_config to stop hashing by changing the yes to a no in the hash line shown below. You could then clean out your known_hosts file and start over with new stuff.

#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts no
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

---

### Post by aspen_dv on 2007-11-15
Thanks a lot Irhogusa! Exactly what I was looking for.

---

### Post by msergent on 2008-03-20
The error message gives you the line number that you need to remove.

# Offending key in /home/vietp/.ssh/known_hosts:24

If you delete line 24 within "/home/vietp/.ssh/known_hosts" and try reconnecting it will prompt you to accept the new key.

---

