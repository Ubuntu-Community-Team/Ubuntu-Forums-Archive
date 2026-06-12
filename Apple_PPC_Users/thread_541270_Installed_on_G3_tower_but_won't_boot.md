---
title: "Installed on G3 tower but won't boot"
date: 2007-09-02
forum: Apple PPC Users
---

### Post by Afishionado on 2007-09-02
Howdy. I've been playing with Ubuntu for a couple years now on PCs; just this week I got my hands on a G3 tower, and thought I'd try installing KUbuntu 7.04 on it and seeing what Linux/PPC is like. :)

After much futzing with a CD that didn't burn right (!) I got the alt install CD up and running, and followed [the instructions here]("http://ubuntuforums.org/showthread.php?t=89960") to shorten the OS X 10.3 partition and make room for Ubuntu. I let Ubuntu automatically carve up the newly available space, and it made a partition for Yaboot, a root partition, and a swap partition.

I finished the install and rebooted. I was greeted with a mac folder icon with the OS Classic happy face inside. For a minute the image alternated between the happy face and a question mark, then OS X launched.

Just to see if I screwed up, I re-did the install a couple times with the same result.

So, what did I do? I'm completely new to Yaboot; some of the howtos I dug up online suggest that it needs to come early in the partition order. The Yaboot partition is immediately after the OS X main partition. Is that the problem?

Otherwise, what should I try here?

Thanks a lot. :)

---

### Post by pxwpxw on 2007-09-03
Something went wrong.

The config file used for yaboot install is /etc/yaboot.conf.

Run the install cd in rescue mode and see if you can mount your installed system root, and post a copy of /etc/yaboot.conf.

Also try to get a ful disk partition list from linux 
```

 sudo mac-fdisk -l

```
You can also get a partition list, and boot-device setting  from macosx terminal app.
```

 diskutil list
 sudo pdisk -l
 sudo nvram boot-device

```

There should be a boot partition of type Apple_Bootstrap with the boot files
(yaboot, yaboot.conf, ofboot/b .... ).
You could also mount and check the boot partition from linux, partition is type hfs.

---

### Post by Afishionado on 2007-09-03
Under OS X, diskutil list outputs:

```
/dev/disk0
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *17.1 GB  disk0
   1:    Apple_partition_map                    31.5 KB   disk0s1
   2:         Apple_Driver43                    27.0 KB   disk0s2
   3:         Apple_Driver43                    37.0 KB   disk0s3
   4:     Apple_Driver_IOKit                    256.0 KB  disk0s4
   5:          Apple_Patches                    256.0 KB  disk0s5
   6:              Apple_HFS Hard Drive         12.1 GB   disk0s6
   7:        Apple_Bootstrap                    977.0 KB  disk0s7
   8:        Apple_UNIX_SVR2                    4.8 GB    disk0s8
   9:        Apple_UNIX_SVR2                    278.5 MB  disk0s9

```
(The last three I recognize as the partitions I created with Ubuntu.)

"sudo pdisk -l" complains that no command is specified. The -dump option seems to produce similar output to diskutil, only the output is less human-readable. :???:

"sudo nvram boot-device" outputs:
```
boot-device     /pci@80000000/pci-bridge@d/ADPT,2930CU@3/@0:7,\\:tbxi
```

Give me a second to reboot, and we'll see where I can get with the Ubuntu CD.

---

