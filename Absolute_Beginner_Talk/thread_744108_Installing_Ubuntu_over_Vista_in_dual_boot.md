---
title: "Installing Ubuntu over Vista in dual boot"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by chelidagreat on 2008-04-03
I have a laptop that came in a dual boot with Windows XP and Vista. I am wondering if it safe to install Ubuntu over Vista as I don't really use Vista. It is a laptop for school and it's a pain to reconfigure the laptop again if something goes wrong. Therefore I want to be 100% sure if it safe or not.

Thanks in advance!

---

### Post by spiderbatdad on 2008-04-03
Hi.
IMHO, no one here should tell you, any dual boot/overwriting operations you perform on your system is 100% safe. Your best bet is to read as much as you can regarding the process, then decide for yourself whether you are willing to take the risk.

Manufacturers are now pre-installing Ubuntu on a number of systems...that's most likely your only guarantee of compatibility between the OSes and your system hardware.

---

### Post by Tomatz on 2008-04-03
> **spiderbatdad said:**
> Hi.
IMHO, no one here should tell you, any dual boot/overwriting operations you perform on your system is 100% safe. Your best bet is to read as much as you can regarding the process, then decide for yourself whether you are willing to take the risk.

Manufacturers are now pre-installing Ubuntu on a number of systems...that's most likely your only guarantee of compatibility.

Yeah good advice :)

It should be fine just formatting the vista partition even if the windows bootloader is there as grub (the ubuntu/linux bootloader) should take over as the bootloader.

As spiderbatdad said get to know the whole process before jumping in at the deep end :)

---

### Post by Tatty on 2008-04-03
Its definately possible.  The most logical way of doing this imo would be to delete your vista partition completely, then install ubuntu as normal with only XP still on the system.

But as spiderbatdad says, nothing is completely reliable with computers, theres always that possiility that it could all go wrong.  So definately back up first.

But most importantly.. are you sure you want to remove vista?  XP is pretty out of date now, and microsoft will stop supporting it for consumers next year..  I have never used vista myself, but its been out over a year now, most of the major bugs will have been ironed over.  If i had a vista machine i definately wouldnt remove vista.

---

### Post by ukripper on 2008-04-03
> **chelidagreat said:**
> I have a laptop that came in a dual boot with Windows XP and Vista. I am wondering if it safe to install Ubuntu over Vista as I don't really use Vista. It is a laptop for school and it's a pain to reconfigure the laptop again if something goes wrong. Therefore I want to be 100% sure if it safe or not.

Thanks in advance!

Indeed it is safe, i would still recommend you should create backup of your important files before you take a plunge dual booting.

---

### Post by chelidagreat on 2008-04-03
Thanks for the advices.
Where do I actually read up on the process? I have tried google but most of the information is on dual booting xp and ubuntu with xp ONLY on the computer.
I am removing vista cause I don't really have a use for it now. My laptop came with a Vista OEM cd anyway, so I can always reinstall Vista over existing OSes after I finish my school if I need to.

---

### Post by Tatty on 2008-04-03
boot with a live CD then use gparted to edit the partitions.

---

### Post by bumanie on 2008-04-03
Partitioning and formatting is never 100% safe, although I have done it many times without problems. If you happen to have an electricity supply problem partway through partitioning/moving partitions, say good bye to the file systems. I would use the gparted live cd to set up the partitions if I were you as it has a gui that is self-explanatory.

---

### Post by prismpirate on 2008-04-03
Dual Booting itself is 99% safe, but Ubuntu might not work flawlessly on your computer, especially if it has hardware problems.

Try the live cd, and if everything works, these forum threads link to tutorials, check them out first:
[http://ubuntuforums.org/showthread.php?t=706813]("http://ubuntuforums.org/showthread.php?t=706813")


Backup your data, then install Ubuntu.

Enjoy:)


If there are some complications that occur during the live-cd, i suggest you try it out on a separate computer as your laptop belongs to the school and you said that it's a pain to configure if anything goes wrong.

---

### Post by chelidagreat on 2008-04-03
Will editting the partitions with gparted mess with the MBR in any way? I had an instance where, after editing partitions, my MBR was lost and I had to use an external boot loader from a CD.

---

### Post by Tatty on 2008-04-03
> **chelidagreat said:**
> Will editting the partitions with gparted mess with the MBR in any way? I had an instance where, after editing partitions, my MBR was lost and I had to use an external boot loader from a CD.

It might do if you delete the parition that the mbr is on.  But when you install ubuntu, it will install its own mbr anyway, which should autodeteact your XP partition and create a boot entry for it.

---

