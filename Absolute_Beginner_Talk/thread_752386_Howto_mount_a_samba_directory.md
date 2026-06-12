---
title: "Howto mount a samba directory"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Ganymedes on 2008-04-11
I am trying to mount a Windows share (w2k) with the standard samba config with Ubuntu 7.10.

According to some hints in the WEB, I am trying with this in the fstab.

//192.168.0.123/music$ /home/music smbfs defaults 0 0

However, it says this:

mount: wrong fs type, bad option, bad superblock on //192.168.0.123/music$,
       missing codepage or helper program, or other error

Do you need to manually load something more? I have it working from the Network menu but I cannot run a script for copying if I do not have it mounted, I think.

---

### Post by Koybe on 2008-04-11
Because you're missing smbfs package.
```
sudo apt-get install smbfs
```

---

### Post by Ganymedes on 2008-04-11
Thank you very much, works now!

I got the username, password thing figured out when written in the fstab, but is there an easy way to have them in some other file?

---

### Post by Koybe on 2008-04-11
Yes it's quite simple.

Create some file, for example /etc/samba/smbcred

Put your informations in it :
```
username=youruser
password=yourpassword

```
Then use credential option in fstab :
```
credentials=/etc/samba/smbcred
```

And ```
 man mount.smbfs
``` to get a lot more informations ;-)

---

### Post by Ganymedes on 2008-04-11
Thanks again!

Now that I have the basic things working, I am sure I can get the rest from the overwhelming WEB-material.

You helped me a lot!

---

### Post by Koybe on 2008-04-11
My pleasure ;)

---

### Post by gsiliceo on 2008-04-13
You can vote to change this in ubuntu using the brainstorm page, theres already an idea voting to make samba easier. Please vote here.
[Improve file/folder sharing experience (Samba)]("http://brainstorm.ubuntu.com/idea/403/")

---

