---
title: "Extract VMware tar and no install.pl file"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by zakeen on 2007-11-24
When I extract both, VMware player and workstation I get an error at the end and it doesnt do the install file.

I notice when I browse the files while zipped the install file has 0kb. If that helps.

any ideas?

---

### Post by apjone on 2007-11-24
> **zakeen said:**
> When I extract both, VMware player and workstation I get an error at the end and it doesnt do the install file.

I notice when I browse the files while zipped the install file has 0kb. If that helps.

any ideas?

Re-download the archives or try a different version. FYI here is a ls -lsh of vmware-distrib

ls -l vmware-distrib/ -sh
total 492K
4.0K drwxr-xr-x  2 apjone apjone 4.0K 2007-10-08 16:19 bin
4.0K drwxr-xr-x  4 apjone apjone 4.0K 2007-10-08 16:19 doc
4.0K drwxr-xr-x  2 apjone apjone 4.0K 2007-10-08 16:18 etc
452K -r--r--r--  1 apjone apjone 447K 2007-10-08 16:19 FILES
4.0K drwxr-xr-x  2 apjone apjone 4.0K 2007-10-08 16:19 installer
4.0K drwxr-xr-x 22 apjone apjone 4.0K 2007-10-08 16:19 lib
4.0K drwxr-xr-x  3 apjone apjone 4.0K 2007-10-08 16:19 man
4.0K drwxr-xr-x  2 apjone apjone 4.0K 2007-10-08 16:19 sbin
4.0K drwxr-xr-x  3 apjone apjone 4.0K 2007-10-08 16:18 system_etc
4.0K drwxr-xr-x  3 apjone apjone 4.0K 2007-10-08 16:18 usr
   0 lrwxrwxrwx  1 apjone apjone   23 2007-11-06 14:04 vmware-install.pl -> bin/vmware-uninstall.pl
4.0K drwxr-xr-x  3 apjone apjone 4.0K 2007-10-08 16:18 vmware-vix

---

### Post by zakeen on 2007-11-26
I dont get it. I re-downloaded it. Then I tried an older version and still the same.

---

