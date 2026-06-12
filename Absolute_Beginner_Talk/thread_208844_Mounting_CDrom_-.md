---
title: "Mounting CDrom -"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Dazaablack on 2006-07-04
I have no idea what I have done but its not working anymore. IT was working, Then it just stopped like 5 mins later.

daz@server:/media/cdrom0$ sudo mount -t iso9660 /dev/cdrom /media/cdrom0/
mount: block device /dev/cdrom is write-protected, mounting read-only
daz@server:/media/cdrom0$ ls
daz@server:/media/cdrom0$ ls
daz@server:/media/cdrom0$ WTF
bash: WTF: command not found

I tried this too
sudo mount -t iso9660 /dev/hde /media/cdrom0

It was working before.

heres my /etc/fstab/
mount -a doesnt work

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hde        /media/cdrom0   udf,iso9660 user,noauto     0       0

there are pages of this in dmesg
[4294801.871000] hde: tray open
[4294801.871000] end_request: I/O error, dev hde, sector 20
[4294801.872000] hde: tray open
[4294801.872000] end_request: I/O error, dev hde, sector 128
[4294801.872000] hde: tray open
[4294801.872000] end_request: I/O error, dev hde, sector 132
[4294801.873000] hde: tray open
[4294801.873000] end_request: I/O error, dev hde, sector 128
blah blah blah 

then this
[4294993.174000] hde: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[4294995.178000] hde: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[4294995.182000] hde: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[4294997.186000] hde: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[4294997.190000] hde: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00

I have no idea whats going on,

did my cdrom drive just die or something?

---

### Post by Dazaablack on 2006-07-04
Forget it guys,

My cdrom just started working after I replied to someone elses post.
No idea how/what or why.
It must be on the way out.

---

