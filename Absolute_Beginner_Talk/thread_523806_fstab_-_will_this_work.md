---
title: "fstab - will this work?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by captlogic on 2007-08-12
Hello all.

I'm getting ready to setup a friends pc.  (We're gettin' rid of windows!!!!)
What I want to know is will a fstab setup like the one below work?

sda1  /
sda2 swap
sdb1 /home
sdc1 /home/music

In particular I'm asking about the last line, can you mount as a sub-folder under home using a seperate partition, in this case a separate hd?

Thanks to the Gurus

Capt. Logic

---

### Post by 1/0 on 2007-08-12
Yes you can do that as long as you don't fiddle around with parallel startup in the boot scripts. That will result in the partition mounting in a partition that is not mounted yet. I would change the /home/music to /home/user/music for convenience, but that's just me. Otherwise you're fine except the UUID, ext3, defaults, etc.

---

### Post by captlogic on 2007-08-12
Thanks for your response.

I'm not sure what your reference 'Yes you can ... parallel startup in the boot scripts.' is about, but that means I'm not messing with it. :)

And yes, I meant /home/user/music

I'm going to assume this also means I can nest nfs shares in a similar manner

server:/home/user1/path/share /home/user/path/share

Thanks

---

### Post by 1/0 on 2007-08-12
Well, I used Gentoo before and a common way to speed up the boot process was to edit the default RC_PARALLEL_STARTUP="NO" to YES in /etc/config.d/rc. This would mount everything at once and start processes at the same time instead of after one another, making the boot process a bit faster. I guess the paths are a bit different in *buntu but except from that the same. 

As for the NFS shares, it works fine to mount under an existing partition in an _empty_ folder.

---

