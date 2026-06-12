---
title: "Asus Eee Box with Lucid Server- file system switching to read only mode"
date: 2011-08-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by michaelb28 on 2011-08-30
Hello everyone! I hope someone can help me figure out how to troubleshoot a file system problem.

I have an ASUS Eee Box EB1007.  I installed Ubuntu Lucid 10.04 server edition.  The PC is at a remote location and I access it by SSH. I'll visit the site in a couple of weeks.

The problem is that the file system has switched to read-only mode.  Manually powering the system off and back returned the file system to read-write mode the last time it happened. However, I'd like to figure out what is causing the problem so it doesn't happen again.

One guess is that perhaps the BIOS has a sleep mode enabled and it's having trouble remounting the drive after resuming.  I won't be able to check that out though until I go to the site.

Currently, I can't get it to reboot over SSH. "sudo reboot" gives the response: 
sudo: unable to execute /sbin/reboot: Input/output error

I can ask a person on site to power it off and back on though.

Are there certain things I should look for in the logs?  Or a certain procedure to troubleshoot this?

Thanks!

------------

UPDATE:
I had the machine rebooted manually (with the power button).

In the /var/log/fsck directory there were two files, checkfs & checkroot.  Nothing logged in the files.

I found you could run fsck on reboot with this command:
shutdown -rF now

So I did that.  But I couldn't find any references in the logs to what fsck did.

the /lost+found directory is empty.  So I guess I'm probably okay.

If there's something else I should check out, please let me know.  I'll check on the BIOS sleepmode settings when I can go there in person.

---

### Post by jain.ambuj on 2011-09-19
Hi Michael,

We are also facing same problem with ASUS EeeBox EB1007. Did you find anything to resolve this problem? 

Thanks in advance.

-Ambuj

---

### Post by michaelb28 on 2011-09-19
I haven't had any more problems for about 2 weeks since running fsck at bootup. I want to check the BIOS settings to see if there is a sleep mode setting I can disable, but I haven't had a chance to visit the site yet. Maybe it was just a one-time problem.

Is your box with you? The only way I could get mine to reboot was to power-off manually. After rebooting that way, I could then issue the following command to run fsck at bootup.

```
sudo shutdown -rF now
```

I thought it didn't leave me any logs, but I was wrong. I just found this in /var/log/boot.log.

```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 228/124496 files, 110673/248832 blocks
/dev/mapper/mb--eeebox-root: clean, 96662/15065088 files, 1356631/60242944 blocks
```

---

### Post by michaelb28 on 2011-09-26
Hmm... the same problem reoccurred today.  Maybe there's a hardware issue.

---

### Post by jain.ambuj on 2011-09-28
Hardware: ASUS EB1007
OS: Ubuntu 10.04.2 64bit Server Edition
Kernel:  2.6.32-32-server

We are also getting system remounting the disk as Read Only HDD 
 
Attached the Sys log error message when we get into the failure with the HDD and also the output for dmidecode and lspci commands.

-Ambuj

---

### Post by jain.ambuj on 2011-09-28
Micheal,

Could you check if your system also reports the same message into log files. You need to check log files before you reboot the machine. After reboot these messages are getting disappeared from files.

Googled for the solution & got some links here

[http://ubuntuforums.org/showthread.php?t=1475124](http://ubuntuforums.org/showthread.php?t=1475124)
[https://bugs.launchpad.net/debian/+source/linux/+bug/256637](https://bugs.launchpad.net/debian/+source/linux/+bug/256637) 
[https://bugzilla.redhat.com/show_bug.cgi?id=249469](https://bugzilla.redhat.com/show_bug.cgi?id=249469)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937)


-Ambuj

---

### Post by michaelb28 on 2011-09-30
Ambuj,

Thanks for the info. If the problem reoccurs, I check those logs and see if there are similarities. But I've already updated my kernel to 2.6.34 based on the advice in this thread:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

I hope the kernel update fixes it.

-Michael

---

### Post by jain.ambuj on 2011-10-11
Micheal,

So you have installed the generic kernel over there. Let me know if the problem is occurred again.

-Ambuj

---

### Post by michaelb28 on 2012-01-01
No more problems after 3 months of running the newer kernel.  I'm going to mark this as solved.

---

