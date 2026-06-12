---
title: "Couple of hard questions -- Plz help!"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Neenjah on 2007-05-26
First off I recently installed SP2 on my WinXP installation.. and well it corrupted a file.  Now since I can view my windows installation while in linux.. I wanted to replace the corrupted file, but I cant becuase it says the file/folder is write protected, I AM logged on as root and still no good, so any help there?

Also for the life of me I cant get 1024x768 to show up on my screen resolutions and its driving me crazy!!!!!!

---

### Post by H.E. Pennypacker on 2007-05-26
You are trying to do something with your NTFS partition.  Ubuntu, by default, does not provide write permissions to your Windows partition.  You could, however, use something called NTFS-3G.  Visit [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/) for more information, and you could also do a forum search for info on this driver.  It will allow you to write to your Windows partition.

I don't know what problems you're having with your resolution, because 1024x768 works perfect for me.  Anyhow, resolution problems are fairly common.  Please do a forum search on this problem.

---

### Post by starcraft.man on 2007-05-26
> **Neenjah said:**
> First off I recently installed SP2 on my WinXP installation.. and well it corrupted a file.  Now since I can view my windows installation while in linux.. I wanted to replace the corrupted file, but I cant becuase it says the file/folder is write protected, I AM logged on as root and still no good, so any help there?

Also for the life of me I cant get 1024x768 to show up on my screen resolutions and its driving me crazy!!!!!!

1) You need ntfs-3g drivers to write to ntfs windows partitions (search forums for guide, they do better job explaining it).

2) First you usually need your cards graphics drivers. Use [envy]("http://www.albertomilone.com/nvidia_scripts1.html") if you don't have them installed, download the stable .93 deb and install it. Then go applications> system tools > envy and install automatically your card's drivers. Once that is done, open up the terminal (Applications > Accessories > terminal) and type this in:

```
sudo dpkg-reconfigure xserver-xorg
```

follow all the prompts select the defaults if you don't understand and when you get to resolution, make sure your screens maximum setting is checked (its a dark circle in the larger circle I think).

That should be it, best of luck with Ubuntu :).

---

### Post by kayvortex on 2007-05-26
To be able to write to ntfs files, you'll definitely need to install ntfs-3g if you haven't already done so. I followed the instructions at [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009), which were pretty clear. If I remember correctly, it is also useful to umount the ntfs filesystem before running ntfs-3g just to avoid some hassle (just type "mount" at the command line to see if it is mounted and where, and then just type "umount /dev/sda2" if windows is on /dev/sda2).

I had trouble getting 1400x900 on my Inspiron 9400, but I googled it. All I can suggest is looking up your graphics card on forums for more information. 

Finally, careful messing about with XP. I once messed up an apparently important file which led to a massive headache. You probably know this already, but back up your important files, or make an image of your windows drive if possible.

---

