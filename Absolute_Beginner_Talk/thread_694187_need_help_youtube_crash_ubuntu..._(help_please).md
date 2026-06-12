---
title: "need help youtube crash ubuntu... (help please)"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by z_sti on 2008-02-11
Hi I'm really new to linux, I usually do a lot of research in odder to find the answer... But for this problem I can't seem to find one that works...

Here is my problem...

When I tried to watch youtube or other flash player videos no sound was coming out... 
So I tested with xmms and it was working... so I googled around and I found the solution to my problem... here is what I did to fix it....

sudo aptitude install alsa-oss
sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP=&#8221;aoss&#8221;

Here is my source.
[http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/]("http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/")

So after I did that, it worked... but within a min of the youtube video, Ubuntu just restarted it self. Like if I pressed ctrl +alt + backspace.

So I have been looking for an answer but I can't find it... 
I'm sorry for the thread, and if this is noobish. Like I said I tried looking for the solution but after an hour of google I decided to come here...


Please, if you have a solution be as specific as posible... I'm really new to this... thank you!


PS: here is my pc spec.
ubuntu 7.10
AMD 64 3200 2.2GHz
Nvidia 6800 GS overclocked...
1.5 gb ram
and about 70gb of hdd left...
600wattz power supply

no sound card... and mobo I'm not really sure what it is...

[B][COLOR="Red"]
This problem has been fixed, please read my third post below.
Like the tittle says, its my hdd not showing up.... Read my third post for more info! 

Thanks
[/COLOR][/B]

thanks once again!

---

### Post by Zero Prime on 2008-02-11
Do you get any sound through any other sources, such as music players?  If so I would recommend uninstalling FF and then reinstalling it.  After that go to Youtube and click on a vid.  When prompted install the flash plugin.  All should work fine now.

If that fails, try installing FF 3.0.  It may be beta, but it works fine.

---

### Post by z_sti on 2008-02-11
> **Zero Prime said:**
> Do you get any sound through any other sources, such as music players?  If so I would recommend uninstalling FF and then reinstalling it.  After that go to Youtube and click on a vid.  When prompted install the flash plugin.  All should work fine now.

If that fails, try installing FF 3.0.  It may be beta, but it works fine.

Thanks for the reply, and yes, I have the sound working on all the media players. With video or music. But all the flash players online seemed to be missing the sound and when I did that code thing to fix it. IT solved that problem... but now it crashes ubuntu every time I try to watch something. not just firefox but the whole ubuntu....

---

### Post by ubuntu-freak on 2008-02-11
I had that problem in Debian. Something is upsetting  the xserver. Have you tried using the Epiphany browser? Also, install the packages in part 1 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) just incase. It will skip anything you already have. 
 
How long ago did you install Ubuntu?
 
Nathan

---

### Post by z_sti on 2008-02-15
Sorry for the delay...

I have been using Ubuntu 7.10, for like a month now. This is my first time with linux. So I'm learning as I go.... 


Either way, some how or another this problem got fixed by it self... 
It's pretty weird. But I'm happy... :lolflag:


BUUUTTTTTTTTT....


For some reason some times my hdd will not show up... they usually show up on the desktop, Both of them... and lately they haven't showed up...

I did a disk check I think... here is the results...

z@z-desktop:~$ sudo fdisk -l

Disk /dev/hdc: 82.3 GB, 82348277760 bytes
240 heads, 63 sectors/track, 10637 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x4e15693a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *         421       10637    77240520    7  HPFS/NTFS
/dev/hdc2               1         420     3175168+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdd: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2e1d2e1

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       12375    99394155    7  HPFS/NTFS
/dev/hdd2           12450       13092     5164897+  83  Linux
/dev/hdd3           12376       12449      594405   82  Linux swap / Solaris
/dev/hdd4           13093       20023    55673257+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 8 MB, 8110080 bytes
2 heads, 16 sectors/track, 495 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         494        7891+   1  FAT12
z@z-desktop:~$ 



Is there anything wrong in there? What am I doing wrong that the HDD is not showing up on the pc, not only not showing up, but I can't access the files on it... the only files I can access are the one saved on the partition of linux, and before I wasn't having this problem...

---

### Post by ubuntu-freak on 2008-02-15
Are they drives you plug in or mounted partitions? Were they mounted during installation? If so, did you do anything that may have effected them? 
 
Nathan

---

### Post by z_sti on 2008-02-15
They are both internal hard drives. The 80GB one has windows xp with some programs. Which the hdd is pretty much full. And the one with 160 GB HDD, has a partition for linux. There is like 70GB just for linux stuff... and the rest I use to store my music and videos... and pictures and what whatever else... And no I haven't done anything to it... NOT that I know of... 


Is there a way to fix this?

I have tried to re-boot the computer couple of times and did not solve the problem.

---

### Post by ubuntu-freak on 2008-02-15
Have you still got your live cd? I used it to edit my partitions. You could mount your storage partition as "/media/STORAGE" and then apply. Then you just exit without install Ubuntu. Or you could install GParted. 
 
Nathan

---

### Post by z_sti on 2008-02-15
> **reassuringlyoffensive said:**
> Have you still got your live cd? I used it to edit my partitions. You could mount your storage partition as "/media/STORAGE" and then apply. Then you just exit without install Ubuntu. Or you could install GParted. 
 
Nathan


Is there any more specific explanations? Lol, sorry I just don't want to lose anything thats on the hdd.

---

### Post by ubuntu-freak on 2008-02-15
You won't lose anything unless you tick it to be formatted. Can you remember if you manually mounted them to /media/whatever when you installed? Just mounting the storage one should be okay.
 
Nathan

---

### Post by z_sti on 2008-02-15
okay... 

I am pretty sure these were the mounts...

one for swap with like a 1gb,
one for /root
and one for / 

that's it... 

man... I think I ****** up huh?

---

### Post by ubuntu-freak on 2008-02-15
> **z_sti said:**
> okay... 

I am pretty sure these were the mounts...

one for swap with like a 1gb,
one for /root
and one for / 

that's it... 

man... I think I ****** up huh?

 
Not really messed things up. Use the install disc, will help you remember for next time. Or use GParted. It's pretty easy, just mount the main storage one to /media/whateveryoucallit. 
 
Nathan

---

