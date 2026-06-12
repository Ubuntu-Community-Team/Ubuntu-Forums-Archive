---
title: "Gutsy does not recgonise any media in dvd drive"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Phil Archer on 2007-11-01
Hi I'm a Newbie and a silver surfer..!!

My pc X86 32 bit is dual booted (XP & Gutsy) in xp my DVD reader works fine as does my CD/RW drive but in Gutsy then whilst my dvd triver is show nom places.Comouter it will not recognise any media at all.

From Sudo LsHw 

CDrom:1 = DV 5700A DVD Reader

   logicak device / Dev/cdrom1
                         /dev/dvd/
                         /dev/sc01
                         /dev/sr1

From fstab 
               dev/hdd/media/cdrom              udf, iso9600  user, no auto

in Places/ Computer I have 4 icons
         cd-rom 1    (noexistent dev/hdc when clicked)
          cd-rom 2   (noexistent dev/hdd when clicked)
         Cdrom /dvd rom   (gives no media when clocked)
         CD-RW Drive   (Gives media description when a cd is loaded)

I've been ploughing  through postings and am coming to the conclusion that Ubuntu and this device don't like each other and are incompatible

How do I get them to make up or do I have to buy a ne DVD drive to keep Ubuntu happy?

If so can any one suggest a budget drive from Aria / Amazon etc that won't blow all my pension in one fell swoop?

Thanks

Phil 

Where have all the PDP's gone or better yet the Norsk Data 100's?     :confused:

---

### Post by rudeboyskunk on 2007-11-01
The dvd is in udf format.  I have this problem in openSuSE.  I can read the dvd in Ubuntu and PCBSD, but openSuSE does not support these dvds.

---

### Post by ofb on 2007-11-02
Let's have a look at something. Post the output for these two,

```
cat /etc/fstab
sudo fdisk -l
```

Can't help with the PDP11. Played tic-tac-toe on one once and that was about it.

---

### Post by Phil Archer on 2007-11-05
*Let's have a look at something. Post the output for these two,*


_cat /etc/fstab_

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=5a5cca85-05e2-45c4-9371-19815e7fa633 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b5274969-69f4-4be6-84cc-75d3da54e3e6 none            swap    sw              0       0

#original with udf support
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0




/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



Sudo fdisk -l

phil@phil-Linux:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb59db59

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       14405    64509007+  83  Linux
/dev/sda3           14406       14593     1510110    5  Extended
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b0d87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3570    28675993+   7  HPFS/NTFS
/dev/sdb2            3571        4865    10402087+   7  HPFS/NTFS


Hope this helps although the one above just gives the partitions on the 2 hard drives


My first taste of PDP was in 74 a PDP 11/40 8k of magnetic core memory, paper tape, Teleprinter console, and prper switches and flashing lights. Never mind command line you could enter and run code via switches..!!

Thanks

Phil

---

### Post by ofb on 2007-11-05
> **Phil Archer said:**
> Hope this helps although the one above just gives the partitions on the 2 hard drives

Indeed it does. What I'm looking for right now is a suspicion.

Notice how your fstab has hda and hdb, while your partition info is sda and sdb?

Somewhere along the line, how the kernel handles the IDE devices has been changed. Right now there are several forum threads about unrecognized devices, burners that read but won't burn, machines that swap hda and hdb assignments to two drives randomly on each boot, and a couple of other things that escape memory because it's 2.30 in the morning here.

What I'm saying is don't go buy a new DVD player just yet, because that may very well not be your problem.

The next question of course, is what to do. That I don't know yet. I've spent hours in threads and bug reports and as yet I haven't made head&tail of this one. Right now my suspicion is a kernel issue that may be farther upstream than the Ubuntu developers.

At any rate it will take a while for the smart people to sift the bug reports into meaningful action paths, and then put a solution in the pipeline. What I'm starting to think is the best thing I can do about it personally is just ignore it for a week and then check the threads again to see where we're at. Right now the information channel is pretty much all noise and near zero signal.

Incidently, congratulations. I was reading your post here three days ago and fired up my other machine to look at how it was set up before answering, when I realized I've been inflicted with this plague too. So in a way I have you to thank & blame for this educational misadventure. ;)

