---
title: "Multiple questions.Require help."
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Atreides2k on 2008-03-24
Greetings. I have recently installed Ubuntu 7.10 and i have met the following problems.

1. I can't see my other hard disk/partitions. It's a 320 hard drive on which i have installed Windows Vista a while ago, and a 80GB Hard drive with the new Ubuntu. I can only access/see the 80 GB one from Ubuntu, but if i restart and boot with Vista, there is no problem. The result for "sudo fdisk -l" is:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd41fd41

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276       38912   302319202+   f  W95 Ext'd (LBA)
/dev/sda5            1276       19760   148480731    7  HPFS/NTFS
/dev/sda6           19761       38912   153838408+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf393f393

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1275    10241406   82  Linux swap / Solaris
/dev/hdb2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/hdb5            1276        9728    67898691   83  Linux

2. This is my 3rd reinstall because each time after i installed Ubuntu, and enabled the Ati Driver Ubuntu failed to load, and got stuck at a black screen. I installed all available updates now and the restricted driver window didn't pop up anymore. Maybe it fixed itself, anyway, ideeas are welcome.

3. Can't install yahoo messenger (and yes i want to use this one, not pidgin). After i download the *.deb file i get the error "Error: Dependancy is not satisfiable: libssl0.9.6" in the installation window. Any ideeas? Thanks in advance.

---

### Post by Fixman on 2008-03-24
> **Atreides2k said:**
> Greetings. I have recently installed Ubuntu 7.10 and i have met the following problems.

1. I can't see my other hard disk/partitions. It's a 320 hard drive on which i have installed Windows Vista a while ago, and a 80GB Hard drive with the new Ubuntu. I can only access/see the 80 GB one from Ubuntu, but if i restart and boot with Vista, there is no problem. The result for "sudo fdisk -l" is:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd41fd41

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276       38912   302319202+   f  W95 Ext'd (LBA)
/dev/sda5            1276       19760   148480731    7  HPFS/NTFS
/dev/sda6           19761       38912   153838408+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf393f393

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1275    10241406   82  Linux swap / Solaris
/dev/hdb2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/hdb5            1276        9728    67898691   83  Linux

2. This is my 3rd reinstall because each time after i installed Ubuntu, and enabled the Ati Driver Ubuntu failed to load, and got stuck at a black screen. I installed all available updates now and the restricted driver window didn't pop up anymore. Maybe it fixed itself, anyway, ideeas are welcome.

3. Can't install yahoo messenger (and yes i want to use this one, not pidgin). After i download the *.deb file i get the error "Error: Dependancy is not satisfiable: libssl0.9.6" in the installation window. Any ideeas? Thanks in advance.


1)
> 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd41fd41

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276       38912   302319202+   f  W95 Ext'd (LBA)
/dev/sda5            1276       19760   148480731    7  HPFS/NTFS
/dev/sda6           19761       38912   153838408+   7  HPFS/NTFS


That is the Vista one

2) Really can't tell you

3) ```
sudo aptitude install libssl0.9.8
```

---

### Post by Atreides2k on 2008-03-24
i know that that is the vista one, my question is, how can i see the drives in "places" or anywhere. i can't access them from ubuntu :|

and i have written sudo aptitude install libssl0.9.8 and still, i get the same error :|

---

### Post by TeoBigusGeekus on 2008-03-24
Have you installed ntfs-3g?

EDIT: As well as ntfs-config?

---

### Post by Atreides2k on 2008-03-24
i guess not, how do i do that?

---

### Post by TeoBigusGeekus on 2008-03-24
System -> Administration -> Synaptic
Do a search for ntfs and mark ntfs-3g and ntfs-config for installation - then click apply.

---

### Post by Het Irv on 2008-03-24
[COLOR="Silver"]> **Atreides2k said:**
> 
3. Can't install yahoo messenger (and yes i want to use this one, not pidgin). After i download the *.deb file i get the error "Error: Dependancy is not satisfiable: libssl0.9.6" in the installation window. Any ideeas? Thanks in advance.

Shouldn't that be
sudo aptitude install libssl0.9.6
Unless 0.9.8 is not a typo, and in fact a newer version[/COLOR]
 
Have you tried looking for it in Synaptic Package Manager?

Edit: sorry 0.9.8 is the newest, have you tried installing from Synaptic?

---

