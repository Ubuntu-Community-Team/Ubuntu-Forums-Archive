---
title: "Dual Boot Ubuntu &quot;FF&quot; 7.04 on macbook without using bootcamp, lilo, or grub manipulat"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by ItsMitsHere on 2007-09-26
Not many guids on installing ubuntu 7.04 on macbook without bootcamp without any hack!!!

Well here's one i suppose.

i got it veryyyy easily without any hassels on my MB 2GHz White with 1 GB RAM and 80G HDD...

Required: rEFIt 0.10 (opensource), ubuntu 7.04 live cd.
NotRequired: Lilo, elilo, grub manupulation etc...
Steps..
1. Back up your data!!! and then...
Partition your hard disk to get atleast 4 gb free space...Hmm...Without bootcamp? Yes! Update TIGER to 10.4.6 or above and fire terminal (Applications/utilities), Now type

***sudo diskutil list*** 

and hit return (it may ask for password)

it will return you the details of your partition...we can split the largest partition (most probably disk0s2, which is your startup disk)  before splitting the disk, let's know what limits do we have for splitting... to do this type

***diskutil resizeVolume disk0s2 limits***

it will show you the resize limits (i.e. minimum and maximum possible size) of disk0s2 which we are going to partition CAUTION: Your disk to be partitioned may be disk0s3 or disk0s4 depending upon the manupulations you have done before. whatever it is, choose the largest partition 

to split the disk you should type 

***diskutil resizeVolume disk0s2 30G***

and hit return

theoritically the disk can be split up to whatever size between minimum and maximum, but you will fail repeatedly if your disk is too full. if your disk is of 80 GB (like mine) and you want to resize it to 70G, you must have 40-45 GB free space. after partition you will be left with some 6G free space which will be used to install ubuntu!!!

