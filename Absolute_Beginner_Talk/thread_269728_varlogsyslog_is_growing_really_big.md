---
title: "/var/log/syslog is growing really big"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by runemol on 2006-10-02
My /var/log/syslog file is growing in size, and has currently reached the size of approx. 2.1 GB. This makes my boot process very slow (it uses a lot of time when starting the syslog daemon). Does anybody know what is wrong and how I can cope with this in order to make it work properly again?

Best regards,
Rune

---

### Post by llamakc on 2006-10-02
Is logrotate operating properly?

If you tail /var/log/syslog is anything throwing copious errors to the file, and filling it up very quickly?

---

### Post by taurus on 2006-10-02
Or you can "empty" it with

```
sudo cat /dev/null > /var/log/syslog
```

---

### Post by runemol on 2006-10-02
> **llamakc said:**
> Is logrotate operating properly?

If you tail /var/log/syslog is anything throwing copious errors to the file, and filling it up very quickly?

Thanks for your reply.

Running tail /var/log/syslog reveals the following content:
Sep 27 02:54:24 localhost kernel: [17185580.940000]     fat_get_cluster: invalid cluster chain (i_pos 3652997)
Sep 27 02:54:24 localhost kernel: [17185580.940000] FAT: Filesystem panic (dev sda2)
Sep 27 02:54:24 localhost kernel: [17185580.940000]     fat_get_cluster: invalid cluster chain (i_pos 3652997)
Sep 27 02:54:24 localhost kernel: [17185580.940000] FAT: Filesystem panic (dev sda2)
Sep 27 02:54:24 localhost kernel: [17185580.940000]     fat_get_cluster: invalid cluster chain (i_pos 3652997)
Sep 27 02:54:24 localhost kernel: [17185580.940000] FAT: Filesystem panic (dev sda2)
Sep 27 02:54:24 localhost kernel: [17185580.940000]     fat_get_cluster: invalid cluster chain (i_pos 3652997)
Sep 27 02:54:24 localhost kernel: [17185580.940000] FAT: Filesystem panic (dev sda2)
Sep 27 02:54:24 localhost kernel: [17185580.940000]     fat_get_cluster: invalid cluster chain (i_pos 3652997)


These log records might have occured when I connected my iPod to the computer. How can I safely delete content from /var/log/syslog or reduce the threshold of logging?

---

### Post by taurus on 2006-10-02
Look at my reply above!!!

---

### Post by runemol on 2006-10-03
Thanks, but your command doesn't work (Permission denied). To empty the file is probably not a solution that lasts - I need to find the things causing my syslog file to grow this big...

---

