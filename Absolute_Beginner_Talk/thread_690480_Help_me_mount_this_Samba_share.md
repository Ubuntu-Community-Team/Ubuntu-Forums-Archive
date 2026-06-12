---
title: "Help me mount this Samba share"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Kethinov on 2008-02-07
This technique from the terminal works fine: "smbclient //server/share --user=my_username --workgroup=corp"

What is the equivalent procedure using Menu -> Places -> Connect To Server, or in /etc/fstab?

---

### Post by Kethinov on 2008-02-07
I've been trying a few other things. For some reason, "smbmount //server/share /media/local/ -o user=my_username,workgroup=corp" does not work, while the smbclient command does. What's the difference?

---

### Post by Kethinov on 2008-02-07
Oops, that should be "smbmount //server/share /media/local/ --username=my_username --workgroup=corp" - That returns: "7050: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)"

Now I've tried "mount -t cifs //server/share /media/local/ -o username=my_username,workgroup=corp" and it says: "mount error 66 = Object is remote"

---

### Post by Kethinov on 2008-02-07
Further research yields this to be my problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183000](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183000)

Anyone know a workaround, besides only using smbclient?

---

