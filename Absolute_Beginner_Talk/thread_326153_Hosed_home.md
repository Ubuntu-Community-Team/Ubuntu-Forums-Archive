---
title: "Hosed /home"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by boydjj on 2006-12-27
Hi all,

After a great deal of fussing about with a wireless card that's apparently the only one of its kind on Earth, I got a Kubuntu dual-boot system up and running with Internet access. Following various sites' advice, I'd created a separate FAT32 partition for holding all my shared data between Windows and Kubuntu. But I had forgotten during the install process to set that partition as /home.

Stupidly, I edited fstab with Kate to mount /dev/hda5 to /home and then rebooted. So now KDE is telling me to "check your install," and it reverts immediately back to the login screen.

Anyhow, my question is how this is resolvable. I imagine I have to get back into fstab, but I don't know whether simply changing /dev/hda5 to mount at /media/hda5 will fix the problem (meaning retrieve the old /home data). Also, the "Console Login..." option seems not to be working terribly well. Using "Failsafe," I can get into a limited KDE session with Konsole, but I'm scared to go any further for fear of messing anything more up. Note: I have no clue how the editing controls in vi work, so any advice including vi will need to be detailed. (Sorry.) =\

When all this is fixed, what is the best way for me to change /home to a folder on the FAT32 partition?

Thanks a bunch. Love (K)Ubuntu, and these forums were a hugely helpful guide in my install.

Jeremy

---

### Post by troymcdavis on 2006-12-27
I'm not entirely sure how KDE failsafe works. Can you run the "kate" command from konsole and simply undo the damage? Another thought: rather than using vi(m) you can use nano (# nano /file/path/filename.extension) to edit your fstab; it's fairly self-explanatory, for instance ctrl-X is exit, and then it just asks you if you want to save y/n.

As for undoing the damage, just change your fstab back to whatever it was and you should be fine. Best of luck.

---

### Post by jvc26 on 2006-12-27
Well first of all I'd remove the line you added to fstab:
```

use the kate command again to open it up, and remove the line.

```
So basically you're wanting to mount hda5 to /home?
If so you can go:
```

sudo umount /dev/hda5
sudo mount /dev/hda5 /home

```
The only thing I'm wondering is whether because you didnt select this at the start its having issues allowing you to do that. Are you sure /dev/hda5 is the correct device for your FAT32 partition?

Oh - actually another thing I've just throught of, you may have to tell it what filesystem you're using here are some good links for fstab the first I can definitely recommend : and it has links to the other two within it.
How to fstab - [http://www.ubuntuforums.org/showthread.php?t=283131&highlight=ownership+remains+bodhi%3Ausers](http://www.ubuntuforums.org/showthread.php?t=283131&highlight=ownership+remains+bodhi%3Ausers)
Filesystem guide -
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)
The linuxwiki entry for fstab:
[http://wiki.linuxquestions.org/wiki/Fstab](http://wiki.linuxquestions.org/wiki/Fstab)

Hope that helps,
Il
:)

---

### Post by az on 2006-12-27
> **boydjj said:**
> But I had forgotten during the install process to set that partition as /home.

By default, you are not asked.  Unless you pick manual partitioning, everything is on one partition to avoid messes like this.

I think it's useless to create a seperate home partition.  It's far easier to back things up the conventional way.  It avoids a lot of breakages, too.  Often, if you reinstall, you need to remove your configuration files too.

> **boydjj said:**
> 
Stupidly, I edited fstab with Kate to mount /dev/hda5 to /home and then rebooted. So now KDE is telling me to "check your install," and it reverts immediately back to the login screen.

Boot into recovery mode.  If you don't see the grub menu when you boot, press escape to reveal the menu.  Pick Recovery mode and you will be dropped to a shell where you are root.

nano /etc/fstab

(CTRL-O to save, CTRL-X t exit.)

run

init 2

to get back into desktop mode.

> **boydjj said:**
> 

When all this is fixed, what is the best way for me to change /home to a folder on the FAT32 partition?


Fat32 does not support filesystem attributes like permissions that are necessary for linux.  That is probably why KDE is complaining.  You can't use fat32 as a filesystem for your /home.

---

### Post by boydjj on 2006-12-27
Thanks to all who replied. I started a recovery session and simply changed the bit in /etc/fstab I'd changed from /home back to /media/hda5, and it's back in working order now. (The wireless is messed up, but I'll fix that later - going out of town right now.)

Given some of the responses (and the excellent link to the fstab primer, thanks!), I need to ask for some clarification:

I followed (roughly) the directions at [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html") with regard to setting up a FAT32 partition to share between Windows and Ubuntu. Various other sites recommended this as well in order to prevent data loss if I choose to switch distros. They may have implicitly meant using ext3, but I don't recall. Now that I re-read that particular site, it appears that I misunderstood. Assuming I still want to do this, is it best for me to use qtparted or a Windows partition manager to insert a new ext3 partition for /home?

Let me be clear about what I'm trying to do. Until I switch to a full-Ubuntu system, I can't afford not to be able to read and write to files from both Linux and Windows. Furthermore, I'd REALLY like to be able to use the same profiles and databases for Firefox and Thunderbird. Is this possible, or is it a pipe dream? I haven't yet installed Mozilla apps on the Ubuntu side, but I've converted everything over to the FAT32 partition, and both FF and TB are reading my profile data from there. Can I use the profiles on the FAT partition with these programs, or will the afore-mentioned permission problems end up making it impossible?

---

