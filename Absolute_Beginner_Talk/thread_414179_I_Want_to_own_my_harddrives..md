---
title: "I Want to own my harddrives."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by B-&gt;J-&gt;Eagle on 2007-04-19
[B][COLOR="DarkRed"]Hi all.

This is proberly easy to configure but i am lost in it, because im new in this OS.

Ive heard that when you are a user in Ubuntu you only own your home folder, which is the hardrive with ubuntu installed, but since i have an ekstra hardrive how do i make it owned by the user that i log in with? Right now it is owned by root.

When i installed Efty Edge i mounted it as /media something but why is it then owned by root?

I know that i can put a folder inside the Hardrive and make owner permissons for that one, but... come on isn't there a fix way to make the harddrive owned by my user account?[/COLOR][/B]

---

### Post by tbg58 on 2007-04-19
CD to the directory where the drive is mounted (e.g. media)
ls -la to see the current owner information and name of the mounted drive.  If it's called, for instance, disk, then 
sudo chown disk (yourusername)
you may also want to 
sudo chgrp disk (yourusername)

Alternately you can leave the ownership of the top of that file system as it is, then just create any directories you wish underneath and chown or chgrp them in the same way.

Hope this helps!  Good luck!
Rob

---

### Post by Austin_KW on 2007-04-19
You can add the disk to /etc/fstab and in the options add your uid (with uid=1000 for the first user)

---

### Post by aysiu on 2007-04-19
One of these should help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by B-&gt;J-&gt;Eagle on 2007-04-21
ok that helped me thx, but What would be a good idea to do when i format my system, i am going to do that within short time, so my question is:

What kind of directory shall i make my harddrives when i reistall ubuntu? 
You know when you are in the install it askes you about /root and stuff. I ofcourse make the /root and /swap but what about the drives that i just use for files which directory shall they be so that i easily can acces them from my normal user?

---

### Post by Rui Pais on 2007-04-21
> **B->J->Eagle said:**
> 
What kind of directory shall i make my harddrives when i reistall ubuntu? 
You know when you are in the install it askes you about /root and stuff. I ofcourse make the /root and /swap but what about the drives that i just use for files which directory shall they be so that i easily can acces them from my normal user?

by default installer will suggest /media/<something> for each partition, with <something> being the partition scheme/number.
So you don't have to do nothing. That way the be available at desktop , too.

---

### Post by B-&gt;J-&gt;Eagle on 2007-04-21
Ok... but i did that on this install and that was why i could'nt get permissions to my harddrives

---

### Post by orb9220 on 2007-04-21
> Ok... but i did that on this install and that was why i could'nt get permissions to my harddrives

Which is always the default. You have to manually change permissions on those drives to get read/write access.

---

