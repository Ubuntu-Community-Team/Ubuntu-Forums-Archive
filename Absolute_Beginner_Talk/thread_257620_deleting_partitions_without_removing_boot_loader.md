---
title: "deleting partitions without removing boot loader?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-09-14
Hi all. One more question about resizing my partitions. If I just want to delete all my partitions (except the Windows one) and start over, can I do this without removing the boot loader? What will happen if I give my whole hard drive back to the Windows partition but not change the boot loader?

I plan to reinstall Ubuntu anyway, but will I encounter some problems even before I get to the reinstallation stage?

Thanks,
John

---

### Post by bodhi.zazen on 2006-09-14
[color=red]If you delete your Ubuntu partition you will need to restore the MBR from your windows XP CD/DVD or you will not be able to boot (windows) from the hd.[/color]

---

### Post by orb9220 on 2006-09-14
When you boot up the livecd to reinstall you can delete and reformat those partitions. And a fressh grub will be installed.

I don't understand what are you trying to achieve.
You can boot up to xp from grub right?
Do you need the partitions for something else?
If not just leave them until you install again.

If you want only xp then insert winXP disc and select fixmbr at the prompt which will remove the loader grub.

---

### Post by JohnJSal on 2006-09-14
What I want to do is make my partitions smaller, but I'm having trouble reclaiming that space and putting it back into the Windows partition. So I figure it would be easier to just delete the partitions and start over, since I kind of need a clean install of Ubuntu anyway, and I won't be losing any information.

---

### Post by Lucidio on 2006-09-18
I have a similar question...I want to completely swiych to ubunto so i need to delete my windows partition and give to ubuntu that gained space?

How can i achieve this without reinstalling my ubuntu? (My ubuntu is working just great!)

Is there a guide, post, wiki, faq, page or something that ca help me?

in advance Thanks!

---

### Post by TSP on 2006-09-18
Is easy, first noot ubuntu and delete the windows partition, next use a ubuntu livecd and reinstall grub, you can find a nice howto in the howto section.

---

### Post by bodhi.zazen on 2006-09-18
Easiest way is to just to re-format the windows partition as ext3 (or whatever) and mount.

Somewhat harder is to use the new gparted CD, delete the windows partition, move the ubuntu partition (to where windows was)and swap (to the end of the drive), and then resize Ubuntu partition to cannibalize the remaining free space.

[Gparted Live CD](http://gparted.sourceforge.net/livecd.php)

You will need only to modify /boot/grub/menu.lst to point to the new Ubutnu partition.

---

### Post by bodhi.zazen on 2006-09-18
> **TSP said:**
> Is easy, first noot ubuntu and delete the windows partition, next use a ubuntu livecd and reinstall grub, you can find a nice howto in the howto section.

You do not need to re-install grub. Depending on what you do with your Ubuntu partition you may need to set up your MBR.

---

