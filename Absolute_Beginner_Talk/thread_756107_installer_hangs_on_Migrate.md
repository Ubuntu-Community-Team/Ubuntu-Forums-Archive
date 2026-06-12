---
title: "installer hangs on Migrate"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by macbheath on 2008-04-15
complete noob here

I have booted LiveCD 7.10 in graphics safe mode and am currently connected to net as I type. I have tried to install onto a partition ( largest free space) and am now at the Migrate documents and settings. The 'create a new user is greyed out' and I am unable to navigate to the next page or enter text.

Windows Vista is installed
Intel Core 2 Duo mobile Coprocessor T8300
2048 MB PC5300 DDR2 DiMM
120 GB SATA drive
512 MB NVIDIA GeForce 8800 GTX

My plan is to install in graphic safe mode and then install a drive for graphics (hope)

any help appreciated
mac

---

### Post by macbheath on 2008-04-15
more info from log ..

Apr 15 17:41:50 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Apr 15 17:41:50 ubuntu 50mounted-tests: debug: mounted as ntfs-3g filesystem
Apr 15 17:41:50 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 15 17:41:50 ubuntu 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Apr 15 17:41:50 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 15 17:41:50 ubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Apr 15 17:41:50 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 15 17:41:50 ubuntu 20microsoft: debug: /dev/sda1 is a NTFS partition
Apr 15 17:41:50 ubuntu 20microsoft: result: /dev/sda1:Windows Vista/Longhorn (loader):Windows:chain
Apr 15 17:41:50 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Apr 15 17:41:50 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 15 17:41:50 ubuntu migration-assistant: info: setting ostype from: '/dev/sda1:Windows Vista/Longhorn (loader):Windows:chain'
Apr 15 17:41:50 ubuntu migration-assistant: info: got ostype of: 'windowsxp', mountpoint is: '/mnt/migrationassistant'
Apr 15 17:41:50 ubuntu ubiquity[9065]: migration-assistant: filtering out Windows Vista/Longhorn (loader) (/dev/sda1) as it has no users
Apr 15 17:41:50 ubuntu ubiquity[9065]: switched to page stepMigrationAssistant
Apr 15 17:58:40 ubuntu -- MARK --

---

