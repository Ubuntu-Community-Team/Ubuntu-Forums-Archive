---
title: "Newbie Questions"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by ausm on 2005-11-09
I have been using DOS/windows for 20 years and I finally decided to try Linux. I am glad I chose Ubuntu and I am amazed at how fast and flawless it runs.

The only problem I had during the installation was it kept hanging up while loading the boot loader. I blew away Win Xp and then it loaded flawlessly.

Here are a couple questions I have.

1)How come the partitions are labled "C" and "D" like in Windows? ALl I have is a floppy,CD-Rom and Home when I use Nautilus.

2)How do properly install 3rd party apps?

3)How do I update my video drivers?

4)Will I be able to set up a Dual boot situation by reinstalling Win XP?

TIA,

Ausm

---

### Post by Cufishing on 2005-11-09
Greetings and Welcome.

Dual boot:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Applications:
[http://ubuntuforums.org/showthread.php?t=87946](http://ubuntuforums.org/showthread.php?t=87946)

Do a search here on the forums for your video card. "mlomker" has written some really good 'how-to's' for the ATI series.
I'm sure there are others for other cards as well.

---

### Post by earobinson on 2005-11-09
All of your questions can be answered by searching the forums (but im not sure I understand question 1)

2) programs are installed using synaptic or apt-get and dpkg

3) ATI: [http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589) (I found this by searching the forums for: ati)
Nvidia: [http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia) (I found this by searching the forums for: nvidia)

4) [http://www.ubuntuforums.org/showthread.php?t=16287&highlight=dual+boot](http://www.ubuntuforums.org/showthread.php?t=16287&highlight=dual+boot) (I found this by searching the forums for: dual boot)

---

### Post by ausm on 2005-11-09
[QUOTE=earobinson]All of your questions can be answered by searching the forums (but im not sure I understand question 
[/QUOTE]


After reading it I don't understand it either :) I meant to say the partions are *not* labled C and D because I have two hard drives in this machine and quite frankly I am not sure which drive I loaded Linux on :confused: One drive is 200 gig and the other is 120 gig. Where do I check to confirm which drive is what and where my files are residing? When I use nautilis it is confusing for me compared to using Windows Explorer.

TIA,

Ausm

---

### Post by kvidell on 2005-11-09
[QUOTE=ausm]After reading it I don't understand it either :) I meant to say the partions are *not* labled C and D because I have two hard drives in this machine and quite frankly I am not sure which drive I loaded Linux on :confused: One drive is 200 gig and the other is 120 gig. Where do I check to confirm which drive is what and where my files are residing? When I use nautilis it is confusing for me compared to using Windows Explorer.

TIA,

Ausm[/QUOTE]
I presume you don't want the command-line answer, as you're comparing it to Explorer...
But here it is, anyway:```
df -h
```That'll show you what's mounted and where, using Linux's very own hd?? naming scheme. HDA for primary master, HDB for primary slave, so on and so forth. Also, each partition is labeled numerically.

I've never really used Nautilus before, so this answer is my assumption after having played with it for three minutes:
Linux doesn't really... care what drive is what. It relies more on it's directory/file system structure.
So while df -h can tell you what drives are where, it doesn't really matter.
Drives chill in /dev/*, but are mounted to the file system as directories in the tree... So calling it "filesystem" is really more correct than pinpointing a specific drive in the system, as trying to change directory in to a drive will give you:```
4/kvidell/happytop: cd /dev/hda1
/dev/hda1: Not a directory.
```Because, well.. it isn't. It's a device.

I know my explaination isn't very good... maybe someone can clear it up a little more? Or if you ask another question related to this, it may spark a better answer in my brain.
- Kev

---

### Post by earobinson on 2005-11-09
a better longer answer was posted above me

linux dose not treat hard drives the same way windows dose, lables dont really exist.

the best way would be to do this
```
cat /etc/fstab
```

this will tell you.

also you may be able to figure this out by runing gparted

---

### Post by ausm on 2005-11-09
Oh thx that helped alot! I just have to learn how the Linux filestructure and hierarchy works and then I will definately be more efficient.

Oh I chose Ubuntu to get away from command lines but I am not afraid to use them :razz: 


Thx,

Ausm

---

### Post by steve.horsley on 2005-11-09
[QUOTE=ausm]Oh thx that helped alot! I just have to learn how the Linux filestructure and hierarchy works and then I will definately be more efficient.

Oh I chose Ubuntu to get away from command lines but I am not afraid to use them :razz: 
[/QUOTE]

Good. You do have some learning to do. Here are a couple of guides:
[http://ubuntuguide.org/](http://ubuntuguide.org/)
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

The linux file system is a single tree. Different partitions are "mounted", grafted onto that tree so that they look like directories. Even remote machines are mounted this way. From the command line, **df -h** tells you what partitions are mounted where adn what free space there is. Here is mine:
```
steve@StevesPC:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6             4.7G  2.9G  1.9G  61% /
tmpfs                 126M     0  126M   0% /dev/shm
tmpfs                 126M   13M  114M  10% /lib/modules/2.6.12-9-386/volatile
/dev/hda8              39G  9.0G   30G  23% /mnt/data
/dev/hda3              25G   20G  4.9G  81% /mnt/windows
```
You see my root filesystem is based on partition 6, and partition 8 is mounted as /mnt/data. If you're interested, I have a Mandrake Linux root system partition on partition 5, which will get overwritten when the next Ubuntu version comes out. I mount hda8 as /mnt/data in Mandy as well, so I can use the same data in both systems. A second hard drive would be /dev/hdb.

The file /etc/fstab tells the system where to mount partitions. Ubuntu normally mounts windows in /media/windows but I got used to it being under /mnt in Mandy, and old habits die hard.

Installing XP will probably trash your Ubuntu so you can't really recover it. It's probably best to wipe the disk, install XP on the first half leaving the second half blank (no partitions allocated), then let the Ubuntu installer make its own partitions - select use free space in the installer.

Have fun learning.
Steve

---

### Post by MichaelM on 2005-11-09
[QUOTE=steve.horsley]Installing XP will probably trash your Ubuntu so you can't really recover it. It's probably best to wipe the disk, install XP on the first half leaving the second half blank (no partitions allocated), then let the Ubuntu installer make its own partitions - select use free space in the installer.[/QUOTE]
Actually, you probably *could* install Windows in any empty partition without trashing Ubuntu. However, it won't boot unless it's on the first one. :)

---

