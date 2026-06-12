---
title: "EXT3-fs error"
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by Xkutzy on 2005-09-19
A few weeks ago I installed Unbuntu Hoary and have been making good, if slow, progress with it. Today I returned to my PC after several hours and found the following error message scrolling across the screen.

"EXT3-fs error (device hda1) in start_transaction: Journal has aborted"

I had to power down the PC to get it to respond. It has re-booted ok (I am using it to make this post) but I have some questions.

1- What should I have done when faced with the error message? Was there any way to regain control other than pulling the power cable out?
2. What the the significance of the error message? I know it indicates some sort of problem with the file system on the hard disk. Should I be concerned or does the message indicated a temporary problem that will have gone once I re-booted?
3. What is my next move? Is there some sort of diagnostic test that I should be running?

Thanks in advance.

Xkutzy

---

### Post by davmac on 2005-09-19
Well, I'd have done exactly what you did. That doesn't mean it's correct though. ;-) 

If you put the error message tex into Google you'll see that other have hits this same problem. One consistent piece of advice is to run fsck to check the disk. 

I think the partition has to be mounted read only to do this. I don't know the "correct" way of doing this but, in your shoes, I'd be booting up with Knoppix for a job like this.

Hope this helps, and if it is wildly inaccurate, somebody corrects me!

Regards,

Dave Mac

---

### Post by Xkutzy on 2005-10-04
Apologies if this makes no sense, but I am still new to GNU/Linux.

Ok, here's the latest situation. After restarting the PC following the episode above it ran quite happily (as far as I could tell) for several days. Then it just froze with a black screen. I powered down, and it re-booted successfully. It ran for a few more days then this morning, the e-mail client was complaining that the file system was read-only. When I went to shut it down, it went into a text screen with the same EXT3-fs error (hda1) ..... message scrolling down the screen.

By now I had got hold of a live CD, so I booted from that and ran fsck on hda1. It seemed to run very quickly but reported no errors. I did notice that it appeared to say that the file system was EXT2. Strange 'cos the error message referred to EXT3 file system.

I re-booted from the hard disk, and the start-up messages also indicated the file system was EXT2. It started up, but the system was running very slowly with very jerky mouse movements. Then I had to leave for work.

Am I right in thinking that if I accepted all the defaults during installation, an EXT3 file system would have been created? If that is the case why would the system now believe the file system to be EXT2?

