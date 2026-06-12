---
title: "yaboot won't install to harddrive"
date: 2005-04-11
forum: Apple PPC Users
---

### Post by liberated on 2005-04-11
I'm trying to install Hoary on an old Powerbook G3 (Lombard), and when everything is almost finished the installer fails to write yaboot to the harddrive, and gives no error information, except that it fails to write yaboot to "/target/".

The system has 64MB RAM, 4GB HD (I said it was old, right?).

When I ran disk druid from the Yellow Dog Linux install-CD it showed the size of /dev/hda2 as 0M, so I remade the partions and the Hoary partioner says /dev/hda2 is 1M (but it did that when disk druid said 0M as well...), I don't know if this has something to do with it.

Just wanna check if someone has encountered this before proceeding with further install efforts.

---

### Post by erkki70 on 2005-04-11
Hi,
I have successfully installed Hoary preview on the same Lombard except 192 Mb RAM and didn't encounter that problem of yours as described here:
[http://ubuntuforums.org/showthread.php?t=21662](http://ubuntuforums.org/showthread.php?t=21662)
I guess you're wiping out your existing Mac OS partition and use the default partitionning table from partman tool within the installer.
Could you give more details on how you proceed exactly and do you select any specific options?

Cheers,
Erkki

---

### Post by liberated on 2005-04-14
...fixed it! I guess it was the /dev/hda2 partition that had become corrupted somehow, because I formatted it to ext2 and then back to NewWorld boot and then it worked.

---

