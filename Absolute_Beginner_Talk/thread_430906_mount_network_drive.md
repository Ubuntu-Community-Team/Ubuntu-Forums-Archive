---
title: "mount network drive?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-05-02
how can i mount a folder/drive on another computer? i tried **sudo mount smb://home-desktop/SharedDocs /media/hda6/** but it said it doesnt allow smb:// adresses.

---

### Post by bodhi.zazen on 2007-05-02
more information would help. Linux to linux, linux to windows, windows to linux ???

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

---

### Post by steve.horsley on 2007-05-02
For temporary access, you can make a connection in nautilus by typing an address like this into the address bar:
**smb://MEGACORP;administrator@10.1.1.1/C$**
where MEGACORP is the domain name. This can done from the command line or can br be put into a desktop launcher with this command:
**nautilus smb://MEGACORP;administrator@10.1.1.1/C$**

For permanant mounts, you can add a line to /etc/fstab. First install package smbfs. Second, read this web site: 
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)
Third, note that when you also need to specify a domain, put it in front of the username, separated by a backslash: username=MEGACORP\administrator but if you are typing this into a command line you need to type two backspaces to allow for shell escaping.

---

