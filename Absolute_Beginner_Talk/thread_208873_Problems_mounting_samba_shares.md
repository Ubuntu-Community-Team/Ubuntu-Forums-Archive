---
title: "Problems mounting samba shares"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by E-Jey on 2006-07-04
I have a fileserver with all my movies and music. To connect to this server I used the places --> connect to server... option. The problem is that I can't play the content with a lot of applications. To fix this I mounted my drives with this command under root: " mount -t smbfs -o defaults,umask=000,uid=1000,user //10.0.0.2/looklisten /home/erik/LookListen/". I have to enter a password,  but I don't no why. I doesn't matter what I type, the share mount always. Does anybody know why I have to enter the password? Anyway, now I can play the music en movies with all players. The share has to be mounted automaticly, so I edit the fstab file. After I reboot my computer, it hangs at the "Starting hardware hald" 
How can I mount my samba share automaticly at bootup?

---

### Post by thumper on 2006-07-04
Not entirely sure why you have to enter a password, but I am guessing that is the default, and there will be an option to login without a password.

BTW smbfs has been deprecated, you should look to use cifs.

You should be able to mount from /etc/fstab - I have had it working before.

---

### Post by E-Jey on 2006-07-04
Thanks for your reply. I've changed smbfs to cifs and everything works, but it's extremely slow...

---

### Post by thumper on 2006-07-07
> **E-Jey said:**
> Thanks for your reply. I've changed smbfs to cifs and everything works, but it's extremely slow...

That's slightly odd.  My cifs share works blindingly fast...

---

