---
title: "Installing Limewire"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by patanjali on 2006-04-23
I have recently tried to mount my XP partition from Ubuntu and failed miserably.  When I try and do this from terminal I get:

patanjali@Sisyphus:/$ sudo mount xp
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

patanjali@Sisyphus:/$  dmesg | tail
[4294722.445000] Bluetooth: Core ver 2.7
[4294722.445000] NET: Registered protocol family 31
[4294722.445000] Bluetooth: HCI device and connection manager initialized
[4294722.445000] Bluetooth: HCI socket layer initialized
[4294722.464000] Bluetooth: L2CAP ver 2.7
[4294722.464000] Bluetooth: L2CAP socket layer initialized
[4294722.504000] Bluetooth: RFCOMM ver 1.5
[4294722.504000] Bluetooth: RFCOMM socket layer initialized
[4294722.504000] Bluetooth: RFCOMM TTY layer initialized
[4294863.535000] NTFS-fs error (device hda1): parse_options(): [COLOR="Red"]Unrecognized mount option nis.[/COLOR]

How can this be when I have not specified "mount option nis"?  The red highlight is mine as this seems to be the problem.

Patanjali  ](*,)

---

### Post by Nikusan on 2006-04-23
[QUOTE=patanjali]I have recently tried to mount my XP partition from Ubuntu and failed miserably.  When I try and do this from terminal I get:

patanjali@Sisyphus:/$ sudo mount xp
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

patanjali@Sisyphus:/$  dmesg | tail
[4294722.445000] Bluetooth: Core ver 2.7
[4294722.445000] NET: Registered protocol family 31
[4294722.445000] Bluetooth: HCI device and connection manager initialized
[4294722.445000] Bluetooth: HCI socket layer initialized
[4294722.464000] Bluetooth: L2CAP ver 2.7
[4294722.464000] Bluetooth: L2CAP socket layer initialized
[4294722.504000] Bluetooth: RFCOMM ver 1.5
[4294722.504000] Bluetooth: RFCOMM socket layer initialized
[4294722.504000] Bluetooth: RFCOMM TTY layer initialized
[4294863.535000] NTFS-fs error (device hda1): parse_options(): [COLOR="Red"]Unrecognized mount option nis.[/COLOR]

How can this be when I have not specified "mount option nis"?  The red highlight is mine as this seems to be the problem.

Patanjali  ](*,)[/QUOTE]

Installing Limewire? Your title is confusing :rolleyes: 
Try something like this:

```

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows -t ntfs -o umask=0222

```

You will find more instructions in yelp under the heading Mounting Windows Partitions or something like that. Hope this helps.

---

### Post by patanjali on 2006-04-24
I put your code into terminal and it worked.  Thanks a lot.  Can I remount this to a different place than /media, for instance root directory?

I presume the command would be
" sudo mount /dev/hda1 /windows -t ntfs -o umask=0222

Patanjali

---

### Post by jazzyt on 2006-04-24
[QUOTE=patanjali]I put your code into terminal and it worked.  Thanks a lot.  Can I remount this to a different place than /media, for instance root directory?

I presume the command would be
" sudo mount /dev/hda1 /windows -t ntfs -o umask=0222

Patanjali[/QUOTE]

Yes you can, just do a 
*mkdir /windows *
beforehand...
The original poster used /media/windows as an example of where you would want limewire.

---

### Post by 2late on 2006-04-25
hi there!

i used this and it worked, thanks!
i want it to autoload when i start ubuntu!
please show me how!

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows -t ntfs -o umask=0222

---

### Post by Nikusan on 2006-04-25
[QUOTE=2late]hi there!

i used this and it worked, thanks!
i want it to autoload when i start ubuntu!
please show me how!

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows -t ntfs -o umask=0222[/QUOTE]

You need to edit your fstab file. To do this:

```
sudo gedit /etc/fstab
```

You'll need to add a line to the bottom that looks something like this:
   
/dev/hda1	/media/windows  ntfs    user,umask=0222 	0	0

---

