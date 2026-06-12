---
title: "Failed to simulate Raid 1 Failure.."
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by 6kwar on 2007-06-27
Hi.

I setup Ubuntu file server. I have 2 WD 250GB YS (Raid Edition) hard drivers.
In Ubuntu installation I followed this [_guide_]("http://users.piuha.net/martti/comp/ubuntu/raid.html") to setup Raid 1 array. 

Everything works great. Linux booted up and everything seems O.K.

Before installing the server in my workplace I wanted to check what will happen if one of the HD will fail. I turned off the computer and disconnected 1 drive. Turned on and I got an error message that there isn't any boot device. The Bios found the drive and set to boot from it.
I turned off again the computer and tested what will happened if I will disconnect the other HD.
In this scenario Grub boot loader ran and in the UBUNTU logo it froze there.

Why?

In the 2nd  paragraph in the guide he tested if everything is OK. I am getting a different results maybe something there

Guide
 > 
martti@ubuntu:~$ grep /dev/md /etc/fstab
/dev/md0        /               ext3    defaults,errors=remount-ro 0       1
/dev/md2        /home           ext3    defaults        0       2
/dev/md1        none            swap    sw              0       0

Mine
> almog@Hura:~$ sudo grep /dev/md /etc/fstab
# /dev/md0
# /dev/md2
# /dev/md1


Guide
> martti@ubuntu:~$ df -h / /home
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              9.2G  2.1G  6.7G  24% /
/dev/md2               11G  129M  9.5G   2% /home

Mine

> 
martti@ubuntu:~$ df -h / /home
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              9.2G  2.1G  6.7G  24% /
/dev/md2               11G  129M  9.5G   2% /home

Guide
> martti@ubuntu:~$ cat /proc/mdstat
Personalities : [raid1]
md2 : active raid1 sda3[0] sdb3[1]
      10707200 blocks [2/1] [UU]

md1 : active raid1 sda2[0] sdb2[1]
      489856 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      9767424 blocks [2/2] [UU]

Mine
> 
almog@Hura:~$ cat /proc/mdstat
Personalities : [raid1] 
md2 : active raid1 sda3[0] sdb3[1]
      232412288 blocks [2/2] [UU]
      
md1 : active raid1 sda2[0] sdb2[1]
      2931776 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      9767424 blocks [2/2] [UU]


Guide

> martti@ubuntu:~$ sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri May 12 00:57:28 2006
     Raid Level : raid1
     Array Size : 9767424 (9.31 GiB 10.00 GB)
    Device Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri May 12 04:38:19 2006
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 754cd310:4f102bc3:b590c767:672a9c4e
         Events : 0.11700

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

Mine

> 
almog@Hura:~$ sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Jun 20 04:08:08 2007
     Raid Level : raid1
     Array Size : 9767424 (9.31 GiB 10.00 GB)
    Device Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jun 27 11:05:38 2007
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 1744d9d3:2b1787e8:f65b596a:cb866cc1
         Events : 0.7

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1



Everything is perfect except for the first command. "grep /dev/md /etc/fstab"

How can I fix it?

Thanks

Note: He uses Ubuntu 6.06 server edition alternative. I am using Ubuntu 7.04 X386 Alternative.

---

### Post by Yoooder on 2007-06-27
Appologies if this is irrelevant, I haven't been able to read your entire message or the linked tutorial thouroughly:

*If* you are using Ubuntu to manage your RAID array, then your motherboard has no knowledge of it.  It is seeing two distinct harddrives.  One will have the mbr (master boot record, used to run Grub) and the other will not.

