---
title: "Crontab failure to backup up to NTFS and FAT32 partitions"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by michaelmoontaco on 2007-10-08
Hi All,

I have a usb hard drive which I use for backups, partioned into ext3, FAT32 and NTFS.

I can use a backup script containing "cp -au /home/user" to all three partions.

Root crontab "cp -au /home/user" works fine on the ext3 partition.
However,  it won't work on either the  FAT32 or NTFS partions.  

User crontab to FAT32 fails too. (Octal permission = 700.)

This seems to be the case in all of my Unbuntu installations: Ubuntu 7.04 and the Ubuntu 7.10 beta.

Interestingly, this is not a problem with either Debian Etch or openSUSE 10.3.  They both will do a crontab backup to FAT32 and NTFS

What am I missing?

Thanks in advance, Mike Moon

---

### Post by myk.dinis on 2007-10-09
Can you describe the setup in a little more detail...

Why are you using the other two fs'?

Are all three partitions mounted and 700 for the user running the script? 

Do you have write permissions set up properly for the user in NTFS because I know that using *buntu it's a couple extra steps to get write set up properly on NTFS...

I'm trying to grasp the reasons for the other filesystems (fs')

How are the other filesystems managed...normally with windows? Were they set up using windows?

You'll just have to give nme a little more info and I should be able to help you...

Cheers,
Myk

---

### Post by michaelmoontaco on 2007-10-12
Fri 12 Oct 2007 06:39:23 AM PDT 

Hi Myk,

Thanks for your reply.

Best Regards, Mike

My USB drive is partitioned into ext3, FAT32 and NTFS
I use the backups to FAT32 and NTFS for use by Windows XP.

The NTFS and FAT32 file systems were setup as follows:
GParted to set up unformatted partitions.
Formatting was then done in Windows .

The ext3 backups for the desired backups from /home works fine.
Not entirely for the NTFS backups.  The backup to ext3 of /home/ubum120 works, 
but the backup for /home/Public does not.  Debian will do both.
Is there a fix for Ubuntu?  This is not a show-stopper.  I can always use a backup
script, instead of crontab.

FAT32 is no longer important to me, since NTFS-3G seems to work well.
the destination permissions and ownership are: 

Ubuntu 7.10 Beta with NTFS-3G

ext3 /home/Public = 777 owner  root group root
ext3 /home/ubum120 = 755 owner ubum120 group ubum120
FAT32 /home/Public = 700  owner ubum120 group root
FAT32 /home/ubum120 = 700  owner ubum120 group root
(attempts to change the permissions in FAT32 failed, since FAT32 doesn't deal with Linux permssions, 
to my understanding.

NTFS  = /home/Public 777 owner root group root
(Despite the fact that permissions and ownership are the same as Debian,
The desired backup of /home/Public to the NTFS partions do not occur.)
NTFS  = /home/ubum120 777 owner root group root
(The backup of /home/ubum120 works well, just as it does in Debian)


The root crontab in Ubuntu 7.10 beta is:

root@ubum120:/home/ubum120# crontab -l
# m h  dom mon dow   command
*/15 * * * * chmod -R 777 /home/Public
*/15 * * * * cp -au /home/Public /media/M120NTFS/home/
*/15 * * * * cp -au /home/ubum120/Documents /media/M120NTFS/home/ubum120/
*/15 * * * * cp -au /home/ubum120/Desktop /media/M120NTFS/home/ubum120/
*/15 * * * * cp -au /home/Public /media/M120-200202ext3/home/
*/15 * * * * cp -au /home/ubum120 /media/M120-200202ext3/home/
*/15 * * * * cp -au /home/Public /media/M120FAT32/home/
*/15 * * * * cp -au /home/ubum120/Documents /media/M120FAT32/home/ubum120/
*/15 * * * * cp -au /home/ubum120/Desktop /media/M120FAT32/home/ubum120/


Debian 4.1 Etch with NTFS-3G
ext3 = 1600777 owner debfan group debfan 
FAT32 = 1600755  owner debfan group debfan
NTFS  = 1600777 owner root group root

Debian crontab will backup both /home/debfan and /home/Public to all three partions: ext3, FAT32, NTFS

The root crontab in Debian is:

# m h  dom mon dow   command
*/15 * * * * chmod -R 777 /home/Public
*/30 * * * * cp -au /home/debfan/.jpilot/* /home/debfan/Documents/JPilot/
*/15 * * * * cp -au /home/Public /media/M120-200202ext3/home/
*/15 * * * * cp -au /home/debfan /media/M120-200202ext3/home/
*/15 * * * * cp -au /home/Public /media/M120FAT32/home/
*/15 * * * * cp -au /home/debfan/Documents /media/M120FAT32/home/debfan/
*/15 * * * * cp -au /home/debfan/Desktop /media/M120FAT32/home/debfan/
*/15 * * * * cp -au /home/Public /media/M120NTFS/home/
*/15 * * * * cp -au /home/debfan/Documents /media/M120NTFS/home/debfan/
*/15 * * * * cp -au /home/debfan/Desktop /media/M120NTFS/home/debfan/

---

### Post by michaelmoontaco on 2007-12-20
Hi All,

Short answer: my crontab USB drive backup failure was a 2.6.22 kernel issue.

My problem was not related to crontab, permissions, or group membership.  Instead it is due to problems with the kernel 2.6.22 handling of USB.

Google: "ehci_hcd module causes I/O errors in USB 2.0 devices"
or "USB device descriptor error"

I have four USB drives.  Those purchased before than 2006 work fine.  Those purchased in 2006 or 2007 are problematic.  Switching to FIrewire ssems to aleviate the problem.

Also, the order in which I turn on the drives is important.  If I start with my older drive and let Ubuntu acquire it, then turn on my 2007 drive.  Everything works, including my crontab backups.

Incidentally, I have an ASUS A7N8XE-e which has a problematic nvidia usb controller chip.

Dapper and Debian Etch have older kernels (2.6.15 and 2.6.18, respectively) which don't seem to be afflicted by this USB bug.

Hopefully, this issue will be resolved in future kernels.

Best Regards, Mike Moon

---