### Post by Afishionado on 2007-09-03
Damn it, I tried to just edit my last post and add an update on the end, and the forum chewed up the yaboot.conf that I retyped into the form. :mad: :mad: (Can't get online under the rescue disk, so I have to retype it ... unless I mount a flash stick and move data that way.)

Anyway, mac-fdisk seems to print out the same partition table as before, just with Linux device names.

/etc/yaboot.conf looks like:

```

boot=/dev/sda7
device=/pci@80000000/pci-bridge@d/ADPT,2930CU@3/@0:
partition=8
root=/dev/sda8
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sda6

image=/boot/vmlinux
    label=Linux
    read-only
    initrd=/boot/initrd.img
    append="quiet splash"

image=/boot/vmlinux.old
    label=old
    read-only
    initrd=/boot/initrd.img.old
    append="quiet splash"

```

If it really does help to have the exact output from these commands, I'll see how to get them online.

At any rate, any help is much appreciated. :KS

---

### Post by pxwpxw on 2007-09-03
Yes a usb flash drive (fat32) is a good helper at times like this.

That all looks ok, except that I dont know about the yaboot.conf device: and boot-device paths, although the partition bit is ok (:7,\\:tbxi), ( I assume you just missed the pci-bridge bit in the retyping.)

You could try this, if it fails, should just default to booting Macosx,
or you can reset by doing Command-Option-P-R at start up for 2 chimes.
(That should put the boot-device to booting macosx.)

```

 sudo nvram boot-device = hd:7,\yaboot

```
hd: is an alias for the hard drive. yaboot bypasses the first stage ofboot.

If thats no good, you could still try mounting the boot partition, 
to see what is there.
```

 mkdir xxx
 mount -t hfs /dev/sda7 xxx
 ls -l xxx

```

I will have to go now, late here.
Will check tmw.

One  other thought, try starting with the Option key held.

---

### Post by Afishionado on 2007-09-03
Yes, I typed the device wrong. I edited my post, and I think it's right now.

I got at an Open Firmware boot prompt, and tried:

```
boot hd:7,\yaboot
```

and got

```
can't OPEN: hd:7,\yaboot
 ok
```

Same if I substitute a forward slash or leave the slash out completely.

(BTW, Open Firmware *does* use hd as the device name, even though it's a SCSI device, right?)

/dev/sda7 contains:

```

total 155
-rw-r--r-- 1 root root 3088 Sep 2 13:32 ofboot.b
-rw-r--r-- 1 root root 153124 Sep 2 13:32 yaboot
-rw-r--r-- 1 root root 693 Sep 2 13:32 yaboot.conf

```

So, any ideas? Would it be worth a shot to try the "reinstall yaboot" option?

---

### Post by pxwpxw on 2007-09-04
I would have a look at the current install before re-installing, to avoid repeating the same problem (unless the install indicated some problem, especially with yaboot install). Problem may be something wrong with the boot files, or not being able to find them.

scsi, might be an issue.

Adaptec scsi - that explains the device path.
"hd" is an alias generally for the main drive, whatever, but not sure if that goes for scsi, might be "sd". Probably the original full path was ok.
 
I know that Blue&White G3 can run ubuntu704, but I don't know if that includes scsi or only IDE. I will see if I can find some info.
May not be your problem.

If anyone knows please post.

But you can clear up the path question and see what is bootable from openfirmware. (i.e. can be opened ). If the boot files are accessible from O/Fw, then it should get as far as a yaboot text menu, by booting yaboot.

(Question: How did you get into Open Firmware? Usually by Command-Option-O-F)

Some O/Fw examples:

```

## list aliases and the full path.
0> devalias
0> devalias hd

```

To see what might be bootable, assuming "sd" is a valid alias for the scsi drive. (there may be others)
```

## for the whole device, lists whatever it finds first
0> dir sd:,\

## for partition 7
0> dir sd:7,\

```

If you find your boot partition it will list the boot files.
Some boot variations, depending what else is on the drive
(The first \ is optional for yaboot here).
```

0> boot sd:,yaboot
0> boot sd:7,yaboot
## this will probably boot macosx if it is first bootable partition.
0> boot sd:,\\:tbxi
## this might boot ofboot.b
0> boot sd:7,\\:tbxi

```

See if you can get something out of that.

---

### Post by Afishionado on 2007-09-04
"devalias sd" tells me "no alias". devalias by itself lists the following aliases:

```

pci
bridge
mac-io
via-cuda
rtc
adb-keyboard
adb-mouse
sound
enet
scca
sccb
nvram
ide0
cd
zip
ide1
hd
ultra0
ultra1
usb
fw
keyboard
mouse
usb-keyboard
usb-mouse
no-boot
last-boot
screen

```

When I try dir on most of these devices, I get "method <dir> not found" (guess I can't get a directory listing of my keyboard :)). If I try the command against hd, ultra0, ultra1, or last-boot, I get "can't OPEN the DIR device". If I put in my Ubuntu boot disk and run "dir cd:,\" I can get a list of what's on the CD.

However, for the life of me, I can't figure out how to see anything on the CD. "mac-boot" works, so there has to be **some** way to get at it. :confused:

(BTW, pxwpxw, just out of curiosity, what time zone are you in? I'm at the west coast of the US, and it's just a little before 8:00 AM as I type this.)

**Edit**: Sorry, yes, I got into Open Firmware by holding down command-option-o-f.

---

### Post by pxwpxw on 2007-09-04
That makes sense as far as it goes, but doesn't devalias list the full paths alongside the aiias? (it varies with the firmware version, mine do that but for version 3 and 4, I think yours may be 2).
I'm looking at your  list now, see if I can suggest something.

---

### Post by Afishionado on 2007-09-04
I forgot to explicitly say in my post :-# yes, it does; I just got tired of retyping them. I can get them, though.

---

### Post by pxwpxw on 2007-09-04
Oh, thats good, well which was the one with the same full path as you get for boot-device?
(see below, typed before I read you latest, maybe redundant)

This might be tedious but it will get a result.
First
```

printenv boot-device

```

( You can set values using "setenv". Command-Option-P-R start restores default values.)

Then check through the alias list, example:
```

 dev hd pwd ls

```
dev makes hd the current device,
pwd prints the full path to the current device
ls lists any further stuff at that level (i.e. like linux ls )
If you go through the whole list should eventually come up with the alias for the boot-device entry for the ADPT.
```

 dev ..

```
Takes you up  a level.

---

### Post by Afishionado on 2007-09-04
This is getting weird.

"pci" is an alias for "/pci"; everything else (except for the HID devices) is an alias for "/pci/@d/[comething]".  boot-device is "/pci@80000000/pci-bridge@d/ADPT,2930CU@3/@0:7,\\:tbxi hd:,\\:tbxi".

last-boot is an alist for "/pci@80000000/pci-bridge@d/mac-io@5/ethernet"; no-boot is an alias for "/pci@80000000/pci-bridge@d/mac-io@5/fdc".

So I'm not seing the alias for the boot device, unless I'm missing the obvious.

---

### Post by Afishionado on 2007-09-04
Just to be clear: boot-device, last-boot, and no-boot all start with "/pci@8000000/pci-bridge@d/", while all the "real" device aliases start with "/pci/@d/"

---

### Post by pxwpxw on 2007-09-04
> **Afishionado said:**
> This is getting weird.

"pci" is an alias for "/pci"; everything else (except for the HID devices) is an alias for "/pci/@d/[comething]".  boot-device is "/pci@80000000/pci-bridge@d/ADPT,2930CU@3/@0:7,\\:tbxi hd:,\\:tbxi".

last-boot is an alist for "/pci@80000000/pci-bridge@d/mac-io@5/ethernet"; no-boot is an alias for "/pci@80000000/pci-bridge@d/mac-io@5/fdc".

So I'm not seing the alias for the boot device, unless I'm missing the obvious.

You got it.

/pci@80000000/pci-bridge@d/ADPT,2930CU@3/@0:7,\\:tbxi
thats  what the installer set.

hd:,\\:tbxi".
thats the default.
 
The question is what is
```

devalias hd

```
But unless you can find the boot files in open firmware, its neve going to boot, so the answer may be that yaboot and co did not get installed, so you may need to try to rinstall yaboot but not the whole install (using rescue).
But I think you need to try to loacate the boot files.
I would expect if you do
```

devalias hd

```
the answer should match the boot-device path up to the colon.

see what happens for
```

boot hd:,\\:tbxi

```
And confirm you have only one drive?

---

### Post by Afishionado on 2007-09-04
boot hd:,\\:tbxi
rewards me with
can't OPEN: hd:,\\:tbxi

I don't know how this thing even boots...

devalias hd is
/pci/@d/pci-ata@1/ata-4@0/disk@0
while the boot-device is:
/pci@80000000/pci-bridge@d/ADPT,2930CU@3/@0

I finally realized that I don't understand OF's naming scheme well enough to know if those are even the same thing. :confused:

---

### Post by pxwpxw on 2007-09-04
Thats a ide drive, have you got 2 drives?

---

### Post by Afishionado on 2007-09-04
As far as I know, there's only one drive in there. I don't think I have the right kind of screwdriver to open the thing up and look. :-k

I was saying SCSI before because Ubuntu mounts the HD as /dev/sda, so now I have no idea what's going on in there.

---

### Post by pxwpxw on 2007-09-04
right - but how do you know you have a scsi drive? Something is very odd.

---

### Post by Afishionado on 2007-09-04
I was under the impression that the Linux device name /dev/sda implied that the device was SCSI. That was probably an incorrect assumption.

I got the machine for free about a week ago, so I really don't know anything about it other that it's a blue and white G3 tower.

---

### Post by pxwpxw on 2007-09-04
OK,  its just a matter of tracking down that boot partition and its files in open firmware.
Its a bit difficult to type that full device path for the scsi drive, the hd alias for an ide drive shows nothing. The nstaller has decded its a ADPT something which is being  reported by open fware, and I assumed that was an ADAPTEC scsi card which is an addon (also my assumption) if you happen to have both a scsi card and an ide drive, confusion may rule. I'd say that screwdriver sound like a good investment.
I dont think I can add much for now, time to sleep. I will keep on this though until you get an answer.

---

### Post by Afishionado on 2007-09-04
Alright, I found a set of allen wrenches in the garage. :)

The drive I see is a Seagate Barracuda 9U2002-001 LVD/SE SCSI drive. The ribbon cable runs from it to a PCI board with a Foxconn sticker on it--I assume that's the SCSI controller.

I'm starting to think that there's something in the expansion bay under the CD drive, but I can't see what it is without taking things apart.

I'll see if I can get photos up in a minute, for the curious.

---

### Post by Afishionado on 2007-09-04
Alright, computer pr0n. :)

[[IMG]http://img514.imageshack.us/img514/4494/g3motherboardld3.th.jpg[/IMG]](http://img514.imageshack.us/my.php?image=g3motherboardld3.jpg)
Here's the motherboard. I should probably take this thing outside and spray all the dust out. :)

The ribbon cables that seem to go straight from the motherboard to the HD actually go under it and on to the power button and CD drive. The PCI cards: The leftmost card is the ATi video card; the rightmost PCI card is the SCSI card (actually an Adaptec SCSI controller--the Foxconn sticker is actually on the ribbon cable). I have no idea what the middle card is.

[[IMG]http://img408.imageshack.us/img408/5719/g3driveszx2.th.jpg[/IMG]](http://img408.imageshack.us/my.php?image=g3driveszx2.jpg)
Up inside the case. On the top left is the CD device; directly below it is the mystery bay.

I tried to get some close-ups of the drive and adapter; none of them came out, and I think I'd have to actually remove them to get good pictures. :(

---

### Post by pxwpxw on 2007-09-05
Good pictures, very interesting. You have scsi. 

You might like to look at the Apple developer notes, full details about the standard ide drvie and the optional scsi, built to order.

NewWorld Power Mac G3 (blue and white) - Developer Notes.  1.1MB pdf.
[http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/PowerMacintosh_G3/PowerMacintosh_G3.pdf](http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/PowerMacintosh_G3/PowerMacintosh_G3.pdf)

I thouhgt it might be a problem with a missing Adaptec scsi module (possibly available for selection during install). But that does not explain not being able to boot the bootstrap files, which you have listed from the bootstrap, unless O/Fware just can't handle scsi, but then how does Macosx boot?

Hence would help to get some/any positve response from Open Firmware manual checks,  to confirm that anything can be booted from there, or files listed with "dir" - either macosx or linux boot files. The test I have used is - if Open Firmware cannot list (dir) a file, it cannot be booted.

If there is nothing in the "devalias" list that seems to relate to the path shown for boot-device = /pci@80000000/pci-bridge@d/ADPT,2930CU@3/@0 then, 
possibly it is just not given an alias, because its not Apple, although the firmware does recognise the scsi device. So you are stuck with using the full path for any booting or checks using "dir". I may be able to suggest some abbreviations (possible with O/Fware sometimes)

So why no ubuntu boot from the Adaptec scsi drive? 

It would be great if a happy B&WG3 scsi user could speak on that, it is not the standard B&WG3 setup.

Still struggling with it, must be a simple answer.

---

### Post by pxwpxw on 2007-09-05
Attachment - inside of bwg3
from apple doc. - see previous post

---

### Post by abtabt on 2007-09-05
hello 

if you skip the scsi card and the scsi drive (remove it)

and put a ide disk then i think you can sucess 

but you need too put the ide disk on the 0 buss not the 1 

and only as master not slave

and mayby you can sucess with old 5.10 cd (i use this for my old PPC with Scsi disks)


i hope you try this and return

good luck

---

### Post by Afishionado on 2007-09-05
Hmm, try with an older CD--that's an interesting idea. BTW, anybody know if I might have better luck with Yellow Dog?

Otherwise, I'm starting to think that the way to go is to buy an IDE drive, and try to set the system up to dual-boot with Linux on the IDE and OS X still on the SCSI.

... Of course, the last time I tried to add a second drive to a computer, I kind of killed it by plugging the ribbon cable in backwards. :) (Fortunately, it was an ancient Dell that I got for $10, so it wasn't a big deal.)

At any rate, I'm still open to ideas. :) Thanks so much pxwpxw and abtabt for your help so far.

---

### Post by pxwpxw on 2007-09-05
It makes sense to me that the ide drive will help with firmware booting (that is before anything except yaboot is loaded , which is the same for all versions back for quite a while.
It seems that you cant even get yaboot to load so far.
I dont see how an earlier version will change the bootstrap loading - but I am frequently wrong, so at least an earlier version might answer that question. I think you find them in ubuntu archives sonewhere - or debian sarge perhaps or another distro. Anythig to stir up some activity.
The apple notes refer to a boot drive, dont know what thats about.
Earlier versions also lack some of the later goodies, but I suppose you can go the upgrade path.

---

### Post by Afishionado on 2007-09-05
Well, right now I'm downloading the Yellow Dog images, on the outside chance that it'll work.

Random thought: I'm used to the grub installer asking for confirmation that it correctly detected any existing operating systems. When I installed on the Mac, the yaboot installer simply plowed through, then announced that the install was complete. Is this normal?

---

### Post by abtabt on 2007-09-05
about the version 5.10 is the best for older PPC if you need newer version of program like 
firefox or dillo (my favorite  ) 

try to change the source list to newer fisty or gusty and upgrade

after 5.10 things change the new x.org makes things harder (ati driver dont work prop the scsi card will not work prop and scsi disk 6.06 6.10 can work but you need to do a new 
initrd.img   if want to now how search for early post with     abtabt   )

good luck

if you try with a ide disk let osx and ubuntu on the same disk and use your scsi disk to 
store files on

:guitar:

---

### Post by pxwpxw on 2007-09-06
> **Afishionado said:**
> Well, right now I'm downloading the Yellow Dog images, on the outside chance that it'll work.

Random thought: I'm used to the grub installer asking for confirmation that it correctly detected any existing operating systems. When I installed on the Mac, the yaboot installer simply plowed through, then announced that the install was complete. Is this normal?

Yes lets see what happens with that distro. The yaboot install procedure varies between Desktop and Live and expert and so on, somtimes asks - its not a yaboot thing, its the installer . Same variation between various i386 installers using grub.

**abtabt** has good points there - if nothing else works, install on an ide disk but still use the scsi for extra space if the linux OS can handle it. Also, an earlier linux kernel version may handle the scsi pci adapter better after the boot phase, when  loading the root system.
Edit: note that there are no scsi buses on the bwg3, its just pci cards.

I still have a few more thoughts, but wait to see what results you get, with great interest.

---

### Post by Afishionado on 2007-09-06
I spent all day yesterday downloading, burning, and booting all six Yellow Dog discs--it turns out it's not happy trying to install from just one disc. :rolleyes: Same result as with Ubuntu: install goes great, won't boot afterwards.

I tried Kubuntu 5.10, but it wouldn't boot; I think I burned a bad CD, and I'm burning another one now. (Something must be up with the drive in my new Dell, because this is at least the fourth coaster I've burned in the last few weeks--I'm used CDs only turning out bad if I do something stupid.)

The reason I was thinking about leaving OS X on the SCSI drive is because I don't have an OS X install disc, and would rather leave the existing install alone if I can help it. For that matter, I'm starting to wonder whether or not I really want Linux on that machine badly enough to get in and mess with the internal drives. :(

We'll see if I can get 5.10 to do anything.

---

### Post by pxwpxw on 2007-09-06
I think they all use the same yaboot package, maybe some local tweaks though.

You probably have a zip drive on the g3. Its a different interface (see the pdf), part of the apple stuff witht the CD, probably might boot, all you need is some 100MB zip disks.

If you want to keep macosx (I would) it would be a good idea to get a macosx install dvd, not too expensive, 10.4 before they go to 10.5, or cheaper on ebay etc. Might need an earlier version to run on the g3, should be info on that in Apple.com. To see what version you have  click the Apple: "about this mac".

Looking back on what you tried so far for OF boot, we never actually got to try a boot or dir command that would have worked, just ran through some that failed because using the wrong device path, so the jury is still out on whether the problem is that the firmware can't boot from scsi pci, or the problem is something in the bootstrap partition. From reading the pdf, I cant see anything that should prevent it, given that the Macos can boot, and they do mention pci and scsi, but possibly vendor dependent.

If you could boot Macosx from open firmware, you should be able to boot linux via yaboot on the macosx partition, rather than direct.

Edit: zip drive and dvd drive are options only.

---

### Post by Afishionado on 2007-09-06
Holy fscking cow on a *sesame seed bun*. Ubuntu 5.10 *works*. I can hardly believe it. I have it and OS X dual-booting on the SCSI disc right now. I'll see (probably not today) whether or not I can bootstrap up to Feisty without breaking the bootloader.

:guitar:

Re the "mystery drive", I would have expected a zip drive in that slot too, but there's no opening whatsoever on the front of the case. If there is a drive for removable media there, it's walled in so I can't get at it.

Thanks so much, guys. I really appreciate your time.

P.S., does OS X set the clock to GMT? I may have just screwed up my calendar. No big deal, though.

---

### Post by pxwpxw on 2007-09-07
Applause, perseverance pays. Cigar to abtabt too.

Will await further developments with interest. I would like to know whether the problem was with the boot files, or with pci scsi support somewhere, or what.

Yes my macosx sets the firmware clock to UTC, date/time as shown on the o/fware opening screen. I once succeeded in setting the time in o/fware using get-time and set-time with forth stack operations.

Here is some apple ppc specific boot and other stuff that may be of interest (also encourage you to find an explanation).
 
In ubuntu you will find the full open firmware device tree at /proc/device-tree/ and see also /proc/scsi/
Its all different to i386.

Some apple ppc boot info is in < man yaboot yaboot.conf ybin mkofboot bootstrap >

see the b&wg3 pdf for more open firmware and other refs.

you can check the hfs bootstrap partition using the hfsutils package, hmount, hls,
Or create one using mac-fdisk, hformat, and hattrib to set file types and bless it. O/fware boots using either file type "tbxi" in a "blessed" directory, or a file name as specified in the boot-device.
```

# hmount /dev/sda2
Volume name is "bootstrap"
Volume was created on Wed Mar 14 18:24:39 2007
Volume was last modified on Fri Sep  7 15:03:33 2007
Volume has 118484992 bytes free
# hls -l
f  tbxi/UNIX         0      3349 Jun 12 23:06 ofboot.b
f  boot/UNIX         0    153124 Jun 12 23:06 yaboot
f  conf/UNIX         0       848 Jun 12 23:06 yaboot.conf
# humount

```

Have fun.:popcorn:

---

### Post by Afishionado on 2007-09-08
Well, I was able to apt-get my way up to Feisty. :)

I would definitely like to probe into this some more, but the next couple weeks promise to be busy ones for me--I don't know when I'm going to have much time to play with this again. :(

I'll keep you posted.

---

### Post by Afishionado on 2007-09-08
FWIW, here's the yaboot.conf from the working Ubuntu install:

```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda7
device=/pci@80000000/pci-bridge@d/scsi@4/@0:
partition=8
root=/dev/sda8
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sda6

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"

```

---

### Post by pxwpxw on 2007-09-09
> **Afishionado said:**
> Well, I was able to apt-get my way up to Feisty. :)

I would definitely like to probe into this some more, but the next couple weeks promise to be busy ones for me--I don't know when I'm going to have much time to play with this again. :(

I'll keep you posted.

Nice work, no hurry.

And re the good yaboot.conf

Looks like the feisty yaboot installer found the wrong scsi device card -
 device=/pci@80000000/pci-bridge@d/ADPT,2930CU@3/@0:

The 510 installer got it right - it was not the adaptec (?)
 device=/pci@80000000/pci-bridge@d/scsi@4/@0:

Why ?  2 scsi cards in pci slots ? 

 # ls -l /proc/device-tree/pci@80000000/pci-bridge@d/

 # /usr/sbin/ofpath /dev/sda

Whenever you get back to it ...

---

### Post by Afishionado on 2007-09-12
```
william@ubuntu-g3:~$ ls -l /proc/device-tree/pci\@80000000/pci-bridge\@d/
total 0
-r--r--r--  1 root root   4 2007-09-12 14:58 #address-cells
dr-xr-xr-x  4 root root   0 2007-09-12 14:58 ADPT,2930CU@3
-r--r--r--  1 root root   4 2007-09-12 14:58 bus-master-capable
-r--r--r--  1 root root   8 2007-09-12 14:58 bus-range
-r--r--r--  1 root root   4 2007-09-12 14:58 class-code
-r--r--r--  1 root root   4 2007-09-12 14:58 clock-frequency
-r--r--r--  1 root root  21 2007-09-12 14:58 compatible
-r--r--r--  1 root root   4 2007-09-12 14:58 device-id
-r--r--r--  1 root root   4 2007-09-12 14:58 device_type
-r--r--r--  1 root root   4 2007-09-12 14:58 devsel-speed
-r--r--r--  1 root root   0 2007-09-12 14:58 fast-back-to-back
dr-xr-xr-x  2 root root   0 2007-09-12 14:58 firewire@0
-r--r--r--  1 root root   4 2007-09-12 14:58 #interrupt-cells
-r--r--r--  1 root root 144 2007-09-12 14:58 interrupt-map
-r--r--r--  1 root root  16 2007-09-12 14:58 interrupt-map-mask
-r--r--r--  1 root root   4 2007-09-12 14:58 linux,phandle
dr-xr-xr-x 13 root root   0 2007-09-12 14:58 mac-io@5
-r--r--r--  1 root root  10 2007-09-12 14:58 model
-r--r--r--  1 root root  11 2007-09-12 14:58 name
dr-xr-xr-x  3 root root   0 2007-09-12 14:58 pci-ata@1
-r--r--r--  1 root root  64 2007-09-12 14:58 ranges
-r--r--r--  1 root root  20 2007-09-12 14:58 reg
-r--r--r--  1 root root   4 2007-09-12 14:58 revision-id
dr-xr-xr-x  4 root root   0 2007-09-12 14:58 scsi@4
-r--r--r--  1 root root   4 2007-09-12 14:58 #size-cells
-r--r--r--  1 root root  15 2007-09-12 14:58 slot-names
dr-xr-xr-x  3 root root   0 2007-09-12 14:58 usb@6
-r--r--r--  1 root root   4 2007-09-12 14:58 vendor-id
william@ubuntu-g3:~$ /usr/sbin/ofpath /dev/sda
/pci@80000000/pci-bridge@d/ADPT,2930CU@3/@0:
william@ubuntu-g3:~$

```

There *is* an extra PCI card of some sort in the machine--I'm tempted to pull it out and see what happens.

---

### Post by pxwpxw on 2007-09-13
> **Afishionado said:**
> ```
william@ubuntu-g3:~$ ls -l /proc/device-tree/pci\@80000000/pci-bridge\@d/
total 0
-r--r--r--  1 root root   4 2007-09-12 14:58 #address-cells
**dr-xr-xr-x  4 root root   0 2007-09-12 14:58 ADPT,2930CU@3**
dr-xr-xr-x  2 root root   0 2007-09-12 14:58 firewire@0
dr-xr-xr-x 13 root root   0 2007-09-12 14:58 mac-io@5
dr-xr-xr-x  3 root root   0 2007-09-12 14:58 pci-ata@1
**dr-xr-xr-x  4 root root   0 2007-09-12 14:58 scsi@4**
dr-xr-xr-x  3 root root   0 2007-09-12 14:58 usb@6
william@ubuntu-g3:~$ /usr/sbin/ofpath /dev/sda
/pci@80000000/pci-bridge@d/ADPT,2930CU@3/@0:
william@ubuntu-g3:~$

```

There *is* an extra PCI card of some sort in the machine--I'm tempted to pull it out and see what happens.

I edited your device-tree listing above to show the device nodes. You can look at the real one in filemanager to see what is below those nodes, or read text in the "files" = open firmware properties.

My guess is that the mystery card is the original scsi card, so the b&wg3 wont boot after removing it. Could it be a second video card? Some have them.

Or just remove the Adaptec card, see if it still runs. 

Look again at the device-tree listing and ofpath.

I don't think you have second scsi drive hidden somewhere. 

ofpath is listing the wrong device now .../ADPT,2930CU@3/@0:
It must have got it right for the good install, because the device path in yaboot.conf comes from ofpath in the yaboot package. I don't know if the yaboot package has changed between the 510 install and your current upgrade.
 
Likely due to something wrong in the data used by ofpath, e.g. 
```
  cat /proc/scsi/scsi 
```. 
If you like shell script, read ofpath to find other suspects.:cool:

---

### Post by Afishionado on 2007-09-13
> **pxwpxw said:**
> My guess is that the mystery card is the original scsi card, so the b&wg3 wont boot after removing it. Could it be a second video card? Some have them.

The card doesn't *look* like a video card to me, but what do I know. :) Actually, it does look awfully like the SCSI card to me.

> Or just remove the Adaptec card, see if it still runs. 

I'm not sure how I'm supposed to access my drive if I do that. :? I'm losing my enthusiasm for mucking around inside the case, anyway. :|

> 
If you like shell script, read ofpath to find other suspects.:cool:

We'll see when I next have some time to kill here. :)

---

### Post by nevermore0069 on 2007-10-20
Son of a monkey! I've been messing with this all day and didn't see the other SCSI card! I am giving it another go at installing, wiping all of the partitions and starting anew. **Crosses Fingers**

---

### Post by nevermore0069 on 2007-10-21
I didn't notice the other SCSI card because it was a low profile. Anyway, I yanked it, reinstalled Feisty and it booted the first time :D

Now it appears I have a different problem. For some reason it is not seeing the network. The odd, very odd, thing that is occurring is that it sees it needs updates and mysteriously looses the ability to find the network? Whiskey-Tango-Foxtrot?!

---