Once Ubuntu starts it will right away treat the two drives as RAID-1, and will maintain equivalent images of the OS across both drives.  However, I'm quite sure this won't affect the mbr as (I don't think) soft-RAID is bit-level replication.

For your desires, your machine would require a **true** hardware RAID controller (almost always an expensive add-in card) which will make your computer's BIOS see the RAID array instead of individual drives.

The reason I emphasize *true* is because many motherboards claim to support RAID features, yet they are basically software-raid, or fakeRAID (google "fakeRAID" to read more about these devices and linux).

---

### Post by 6kwar on 2007-06-27
In this guide [http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)
that I gave above. He installed on empty HDs and enabled Boot Flag to both drivers. After he configured everything he simulates a HD failure. He just turns his computer off and disconnects a HD. In his case he can boot to Ubuntu without any problem but when he write this command 

> martti@ubuntu:~$ cat /proc/mdstat
Personalities : [raid1] 
md2 : active raid1 sdb3[2] sda3[0]
      10707200 blocks [2/1] [U_]
      	resync=DELAYED
      
md1 : active raid1 sda2[0] sdb2[1]
      489856 blocks [2/2] [UU]
      
md0 : active raid1 sdb1[2] sda1[0]
      9767424 blocks [2/1] [U_]
      [>....................]  recovery =  2.2% (215168/9767424) finish=16.2min speed=9780K/sec 

He gets this info. As you can see the raid array is broken. But the Ubuntu still running. In my case both HDs fail to load.

Any other suggestions?

---

### Post by Limpan on 2007-06-27
My guess is that the raid array is never initiated because not all devices are available. It would probably continue to run if you disconnected the power to one drive when running and initiated but then you would risk to destroy your hardware for real! (But that would be a really good test! Not very wise thou!)

btw: What's the use of booting the 'broken' system? Wouldn't it be nice to know that something is wrong? I totally agree that it's nice to have redundancy for your data, but for the system?

---

### Post by 6kwar on 2007-06-28
This system is going to be a file server.
What I want to do is to be ready if this situation will ever occur. 

The idea of setting Raid 1 like all the guides that I read is that if there's a disk failure I will turn off the Server and disconnect the faulty hd and turn on the computer with only one HD. Raid will be broken but at least the server will be on in 5-10 min. And when I'll get the new HD I will rebuild the raid array.

Guides that I read show you that if you disconnect one of the HD and power on your machine Linux will boot normally but the /md will be 1\2 and not 2\2

I tried Ubuntu 6.06 and 6.06 server. 7.04 and 7.04 alternative.

If you can see in the guide that I gave above. He just disconnected the HD and turns his computer on and that is it. He doesn't do nothing special.

Every help would be appreciated.
Thanks

---

### Post by Limpan on 2007-06-28
Have you tried simply editing your fstab to be more like the one in the guide?

---

### Post by 6kwar on 2007-06-28
The problem is that Fstab looks the same. If I'm trying to edit fstab I got the same lines as the guide.  But they have # sign. If I remove it it doesn't help at all

When I write
almog@Hura:~$ sudo grep /dev/md /etc/fstab
I get this result

# /dev/md0
# /dev/md2
# /dev/md1  

And the lines in Fstab are:

/dev/md0 / ext3 defaults,errors=remount-ro 0 1
/dev/md2 /home ext3 defaults 0 2
/dev/md1 none swap sw 0 0 

If I remove the # sign I am getting


/dev/md0
/dev/md2
/dev/md1  

Got something else that I can check?
Thanks

---

### Post by 6kwar on 2007-06-29
I got something very interesting. I took an old computer that I got. Found 2 4.3gb HDs and tried it on this computer.

Started the install. Build the raid 1 array. Linux booted up and everything seemed fine! But when I tried to simulate Raid failure on this machine it did the same thing!

Failed again to boot up. gave me kinda the same error messages. one HD booted up and stuck on Ubuntu's logo. and the other just gave me some unknown letters. 
apart they fail to work, when both drivers connected Ubuntu boots up.

Tomorrow I will try it on 6.06 server edition. Maybe there's some bug in 7.04. Dunno.

---

### Post by 6kwar on 2007-06-30
I succeeded! \

With 6.06 everything worked as planed! I succeeded to built. after that to destroy the array and rebuild it again. without any problems and it worked great,

Someone needs to check mdadm in 7.04

---

### Post by Limpan on 2007-07-01
Not that I am the right person to check or test anything but...
I think that it would be interesting to know which versions of the relevant software you were using when you got it to work.

---

