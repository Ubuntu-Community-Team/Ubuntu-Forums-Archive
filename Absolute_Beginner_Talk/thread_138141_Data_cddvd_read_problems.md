---
title: "Data cd/dvd read problems"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-03-01
I have recently boght a new LG dvdrw drive and it has been working fine for me writing and reading cds and dvds. however, whenever i write anything like say a few series of scrubs onto a dvd on my friends computer, who uses winxp, ubuntu doesnt seem to be able to read them. the title comes up when the cd dive is mounted but there is no data visible. if i open K3b and right clik the drive in there i can view the disc data which reveals theres is for example one data track written and gives me the size of it, but the file browser doesnt see it. and whats more i cant get to the files through K3b either even though it knows there is something there.

most of the disks i have been trying to read have been written in nero burning rom and deep burner on winxp and win2kpro, at the moment i have had to set up an xp partition and i`m ripping the files in there and then importing them to my ubuntu partition, but i wish to erase windows in the next week or so as it has been nothing but trouble since day 1 (which was about 8 days ago) and probably have a tinker with red hat.

i digress, anyhoo, if any of you lovely people can shed any light on this situation can u please let me know what`s up...

thanks 

DK

---

### Post by Pragmatist on 2006-03-01
What happens if you mount the disk using ```
mount
``` in a terminal?

If it is automounting, try just typing ```
mount
``` with nothing else.  This will show what devices are currently mounted and will provide other useful info such as what filesystem is assumed for that device.  Post the output of just typing mount at a prompt.

---

### Post by richbarna on 2006-04-30
Hi Pragmatist, Sorry to butt-in DiscoKiller, but i,ve been having the same problem. The main problem being that I have a lot of stuff saved on DVD, backed up files etc, and it is all stored in Windows Folders. With linux, I can't get access to the data. If I burn music, vids etc fine. But as soon as the stuff gets put in a folder, no go.

I typed mount and got this :-
> ****@dhcppc0:~$ mount
/dev/hdc2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hdd1 on /media/music type vfat (rw,iocharset=utf8,umask=000)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=****)
****@dhcppc0:~$


This being the interesting part :-
> /dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=****)

---

### Post by richbarna on 2006-04-30
Hi again,
It's definitely a DVD ROM problem, I just put an old backup CD in the CD ROM and that reads fine.

---

