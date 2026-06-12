---
title: "Single EFI boot Ubuntu on MacBook Air 2013"
date: 2014-05-08
forum: Apple Hardware Users
---

### Post by eugene11 on 2014-05-08
A couple of weeks ago I decided to wipe out OS X from my MacBook Air 2013 (Haswell) and install Ubuntu 14.04 as the only one OS on the machine. I completely wiped out the disk and gave it whole to Ubuntu.
Installation went smoothly and everything was working fine apart from:

[LIST=1]
[*]Turbo Boost &#8212; my MBA is 1.7 GHz capable of boosting up to 3.3 GHz. I actually saw it running at 3.3 GHz on Mavericks (just tasked to calculate md5 of a really big file), but on Ubuntu in /proc/cpuinfo I saw various frequencies like 900, 1200, 1700 MHz and never above that. 
[*]Thunderbolt to Ethernet adapter was not recognized, which meant I could not use wired networking. 
[*]Wireless speed was [behaving strange]("http://ubuntuforums.org/showthread.php?t=2220007&p=13003319") 
[/LIST]
I was not worried much about all the above although I definitely wanted to have it sorted.
The actual bad thing happened later. After another shutdown, Ubuntu did not boot :(:

[ATTACH=CONFIG]252976[/ATTACH]

A bit of googling revealed ([one]("https://bugzilla.kernel.org/show_bug.cgi?id=60635"), [two]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451")) that it is actually a bug:
> It's a bug in the Compatibility Support Module that emulates a BIOS environment.
EFI boot makes it see *all* CPUs and boot.
Therefore, there is little interest left in fixing this bug.
It should work with the emulated BIOS environment but I'm not sure if it make sense to invest resources in trying to fix it.
It's still unclear though how come that I was able to boot it several times but it stopped working after another attempt. It could be some updates that I installed.. but anyway, the main point of this thread is **how to install Ubuntu 14.04 on a Haswell Mac with EFI boot**? 

Some howtos (like [this]("http://www.rodsbooks.com/ubuntu-efi/")) suggest to install rEFInd from Mac OS, but sorry guys I have wiped it out. What I have is just a nice piece of hardware and a Ubuntu 14.04 USB key, and I just want Ubuntu to be installed, work and boot reliably.

So is there a definite way to install Ubuntu on a Mac with EFI boot from scratch?

---

### Post by Vinodh Moodley on 2014-05-08
I have a 2013 MacBook Air and I use EFI boot without rEFInd to run Ubuntu 14.04 LTS. I kept OS X because i used it to bless GRUB. Without that, Ubuntu refused to work. There is a way to run the bless command from a live USB environment but I have not tried that method yet.

---

### Post by eugene11 on 2014-07-04
I got it done by blessing EFI boot file on a small HFS+ partition. The following resources were very helpful:
[https://help.ubuntu.com/community/UEFIBooting#Apple_Mac_EFI_systems_.28both_EFI_architecture.29](https://help.ubuntu.com/community/UEFIBooting#Apple_Mac_EFI_systems_.28both_EFI_architecture.29)
[http://glandium.org/blog/?p=2830](http://glandium.org/blog/?p=2830)

Also I got Turbo Boost work by enabling intel_pstate in grub! Yeees! Here is how: [http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html](http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html)

---

