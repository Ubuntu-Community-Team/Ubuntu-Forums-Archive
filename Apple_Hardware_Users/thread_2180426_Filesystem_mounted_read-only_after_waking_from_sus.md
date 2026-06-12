---
title: "Filesystem mounted read-only after waking from suspend"
date: 2013-10-12
forum: Apple Hardware Users
---

### Post by Stuart_Isaac on 2013-10-12
I recently installed Mythbuntu 12.04.3 LTS on my 2011 Mac mini, on an external Firewire 800 drive (Mac OS X still on the internal drive). Other than for my desire to have the system sleep to save energy, things have been going pretty well. When it comes to suspending, however, there's trouble. The system seems to suspend just fine, but I when I wake it up, the filesystem is being mounted in read-only mode, so I can do nothing except forcefully power it down. I've checked /var/log/syslog and haven't seen anything suspicious (such as what was posted on this [thread]("http://askubuntu.com/questions/186143/how-do-i-prevent-my-filesystems-from-being-mounted-read-only-after-suspending"); I did try forcing it to remount in read-write mode as in that thread, and that did not work at all). I've also dug around in the scripts in /usr/lib/pm-utils and in /etc/pm, but again have not found anything suspicious. Does anyone have any insight into this, or any suggestions as to how to figure this one out?

In case it matters, I'm using btrfs on my root filesystem (on the Firewire drive) and ext4 on the /boot partition on the internal drive. Here's the relevant /etc/fstab entry for /:
UUID=a1b4e3df-f49e-40db-8378-2f3e0b3c9e0d /               btrfs    defaults 0       1

---

