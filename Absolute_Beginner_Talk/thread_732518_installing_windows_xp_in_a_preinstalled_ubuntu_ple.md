---
title: "installing windows xp in a preinstalled ubuntu please help"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by poisonedapple on 2008-03-23
Hi all,

       I recently bought a laptop from dell with ubuntu preinstalled in it. I already had a XP cd so I thought when I get it I will install XP. 

First thing I did:
                    - I used GPart Cd to partition the drive so that I have space for windows xp
                    -I made 100gb available for windows and 60gb for ubuntu
                   
Second thing I did:
                    - I put the XP cd to boot and the problem occurs
                   
I get this message:: Cannot find the hard disk on the drive

xp does not run at all

Third thing::
                   -I installed ubuntu again hoping something out of it.
Now I tried booting XP cd again no it shows the same problem

Is ubuntu so bad that I could not installl any other OS besides ubuntu I have to say I regret getting a preinstalled ubuntu. I would be more than glad if anyone can help me in this issue. I have spent two days on figuring out how to do this and I am very tired with ubuntu. May be it is microsoft but there should be something.




thanks

---

### Post by kbless7 on 2008-03-23
Is the windows partitioned spaced formatted to ntfs or fat32?

---

### Post by FrozenFox on 2008-03-23
Windows needs to be installed to the first partition of the drive and let its bootloader install itself, because it refuses to run on any other partition or setup unless you jump through flaming hoops to trick it into thinking it is. If you want to install windows, you will need to have it in the first partition, which means moving over ubuntu and possibly (I think Gutsy handles it ok though) changing the /etc/fstab file on gutsy to rectify the difference. Ubuntu has pretty much nothing to do with your inability to install windows, only your lack of experience and Windows' lame obsession with being first and problems reading the hd when it has something on it.. **Oh, and sometimes the windows cd won't run unless the entire HD is totally blank**, formatted, who tf knows why! So if all else fails or you dont want to mess with the possibility of failure in the previous steps, then format the drive completely, install windows, defragment windows (perhaps several times),  resize windows' NTFS partition, then install ubuntu. That will work without issue.

---

### Post by brownknight on 2008-03-23
It is usually easier to install windows then  install ubuntu.

---

### Post by poisonedapple on 2008-03-23
ok what I did to format it from Gpart was

the partition:(the list is in order of the memory scale the first one is the frist chunk of memory)
                 ntfs-85gb
                 fat32-15gb (in case I need some data that can be accessed by both ubuntu and windows)
                 ext3-25gb
                 extended-5.88gb
                 linux-swap-5.88gb
Now how am I supposed to format it to run windows.

Well can you possible elaborate more on that nothing else works part. 

I also deleted everything in partition :
                160gb unallocated
and tried running windows and still failed the message that XP gives me is

"setup cannot find hard disk in your computer"

so if I wanna delete ubuntu completely and install xp how should I format it
Do I need to have large chunk of ntfs or I have to have everything unallocated

The only I can run though is ubuntu I have installed and partitioned  more than 5 times now.

I would like to elaborate on the scenario where I can install XP without ubuntu nothing else just XP
I have not even able to do that as of now


Thanks for the responses I appreciate

---

### Post by shuttleworthwannabe on 2008-03-23
when you boot from XP CD, in one of the blue screen under drives, does XP not recognize the drive? If it does then, delete the partition, create a new partition according to your needs, and format the partitions you want wondows to see. Install XP. Then install Ubuntu on the rest of the partitions not formatted in Wondows. Ubuntu disc partition use MANUAL and select the partitions for ubuntu/swap etc.

or else boot using a GParted ISO, partition the entire drive the way you want for XP and Ubuntu. Install XP to the windows partition, and Ubuntu on the other partitions.

That is what I do normally. The trick is to install Windows first, then Ubuntu. GParted is great as a starting partitioning tool.

ATB,
S

---

### Post by poisonedapple on 2008-03-23
Thanks,
           What I did was I completely unallocated the disk for now since it was next to impossible for windows to recognize any kinda partition and it was all messy for me as a newbie to the installation process it self

the problem for the setup

I solved it through making SATA operation to ATA instead of the default AHCI

1.now does anyone knwo what difference does it make ?
2.Will I still able to partition after I install XP to install ubuntu again? and how in brief?
3.I also have an upgrad version of vista which I am planning to upgrade from xp after I finish installing xp
so will I be able to that with SATA operation in ATA?


I would appreciate if you anyone can guide me though this since dell customer support is nice but most of the time very helpless they just want me to ship it back to them and earn some money out of it because they want me to buy vista from them when I already have it.


----THANKS A LOT------looking forward for some answers definitely I am not even close to good at this

---

### Post by 3rdalbum on 2008-03-23
Ahh yes... I guess everyone here forgot that Windows XP's installer doesn't have support for SATA.

1. You should get drivers for your SATA controller, that work on Windows, and then turn your BIOS back to SATA.

2. You will be able to run the Ubuntu installer to resize the Windows partition and install Ubuntu.

3. Vista should recognise the SATA controller.

---

### Post by fourthofjuly on 2008-03-23
> **poisonedapple said:**
> Hi all,

       I recently bought a laptop from dell with ubuntu preinstalled in it. I already had a XP cd so I thought when I get it I will install XP. 

First thing I did:
                    - I used GPart Cd to partition the drive so that I have space for windows xp
                    -I made 100gb available for windows and 60gb for ubuntu
                   
Second thing I did:
                    - I put the XP cd to boot and the problem occurs
                   
I get this message:: Cannot find the hard disk on the drive

xp does not run at all

Third thing::
                   -I installed ubuntu again hoping something out of it.
Now I tried booting XP cd again no it shows the same problem

Is ubuntu so bad that I could not installl any other OS besides ubuntu I have to say I regret getting a preinstalled ubuntu. I would be more than glad if anyone can help me in this issue. I have spent two days on figuring out how to do this and I am very tired with ubuntu. May be it is microsoft but there should be something.




thanks
if you would simply like to have Ubuntu and also use XP, without any partition related woes, try Virtualbox

Simply delete all partitions, install Ubuntu and then install Virtualbox in Ubuntu...

run Virtualbox and install XP within Virtualbox 

XP will run as a guest OS within Ubuntu, no need to dual boot...

this link is a very easy guide...

[http://liferedux.wordpress.com/2008/01/01/howto-run-windowsxp-inside-ubuntu/](http://liferedux.wordpress.com/2008/01/01/howto-run-windowsxp-inside-ubuntu/)

regards,

devang.

---