### Post by Atreides2k on 2008-03-24
did that, ntfs 3g was already installed, i installed the config, and still i can't see the other partitions, or does it need a restart first?

and how do i fix the problem i have with yahoo messenger?

---

### Post by TeoBigusGeekus on 2008-03-24
Do a restart.
After that go to 
Applications->System tools->Ntfs configuraton tool
Tick all boxes press ok and then post us the result of 
```
ls /media
```

---

### Post by Atreides2k on 2008-03-24
cdrom  cdrom0  floppy  floppy0  sda1  sda5  sda6

after i ticked boxes i had an error that said some error encountered while trying to mount sda1,5,6 and if i have windows to disconnect the hardware, if i don't then i could use "force" at my own responsability. still can't see the drives btw

---

### Post by TeoBigusGeekus on 2008-03-24
Sda1,5 and 6 are your vista drives.
Type
```
ls /media/sda1
```

---

### Post by Atreides2k on 2008-03-24
> **Het Irv said:**
> [COLOR="Silver"]

Shouldn't that be
sudo aptitude install libssl0.9.6
Unless 0.9.8 is not a typo, and in fact a newer version[/COLOR]
 
Have you tried looking for it in Synaptic Package Manager?

Edit: sorry 0.9.8 is the newest, have you tried installing from Synaptic?

yes i did, it doesen't find it in synaptic..so what the hell should i do :| 

i wrote ls  /media/sdal nothing happeaned, i didn't do a restart either, but still, no drives

later edit: i copied and pasted the command from here, but when i write ls /media/sdal it sais no such file or dir.

---

### Post by Het Irv on 2008-03-24
Search for 0.9.8, I found it in mine, and it was already installed, but it may have been installed by another program.

---

### Post by TeoBigusGeekus on 2008-03-24
```
ls /media/sda1
```
That's SDA1 not L

---

### Post by Atreides2k on 2008-03-24
> **Het Irv said:**
> Search for 0.9.8, I found it in mine, and it was already installed, but it may have been installed by another program.

i did, they are both installed, BUT the error is with 0.9.6 not 0.9.8 :(

---

### Post by Atreides2k on 2008-03-24
> **TeoBigusGeekus said:**
> ```
ls /media/sda1
```
That's SDA1 not L

my bad, didn't notice, still i press enter, nothing happeans, it just goes down one line waiting for me to write something else. should i restart?

---

### Post by TeoBigusGeekus on 2008-03-24
Why not?

---

### Post by Het Irv on 2008-03-24
The Yahoo client may not recognize 0.9.8 as an updated version of 0.9.6. (old script that hasn't been maintained?).  Check to make sure you have the newest version of Yahoo's client.

---

### Post by Atreides2k on 2008-03-24
i downloaded from the official website under /unix dir so it should be the latest...i will however try with older versions see if it works, doing that restart now..hope i get to see my other drives :| funny thing is, i reinstalled ubuntu 4 times today, and i could see the drives on my first install...i didn't mess with the partitions or anything, followed the exact same steps..

---

### Post by Atreides2k on 2008-03-24
yup, nothing changed in "places" and "computer" i can only see floppy 1 the cd/dvd rom and "filesystem" witch seems to be the place where i installed ubuntu on

---

### Post by TeoBigusGeekus on 2008-03-24
Type again

ls /media

---

### Post by Atreides2k on 2008-03-24
cdrom  cdrom0  floppy  floppy0  sda1  sda5  sda6 :|

---

### Post by TeoBigusGeekus on 2008-03-24
It might be that you need to mount these drives. Try
```
sudo mount /media/sda1
```

---

### Post by Atreides2k on 2008-03-24
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0




hmmm...could it be because i restarted from the button while i was in windows or what? :| what to do anyway?

---

### Post by TeoBigusGeekus on 2008-03-24
Yeah, try that. Boot to windows, shut down properly and then boot again to Ubuntu and try to mount your sda1 drive.

---

### Post by Atreides2k on 2008-03-24
yes...it worked...christ, would have never thought of that...damn microsoft sabotage ^_^ thanks a lot for your help

quick question. is there any way to disable the password input for every important operation i do? since  i am the only one who uses this pc.

---

### Post by TeoBigusGeekus on 2008-03-24
You can create a password for root and always log in as root _BUT_
you should avoid doing so even if it pisses you off: it's far too dangerous for your system...

---

