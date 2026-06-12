---
title: "Losing sound on reboot"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by BobLand on 2007-05-28
This morning sound was working on all modules.  I watched videos on YouTube, MySpace and a few demos on other sites.  Amarok, Xine, and all other sound making modules worked as expected.

After running the updates I rebooted as the updates requested.  At the login screen, no sound.  Amorak and Xine - no sound, YouTube, MySpace - no sound.  System/Prefs/Sound - sound on devices tab but not other tabs.  Only sound is RhythmBox and Movie Player.

This happens everytime I reboot.  I usually run a few lines from the Comprehense Souund page to get things to work but lately, it becomes more and more difficult to get full sound.  Today, after the reboot, I ran the full Comprehensive Sound procedure but still no sound.  Found a few other threads, tried them.  Nothing.

In the past, I would create a new user and log in under that user.  I would get all sound.  This time, nothing.

My card is a Creative Labs SB Audigy LS.  I also installed the libxine-extracodecs.  This time it didn't do anything.

I'm wondering if this is a bug since it is repeatable.
Bobland

---

### Post by BobLand on 2007-05-28
One thing I noticed was a list of drivers in /etc/modules.  The driver for my sound card is ca0106.  In /etc/modules is listed in order:

ca0106
fuse
lp
sbp2

I got a little suspicious about sbp2 thinking it might be conflicting with ca0106 since it sounded like a sound blaster driver so I commented everything except ca0106.  Removed the linux-sound-base...etc, reinstalled the linux-sound-base...ect and reinstalled gdm.  After a reboot the sound was 100%.  Just to be sure I rebooted again.  Sound still there.

Hopefully, this will help someone with similar problems.  However, if anything changes, like spotty sound again, I'll update this thread.

bobland

---

### Post by BobLand on 2007-06-06
Guess I'm using this thread as a reference to what works and not.

Saw post #110 in the Comprehensive Solution whatever re user with out-of-date kernal.  Just for the heck of it I ran the code:

```
sudo apt-get update && sudo aptitude dist-upgrade
```

rebooted and all sound was restored.  Since the kernel version did not change I can only imagine that a few minor fixes were made or with all of the "try this, try that" things I've been doing the kernel straightened it all out.  Or something like that.

Ahh.  The journey continues.  

Hope this helps someone.

---

### Post by systemintheglitch on 2007-06-15
> **BobLand said:**
> Guess I'm using this thread as a reference to what works and not.

Saw post #110 in the Comprehensive Solution whatever re user with out-of-date kernal.  Just for the heck of it I ran the code:

```
sudo apt-get update && sudo aptitude dist-upgrade
```

rebooted and all sound was restored.  Since the kernel version did not change I can only imagine that a few minor fixes were made or with all of the "try this, try that" things I've been doing the kernel straightened it all out.  Or something like that.

Ahh.  The journey continues.  

Hope this helps someone.


THANK YOU!!!!!

Worked for me!;)

---

### Post by BobLand on 2007-06-18
06/18/2007
I've been trying to access my Windows partition for the past 2 weeks to no avail.  In fstab the windows partition was assigned to /dev/hda1 which seems to be a "standard."  Unfortunately for me there is no /dev/hda1 anywhere in my system.

Every time I tried to cd into it I'd get a "no directory or file found."  One of the error messages said something about mtab.  I compared fstab to mtab and they were different.  mtab said the Windows partition was in /dev/sda1.

I changed fstab and rebooted, reluctantly.  As I feared...[COLOR="Red"]NO SOUND AGAIN!](*,)[/COLOR]. [SIZE="3"][SIZE="1"]*[COLOR="DarkOrange"](but at least I could access my Windows partition...)[/COLOR]*[/SIZE][/SIZE]

Ran
*```
sudo apt-get update && sudo aptitude dist-upgrade
```*
rebooted
No Sound, just as I feared.

First thing I checked was /etc/modules.  

I went from this
```
ca0106
```
to this
```
ca0106
snd=sb16
snd=sb32
fuse
lp
sbp2
```

Where'd these drivers come from?

I commented them out
```
 ca0106
#snd=sb16
#snd=sb32
#fuse
#lp
#sbp2
```
rebooted

Sound back!
This is driving me crazy!!!!!!:evil::x:frown:

---

### Post by bren on 2007-06-18
> **BobLand said:**
> 06/18/2007
I've been trying to access my Windows partition for the past 2 weeks to no avail.  

Hi bob,

I have two suggestions

1) which I think you have already done is 

sudo apt-get install ntfs-3g

then go system/admin/ntfs config and select both options