Now, if your attempts at partitioning the disk fails, donot panik and keep trying with different sizes...(i was successful at my 11th attempt ant then i learned the funda of free space i mentioned above) basically you can free up maximum of your space and your chances of failures will be less, else try with 60, 62, 65 etc values untill you get successful. it will hopefully not harm your system ('coz its Mac - perfect!)

once you have created partition, type exit, hit return and close terminal.

2. download opensource boot manager called rEFIt. current version is 0.10. download the lattest...It is a .dmg file to be installed on mac. install it (installation is very easy) 
again fire terminal and type

***cd /efi/refit***

hit return and type again

***./enable.sh***

hit enter again. now reboot your computer and wow, now you see something else then apple boot screen, yes! this is rEFIt. if you are successfull up to this what follow is a cake walk...

3. insert the ubuntu 7.04 cd and restart the computer. while restart, hold the C key to force the computer boot from cd, it may take some time though (2-5 min) or 2-3 unsuccessful attempts, but once you boot, you can start the installation of ubuntu by doubleclicking the install icon on desktop. When asked for disk partitioning during the install, choose manual, you will see the free space as /dev/sda3 or like. mount point for this partition should be /. if you wish swap partition, you can make this from the free space. if you wish to have another 'shared partition' to move files to and from other os, that can be acheived too. the game is all yours now. after complition of the install, which will be as smooth as ever, choose reboot and you will see again rEFIt menu, but now with TUX. by default you will boot into mac if you do not make any choice in 20 sec. else use left-right arrow keys to select your os, hit enter and feel free. 

BTW, this is my first post on ubuntuforums, i m a linux newbee (4 days old) and info presented here is from this forum, some googling and my own experience. i have also found that most of the things run perfectly well under this newly installed ubuntu. some minor driver problems can be fixxed by some googling...i got everything working except rightclick on trackpad by two fingers!

---

### Post by dppowell on 2007-09-26
> **ItsMitsHere said:**
> BTW, this is my first post on ubuntuforums, i m a linux newbee (4 days old) and info presented here is from this forum, some googling and my own experience. i have also found that most of the things run perfectly well under this newly installed ubuntu. some minor driver problems can be fixxed by some googling...i got everything working except rightclick on trackpad by two fingers!

Great first post!

---

### Post by ItsMitsHere on 2007-09-27
> **dppowell said:**
> Great first post!

thanks for appretiation...

---

### Post by ItsMitsHere on 2007-09-27
Anybody tried???

---

### Post by IMcD23 on 2007-10-14
Trying it right now...Will post w/ results

EDIT: Actually, no.  I'm not doing that

---

### Post by Frisby on 2007-10-18
I'm gonna try this on my MacBook now... I'll post back if it installs successfully. If not, you wont hear from me xD

[COLOR="Teal"]**EDIT: sorry peoples, I can't get enough space to split up my harddrive this way. Maybe I'll try another time. I failed while splitting like 20-30 times. Damn:P**[/COLOR]

---

### Post by secundar on 2007-10-19
I've gone thru the instructions but when I select Tux at the rEFIt menu he just sits there for some time. After a while I just power down the MacPro. Here's the otput of Partition Inspector...


```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    398868519  Mac OS X HFS+
 3      422199336    488397127  Basic Data
 4      398868520    422198598  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    398868519  af  Mac OS X HFS+
 3      422199336    488397127  0c  FAT32 (LBA)
 4      398868520    422198598  82  Linux swap / Solaris

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 422199336:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0c  FAT32 (LBA)

Partition at LBA 398868520:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris


```

I have a drive with Mac OS X, WinXP, and a linux swap. Another drive has an ext3 for /, ext3 for /home, and a fat32 for /mnt/shared.

I'll see if the 7.10 install CD has Gparted. Perhaps there's a boot flag missing on /.

EDIT: Gparted boot flag does not help. Still will not boot to Ubuntu.

rEFIt works great for Mac, Windows booting though.

---

### Post by ItsMitsHere on 2007-10-23
> **Frisby said:**
> I'm gonna try this on my MacBook now... I'll post back if it installs successfully. If not, you wont hear from me xD

[COLOR="Teal"]**EDIT: sorry peoples, I can't get enough space to split up my harddrive this way. Maybe I'll try another time. I failed while splitting like 20-30 times. Damn:P**[/COLOR]

Partitioning the disk will only be possible if you have enough free space, 'coz the free space will be required to shift original files to some another place to create a continuous junk of free space that will be your new partition. 

I will suggest to free up more space if possible.

for more info, please check [http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes]("http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes") ; [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp") and [http://ubuntuforums.org/showthread.php?t=452262]("http://ubuntuforums.org/showthread.php?t=452262")

The thing is, bootcamp does the same thing to partition the mac hdd, though in a graphical way and may be through much more profound mechanism. but there is no reason why it should fail!

---

### Post by ItsMitsHere on 2007-10-23
dear secundar, 
I think there is some problem with your partitions, How come your linux swap partition is around 40 gigs? swap partitions are generally of around 512 mb to 1 gig. and i dont see any linux partition there!!!

What you should try next is...
1. insert ubuntu live cd in cd/dvd drive and restart the comp. in rEFIt manu you will see some tux with cd icon (apart from a tux with HDD icon).
2. select the tux with cd icon and live cd should run. then doubleclick the install icon and start installation.
3. while partitioning option appears select manual and in the next screen select linux partition (most probably /dev/sda3) and mount it as /, leaving around 1 gig for swap partition.
4. next option will be a newly added partition called /dev/sda4 of the remaining space which you should mount as swap partition. click next and after 2-3 next-next, your linux should have been installing.
5. after installation is complet restart after removing the cd and you should be ready to rock!

N.B. Though linux swap partitions are obsolate these days, it is always a good idea to create one!!!

Edit: I have some strange feeling that i have misunderstood something!!! can u post me what you see when you type **sudo diskutil list** ?

---

### Post by JRoDDz on 2007-11-07
I ran through your instructions on a Macbook Pro and they worked perfectly.  I'm using Ubuntu 7.10 Gutsy amd64 build.

thanks!

---

### Post by ItsMitsHere on 2007-11-07
Anytime buddy :)

---

