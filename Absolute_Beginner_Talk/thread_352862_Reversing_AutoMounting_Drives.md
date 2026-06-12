---
title: "Reversing AutoMounting Drives"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Tiburon41 on 2007-02-03
Hi all.

Currently I have a dual boot system with Win XP Pro and Ubuntu 6.06.  I followed instructions here on the forums to automount my drive partitions on boot, and I correspondingly have the icons for said partitions on my desktop when I boot into Ubuntu.  

Here's my problem.  I'm looking into using VMWare to run my existing XP install as a virtual machine (instructions [on another site]("http://news.u32.net/articles/2006/7/18/running-vmware-on-a-physical-partition")), and I don't think VMWare will work well if the existing partitions are all mounted in Ubuntu.

First of all, is this true?  Will auto-mounted partitions screw up the works if I'm running a virtual machine from one of those partitions?

Secondly, if this is the case, how do I eliminate the auto-mounting of these partitions on boot up?

Thanks in advance for your help!

---

### Post by pseudonym on 2007-02-03
I haven't gotten into vmware yet, so I don't know much about it, but if you want to stop a partition from being mounted at startup you need to edit your /etc/fstab file - ```
sudo gedit /etc/fstab
``` You can just delete the line which refers to the partition in question, but it would be better to comment it out - ie. put a '#' at the start of it so Ubuntu knows not to read that line. This way you can easily 'uncomment' it (remove the '#') if you want to have the partition back in your fstab one day.

---

### Post by Buck2348 on 2007-02-03
If I am understanding properly what you said:  To install vmware server on your Linux system so as to run Windows in it as a virtual machine, the space for the virtual machine will have to be in a partition that is mounted in Linux.  In other words, you can't get vmware to absorb a previously existing and installed system like the Windows installation you have on your machine already.

Edit:  looked at your link above and it appears to be contradicting me.  Good luck

Buck

---