2) run testdisk to check your partition table isnt disrupted
available via live cd here [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

hope that helps
let us know

bren

---

### Post by BobLand on 2007-06-18
bren,
The problem was an incorrect entry in fstab.  It stated that my Windows partition was on /dev/hda1.  In fact the partition was on /dev/sda1.  Once I made that change and rebooted I had no problem accessing the partition.

---

### Post by BobLand on 2007-06-25
Installed ntfc-config to employ read-write access to my ntfs drives.  As of this posting, I cannot get write access to these drives.  However, after installing this utility, sound went off again.

This time, /etc/modules was changed from
```
ca0106
```
to
```
ca0106
palm
fuse
```

Since my palm also doesn't work and has never worked with Ubuntu I commented it out but left fuse because this allegedly has something to do with ntfs-config.

Ran 
```
sudo apt-get update && sudo aptitude dist-upgrade
```
rebooted

No sound

commented out fuse
```
ca0106
#palm
#fuse
```
rebooted

Sound

Looks like everytime something is installed I have to check /etc/modules, comment everything out then reboot.  I may modify this procedure in order to fix the Palm but more about that later...

bobland

---

### Post by BobLand on 2007-06-25
06/25/2007 part II

I'm unable to reach my ntfs drives and finding ntfs-3g to be of no help, perhaps, even the source of this problem.

fstab created after installing ntfs-config
```
cat   /etc/fstab.backup
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdc2 :
UUID=e6511fca-c97e-4972-ad09-c350d33094e4 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdc7 :
UUID=a71279b3-57e2-40d0-ae61-d1f97f2fe839 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```

None of my ntfs partitions, or for that matter ext3 partitions, are listed.  
Let's get rid of the ntfs-config installation.
```
sudo apt-get remove ntfs-config
```
Just to be sure
```
sudo apt-get update && sudo aptitude dist-upgrade
reboot
```

Arrgggghhh........
no sound
no mounts

Checked fstab.  No change.
Restore original fstab
```
sudo cp /etc/fstab~ /etc/fstab
```
Now it reads correctly
```
 cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdc2 :
UUID=e6511fca-c97e-4972-ad09-c350d33094e4 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdc7 :
UUID=a71279b3-57e2-40d0-ae61-d1f97f2fe839 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

/dev/sda1 /media/Dual_Boot ntfs-3g rw,nosuid,nodev,umask=222,utf8 0 0
/dev/sdb1 /media/Photos ntfs-3g rw,nosuid,nodev,umask=222,utf8 0 0
/dev/sdc5 /media/W2K_Bkup ntfs-3g rw,nosuid,nodev,umask=222,utf8 0 0
/dev/sdc6 /media/Linux_Bkup ext3 rw,noexec,nosuid,nodev 0 0

```
(I'm guess that explicitly installing ntfs-config only adds ntfs-3g, which for me was useless and perhaps introduced some bugs).

Now that fstab is correct mount everything
```
sudo mount -a
```

Errors:  no such file or directory found

Check /media
No listings for the desired partions so
```
sudo mkdir /media/Dual_Boot
sudo mkdir Photos
sudo mkdir W2K_Bkup
sudo mkdir Linux_Bkup
```

Try to remount again
```
sudo mount -a
```
Good.  Everything mounted.  Not only that *but all of the ntfs drives are **_read-WRITE!!!_***

Still have to fix sound.  linux-sound-base is once again broken.  At least /etc/modules is correct so time to run
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
```
but before rebooting...
```
sudo apt-get update && sudo aptitude dist-upgrade
reboot
```

Finally, everything mounted and sound!

If anybody reads this and finds it helpful, please post what you were doing prior to having the sound go dead.

alsamixer
I've never had any problems with alsamixer.  I never even set it.  It has never been an issue for me.

Kernel version
```
uname -r
2.6.20-16-generic

```

bobland

---

### Post by BobLand on 2007-06-28
06-28-2007
Shut down the computer to get rid of the wire snake pit under my desk.  Machine off for 1.5 hours.  Did not change anything regarding connections nor add new components.  Labeled power modules and bundled and labeled similar wires.

Plugged everything in and turned on the machine.

Guess what?
No Sound

Ran
```
sudo apt-get update && sudo aptitude dist-upgrade
rebooted
```

No Sound

Ran
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
```

And just to be sure...
```
sudo apt-get update && sudo aptitude dist-upgrade
reboot
```

Sound

Had to reinstall fiesty 2 days ago because Partition Magic crashed my boot sector.  Unbelievable, but Windows 2000 refused to install, saying my disk is bad.  Ubuntu plowed right through.  Decided to run over Windows once and for all.  So now, I'm ***[COLOR="Magenta"]exclusively linux!!!.[/COLOR]***


bobland

---

### Post by BobLand on 2007-07-11
07/11/2007

Made changes to /etc/gnome/default.lists.  Defaulted SMPlayer to avi, mpg, & wav.  Would not default to wav - still defaults to totem.   Drat...

Rebooted to see if that helped.  Didn't.  Lost sound...again.

/etc/modules OK - no changes.

Ran the famous 4
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
sudo apt-get update && sudo aptitude dist-upgrade
rebooted
```

Sound back but stil wrong default on wav files.

---

### Post by expatCM on 2007-07-14
BobLand, you have not made a post for two days .... does this mean that you are now happy and have working sound all the time?

I have the same sound card and it is driving me to distraction.  I get lots of headaches now which go along the lines of the settings are all lost on reboot and the Master Sound in the system tray is always muted out on
reboot  (but is always set to IEC958 Centre for some reason).  I think the mic works now as long as I change the settings....

I appear to have followed a similar route to you in installing drivers and who knows what else.  There is only one difference, I have not reinstalled to try and get the card working properly.  Do you think this is the only solution remaining or did you do something else which you did not write in this thread?

---

### Post by BobLand on 2007-07-14
expat,
**Don't reinstall**.  I did that because of system crashes.  
Sometimes when I reboot the master sound reverts to IEC958.  When I change to alsa it works.  Sometimes I ignore it and still get normal sound.  
I'm assuming your driver is ca0106.  If not, what is it?

Can you send me the output of 
/etc/modules
/proc/asound/modules

And, I will assume
```
aplay -l
```
displays your driver as the FIRST driver, that is card 0, not card 1 with and intel chipset as card 0.

Since you are getting sound then
```
lspci -v
```
is displaying your sound card correctly.

Have you run the code in the post before yours?  That always works for me.

Let's review:
reboot - no sound
What's in /etc/modules?  It should only contain your driver and no others.
If you do see others, comment them out or delete them.

run
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
sudo apt-get update && sudo aptitude dist-upgrade
reboot
```

You should have sound.  
No?  
What are you doing to get it back?


So far, I have not added any programs that have broken sound.  That's why no new entries.  I'm sure this is not the last post I'll be writing...

bobland

---

### Post by bodhi.zazen on 2007-07-14
Bob:

You are doing awesome ;)

You could :

1. black list modules. This keep them from being loaded at boot.

[http://doc.gwos.org/index.php/Get_rid_of_useless_modules_loaded_at_boot](http://doc.gwos.org/index.php/Get_rid_of_useless_modules_loaded_at_boot)

I see you are removing more then your sound modules and I would ask why ? At any rate, make sure you are not using a module before you black list it.

Like fuse for example : [http://en.wikipedia.org/wiki/Filesystem_in_Userspace](http://en.wikipedia.org/wiki/Filesystem_in_Userspace)

So, research the modules before you inactivate them ;)

=====

Or 

2. You could set a default sound device 

```
sudo asoundconf list 
# This lists your sound cards


sudo asoundconf set-default-card <desired default card>
#This sets the default sound card for root (I tink this will set sound for your log in screen)

asoundconf set-default-card <desired default card>
#This sets the default sound card for you as a user (after log-in)
```

Have fun ;)

---

### Post by expatCM on 2007-07-14
Hi BobLand,

Thanks for your reply.   I have been to hell and back again with this one, saddened to see that I am not alone.

What happens for me is that when I start the system (cold or reboot) the system first comes to the login window.  It should sound a single drum to prompt data entry.  No sound. The system then loads and the startup sound is heard.  It comes at a very loud volume.  System loads no problem.  Skype loads and the skype sound is heard as the software registers.  So far so good.   The volume control in the system tray is always in the mute position on load and it is always IEC958.  It does not seem to do anything even if it is not muted so I do not worry.

Sound related programs generally sort of work.   XMMS works in that it will play sound but the volume control does not function.   MP3's are played over Totem by default and the volume control works.   

Audacity is very hit and miss, sometimes it will work and sometimes it will not.  This is either getting the mic to work or getting the sound to play back.  At this point Skype is also a no go ...  either there is a reported problem with the audio playback device or that works and there is no sound recorded from the mic.

Alsamixer helps.   I have to turn down the Analog Front to lower the overall volume.  Turn down the record for  Line in and Phone and turn the Mic up from zero.  I also change the Analog source from Line In to Mic, the Shared Mic / Line In from Line In to Mic.  Then I seem to have some better listening experience.  However, the settings are always lost on reboot.  It matters not whether I start as sudo alsamixer or alsamixer, the effect is the same.   From this however I suspect that something is not quite right and that is preventing the settings from being saved.  


To answer your questions .... yes it is ca0106.  I technically have on-board sound as well but I took it out in the BIOS (since it is defective).  I cannot see anything you have done that I have not.

cat /etc/modules

```

# /etc/modules: kernel modules to load at boot time.

#

# This file contains the names of kernel modules that should be loaded

# at boot time, one per line. Lines beginning with "#" are ignored.



ca0106

# fuse

# lp

# sbp2


```

 cat /proc/asound/modules
```


 0 snd_ca0106

```

aplay -l
```


**** List of PLAYBACK Hardware Devices ****

card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]

  Subdevices: 1/1

  Subdevice #0: subdevice #0


```
lspci -v

```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)

        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard

        Flags: bus master, fast devsel, latency 0

        Memory at f8000000 (32-bit, prefetchable) [size=64M]

        Capabilities: <access denied>



00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])

        Flags: bus master, 66MHz, fast devsel, latency 64

        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

        Memory behind bridge: fc900000-fe9fffff

        Prefetchable memory behind bridge: d7f00000-f7efffff



00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])

        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard

        Flags: bus master, medium devsel, latency 0, IRQ 16

        I/O ports at eec0 [size=32]



00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])

        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard

        Flags: bus master, medium devsel, latency 0, IRQ 17

        I/O ports at ef00 [size=32]



00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])

        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard

        Flags: bus master, medium devsel, latency 0, IRQ 18

        I/O ports at ef20 [size=32]



00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])

        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard

        Flags: bus master, medium devsel, latency 0, IRQ 16

        I/O ports at ef40 [size=32]



00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])

        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard

        Flags: bus master, medium devsel, latency 0, IRQ 19

        Memory at febffc00 (32-bit, non-prefetchable) [size=1K]

        Capabilities: <access denied>



00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])

        Flags: bus master, fast devsel, latency 0

        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64

        I/O behind bridge: 0000d000-0000dfff

        Memory behind bridge: fea00000-feafffff

        Prefetchable memory behind bridge: 50000000-500fffff



00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)

        Flags: bus master, medium devsel, latency 0



00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])

        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard

        Flags: bus master, medium devsel, latency 0, IRQ 18

        I/O ports at 01f0 [size=8]

        I/O ports at 03f4 [size=1]

        I/O ports at 0170 [size=8]

        I/O ports at 0374 [size=1]

        I/O ports at fc00 [size=16]

        Memory at 50100000 (32-bit, non-prefetchable) [size=1K]



00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])

        Subsystem: ASUSTeK Computer Inc. P4P800 SE Mainboard

        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18

        I/O ports at eff0 [size=8]

        I/O ports at efe4 [size=4]

        I/O ports at efa8 [size=8]

        I/O ports at efe0 [size=4]

        I/O ports at ef90 [size=16]



00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)

        Subsystem: ASUSTeK Computer Inc. P4P800 Mainboard

        Flags: medium devsel

        I/O ports at 0400 [size=32]



01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1) (prog-if 00 [VGA])

        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16

        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]

        Memory at e0000000 (32-bit, prefetchable) [size=256M]

        [virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]

        Capabilities: <access denied>



02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

        Subsystem: ASUSTeK Computer Inc. Unknown device 8026

        Flags: bus master, medium devsel, latency 64, IRQ 20

        I/O ports at d800 [size=256]

        Memory at feaffc00 (32-bit, non-prefetchable) [size=256]

        Capabilities: <access denied>



02:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10 [OHCI])

        Subsystem: Unknown device 1976:0314

        Flags: bus master, medium devsel, latency 64, IRQ 21

        Memory at feafe000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



02:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS

        Subsystem: Creative Labs Unknown device 100a

        Flags: bus master, medium devsel, latency 64, IRQ 20

        I/O ports at df80 [size=32]

        Capabilities: <access denied>



02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

        Subsystem: CNet Technology Inc ProG-2000L

        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22

        I/O ports at d400 [size=256]

        Memory at feaff400 (32-bit, non-prefetchable) [size=256]

        Expansion ROM at 50000000 [disabled] [size=128K]

        Capabilities: <access denied>




```

I am really thinking what on earth to do about this.  I live in a part of the world where it is Creative or nothing off the shelves and mail order is not for the feint of heart.  So I am thinking that perhaps my way forward will be to buy another motherboard with working on-board sound and in theory it will be problem solved.  Trouble is that I also have a Windows dual boot on this system and changing the board is going to make Windows throw up big time.  So I am pondering .....

---

### Post by BobLand on 2007-07-14
expat,
You're doing all the right things.  The only thing I can think of, and I wouldn't bet the farm on this one, is your sound card might be showing signs of declining old age.  I believe my card was bought for a computer 3 generations ago.  For my purposes, it's fine.  Gives me good sound on Half-Life2 but I don't know how much life is left in it.

Would you say your Windows sound is transparent, that you don't pay any attention to it because it works as expected?  If no, then I'd say the card is defective and needs replacement.  If yes, it would point to a conflict in fiesty.

Some options:
   - Backup everything to either a second hard disk or tar/zip files.  

   - Go [[COLOR="Red"]_here_[/COLOR]]("http://www.acronis.com/homecomputing/download/trueimage/") to get Acronis True Image 15 day trial.  I used this to copy my Windows 2000 to a different hard disk when I upgraded my boot disk.  Worked perfectly.  If you decide you like this program (I like it a lot!) then get the CD.  Don't download unless you immediately burn it to disk. (I'd stay about 1,000 miles away from Norton/Symantec).

   - Buy a new card locally, install it, and if it doesn't work, return it for a full refund only if your store allows this.

   - Reinstall fiesty after backing up everything.

   - Post more and be obnoxious if you have to.  Try beginners, general, hardware, multimedia, everywhere.  Eventually, someone might pop up with something different.

   - And of course, the new motherboard.

