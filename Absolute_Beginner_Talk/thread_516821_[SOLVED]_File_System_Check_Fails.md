---
title: "[SOLVED] File System Check Fails"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by lakelovers on 2007-08-03
When I boot, I get a "File system Check Failed. Please repair manually." /sys/devies/platform/:82365.0/bus filed to [3146]."  My searches turn up the problem after new installs, but I have not intalled anything except for the periodotic updates of apps through Synaptic. I'm running Ubuntu 6.06, on a Dell computer. I have an additional problem  that I have not solved. When I boot, I am always asked to insert a system disk, then I get a selection of boot from a hard drive or CD drive. This problem popped up a few weeks ago for no apparent reason and after funning Dapper for a number of months without problems. I reinstalled the grub files, but that didn't solve the problem. The file system check failer started yesterday, so I doub my two problems are connected. I've thought about upgrading to Edgy thinking that my solve these problems. Anybody have an idea what's going on?
Jerry

---

### Post by Inxsible on 2007-08-03
Pop in your LiveCD and then run 
```
sudo fsck
```  that should fix it.

---

### Post by lakelovers on 2007-08-03
I put in a 6.06 CD, proceeded with "sudo fsck" and got the message below. Where do I go from here?


fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hda1 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
e2fsck 1.38 (30-Jun-2005)
fsck.ext3: No such file or directory while trying to open /dev/hdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by splintercellguy on 2007-08-03
Make sure to sudo umount -a before starting fsck.

---

### Post by lakelovers on 2007-08-04
Funny things continue to happen with my Ubuntu 6.06. I have a second drive that I use for backup. Yesterday when I looked at it everything was gone. Today, there's one full backup. (I'm using Sbackup). Also, when I look at the drive on System/Administration the free space on the drive is not available, and the option for Enabling is grayed. I have to believe this has something to do with the messed up file system or, more probably, is a result of the messed up file system. As far as I can determine, I have done nothing out of the ordinary to cause this problem. I'm very puzzled why my system is going whacko all of a sudden. I am somewhat hestiant to proceed with "sudo umount -a" and "sudo fsck" for fear I'll get into deeper trouble. But I'll follow your lead and see what happens. In the worst case senario, I'll start over with Edgy, but I'd hate to lose some of my more important files.

---

### Post by davahmet on 2007-08-04
Actually, this sounds very much like a hardware failure, especially since you reported that it has only recently started.  While the usual assumption is the hard drive, because you have a second drive that is behaving inconsistently, I would suspect the drive controller or the bus on your motherboard.  Additionally, it could also be caused by power supply issues, although that will typically show itself with intermittent problems in video and networking.

If it is a filesystem problem, then fsck is the correct tool.

After umounting the filesystems from a liveCD, you should first check the condition of the filesystems with 'sudo fsck -N' which will check the current condition of the filesystems without making any changes.  If corruption is shown, you can force correction noninteractively with the command 'sudo fsck -a'.

---

### Post by lakelovers on 2007-08-04
One question: I have a 6.06 install CD, but not a "live" CD. Will the install CD do the job? One more question: How do I unmount from the CD? I would think that I would unmount from the terminal within installed Ubuntu.

---

### Post by davahmet on 2007-08-05
The install CD from 6.06 is exactly that, an install CD.

You will need a liveCD, such as 7.04.  Since it is a liveCD, there is no installation unless you specify it to do so.  Once it has booted, you should be able to access your hard drive for checking.

---

### Post by lakelovers on 2007-08-06
I knew my familiarity with Ubuntu/Linux was very shallow but I didn't relize how shallow. I downloaded 7.04 and burned it on a CD. I assumed that LIve 7.04 would be on that download. Apparently it is not, and I have been unable to find a specific "Live" 7.04 download.. Anyway, I clicked on the "Start or Install" option, and nothing happened. I got a blank screen, and waited for something to appear; waited for 15-30 seconds. Nothing came up on the screen. I have an old 5.04 live cd, so I installed that and tried to umount -a, and got the message that it was busy. Then I tried sudo fsck -N, and got a file and date, I didn't know the signicance of that. Then tried sudo fsck -a, and go the same file and date. 

Anyway, I would appreciate more specific instruction: How do I get a live 7.04? How do I get the sudo commands to perform as expected from a live CD? Can I use the old 5.04 live CD to accomplish the same thing?

By the way, I tried booting the 7.04, in safe mode. Nothing happened. Sounds like a got a faulty CD, I'd appreciate some help.

---

### Post by Inxsible on 2007-08-06
The live and install CDs have been combined into 1 for Feisty. you should use the Start and Install option. Since you already tried that and it didnt work, here are some things to check :

1) Did you do the md5 checksum after downloading it?

2) What speed did you burn the CD at ? Recommended speed is 4x or less

3) After burning it, check the CD for correctness/integrity. Its one of the options below Start and Install

---

### Post by Dr Small on 2007-08-06
Could try this: [http://ubuntuforums.org/showthread.php?t=394375](http://ubuntuforums.org/showthread.php?t=394375)

---

### Post by lakelovers on 2007-08-06
The situation is getting worse. I'm on my wife's laptop (Win). Amazingly, I got 7.04 live to load once. I selected the option to test the CD, which it did after a fairly long wait and then surprisingly launched 7.04 live. So, with that up I load the terminal and tried to "unmount -a" I got a "busy" response on /temp; /dev; /var; /proc; and /sys. Then I tried sudo fsck -N and got "fsck 1.04-wip (14-Nov-2006)". Then I tried sudo fsck -a, and got the same response as with sudo fsck -N. I don't know what any of that means but it's not solving my problem which has grown to prevent me from launching 7.04 and Dapper 6.06. I did a HD diagnosis that reported the HD is okay.

I'm wondering why the 7.04 live loaded once but failed to load before and after that one launch. I've not been able to launch 7.04 by selecting "start ubuntu or install." Another thing that puzzles me is that I changed the bios to boot from the CD first and disabled the floppy drive, however the computer tries to boot from the floppy. I am beginning to think that I do have a hardware problem but I have no idea where to start repairing it. If the primary HD is okay, then where would I go from there?

**Edit** Please excuse my long winded post. I got 7.04 live loaded, again. Now how do I get fsck to fix my file failier. I followed the instructions on these posts but nothing happens from the live CD's except busy signals as I said above. Or, does the reponses I get from the live CD (i.e., busy) mean that there is no file corruption. Should I umount -a from the terminal in Ubuntu 6.06, and then do the fsck -a from the live CD? I think there must be something that I'm not doing right. I assume that doing fsck -a from a live CD, installs the correct files into on to Ubuntu on the HD. Is that correct?

---

### Post by lakelovers on 2007-08-07
After messing around for several days, [COLOR="Red"]I found a hardware problem exactily as davahmet suspected.[/COLOR] Because my second drive was not backing up or even loading, I decided to take a look inside the box. What I found was that the primary drive ribbon connector was loose. In fact it practically fell out as I was examing it. I'm quite sure that when I installed the second drive, I didn't get the primary drive cable connected propertly as I was hooking up the second drive. It's a wonder my computer worked at all and for as long as it did. The bottom line is that Ubuntu and my computer operation is totally back to normal. Thank you all for sticking with me on my problem.
Jerry

---

### Post by Inxsible on 2007-08-07
Whew !! :)

Dont forget to mark the thread solved :)

---

