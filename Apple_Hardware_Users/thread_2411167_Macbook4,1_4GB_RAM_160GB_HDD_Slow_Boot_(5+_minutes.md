---
title: "Macbook4,1 4GB RAM 160GB HDD: Slow Boot (5+ minutes)"
date: 2019-01-25
forum: Apple Hardware Users
---

### Post by barddzen on 2019-01-25
I've gotten lubuntu to boot onto an old Macbook and the install seems to work and it functions pretty well (considerably faster than mint mate) but it takes over 4 minutes to boot to the login prompt and another 2 minutes for the desktop to show up.

Anyone have any ideas on what I might be able to do to speed up the initial boot process?

Mint MATE was well over 10 minutes total, but once at the desktop it also ran pretty well.

However, the long boot times are a killer,

Ideas, thoughts appreciated.

---

### Post by wildmanne39 on 2019-01-25
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by gsahli on 2019-01-26
I'm thinking it's your hard drive - too old or failing. You can test this (kind of) by installing onto a USB drive or even better a firewire drive and booting from that.

---

### Post by oldfred on 2019-01-27
I have this in my notes, but now may be old?
       Slow Boot 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1763611](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1763611)
/etc/initramfs-tools/conf.d/resume
So I think Lubuntu has a left-over file from when it used a swap partition, and a quick fix is to simply remove it and run
sudo update-initramfs -u 

I have a standard PC, running Ubuntu, but gnome-panel.
      
 fred@Bionic-Z170N:~$ systemd-analyze
Startup finished in 9min 10.611s (firmware) + 2.221s (loader) + 2.853s (kernel) + 23.190s (userspace) = 9min 38.877s
graphical.target reached after 23.185s in userspace
fred@Bionic-Z170N:~$  systemd-analyze
Startup finished in 2.932s (kernel) + 23.132s (userspace) = 26.064s 
    

I did not do much and desktop normally appeared quickly. But it was running something in background for quite a while.
Now much better.  I did remove snaps, as I prefer standard applications.
       boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341) 
            [https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb)

---

### Post by mjanik on 2019-01-27
I would look into oldfred's post, then maybe try writing some large files to the disk and see how long it takes compared to other systems. Maybe put a video file onto a USB and copy it to lubuntu, note the time, then copy it to some other OS and note the time. But this varies if the other system has a different hard drive/cpu, etc.... so it might not be the best benchmark.

Something that can give you an idea of whether the hard drive may be failing/slowing down. If your average use (copying/duplicating files on a disk) isn't encumbered, then a failing hard drive might not be the issue.

---