Try some of the above and keep me posted.  Your resolution would be valuable for someone else who runs into the same problem someday.

bobland

---

### Post by BobLand on 2007-07-14
Bodhi,
You may have supplied the missing key that I've been looking for - locking it all down.

Most of my recovery process was culled from the "Comprehensive Sound Problem Solutions Guide v0.5e"  ([http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)).  Basically, I am removing alsa base and utilities.  Along with that goes the gdm that's why it needs replacement.

Hopefully, the black listing will help reduce extra steps.

Only recently have I questioned what the actual doings are.  Often, when I loose sound, especially, on a large upgrade, the /etc/modules gets overwritten.  fuse is always there.  I always delete it since I haven't seen any anomalous behavior.  But that may indicate I haven't had the need for it.

I haven't been able to check out [http://doc.gwos.org/index.php/Get_ri...loaded_at_boot](http://doc.gwos.org/index.php/Get_ri...loaded_at_boot) as I can't seem to get a connection.  I'll keep trying throughout the day.

I want to thank you for this excellent tip!
bobland

---

### Post by expatCM on 2007-07-15
Hi BobLand,

The idea of buying another card and trying it and taking it back if it does not work will not succeed.    If you say Ubuntu Linux to the computer trade here they think it is a sandwich filling and you are really in need of a restaurant.  So after testing a card you take back they will put it on the only computer system they know which is an XP box and show you that the card works.  Since they sold you a working card the defect is your box which means no refund.

