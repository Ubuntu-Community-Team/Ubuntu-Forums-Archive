---
title: "[SOLVED] I think i just made my C;// into swapspace."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by bazil270 on 2007-12-04
What does this mean? are all my data on C;// erased?:confused:

---

### Post by caravel on 2007-12-04
Hmmmm... can you still boot into windows?

How did you do your partitioning?  Automatically or manually?

---

### Post by bazil270 on 2007-12-04
i tried. i dont think i can. kept pressing f8 f8 f8. lol. its gone! :)  

manually i think. i did put c:// as swapspace since i din know it would use all of it lol. all my stuff gone!

---

### Post by tact on 2007-12-04
Welcome to ubuntu as your only OS!  congrats on the brave move to just jump straight in like that..  :)

---

### Post by caravel on 2007-12-04
When you boot the machine do you get the grub boot menu and is Windows listed as one of the bootable OS's?

---

### Post by bazil270 on 2007-12-04
lol! yeah! down to windows! xD

and it wasnt very important stuff though. jus a bit of games and everything like old photos but that's backed up. 

lol i just started using it for like 2 hrs and guess what? My windows gone!

---

### Post by bazil270 on 2007-12-04
> **caravel said:**
> When you boot the machine do you get the grub boot menu and is Windows listed as one of the bootable OS's?

i did get the grub, but windows wasnt listed. in fact, i didnt get a chance to see anything after grub loads. it just goes straight to ubuntu. anyway my dad was asking "How do you get rid of windows now?" lol i guess it just went by itself.

---

### Post by Calash on 2007-12-04
It you set the partition that your Windows install (C:) was on as the Linux swap partition then it would reformat the partition, erasing all of your data.

Is your Ubuntu install working?  If so boot into it and see if there are any NTFS or FAT32 drives listed.  These would be where the Window would have lived.  If they are there, but you just cannot boot, then it will be easier to get you back up and running.  Otherwise I believe you lost all the data.


Good Luck.

---

### Post by bazil270 on 2007-12-04
> **Calash said:**
> It you set the partition that your Windows install (C:) was on as the Linux swap partition then it would reformat the partition, erasing all of your data.

Is your Ubuntu install working?  If so boot into it and see if there are any NTFS or FAT32 drives listed.  These would be where the Window would have lived.  If they are there, but you just cannot boot, then it will be easier to get you back up and running.  Otherwise I believe you lost all the data.


Good Luck.

Ubuntu is working perfectly. No bugs yet. (None at all i hope). Im running from ubuntu now. There is the hd listed but its empty. its linux swap. so its safe if i repartition it to just 2 gb? so i can use the extra space.

---

### Post by caravel on 2007-12-04
The NTFS or FAT/FAT32 partitions often appear on the desktop.  If there's nothing and Windows is not listed in grub's boot up menu then Windows has probably gone into the ether.  This basically means your files have been lost.

---

### Post by bazil270 on 2007-12-04
> **caravel said:**
> The NTFS or FAT/FAT32 partitions often appear on the desktop.  If there's nothing and Windows is not listed in grub's boot up menu then Windows has probably gone into the ether.  This basically means your files have been lost.

oh well. no regrets there. except maybe sum of my music files i'll miss but i still have the cd. and sum games. i hope there is none of my dad's files anymore in C;/ or else he's gonna kill me. 

anyway, thanks everyone!

---

