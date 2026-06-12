---
title: "permissions users"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by locutuz on 2008-01-19
Hi all,

I am sure this is an easy one. This is the situation: I have an ubuntu pc at the office, it's function is a web agenda for the reception. So it's 99,9% of the time doing nothing. So for a little project, I made a little NAS of it with samba. Thanks to some tuturials over here, things are working just fine.

There is just one thing: the desktop user can read the files/directories of the accounts of the samba users. Do I have to chmod those samba directories? and yes, what setting is used?

TIA

---

### Post by njparton on 2008-01-19
You could probably do two things.

Change the ownership and permissions of the directories shared such that the group of the web user isn't allowed access

and/or

you can edit your smb.conf file to only allow specific user access to the shares (you could even deny access to the IP address of the NAS PC itself).

use "chown" to change the owner of a directory e.g.

```
sudo chown bob /etc/example/directory
```

use chmod to disallow access of others but allow group access (then make sure the NAS web user isn't in bob's group):

```
sudo chmod o-rwx /etc/example/directory
sudo chmod ug+rw /etc/example/directory
```

In /etc/samba/smb.conf, under the share sections at the bottom you can add these lines:

```
valid users = bob, fred, betty
hosts allow = 192.168.1.1 192.189.1.3
```

Don't include the NAS web user in the list of users in the first line and add a space seperated line of IP address of PC's you want to allow access to the share.  Also, don't allow public access to the shares and under global set "security = user" not share.

Then restart samba:

```
sudo /etc/init.d/samba restart
```

---

### Post by spiderbatdad on 2008-01-19
from what it sounds like you want only the owner to be able to read/write the shared folders? I'm not sure you can simply change the permissions without screwing up samba, maybe you can. Did you use the samba wiki to set the share up?[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)
The guide is fairly accurate and useful, however where it talks about setting the permission it is wrong. You have to use a real octal number...not what the guide shows. So, some four digit like 7700 might be what you are looking for or 0644...I have a little trouble with octal permissions myself, but here is a link explaining a little.[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by locutuz on 2008-01-24
> **njparton said:**
> 
```
sudo chown bob /etc/example/directory
```

```
sudo chmod o-rwx /etc/example/directory
sudo chmod ug+rw /etc/example/directory
```


Thanks, that's what I am looking for!

One point still: One share is for my local webserver. I am afraid that if I do the above, that apache has no access to the files anymore.. Am I right? Should I do the trick above but with user "apache"?

---

### Post by hyper_ch on 2008-01-24
well, you cuold also force samba to use a certain user/group for the file permissions.

---

### Post by locutuz on 2008-01-31
Worked like a charm!

---