The last time I booted to Windows (which like you is also Windows 2000) I had to install the card (new card).  Installation was like falling off a log and of course it works properly and all the time.   I rarely boot to Windows now.

I discovered a new command today which you are supposed to use to save alsamixer settings.  It is - 

sudo alsactl store 0

but whilst the command apparently runs it actually has no effect at all.  The "0" at the end of the line may be increased to "1" if you have two sound cards and need to differentiate between the two.

I was just reviewing my settings and saw this line in describing the card

"Subsystem: Creative Labs Unknown device 100a"

I have not been able to find out what this means but if part of the card is not properly recognized then that could perhaps explain many things .....


To try and discover ideas / solutions I have been reading a lot of sound postings on three forums.  I come to a number of conclusions - 

1.  Sound support has a long way to go on Linux
2.  Many people have problems which they cannot fix.
3.  Many people offer basic help but do not know how to get to the guts of a problem.
4.  Quite a lot of sound posts are either unanswered or quickly passed over.
5.  Sound problems are really not for the beginner like me, but there should not be problems like this if Ubuntu (say) is to reach the mass market. In Windows you do not need even half a brain to install a sound driver, just click and go.
6.  Too many solutions need "if you know, fine, if you don't it is a pain to really find out".  There is a huge learning curve.  For example, saving the settings for alsamixer or even knowing what the individual settings mean.

