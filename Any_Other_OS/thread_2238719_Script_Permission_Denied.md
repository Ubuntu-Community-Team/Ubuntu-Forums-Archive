---
title: "Script Permission Denied"
date: 2014-08-09
forum: Any Other OS
---

### Post by _masterjonny on 2014-08-09
Hi,

Firstly this question relates to Debian, but I've always found quick answers here, so I thought I'd try my luck and post here anyway.

I have a script on an external hard drive:

If I type "./rsync-snapshot" to run it as root I get: "zsh: permission denied: ./rsync-snapshot.sh"

However if I type "bash rsync-snapshot" it works perfectly....?

I'm at my wits end and run out of stuff to try.

The output of the permissions on the script from ls -l are "-rwxrwxrwx 1 root root"

I've also considered it might be something to do with the permissions on the file system on running from an external hard drive, but from what I can tell its mounting with all necessary flags to allow execution. The output of the fstab for the external drive is "UUID=0af2b364-ce46-4583-b8f9-8fd72c9d86d6 /home/jonny/usb_2tb ext4 user,auto,noatime,defaults 0 0"

Anyone got any insight? Because I can't run it without prefacing the command with 'bash' it means I can't run it from the cron-tab, which obviously for a backup script would be ideal.

Cheers! :KS

---

### Post by howefield on 2014-08-09
Thread moved.

---

