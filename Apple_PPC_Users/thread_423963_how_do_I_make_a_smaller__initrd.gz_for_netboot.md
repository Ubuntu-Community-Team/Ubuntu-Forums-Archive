---
title: "how do I make a smaller  initrd.gz for netboot?"
date: 2007-04-26
forum: Apple PPC Users
---

### Post by tonyr on 2007-04-26
There is a long standing issue with tftp transfers of files bigger than about 6.1MB during netboot. 
It doesn't work.   The failure appears during netboot as someting like 'ramdisk load failure'.  There are posts about this in several places, and a bug at launchpad.  I seem to recall one post in which the writer said he had uncompressed the (cpio) initrd.gz, removed some unecessary drivers
and re-cpio'd an gzipped it.

I tried that without success, but I think I didn't do everything required.  I removed the actual driver
files, but I think that maybe there is some configuration information (actual config files, files that list modules) that I missed.

Does anyone know how to do this, or have a pointer to more info about how to do this?

- tony

---

### Post by tonyr on 2007-04-28
Maybe, someday, five thousand years from now, aliens digging through the remains of human 
civilizations will be interested in this information, so I'll leave it lying around here.

To make initrd.gz smaller, using a hint from a post out there whose location I neglected to
save, I took the following steps:
[LIST=1]
[*] Become root (sudo -s)
[*]Extract the contents of initrd.gz with gunzip and cpio into a directory, say, initrd_dir
[LIST]
[*]**gunzip initrd.gz ; mkdir initrd_dir ; cd initrd_dir ; cpio -i < ../initrd**
[/LIST]
[*]Remove all unnecessary network drivers from lib/modules/2.6.20-15-powerpc/kernel/drivers/net .  I sort of guessed at what was 'unnecessary'.  I left the airport driver and everything starting with 'sun', since most modern Macs use the sungem interface
[*]Remove all references to the removed driver files from the modules.<whatever> files in lib/modules/2.6.20-15-powerpc 
[*]Recreate the initrd.gz file with cpio and gzip
[LIST]
[*]**cd initrd_dir ; find . -depth -print | cpio -oc > ../newinitrd ; cd .. ; gzip newinitrd**
[/LIST]
[/LIST]

The resulting newinitrd.gz file was something over 6200000 bytes, which is apparently small 
enough for **tftp** to swallow.  I moved newinitrd.gz to initrd.gz in the tftp server directory

That was not all of the story, however.  It still didn't work.  Persevere, dear reader.

The netinstall process got into **vmlinux** startup and died trying to mount the initramfs
(initrd.gz), which it didn't think was anything recognizeable.  

And here is why:

Through **Dapper**, I believe,  **initrd** was constructed as a **cramfs** filesystem. 
Beginning with **Edgy**, **initrd** became a **cpio** archive.   The powerpc versions
of netinstall files didn't make the transition, however (maybe one of those issues 
contributing to powerpc being relegated to the **ports** pile).   **cramfs** versions of 
initrd look something like  the name **initrd.img**.   **cpio** versions of **initrd** look 
something like the name **initrd.gz**.  Somewhere in the netboot version of **vmlinux**,
I guess, is the expectation that **initrd** will be exactly one or the other form.  The **initrd** 
file is specified in **yaboot.conf**.  In the **Dapper** netboot files,  **yaboot.conf** 
uses **initrd.img**.  The **Edgy** version has **initrd.img**  commented out and a line
containing **initrd.gz** added.  Starting to get the picture?   The  **Feisty** versions (remember 
I'm talking powerpc here) have not been adapted.  **yaboot.conf** references **initrd.gz**,
the **cpio** version, but **vmlinux** apparently expects the **cramfs** version **initrd.img**.   
What happens is that the netinstall process dies in a kernel panic unable  to recognize/mount
the initial ram file system.

Sooooo...go back and make a cramfs image with the modified initrd extraction:

[LIST=1]
[*]As root...
[*]Install mkcramfs: 
[LIST]
[*]**apt-get install cramfsprogs**
[/LIST]
[*]Use mkcramfs to create a cramfs version of initrd:
[LIST]
[*]**mkcramfs initrd_dir newinitrd.img**
[/LIST]
[*]Move newinitrd.img to initrd.img in the tftp server directory
[*]Edit yaboot.conf to comment out the initrd line using initrd.gz and adding a line using initrd.img, in each boot stanza.
[/LIST]

Then the netinstall boot succeeded.

This is a bothersome workaround.  I suspect that the real solution  is to rework the
netboot files to use the newer  **cpio** initrd convention, and to fix the 6MB limit in 
**tftp**. They  (the powerpc team) didn't get to it for Edgy,  although the workaround 
was released.  I don't see any attempt to deal with it in **Feisty** yet. (28 April 2007)

---

### Post by coolaj86 on 2007-11-02
I have a teal / blue clamshell 300mhz with a busted cd-rom drive that even when it wasn't busted wouldn't read burnt cds too well.

Could you please post a link to the initrd.img you had that worked?

What I actually want to do is somehow replace the 6gb drive which has panther installed on it with a 20gb drive a friend gave me, but I figure if I can get linux on it maybe I can work from there to somehow clone the  and I just put a 20g pc formatted hard drive in it.

Or perhaps I could somehow clone the 6gb image to my linux box, clone it to a flash drive, boot off of the flashdrive and copy the image back over to the 20gb.

Any ideas would be greatly appreciated. I just don't know mac well enough yet to get this done.

---

### Post by 7upers on 2007-12-07
**cd initrd_dir ; find . -depth -print | cpio -oc > ../newinitrd ; cd .. ; gzip newinitrd**

The script is not quite correct and does not always work!
Here, I get everything done so:
**cd initrd_dir ; find . | cpio -o -H newc > ../newinitrd ; cd .. ; gzip newinitrd** :)

---

