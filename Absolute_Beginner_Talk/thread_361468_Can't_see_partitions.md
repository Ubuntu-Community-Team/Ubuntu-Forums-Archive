---
title: "Can't see partitions"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Telecaster72 on 2007-02-14
Hello all
I am about one week into linux-land so i would definitely qualify as a newbie...

My problem is my partitions is not visible either in nautilus or on the desktop.
I have a IDE HD with the following partitions i made with Gparted during installation from the live CD:
Hda1=NTFS (XP)
Hda2=Ext3 (/)
Hda3=Swap
Hda4=Ext3 (home)

The only visible disk i have is the NTFS partition. I can access the other partitions through the filesystems  "media" folder.

Ubuntu is working well except this thing , but i get curious since all i have found on the net is the opposite problem, that people cant see their windows partition but they can see their ext3-partitions.

Does anyone have a clue on what i did wrong and how i can fix it?

This is a fresh install might i add so i haven't screwed it up myself yet (now, it is not the first install though, i have messed up may installations through the week through kamikaze-experimenting with sudo commands, never underestimate the power of sudo nautilus!! ;-)

Here is the fdisk and fstab for clues:

Sudo fdisk -l:

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/hda2            1021        2614    12803805   83  Linux
/dev/hda3            7384        7476      747022+  82  Linux swap / Solaris
/dev/hda4            2615        7383    38306992+  83  Linux

Partition table entries are not in disk order

cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                            0  0  
# /dev/hda2
UUID=4efd93cb-9502-4dc9-85be-13a575764e19  /               ext3         defaults,errors=remount-ro          0  1  
# /dev/hda4
UUID=4ec2bbf0-356c-4b82-8e4e-0946b1fa0691  /home           ext3         defaults                            0  2  
# /dev/hda1
UUID=2074FCE874FCC198                      /media/hda1     ntfs         defaults,nls=utf8,umask=007,gid=46  0  1  
# /dev/hda3
UUID=5bc6cf2a-0b15-4892-8a5f-4e0e0c9594ca  none            swap         sw                                  0  0  
/dev/hdb                                   /media/cdrom0   udf,iso9660  user,noauto                         0  0  
/dev/hdc                                   /media/cdrom1   udf,iso9660  user,noauto                         0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto                      0  0  
/dev/hda1                                  /media/hda1     ntfs         defaults                            0  0  
/dev/hda2                                  /media/hda2     ext3         defaults                            0  0  
/dev/hda3                                  /media/hda3     swap         defaults                            0  0  
/dev/hda4                                  /media/hda4     ext3         defaults                            0  0  

I hope someone has the time and will to help me understand this, i really like Ubuntu and want to learn as much as possible to one day get totally off the m$ sinking ship!

If you need more info just tell me.

Telecaster72:guitar:

---

### Post by OldTimeTech on 2007-02-14
Check this out, think it will help you get rid of your problem!

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by OldTimeTech on 2007-02-14
Here's another link that may help also:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by Telecaster72 on 2007-02-15
Thank you for replying Oldtimetech!
I tried both the first and second method but nothing changed with my partitions, still just hda1 on my desktop and in nautilus.
For the second link you gave me i would need the alternate install disc right? I just have the Live CD6.10.

It boots up just fine but both tips were about grub and mbr so i guess you are suspecting something about grub is not telling ubuntu wich drives it has and therefore they do not show up in Ubuntu or what?
They do however show up in fdisk and fstab and doing the second method everything showed up in the terminal nice and neat with no errors...

Please have patience with my low level of knowledge in linux, i am just a one week old trying to separate from XP´s nursing bussom because the milk is sour...

---

### Post by I_have_seen_the_light on 2007-02-15
Hi

I am a bit confused about the question that you have.  let me see if I understand.  when you boot to ubuntu, you see an icon for your NTFS partition but you dont see anything else right?

if that is the case, everything should be fine.  now if you are wondering how would you be able to see icons of your partitions. you could probably use the disk analyzer.  it should be under the system menu.

you might wnat to read this.

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

Hope this helps.

---

### Post by Telecaster72 on 2007-02-15
Thank you Ihaveseenthelight.
I wonder how come i can see an icon for hda1 (ntfs) partition in nautilus and on the desktop, but not hda2 (root) and hda4(home).
I am at work now at a windowsmachine and i dont have a complete image of ubuntu in my head yet ;) but if i go to the "computer" in nautilus i get all devices listed as floppy, cdrom, dvd , filesystem and the Hda1 ntfs partition, i just think it strange that i get that partition listed and not the other ones that exist on the same drive, i can still access the partitions through the media folder though so it is not an acute problem, it´s just a little odd and confusing and makes no sense.
But if you are not supposed to get them listed as devices, then i will stop my whining.

Do the rest of you see your partitions listed in nautilus or just "Filesystem" (and if you have dual boot the windowspartition)?
If you dont i´ll be quiet, if you do i want to do it too! *wants the same nifty toys as the other boys in school*

Great link also for the basics of the linux filesystem! True that i am still in the windows mindset looking for windows way of doing things.

Telecaster72:guitar:

---

### Post by louieb on 2007-02-15
In nautilus you see the Ubuntu install as  one seamless "Filesystem". 
To see the different partitions and where there mounted  Open Applications>Accessories>Terminal and enter
```
df -Th
```and you will see something like this:

```
 
Filesystem    Type      Size  Used Avail Use% Mounted on
/dev/hda3       ext3      9.7G  3.2G  6.0G  35%  /
varrun           tmpfs    189M  144K  189M   1%  /var/run
varlock          tmpfs    189M  4.0K  189M   1%  /var/lock
udev             tmpfs    189M  112K  189M   1%  /dev
devshm         tmpfs    189M       0  189M   0%  /dev/shm
lrm                tmpfs    189M   19M  171M 10%  /lib/modules/2.6.15-28-386/volatile
/dev/hda1        ext3     59M   31M   25M   56%  /boot
/dev/hda4        ext3     18G  391M   17G    3%  /home
/dev/hdb1         ntfs    7.9G  3.7G  4.3G   46%  /media/windows

```
BTW df is primarily used to show free space.

---

### Post by Telecaster72 on 2007-02-15
Ok so it seems everything is in order, just me expecting nautilus to be like the explorer in windows, maybe i should contact a deprogrammer helping me to deprogram from the cult of XP...

Thank you all for your help anyway!!

---