Another question that occurs to me is did I do anything to make this happen? The potted history of the PC is as follows. Installed Ubuntu 5.4 from a CD on an old spare PC (Celeron 660MHz, 192Mbyte, 10Gbyte). Clean install. No dual boot. No errors noticed. Installed all the updates as soon as they became available (should I have re-booted after updates?) Used EasyUbuntu to get realplayer and other stuff. Seemed to work ok. Added a udev local rule to get my Palm pda working. Got e-mail working. Not much more really. (I just got married so can't spend much time on it!).

Finally, where do I go from here? Is there anything I should try to save the current installation? Though this PC is only an experiment for me to learn Linux, so there is no real data on it, I want to learn how to fix it if possible. If I do need a re-install, should I wait for breezy and do a clean install of that from CD?

Thanks in advance

Xkutzy

---

### Post by mlomker on 2005-10-04
> Am I right in thinking that if I accepted all the defaults during installation, an EXT3 file system would have been created? If that is the case why would the system now believe the file system to be EXT2?


I explain it in [this thread.]("http://www.ubuntuforums.org/showthread.php?t=69076")

---

### Post by Xkutzy on 2005-10-06
Thanks Mlomker. Tried sudo tune2fs -j /dev/hda1, and it reported that the drive was already journaled. So I rebooted, and everything seemed to run up ok. Mount reported the file system as ext3. It seemed to have fixed itself somehow.

This morning, I noticed that the running copy of evolution had disappeared, and when I tried to re-start it, it would not run. No error was reported. I tried to run a terminal from the menu, and it reported that the selection was not executable! I did reboot and again everything is running ok as far as I can tell. 

I obviously have a fault somewhere. The PC will run quite happily for a few days then there will be a problem (file system goes read only/blank screan/running programs stop). The trouble is I don't know where to start looking. Does anyone have any suggestions for diagnostic tests I should run, or perhaps logs I should look at to find the problem?

Thanks in advance.

Xkutzy

---

### Post by mlomker on 2005-10-06
> . Does anyone have any suggestions for diagnostic tests I should run, or perhaps logs I should look at to find the problem?


/var/log/syslog, messages, and kern.log.  There are a few others but they're specialty logs.

---

### Post by Xkutzy on 2005-10-21
Thanks for the help so far. Here is the latest update.

I checked the log files mentioned in the previous post. There were no obvious error messages. The logs just stopped. There was a warning in one during boot up about ACPI. It didn't look likely to be the cause, but I disabled ACPI in the bios. The warning in the log file went away, but my PC is still crashing. If there is something specific I should be looking for in the logs, please let me know. I could perhaps attach copies of the logs if anyone thinks that it would be worth their time having a look.

I downloaded Seagate's diagnostic SEATOOLS, and checked the drive several times. No faults were found in the drive or controller, though SEATOOLS did lock up a couple of times. So maybe a hardware issue?

I ran memtest from the GRUB menu for over 72hours. No faults. No lock ups.

In another thread, I forget which one, it was suggested that I leave a cd in the cd-rom drive all the time. I didn't expect it to work, but it was a simple idea so worth a try. That didn't do the trick.

One thing I have noticed is that the fault is becoming more repeatable. I re-boot the machine, do various things, and all is fine. I leave the machine, usually with evolution running. After 24-48hrs I return evolution is no longer on the lower panel. I open the menus. This icons are mostly missing. I select an option from the menu. Crash. The top an bottom panels disappear, and I am left in an empty desktop. Try ctrl-alt-bksp to restart x, and drop to a screen with the EXT3-fs error message scrolling down it. The only way I know to get out of this is to pull the power cable.

I am starting to think that this is a hardware problem. Does that seem most likely? Does anyone have any suggestions for the best way to proceed from here? Any other diags I should be running? Or am I left with the brut force approach of replacing bits until the problem goes away? Perhaps I should try breezy (my disks should be arriving any day now)?

Any suggestions would be much appriecated.

Xkutzy

---

### Post by mlomker on 2005-10-21
I did another Google search and came [across this]("http://www.linuxquestions.org/questions/showthread.php?s=&postid=1910346#post1910346").  There's a suggested fix that worked for the original poster.

---

### Post by Xkutzy on 2005-10-21
Very interesting posts. I may get a chance to try a fix this weekend, but them am away for a few days so will probably have to wait till after that.

Reading the posts did start me thinking about memory. When I installed Ubuntu, the machine had 192meg ( 128+64 ). I later increased this to 256meg ( 128+128 ) . Does Ubuntu "self tune" if the memory changes, or is there anything I should have done, e.g. change swap partition size?

I remember a few years back doubling the memory in a DEC alpha VMS machine without re-doing autogen to tune the os. It worked fine for several weeks, then crashed spectacularly! It worked fine after re-running autgen though.

Xkutzy

---

### Post by Xkutzy on 2005-11-26
Well I tried the fix suggested in mlomker's last post. Unfortunately it didn't solve the problem. However, the true cause of the errors became apparent a few days later when what had clearly been an intermittent fault on my hd became a permanent fault. Seagate's diagnostics tools now confirms a defective sector fault. It may be fixable with a re-format, but I don't want to rely on it.

I have now replace the hd with a spare, and after my breezy disks arrived, I installed that. So I am back up and running, this time on Ubuntu 5.10. The install has gone fine. My Palm works "out of the box" on Breezy. Easy Ubuntu took the pain out of setting up most other stuff again.

Thanks for all your help.

Xkutzy

---

