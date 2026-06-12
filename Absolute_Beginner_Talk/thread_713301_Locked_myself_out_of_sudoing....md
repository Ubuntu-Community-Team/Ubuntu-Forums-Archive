---
title: "Locked myself out of sudoing..."
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by ironmonkeygf on 2008-03-02
I was trying to beef up security for ssh on my server, and locked my user account's password (with sudo passwd -l user), so now I can't log in locally.  I can get in remotely with my public/private key, but once I get in, I can't sudo.  Is there anything I can do to get myself sudo access?  I only had the one account on the server, so there's no logging in as anyone else...

I'm going to wipe ubuntu and reinstall if no one can come up with anything, but I don't really want to set everything up again, so I'm hoping that there's a way to get sudo back.

---

### Post by Oldsoldier2003 on 2008-03-02
> **ironmonkeygf said:**
> I was trying to beef up security for ssh on my server, and locked my user account's password (with sudo passwd -l user), so now I can't log in locally.  I can get in remotely with my public/private key, but once I get in, I can't sudo.  Is there anything I can do to get myself sudo access?  I only had the one account on the server, so there's no logging in as anyone else...

I'm going to wipe ubuntu and reinstall if no one can come up with anything, but I don't really want to set everything up again, so I'm hoping that there's a way to get sudo back.
if you have physical access to the server you can reboot it into recovery mode and add a new user,  then put the new user into the admin group. with the new user sudo passwd -u userthatwaslocked , then reboot.
All should be well and you could delete the new user of keep it as a backup for these kind of emergencies.

---

### Post by Oldsoldier2003 on 2008-03-02
> **ironmonkeygf said:**
> I was trying to beef up security for ssh on my server, and locked my user account's password (with sudo passwd -l user), so now I can't log in locally.  I can get in remotely with my public/private key, but once I get in, I can't sudo.  Is there anything I can do to get myself sudo access?  I only had the one account on the server, so there's no logging in as anyone else...

I'm going to wipe ubuntu and reinstall if no one can come up with anything, but I don't really want to set everything up again, so I'm hoping that there's a way to get sudo back.

oh beef up SSH security by installing denyhosts once you resolve your current issue.


```
sudo apt-get install denyhosts
```

---

### Post by ironmonkeygf on 2008-03-02
Thanks.  Luckily my "server" (aka old laptop) is 3 feet away.  I didn't realize that recovery brought me right into root@mycomputer.  I just unlocked the account from that command line and it worked like a charm.

As for the security thing, I found how to do what I was originally attempting.  Changing the following in sshd_config:
```
#PasswordAuthentication yes
```
to
```
PasswordAuthentication no
```

I'll look into DenyHosts next.  Thanks a bunch for the help.

---

