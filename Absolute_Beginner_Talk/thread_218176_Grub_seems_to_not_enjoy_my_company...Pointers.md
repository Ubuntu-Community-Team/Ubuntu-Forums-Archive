---
title: "Grub seems to not enjoy my company...Pointers?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by SkyNet2029 on 2006-07-18
What I set out to do : I need Windows for AgeofEmpires (IT eats wine's binaries and laughs, crashing wine meserably, so there is that. I was windows free for the last 4 or 5 months and have looked through the forums, to no avail.

this is what is listed from my /etc/fdtab: it's long ,BTW;;;

oot@NTAuth:~# more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /NTFS           ntfs    defaults,nls=utf8,umask=007,gid=46 0
   1
/dev/hdb3       /boot           ext3    defaults        0       2
/dev/hdb1       /edubuntu       ext3    defaults        0       2
/dev/hdb6       /home           ext3    defaults        0       2
/dev/hdb11      /opt            ext3    defaults        0       2
/dev/hdb2       /sharedOS       vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb12      /srv            ext3    defaults        0       2
/dev/hdb9       /tmp            ext3    defaults        0       2
/dev/hdb7       /usr            ext3    defaults        0       2
/dev/hdb10      /usr/local      ext3    defaults        0       2
/dev/hdb8       /var            ext3    defaults        0       2
/dev/hdc2       /winshare       vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb13      none            swap    sw              0       0
/dev/hdc1       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0      


Aaappologies for the mess. I did this : Install Windows server /installed Edubuntu for my kid to get a head's on Linux. The I installed Dapper on my own Partition. It looks like I may have mounted the /edubuntu (Which USED TO BE my Edubuntu install.  My query is thus:  ----> Me right now ](*,)  as Kubuntu 6.06 boots sweetly. so does the Server3k3. sort of. I sat here and smoked three ciggarettes while waitng for it to boot into windows. To no avail.   As yoou can tell, rhis is my 'test' machine, I totally do not use it for producion , The thing of it is this, when running update-grub, all I get is my new install -The KDE6.06, and a mounted folder to what used to be my son's Edubuntu partition. The rest I could stand to lose, but the litle man is about to be three, helps me navigate websites, (by way of scroll up and /home button
**********NOTE************** Apologies for such a long post, but this is where I spend my nights (insomnia ) in hopes of being able to help a user out. Argh. Frutrated because this all started with wanting to play Agempires (M$ Game) also for my sons. Main question is how do I go about fixing this. Again, I have all of the resources to do it good, but when my son wakes up for kis daily k-turtle sessioin I would very much like for him to be ablt to just boot over to Edubuntu and be set....instaed of upset at me. So, like I said .. I ran 'update-grun' minus the quptes and this is what it spits out :
```
root@NTAuth:~# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.15-23-386
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

```   from where I am at, am I missing the grub entry fot the 12.8 (Breezy) initramfs/or is grub just kind of dumb and can't find it>? Argh.. I will check back in a couple hours for any ideas, sort of a not so fabulous reinstall. Cheers to anyone who helps, if only to point out that when my son'machine is on the line, that's all I can think about. Picture this : A saddened 3 year old boy. Pretty sad, eh. Pleeease somebody shoot me link. If aftr peeping out my mounting setup, its hosed, tell me and I guesss I will just go from there.  
Thanks 
-Jim

---

### Post by wahman143 on 2006-07-18
Hi - I've got a 3yr old as well, so I am very sympathetic to your situation :wink:

Please clarify what you are trying to accomplish and I will do my best to assist - from what I gather, you are unable to boot into your windoze install(?).  

Can you post your grub.conf as well?  That would help greatly!

Cheers,
Wah

---

### Post by SkyNet2029 on 2006-07-22
Sort of. Sorry about the wacky spelling on my previous post, took some cough syrup (wrong one, it seems.. ) . What the problem was that I had set the *bootable* flag to only boot Edubuntu. By the time I realized what I had done, it was too late. 
So now I have a proper install (Redid all three) again. Sheesh, the things I get myself into. 
Thanks though.

---

