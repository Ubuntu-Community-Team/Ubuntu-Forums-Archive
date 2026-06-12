---
title: "flash drives won't mount"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by knome on 2008-02-18
Hi all,
Having used Wubi for a couple of weeks with 7.04 I've just given Ubuntu  its own partition, and then upgraded 7.04 to 7.10 . and everything seemed fine, but now I've found that I can't access MP3 players or flash drives. Tried as many as I could lay my hands on. Same result.
I get this message;
**"Mounts: wrong fs type, bad option,bad superblock on /dev/sdal. missing codepage or helper programme or other error."** Then suggests I try syslog, dmesg | tail or so."
 Tried that (I think) Came up with;
 **FAT: Unrecognised mount option. "use free" or missing value**. 
Any suggestions gratefully received.
Rob

---

### Post by Tatty on 2008-02-18
Cant promise to help as im not an expert in this field, but have you tried mounting manually?

```
sudo mkdir /mnt/myusbdrive
sudo mount /dev/sdb1 /mnt/myusbdrive
```

If that fails could you post the output of:

```
lsusb
```

---

### Post by knome on 2008-02-18
Tatty, Hi Tried those commands and no luck, but, I'm not used to the terminal stuff, but will try again.
lsusb gave this
rob@ubuntu:~$ lsusb
Bus 004 Device 002: ID 0d49:3200 Maxtor 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04b8:080e Seiko Epson Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1241:1503 Belkin 
Bus 002 Device 001: ID 0000:0000  


All my other USB stuff works fine. External Drive, Printer, Router. Its just the flash, I think.
Thanks again,Rob

---

### Post by knome on 2008-02-18
Tatty, just ran lsusb with a flash drive in, if that's any halp- Rob

rob@ubuntu:~$ lsusb
Bus 004 Device 010: ID 3538:0054 Power Quotient International Co., Ltd 
Bus 004 Device 002: ID 0d49:3200 Maxtor 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04b8:080e Seiko Epson Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1241:1503 Belkin 
Bus 002 Device 001: ID 0000:0000

---

### Post by knome on 2008-02-18
Solved!!!!! 

go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options

Remove the “usefree” option from the list.

Exit gconf-editor, and try hotplugging your drive again.

Your USB key should mount as expected now.


Works a treat.:)

---

