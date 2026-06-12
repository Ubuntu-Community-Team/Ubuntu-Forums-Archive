---
title: "help with samba mount"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by ac251404 on 2007-02-04
Okay, I am trying to mount a network drive from another ubuntu pc. The other pc is sharing via samba because windows boxes access it as well (and works great), but I cannot get my ubuntu box to mount it.

I have added the following to fstab:
```

//ac-server/share /media/share smbfs auto,username=,password= 0 0

```
(the samba share has no authentication)

And I am seeing this:
```

mount: wrong fs type, bad option, bad superblock on //ac-server/share,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

And from 'dmesg | tail':
```

alex@alex-desktop:~$ dmesg | tail
[17342358.280000] smbfs: mount_data version 0 is not supported
[17342493.604000] smb_fill_super: missing data argument
[17342548.004000] smb_fill_super: missing data argument
[17342570.516000] smbfs: mount_data version 1919251317 is not supported
[17342599.780000] smbfs: mount_data version 1919251317 is not supported
[17342636.624000] smbfs: mount_data version 1919251317 is not supported
[17343128.616000] hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17343612.452000] smbfs: mount_data version 1029990773 is not supported
[17343631.060000] smbfs: mount_data version 1919251317 is not supported
[17343818.164000] smbfs: mount_data version 1919251317 is not supported


```

Any ideas?
thanks

---

### Post by ifrflyer on 2007-02-04
Have you got smbfs installed on your machine? 

apt-get install smbfs

:)

---

### Post by ifrflyer on 2007-02-04
That was dumb of me - your error says smbfs - sorry about that!

I just know that it doesn't work right out of the box. . . .

---

### Post by R.J.R. on 2007-02-04
I used this command to mount to a Windows Server hidden share, and it worked fine. Not sure if that will help or not, but I figured i'd throw it out there. Good Luck 

sudo smbmount //ixs01/c$ /ixs01 -o username=useracct,password=pwd

---

### Post by james.wilde on 2007-05-07
> **ifrflyer said:**
> That was dumb of me - your error says smbfs - sorry about that!

I just know that it doesn't work right out of the box. . . .

The man's right.  Just discovered that Feisty doesn't install either nfs-common or smbfs support out of the box.

sudo apt-get install nfs-common
sudo apt-get install smbfs

And don't forget that linux seems to prefer username=name without spaces between username and = and = and name (so not username = name).  Solaris, if I remember correctly is the reverse.  That's if you put these details in a credentials file.

//James

---

