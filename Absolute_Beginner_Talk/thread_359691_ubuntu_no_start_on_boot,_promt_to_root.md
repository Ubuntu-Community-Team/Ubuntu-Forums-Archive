---
title: "ubuntu no start on boot, promt to root"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-02-12
I randomly have startup problem on boot without any reason!!!!!! 
prompts to root without coming to login screen. I get the following error:
```
sys/devices/platform/i8042/serio0/serio2/bus failed
check, force check
serio2 bus failed checking root system
/dev/sda3 contains a file system with errors, check forced.
Inode has illegal blocks
/dev/sda3: unexpected inconsistency: run fsck manually
fsck died with exit status 4
the reoot filesystem  is currently mounted  in read-only mode
maintenance shell will now be started
bash: no job control in this shell
bash: groups: command not found
bash:lesspipe: command not found
bash: dircolors: command not found 
root@test:~#
```

ANY IDEA??????????

---

### Post by findik1 on 2007-02-12
BY THE WAY, my linux is now on /dev/sda5 not on /dev/sda3. Previously it was on /dev/sda3, but I reinstalled ubuntu into /dev/sda5, and I made /dev/sda3 as alinux file system to store my files

---

### Post by FenrisAbraxas on 2007-02-12
> **findik1 said:**
> I randomly have startup problem on boot without any reason!!!!!! 
prompts to root without coming to login screen. I get the following error:
```
sys/devices/platform/i8042/serio0/serio2/bus failed
check, force check
serio2 bus failed checking root system
/dev/sda3 contains a file system with errors, check forced.
Inode has illegal blocks
/dev/sda3: unexpected inconsistency: run fsck manually
fsck died with exit status 4
the reoot filesystem  is currently mounted  in read-only mode
maintenance shell will now be started
bash: no job control in this shell
bash: groups: command not found
bash:lesspipe: command not found
bash: dircolors: command not found 
root@test:~#
```

ANY IDEA??????????

Just an idea, did you make a clean reinstall? is your grub entry pointing to te proper partition? have you tried to stop automounting sda3 at the boot time? 

Obviosuly somthings wrong with your /dev/sda3 partition probably it just need to be reformated.

---

### Post by findik1 on 2007-02-12
thank you for the reply!
I had a different problem after my install but with the help of another person I had resolved that problem and I was using this system for a month. Please see for a quick link:
[http://www.ubuntuforums.org/showthread.php?t=337235](http://www.ubuntuforums.org/showthread.php?t=337235)

How do I do stop automounting sda3 at the boot time. Every 30 automounting, the system was requiring rechecking the file system due to unmount related issues.

My today problem is so weird, brand new day I just turn on the computer and a problem, Last night I only did to switch off the wireless.

Would you help on any idea what to do: In the attached thread, you may see my file system, and partitions
thanks again
findik1

---

