---
title: "cdrom mount problem and 'lost interrupt'"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by anaxolotl on 2007-01-21
ugh.  i've read every single post in these forums with the words "cdrom mount" in it and still nothing.

a couple days ago i took my new laptop (Gateway mx6920), did some partitioning and installed 6.10 from a cd.  as i'm slowly getting everything working i finally ran into a problem that i haven't been able to fix by extensive googling.  

if i put a cd/dvd in after i boot into ubuntu, the cd doesn't auto mount of the system.  if i go into Computers and try and mount the drive by right clicking on it, nothing seems to happen.  if i double click on it it tells me it is accessing the drive and nothing happens (note, the windows os on this same machine has no problems reading cds/dvds)  i've also tried multiple discs of various types (audio cd, video dvd, data dvd, data cd, etc) 

my fstab has the pretty standard line:
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

and if i run dmesg | grep 'hda' i'll get:
[17179571.956000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179572.696000] hda: PHILIPS DVD+/-RW SDVD8820, ATAPI CD/DVD-ROM drive
[17179573.388000] hda: ATAPI 63X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179633.396000] hda: lost interrupt
[17179725.132000] hda: lost interrupt

(the lost interrupt lines seem to come every time i attempt to mount)

finally from a diagnostic command i saw somewhere on here:
              *-cdrom
                   description: DVD writer
                   product: PHILIPS DVD+/-RW SDVD8820
                   vendor: Philips
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: AX03
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
 dvd dvd-r
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hda

if anyone can help me i would really appreciate it...

---

### Post by ajmorris on 2007-01-21
you didn't mention trying to maually mount it through a command line. Maybe try that, also try with the various options that the mount command has.

---

### Post by anaxolotl on 2007-01-21
after inserting a DVD of files i see:
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/sda6 on /home type ext3 (rw)
/dev/sda2 on /media/sda2 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda7 on /shared type vfat (rw,utf8,umask=007,gid=46)
/dev/sda1 on /windows type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

so it is still not automounting but...

if i type mount /media/cdrom
i get:
mount: block device /dev/hda is write-protected, mounting read-only

and now mount includes the line
/dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=mattie)

and i can access the files via the command line but i still cannot see the CD in the File Browser.  Also, if i try and mount it now within file browser it tells me the resource is busy.

Finally, ejecting no longer works by hitting the CDROM button or typing
/media/cdrom$ sudo eject /media/cdrom
Password:
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/media/cdrom0' failed

so the disc is stuck in there until i restart and i still cannot play audio or movie cds in X at all.

any other ideas?

---

### Post by b_pudliner on 2007-01-28
I have been experiencing very much the same problem that you have been.  I have exactly the same CD/DVD drive on a new Gateway MX6960 laptop.  Instead of Ubuntu, I just installed Fedore Core 6.  

Data CDs will generally not auto mount.  When I manually mount them, I get the 'hda: lost interrupt' message.  I have no problem accessing the CDs once they've been mounted.  Occasionally, if I mount it by hand and then unmount it, eject the CD and put it back in, the CD will auto mount.

When I try to play audio CDs I get random bad behavior.  Sometimes nothing will happen until I try to eject the CD and then the CD player will pop up.  Sometimes the machine will just lock up and the CD drive will spin like there is no tomorrow.  The messages file spits out the following info:

Jan 28 03:47:23 localhost kernel: hda: lost interrupt
Jan 28 03:47:29 localhost kernel: hda: DMA timeout retry
Jan 28 03:47:29 localhost kernel: hda: timeout waiting for DMA
Jan 28 03:47:34 localhost kernel: hda: status timeout: status=0xd0 { Busy }
Jan 28 03:47:34 localhost kernel: ide: failed opcode was: unknown
Jan 28 03:47:34 localhost kernel: hda: drive not ready for command
Jan 28 03:47:38 localhost kernel: BUG: soft lockup detected on CPU#1!
Jan 28 03:47:38 localhost kernel:  [<c0405018>] dump_trace+0x69/0x1b6
Jan 28 03:47:38 localhost kernel:  [<c040517d>] show_trace_log_lvl+0x18/0x2c
Jan 28 03:47:38 localhost kernel:  [<c0405778>] show_trace+0xf/0x11
Jan 28 03:47:38 localhost kernel:  [<c0405875>] dump_stack+0x15/0x17
Jan 28 03:47:38 localhost kernel:  [<c04522c5>] softlockup_tick+0xad/0xc4
Jan 28 03:47:38 localhost kernel:  [<c0430d8f>] update_process_times+0x39/0x5c
Jan 28 03:47:38 localhost kernel:  [<c0419f5a>] smp_apic_timer_interrupt+0x95/0xb3
Jan 28 03:49:59 localhost kernel:  [<c0404a57>] apic_timer_interrupt+0x1f/0x24
Jan 28 03:49:59 localhost kernel:  [<c05747a3>] ide_inb+0x3/0x7
Jan 28 03:49:59 localhost kernel:  [<c05757bc>] ide_wait_stat+0x98/0xf5
Jan 28 03:49:59 localhost kernel:  [<c0573981>] ide_do_request+0x3ff/0x8db
Jan 28 03:49:59 localhost kernel:  [<c0574608>] ide_timer_expiry+0x259/0x26e
Jan 28 03:49:59 localhost kernel:  [<c0430cef>] run_timer_softirq+0x105/0x16c
Jan 28 03:49:59 localhost kernel:  [<c042c041>] __do_softirq+0x5a/0xbb
Jan 28 03:49:59 localhost kernel:  [<c0406435>] do_softirq+0x55/0xb5
Jan 28 03:49:59 localhost kernel:  =======================
Jan 28 03:49:59 localhost kernel: hda: status timeout: status=0xd0 { Busy }
Jan 28 03:49:59 localhost kernel: ide: failed opcode was: unknown
Jan 28 03:49:59 localhost kernel: hda: drive not ready for command
Jan 28 03:49:59 localhost kernel: hda: status timeout: status=0xd0 { Busy }
Jan 28 03:49:59 localhost kernel: ide: failed opcode was: unknown
Jan 28 03:49:59 localhost kernel: hda: drive not ready for command
Jan 28 03:49:59 localhost kernel: hda: status timeout: status=0xd0 { Busy }

I can't help thinking that we are encountering a similiar problem.  Perhaps it is something wrong with this specific driver or just faulty hardware.  Anyway, I am sorry that I cannot provide anything more than company for your misery.   If anyone has ideas, I would love to hear them.  Thanks.

---

