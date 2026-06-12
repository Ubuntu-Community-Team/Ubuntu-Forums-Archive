---
title: "Help with formatting external USB - HDD"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by lodravah on 2007-01-10
I've looked around for answers, and I've found info, but still uncertain. I've been having some serious "read - write - permission" issues with my external Iomega 320 Gb USB - HDD. So I've decided to format it to get a fresh start. I would like to format it into FAT32 because it is compatible with Win and *nix OS's. I still know people who actually run Win :P 

What I would like to know:

How do I format my HDD to FAT32 in Ubuntu? 

And if you know, how to do this in Win (as my flatmate has that)?

I've heard talk that formatting such a big HDD will offer problems, that there is a 4 Gb limit to formatting into FAT32. What is all that about?

How do I format into ext3 in Ubuntu?

---

### Post by jvc26 on 2007-01-10
For formatting you can use the Gparted disk partitioner either on the live cd or on the Gparted live cd (see: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) To format from Xp you can go and right click on the drive and select 'format' then select the type of format. You can do the same from the GUI on the Gparted. To format ext3 go and select the drive and then select the format. FAT32 I think has a limit of 32GB or something - Im afraid I dont know 100% about that but Ive read that in several places.
Il

---

### Post by bodhi.zazen on 2007-01-10
FAT:```
sudo mkfs.vfat <device>
```

Ext3:```
sudo mkfs.ext3 <device>
```

<device> = your hads drive (/dev/sda or /dev/sda1)

You can format via a gui, gparted:

```
sudo aptitude install gparted
```

FAT will have a 4 gb file size limit (I think)

You can read/wirte ext2 and ext3 from windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by lodravah on 2007-01-10
Is vFat the same as FAT32?

---

### Post by jvc26 on 2007-01-10
If I remember rightly, vfat is the tag that Linux gives to FAT partitions (someone more in the know do correct me if I'm wrong) see here: [http://www.ubuntuforums.org/showthread.php?t=283131&highlight=how+to+fstab](http://www.ubuntuforums.org/showthread.php?t=283131&highlight=how+to+fstab) If you're more interested
Il

---

### Post by lodravah on 2007-01-10
here is what just happened, not five minutes ago:

I unmounted and unplugged my HDD, carried it over to my flatmate's room, plugged it in his Win - box and mounted.

He opened a program called "Max Blast," ran it selecting to "format my device in FAT32."

It took all of two seconds as the program didn't have to make a new filesystem, but just reinstalled FAT32. 

Unmounted and unplugged, carry to my room, plug and mount.

Hey presto: it works. HDD is formatted, all 320 Gb are recognized as usable space and all permissions are restored to normal. 

Sometimes, just sometimes, the solution is simple :)

---

### Post by jvc26 on 2007-01-10
fantastic :)
Il

---

### Post by lodravah on 2007-01-10
Of course, now comes the final test.. Rebooting, and then to see if it still works after that. Here goes!

lo

---

