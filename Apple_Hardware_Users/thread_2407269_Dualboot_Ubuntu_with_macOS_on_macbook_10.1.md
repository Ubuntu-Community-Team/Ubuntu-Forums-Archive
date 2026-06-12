---
title: "Dualboot Ubuntu with macOS on macbook 10.1"
date: 2018-12-01
forum: Apple Hardware Users
---

### Post by cheese66 on 2018-12-01
Hello ubuntuforums,

I would like to make my macbook a dualboot with ubuntu mate. Can I get any help for this?
I have my partition layout different than normal.(I converted my file system to the latest APFS when I reinstalled macos)

```

[COLOR=#000000][FONT=Menlo]$ diskutil list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/disk0 (internal, physical):[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   #:                       TYPE NAME                    SIZE       IDENTIFIER[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   0:      GUID_partition_scheme                        *500.3 GB   disk0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   1:                        EFI EFI                     209.7 MB   disk0s1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   2:                 Apple_APFS Container disk1         500.1 GB   disk0s2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/disk1 (synthesized):[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   #:                       TYPE NAME                    SIZE       IDENTIFIER[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   0:      APFS Container Scheme -                      +500.1 GB   disk1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]                                 Physical Store disk0s2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   1:                APFS Volume disk0s2                 172.7 GB   disk1s1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   2:                APFS Volume Preboot                 44.5 MB    disk1s2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   3:                APFS Volume Recovery                509.8 MB   disk1s3[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   4:                APFS Volume VM                      2.1 GB     disk1s4[/FONT][/COLOR]

```

What stept to I need to make to get a dualboot? I have no more than 500GB ssd.

Thnx!

---

### Post by oldfred on 2018-12-01
Moved to Apple sub-forum.

Do not know Mac, but  with Linux you will need to use Linux formats for / like ext4.
It does not seem Apple has well documented the APFS system.

[https://askubuntu.com/questions/1090652/ubuntu-18-10-grub2-wont-recognize-apfs-filesystem](https://askubuntu.com/questions/1090652/ubuntu-18-10-grub2-wont-recognize-apfs-filesystem)
[https://superuser.com/questions/1267291/how-to-mount-apfs-on-linux-or-windows](https://superuser.com/questions/1267291/how-to-mount-apfs-on-linux-or-windows)

---