Of course it is easy to point fingers and I am sure that many offer help when they have a clue.  It seems that major sound card vendors simply do not care about the Linux market, they could be a lot more cooperative in giving information but choose not to do so.  For them closed source gives them an effective oligopoly protecting their inflated product prices.

For me I guess it looks like a new motherboard (the cost is only slightly more than a sound card) but I really hate this as a solution since my sound card works, it just does not work properly with 7.04.   I shall wait a while.

---

### Post by BobLand on 2007-07-15
expat,
Your output of lspci -v
```
02:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
        *Subsystem: Creative Labs Unknown device 100a*
        Flags: bus master, medium devsel, [COLOR="Red"]latency 64,[/COLOR] IRQ 20
        I/O ports at df80 [size=32]
        Capabilities: <access denied>
```

Mine
```
02:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, [COLOR="Red"]latency 32[/COLOR], IRQ 21
        I/O ports at a400 [size=32]
        Capabilities: <access denied>
```

Difference in red.
Since we have different boxes with different hardwared/software I'm assuming the IRQ and I/O ports are box dependent and nothing to concern us.  As far as latency, perhaps, the same thing.  

Did you include the entire contents of aplay -l?  What I'm curious about is no listings for a sound chip.
Here's mine
```

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[I]card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
[/I]Note the last two entries. I know the IEC958 is a sound chip.  Not certain about the other.

I'm guessing we have the same motherboard - ASUSTeK so I'm thinking it's NOT the motherboard, especially since sound works in W2K.


How about the output of 
```
/etc/modprobe.d/alsa-base
```

Here's what mine looks like
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-i$
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modpro$
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -$

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/mo$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/mo$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -$

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-s$
# Prevent abnormal drivers from grabbing index 0
**[COLOR="Red"]options snd-ca0106 index=-1[/COLOR]**
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

A few posts ago, I was advised to add this command
```
asoundconf set-default-card <desired default card>
```
Where card was ca0106

When I just opened /etc/modprobe.d/alsa-base, the line highlighted in red was not there!  This would have killed sound if I rebooted!

I added the line back when I saw it was missing.  You can see how easily it is to corrupt sound in Ubuntu 7.04.

I hope this works!
bobland

---

### Post by Benthe1st on 2007-07-15
Hi everyone!

When i found this topic i was very happy, because i had the same problem as you. But i was able to fix it and now everything works fine (except tv-tuner card. So i would like to help you if you need. I have the same soundcard (Creative Labs Soundblaster Audigy LS) and a motherboard-integrated (Realtek AC'97). Of course i wanted to use my soundblaster, but i had the "reboot-problem". As i mentioned i fixed it. The big help for me was  ubuntu soundtroubleshooting: [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")
Just follow this, and u can usem ur soundcard nearly perfectly. If u have question just ask me.

---

### Post by Benthe1st on 2007-07-15
Hi everyone!

When i found this topic i was very happy, because i had the same problem as you. But i was able to fix it and now everything works fine (except tv-tuner card. So i would like to help you if you need. I have the same soundcard (Creative Labs Soundblaster Audigy LS) and a motherboard-integrated (Realtek AC'97). Of course i wanted to use my soundblaster, but i had the "reboot-problem". As i mentioned i fixed it. The big help for me was  ubuntu soundtroubleshooting: [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")
Just follow this, and u can usem ur soundcard nearly perfectly. If u have question just ask me.

---

### Post by BobLand on 2007-07-15
Most of this thread was based on this original thread called the "Comprehensive Sound Problem Guide v0.5e, found [[COLOR="Red"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound") which demonstrated how to set up a sound card.

The guide you mention is a word for word copy - probably a rewirte for that particular format.

What I'm attempting to do with this thread is show ways to fix sound when other programs break it, which is fairly common.

bobland

---

### Post by expatCM on 2007-07-16
Hi BobLand,

Yes, I agree with your comments, the reason why we are not showing identical output on the lspci -v is due to the different motherboard models.  I do not think it is a problem at all.  I am using an Asus P4P800-X.

You ask about the aplay -l and no listing for the sound chip.  What I have shown is the complete list BUT please note that I went into the BIOS and took out the on-board sound card in the settings so whilst the chip is physically there the BIOS is not going to detect it.

Now here is the curiosity....  if the IEC958 is a sound chip and I guess it is an on-board sound chip, why is it being detected if the on-board sound has been taken out in the BIOS.  Perhaps there is a setting which I have missed.

Here is cat /etc/modprobe.d/alsa-base
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

But I must say it looks very much like your own .....  but it is not quite the same....

You say that you used asoundconf to set the default card ....  me too ...  but I am not quite clear .... you then edited the /etc/modprobe.d/alsa-base to include the line options snd-ca0106 index=-1 or did you set a statement somewhere else?

---

### Post by BobLand on 2007-07-16
expat,
You are missing the crucial data in the /etc/modprobe.d/alsa-base.  Without the inclusion of your card, your sound will not work.  You MUST add that line in and reboot.  I believe that after the reboot you will have sound again!

Because you ran asoundconf it removed your sound card from alsa-base as it did to me, and therefore, no sound.  I've seen this thrown around in many posts.  All of the asoundxxx commands never worked for me and just threw me off course.

In fact, some posts will recommend removing .asound from the home directory if found.  For many, that resolves sound issues.  I'm pretty sure this worked on versions prior to 7.04.

bobland

---

### Post by Benthe1st on 2007-07-16
Hi expatCM !

About IEC958: Yes its an on-borad sound chip, in my case Realtek AC'97. 
Alsa-base:My problem was that ubuntu changes the primary sound-chip on every boot. And if isnt my soundblaster, theres no sound. So i edited my alsa-base file, as its written in the troubleshooting (link added in earlier post, or the 1 Bobland added, they are the same).
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe $

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
[COLOR="Red"]options snd-ca0106 index=0
options snd-intel8x0 index=1[/COLOR]

```
So i added to lines to it (in red). It makes my soundblaster card primary at every boot, and my on-borad chipset secondary. 
I also edited my /etc/modules file:
```
fuse
lp
[COLOR="Red"]snd-ca0106[/COLOR]
```
Adding a plus line here too.
Then i saved my alsa-mixer settings with [COLOR="Red"]sudo alsactl store 0[/COLOR] command. I rebooted before it, so my soundblaster became the primary (=0).
And now i have sund in every session. The only thing i havent been able to make work is the sound of tv-tuner card, its connected to an auxiliary port of my soundblaster, but i cant find it in alsamixer, so i cant turn it on. I hope ive helped.