I do hope I just made sense. Feel free to ask me to explain any dicey bits.

---

### Post by Phil Archer on 2007-11-05
OFB you made sense.

I did havit sortof workinh umder fiesty as a newbie I just chucked gstreamer and xine bits at it until something worked. But even then it was flakey. After the nth try it would suddenly reconize and play very jerky the DVD. Since then I have got a cheap Nvidia Force four 64mb card of Ebay and also put XP back on and then set up for dual boot Gutsy.

If its any help this DVD player is from an Old DEll I had new around 1999 with Windows 98 on it.

When I do Sudo lshw it finds it just fine. So lets see what happens.

Were you invoved with radio communications, the reference to signal to noise ratio, I was an apprenice with Pye Telecomm in the 60's just as these new fangled transistor things came into being

Thanks

Phil

---

### Post by ofb on 2007-11-05
As long as the DVD player still works fine in XP, I wouldn't be suspicious of it. Support for older hardware in Linux is generally pretty good.

You can of course do searches with the model name and 'Linux' or 'Ubuntu', but those searches tend to turn up old troubles that have long been taken care of. I usually find it's best not to try old fixes because the kernel moves on.

As for the troubles in 7.04, codec support was hit&miss under that distribution. I ended up using several movie players - I could never get one to play everything, and there were still a few video files that would not play flawlessly. It was a poor showing for a distro that was supposed to be good with codecs. I'm hoping that's been better sorted in 7.10 - I did a fresh install mainly to clear out such cruft-fixes I'd inflicted on 7.04.

If you're curious, you can run 'dmesg' after a boot and see what's being returned for the IDE detection. I say "after a boot" because dmesg can include quite a bit more once you've been running for a bit. But whatever that returns, I don't see there's much we can do with it. Probably it's best to just wait for some updates to kernel or libata or somesuch.

I've never worked with radio, though I've tinkered with too much to remember. At this point I couldn't say where I picked up noise vs signal. It's common in information theory of course, and also quite common on the web depending who you chat with. 

Possibly I should add that I was only a young brat in the 60s. I definitely grew up with the transistor, though of course I remember all hardware stores had tube testers. Back then it was all about the Bullet Train and then Concorde and a quite unbelievable future to come. Funny how the only magical difference that came to pass is these "film-less" digital cameras. 

Cell phones and the Web are quite nice, but things really haven't moved on at the clip we were expecting. The forward momentum sort of jammed in the late seventies somehow.

---

### Post by ofb on 2007-11-06
Does your motherboard use an Intel chipset? Do a 'sudo lshw' and have a look for the IDE section. It'll look something like this,

```
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=32 module=ata_piix
```

That's my afflicted computer. The one that's okay uses a VIA chipset. I'm looking at this bug,
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/133666](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/133666)

They're discussing boot failures of course, but as I mentioned there seems to be a rash of trouble around IDE devices in general. Just how much this patch will solve is an open question, but it does look like things are getting past the exploration stage.

---

### Post by Phil Archer on 2007-11-06
Sudo Lshw gives

  *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128 module=pata_sis



I ran Dmesg but there doesn't seem to be anything that looks untoward so as you say lets sit and wait. Some update have just come through for printer services and process monitors but I don't think that will change things.

Thanks
Phil

---

### Post by nae5 on 2007-11-18
sudo lshw puts this out.  I'm trying to read a UDF data dvd i burned in winxphome on a different pc with drag and drop, i believe the dvd software that came with that pc was roxio 5 or something.  Isn't UDF a popular data dvd format? why no support?  however i can play commercial dvds and read cds fine and i have been able to burn cds on the cdrw drive so it's possible to work around by file transfers on local network and stuff..
```
 *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM DVD-115
                vendor: PIONEER
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.22
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-RW CED-8120B
                vendor: LG
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.03
                serial: LG      CD-RW CED-8120B 1.03
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=open
           *-disk:0
```

---

### Post by ofb on 2007-11-18
Hmmm. Have a look through these, which are supposedly fixed. Stange.
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233)
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/112584](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/112584)

You might try changing the 'udf,iso9660' to 'auto' as an experiment.

---

