---
title: "Can't dual boot Ubuntu with BootitNG"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by BuckoA51 on 2007-04-20
I'm really stuck, I have installed Ubuntu 7.04 to a hard drive, got it booting and everything. Now, I put another hard drive in that was to contain Windows, XP and Vista. I installed BootitNG to this hard drive and got Vista booting OK. Once that was done, I put the drive back in that contained Ubuntu but when I try to boot Ubuntu from within BootitNG it says "the partition is not bootable" even though I know it is because I can change the boot priority in the bios to boot the ubuntu drive first (or remove my windows drive altogether) and it boots just fine.

I also tried installing Bootit NG to the drive with Ubuntu but that completely killed it (im guessing by writing over linux MBR?)

Please has anyone got this working? it is driving me crazy...

---

### Post by bapoumba on 2007-04-20
@ BuckoA51: I removed your duplicate thread.

---

### Post by BuckoA51 on 2007-04-20
Sorry, I had no idea i'd posted it twice...

---

### Post by AClark on 2007-04-20
I used BootITNG when I first started using Fiesty to do a conventional dual boot with one drive.

As I came to have a better understanding of Grub I decided that BootIT was redundant for my 
purposes and just complicated matters - so I removed it and now use Grub only as my boot loader.

I realize your setup is more complicated, but I think a good understanding of how Grub works will go a long way toward solving your problem, whether you use BootIT or not.

 [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)    for the Grub manual

This is a good thread that has a huge amount of info on how others dealt with booting from two different drives  [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

In case you haven't seen it here is the link for the knowledgebase article "How to use linux boot loaders with BootITNG" from Terabyte 
  [http://www.terabyteunlimited.com/kb/article.php?id=164](http://www.terabyteunlimited.com/kb/article.php?id=164)

Here is another thread that may be of help
 [http://ubuntuforums.org/showthread.php?t=413122](http://ubuntuforums.org/showthread.php?t=413122)

From what little I know of this subject it seems to me that you should be able to set up Grub to boot to Ubuntu or the Vista boot loader which would then give you the choice of Vista or XP.
The only reason to use BootIT would be for the other features it has besides multiple OS installs.  

I'm sorry I can't explain things myself - hopefully some of these links will be of help.
Good Luck !

---

### Post by BuckoA51 on 2007-04-21
I'm still really confused, surely GRUB >must< be on the disk else it would not boot at all, so why can't BootitNG boot the partition?

---

### Post by steve.horsley on 2007-04-21
GRUB normally gets installed onto the MBR of the hard disk. As the PC boots from the MBR, it loads GRUB and GRUB then loads Linux from the partition it has been set for. At no stage does the **partition** get booted. 

If you want to make the Ubuntu root partition bootable, you shoud boot into Ubuntu and then issue the following command:
**sudo grub-install /dev/xxx**
where xxx is the device id of your root partition. Youcan get this from the command 
**df -h**
For instance, my df -h says that my / is on filesystem /dev/sda7 so I would say grub-install /dev/sda7. This installs grub into the root partition and makes the partition bootable, so now your other funny bootloader should be happy. You haven't deleted the boot code from the MBR though, so now you have two ways of booting Ubuntu.

---

### Post by AClark on 2007-04-21
steve.horsley's instructions should do the trick as long as you can boot into Linux

If you can't boot into Ubuntu to reinstall Grub to the Linux root partition Terabyte's BootIT documentation has a good tutorial on how to deal with that situation.  I used the bootable CD (Linux FSRD) that they link to in this article.  [http://www.terabyteunlimited.com/kb/article.php?id=232](http://www.terabyteunlimited.com/kb/article.php?id=232) 

Just remember that Grub starts counting from 0 so  /dev/hda1 in Linux is hd0,0 from Grub and /dev/hdb1 would be hd1,0  when at the Grub prompt.

---