---

### Post by BobLand on 2007-07-16
Benthe1st,
You do not have to include the sound chip in /etc/modprobe.d/alsa-base.  Indexing the ca0106 below 2 will work fine.  I've found that on my system indexing to 0 is not as reliable as indexing to 1.

Your code for /etc/modules
```
fuse
lp
snd-ca0106
```
will kill sound on my system.  I can't have anything other then ca0106 in /etc/modules.  If you do an upgrade or install a program that kills your sound, then try using just your driver in /etc/modules, commenting out or deleting the other entries.

bobland

---

### Post by BobLand on 2007-08-03
08/03/2007
The bizarreness never stops!

Last night I watched a few videos from different sources.  All worked as expected.  This morning I clicked on UPI to watch breaking news.  Video starts.  No sound.  Checked a few sound programs, still no sound.

Ran the purge routine with updates.
No sound.

Checked /etc/modules.  OK
Checked /etc/modprobe.d/alsa-base.  Not OK.  File was overwritten.
I realized that this file is overwritten randomly.  Since I tend to lose sound fairly often, I usually just run the purge/restore sequence and sound comes back on after reboot.

When sound does not come back I check /etc/modules and /etc/modprobe.d/alsa-base.  Most of the time /etc/modprobe.d/alsa-base is not overwritten.  Perhaps, with the past few system updates this has changed and there is now a need to modify this module after running the purge/restore sequence.  

