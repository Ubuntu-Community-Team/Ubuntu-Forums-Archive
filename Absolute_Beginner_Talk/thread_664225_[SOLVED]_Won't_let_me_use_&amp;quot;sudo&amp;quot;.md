---
title: "[SOLVED] Won't let me use &amp;quot;sudo&amp;quot; command."
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by gibberman on 2008-01-10
I've been trying to get Permissions set to read/write as opposed to read only, so I screwed around with the "chown" command and, I guess I must have changed the permissions for all my folders in the process and now it won't even let me use the "sudo" command. :(

```
akersh@OptimusPrime:~$ sudo su
sudo: /etc/sudoers is owned by gid 1000, should be 0

```

That's basically what I see in my terminal.

So far, I've tried logging into the recovery console and typing this, verbatim:

> chown root:akersh /etc/sudoers
chmod 440 /etc/sudoers
reboot

God, I need help. :confused:

---

### Post by theRightNee on 2008-01-10
see if you can run "sudo -s" so you can log in as root,
from there you can change permissions back.

hope this helps

---

### Post by nikoPSK on 2008-01-10
yes, sudo -s or sudo -i. If there isn't a required rot login you can alkways just add sudo infront of the command.

---

### Post by scxtt on 2008-01-10
the gid of /etc/sudoers needs to be 0 (i.e. root), not the gid of your user

sudo: /etc/sudoers is owned by [COLOR="Red"]gid[/COLOR] 1000, should be 0
```
:> ll /etc/sudoers
-r--r----- 1 root [COLOR="Red"]root[/COLOR] 496 Nov 30 03:37 /etc/sudoers
```

---

### Post by gibberman on 2008-01-10
> akersh@OptimusPrime:~$ sudo -s
sudo: /etc/sudoers is owned by gid 1000, should be 0
akersh@OptimusPrime:~$ sudo -i
sudo: /etc/sudoers is owned by gid 1000, should be 0


Tried both sudo -s, and sudo -i...again same results. :(


AND this is what happens if I try running a command with the sudo prefix:

> akersh@OptimusPrime:~$ sudo dir
sudo: /etc/sudoers is owned by gid 1000, should be 0


As opposed to when I don't use the prefix:

> akersh@OptimusPrime:~$ dir
Desktop    Examples  nautilus-debug-log.txt  Public     Videos
Documents  Music     Pictures                Templates


:mad: Thanks guys, I'm appreciating this.

---

### Post by gibberman on 2008-01-10
> **scxtt said:**
> the gid of /etc/sudoers needs to be 0 (i.e. root), not the gid of your user

sudo: /etc/sudoers is owned by [COLOR="Red"]gid[/COLOR] 1000, should be 0
```
:> ll /etc/sudoers
-r--r----- 1 root [COLOR="Red"]root[/COLOR] 496 Nov 30 03:37 /etc/sudoers
```



wait, can you explain this? thanks. :)

---

### Post by buccaneere on 2008-01-10
How about [HTML]exec sudo -s[/HTML]???

Gets you a new shell I believe...

---

### Post by scxtt on 2008-01-10
doing **chown root:akersh /etc/sudoers** isn't right, since /etc/sudoers should be owned by root:root ... do the following in recovery mode:

chown root:root /etc/sudoers
chmod 440 /etc/sudoers

then reboot.

the 1st command takes care of the "sudo: /etc/sudoers is owned by gid 1000, should be 0" part and the 2nd command makes sure the file is "read-only" by owner/group.

---

### Post by gibberman on 2008-01-10
> **buccaneere said:**
> How about [HTML]exec sudo -s[/HTML]???

Gets you a new shell I believe...
 


no didn't do the trick. :(


all that it did was close my current terminal window...

---

### Post by gibberman on 2008-01-10
> **scxtt said:**
> doing **chown root:akersh /etc/sudoers** isn't right, since /etc/sudoers should be owned by root:root ... do the following in recovery mode:

chown root:root /etc/sudoers
chmod 440 /etc/sudoers

then reboot.



OHHH RIGHT RIGHT


gotcha. okay i'm gonna try it out. thanks. :)

---

### Post by nikoPSK on 2008-01-10
> **gibberman said:**
> OHHH RIGHT RIGHT


gotcha. okay i'm gonna try it out. thanks. :)

:) you can edit posts too by clicking edit at the bottom. :)

---

### Post by gibberman on 2008-01-10
Right, so problem solved! :-) Thanks guys

---

### Post by nikoPSK on 2008-01-11
Please mark this thread as "SOLVED". :)

---