On my system /etc/modprobe.d/alsa-base would look like this (just the pertinent code)
Before overwrite
```
# autoloader aliases...

# Prevent abnormal drivers from grabbing index 0
[COLOR="Red"]options snd-ca0106 index=-1[/COLOR]
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```
Note the line in red.  That's my driver.

After overwrite
```
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```
Note the absence of the red line.  Without it there will be no sound.

After making the modification and rebooting, no sound.
Now what?!

Tested system mute - off.

Tried
```
alsamixer
```

much to my surprise I get this error
```
alsamixer: function snd_ctl_open failed for default: No such device
```

go to synaptice and install gnome-alsamixer.  After reboot, no sound, no alsa-mixer.
go back to [[COLOR="Blue"]_Comprehensive Sound Problem Solution_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound")

run this code
```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
sudo dpkg-reconfigure alsa-source

``` hoping it will restore alsa-mixer
I select my driver
```
ca0106
```
No errors reported
Run
```
sudo module-assistant a-i   alsa-source
```
compile stops.  zillion errors.  exit.
Just for heck, I reboot.

Sound!
Strangely, this time I get bongos on login but no theme on password.  Check UPI.  Sound on video.  Check other sound producting modules.  All work.
WTF?

For this reason, I will not install fiesty on my wife's computer.  It's bad enough wasting 2 hours trying to get my sound to work again, including this documentation.  Don't want to redouble this effort.  If I recommend this to a non technical type then I'll be in the tech support hell.  No thanks!
[SIZE="2"]
[FONT="Comic Sans MS"]Hope gutsy doesn't turn into pukey[/FONT][/SIZE]

bobland

---

### Post by BobLand on 2007-08-08
08/08/2007
I'm sure there is a bug lurking between partitioning and sound.  I deleted some old ntfs partitions on a drive I used for W2K backups.  Since no trace of Windows exists on my system, I deleted these partitions.

I created a second, larger swap of 5 GB and a 25 GB logical.  No errors detected.  Partition was OK.  Since the partition was named 'disk' I decided to change it to 'lfs'.  There was no entry in fstab.  In mtab the entry was there.  I copied the entry and changed /media/disk to /media/lfs.  After saving the file I got this:

```

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'ca0106'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'ca0106'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'ca0106'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'ca0106'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'ca0106'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'ca0106'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'ca0106'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
```

Of course, sound was dead...AGAIN!!!!  Had this problem when using ntfs-config.  Checked the usual suspects.  Everthing was normal and in place.  The errors mostly say "No such device," but the device is there.

Ran the usual lines of code.  Rebooted.  Sound OK
Tried editing /etc/mtab and the system vomited again but this time sound did not go away.  Don't know why editing mtab would make alsa-base throw up.

bobland

---

### Post by paulroberts on 2007-08-08
Does anyone have a SIMPLE solution to this?

I installed 7.04 last week, sound worked no problem. Then for some reason a few days later it has stopped. I think it might have been after I downloaded a bunch of updates.

I'm using an Audigy card and the various tests I have run (mentioned in this post) show that the system recognises it and has all the drivers loaded, none of the outputs are muted in the mixer, so why has it stopped working? :-(

Is there a simple fix that doesn't involve wading through pages of posts? :-)

Cheers,

Paul

---

### Post by BobLand on 2007-08-09
Paul,
Have you run through every procedure in this thread?  Seems to me that some computers with the Audigy card simply don't have sound stability.  Not only you and me, but many others too.

I use this thread as a journal to document the possible program that broke sound and the possible fixes.  So far, I've been able to get sound back, but each time the process gets longer and more complicated.

I'm pretty sure I've either created or discovered a bug because I will get the alsa "dump" when looking at /etc/modprobe.d/alsa-base and when running partitioning software (GParted).

Hopefully, this may be addressed in the next release, but I don't have much confidence that will happen.

bobland

---

### Post by BobLand on 2007-08-09
08/09/2007
While killing some time with StumbleUpon, I noticed a quick flash of the browser and a reduced browser window literally sinking below the the lower panel.  I was able to catch the title as "Embedded Java."  WTF?

No sound.

Ran the purge/routines.  Restored /etc/modprobe.d/alsa-base then rebooted.
No sound.

Ran
```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
sudo dpkg-reconfigure alsa-source
```

Ran
```
sudo module-assistant a-i alsa-source
```
At the window that requested to run debug I selected no.
After a minute or 2 the error window opened (see attachment)
I selected Continue.
The window closed and brought me back to the command line.

Rebooted.
Heard the bongos but no theme.  Don't know if the theme got blasted or something else is bollixed.

bobland

---

### Post by paulroberts on 2007-08-16
Have to say I don't really understand much of this but this is some of my output:

```
paul@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 4 [SB0610]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy2 [Audigy 4 [SB0610]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 4 [SB0610]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
paul@ubuntu:~$ 

```

My speakers are plugged into the Audigy card and it did work at first. It did seem to break when I downloaded some updates but so many came down I don't know what broke it. :-(

```
paul@ubuntu:~$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
paul@ubuntu:~$
``` 

```
paul@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
paul@ubuntu:~$ 
```

I've also tried:

```
paul@ubuntu:~$ sudo asoundconf list
Names of available sound cards:
Intel
Audigy2
paul@ubuntu:~$ sudo asoundconf set-default-card Audigy2
paul@ubuntu:~$ asoundconf set-default-card Audigy2

```

No luck so far, on the verge of giving up with this. :-(

---

### Post by punkrokk on 2007-08-16
I found [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108392/comments/31") after doing some googling. It says if you hibernate you will lose sound. And I HAD hibernated.

The fix is to suspend and resume and viola! My sound is back! I have a thinkpad t60 as did the guy who posted my link, but maybe this will help someone else!

I sure wish I knew what command suspend resume ran to get my sound back!

---

### Post by BobLand on 2007-08-29
Paul,
I would try adding your driver to the beginning of the options section in /etc/modprobe.d/alsa-base
```
# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
[COLOR="Red"]options snd-emu10k1 index=-1[/COLOR]
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

In /etc/modules, you are not listing your driver at all.  I would also change your /etc/modules to just this
```
emu10k1
```

Sometimes, an update will run something like apt-get update.  This will change your /etc/modprobe.d/alsa-base to its original condition, i.e., your entry for your sound card will disappear and you will lose sound.  This will also randomly happen to /etc/modules, or /etc/moudles will have other entries inserted.  I've found that these entries create a conflict and are best removed.

After you make the above changes, reboot.  If you still don't get sound then run through all of the  procedures mentioned in this thread but do the above last as running any type of upgrade will revert /etc/modprobe.d/alsa-base to the original.

Let me know how this works.
bobland

---

### Post by BobLand on 2007-09-02
09/02/2007
My last post on this topic.  Downloaded linux-headers update, rebooted, sound failed.  Ran thru the usual stuff and got sound back.

What's the point?  The slightest thing will break sound.  This is a given so more blah-blah-blah serves no purpose.

Hopefully, this thread will serve as a vehicle for others to help solve their sound problems and bring up issues not discussed to date.

bobland

---

### Post by BobLand on 2007-09-29
09-29-2007
The last update killed sound.  During a past upgrade of Ubuntu or some other file, alsamixer vanished
```
alsamixer: function snd_ctl_open failed for default: No such device
``` 

so I ran this code, which in an earlier post, restored sound but not alsamixer.  I could not remember the sequence of steps so it didn't restore sound.
```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
sudo dpkg-reconfigure alsa-source
```
I've been running for a few months without alsamixer not noticing any problems other than a random "Max Headroom" stutter in YouTube.

Then, went back to what works...most of the time.
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
sudo apt-get update && sudo aptitude dist-upgrade

```

/etc/modules has remained constant but I check it anyway
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ca0106
```If other entries sneak in I delete them.


Modified /etc/modprobe.d/alsa-base because every time this code is run
```
sudo apt-get update && sudo aptitude dist-upgrade
```
the file is overwritten with the original, wiping out my driver addition.

Here's what /etc/modprobe.d/alsa-base should look like before rebooting.  In this case I've added my driver, ca0106.
```
[COLOR="Red"]options snd-ca0106 index=-1[/COLOR]
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
```

Now, reboot!
Ugh.   no sound.

Rather then even think of something else, I rebooted again.
What do you know?  Sound!  This was the reason why I would run the above code, reboot and sound wouldn't work sometimes.  

The answer:  reboot, reboot.

I surely hope gory gibbon fixes this and other sound/video problems.  After each upgrade my system gets slower and slower.  If this continues I"ll be looking for a different distro.

Hoping this is the last post...
bobland

---

