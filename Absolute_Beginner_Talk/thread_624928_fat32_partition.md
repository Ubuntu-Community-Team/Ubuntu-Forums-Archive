---
title: "fat32 partition"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by azizzle on 2007-11-27
Hi everybody! I just need some direction. I have recently done a fresh install of xp, and gutsy. My hdd is 320gb. First, I installed xp, and allocated 70gb to that os. Then, gutsy, with 50 gb. I would like to make a fat 32 partition for the rest of the hd, like the one i saw on the psychocats website, [http://img379.imageshack.us/my.php?image=partitioning3gs4.png](http://img379.imageshack.us/my.php?image=partitioning3gs4.png). 
I'm thinking I can and should do this with the ubuntu live cd? Will that work because I don't want to install another copy of ubuntu on the fat32? 
Also, when I do have that partition will ubuntu and windows automatically recognize it? What do I need to do to mount it on both systems? How do I save files onto this partition? Sorry for the noobish questions. I did search but I couldn't find something that answered my specific questions. Thanks, in advance.

---

### Post by OldTimeTech on 2007-11-27
Check this link out and you'll have your answer 

[http://ubuntuforums.org/showthread.php?t=469666&highlight=sharing+partition+for+windows+linux](http://ubuntuforums.org/showthread.php?t=469666&highlight=sharing+partition+for+windows+linux)

---

### Post by stchman on 2007-11-27
> **azizzle said:**
> Hi everybody! I just need some direction. I have recently done a fresh install of xp, and gutsy. My hdd is 320gb. First, I installed xp, and allocated 70gb to that os. Then, gutsy, with 50 gb. I would like to make a fat 32 partition for the rest of the hd, like the one i saw on the psychocats website, [http://img379.imageshack.us/my.php?image=partitioning3gs4.png](http://img379.imageshack.us/my.php?image=partitioning3gs4.png). 
I'm thinking I can and should do this with the ubuntu live cd? Will that work because I don't want to install another copy of ubuntu on the fat32? 
Also, when I do have that partition will ubuntu and windows automatically recognize it? What do I need to do to mount it on both systems? How do I save files onto this partition? Sorry for the noobish questions. I did search but I couldn't find something that answered my specific questions. Thanks, in advance.

First off create your 70GB partition in NTFS for XP.  Then install XP.

Once that is done use the Ubuntu LiveCD to create free space and the 200GB FAT32 patrtition.  Once this is done install Ubuntu.

Tell the installer to use the largest available free space.  After all is done you will have a 70GB NTFS, a 50GB EXT3 and a 200GB FAT32 partition.

---

### Post by phr0ze on 2007-11-27
Launch Synaptic and install gparted. Its easy to use. Select the unpartitioned space and partition it. Then select this partition and format it with Fat32. 

The partition should appear in ubuntu and XP with no problems.

---

### Post by luisfcup on 2007-11-27
You don't need to use a live cd neither a fresh install.
Use gpart, or other partition manager in Ubuntu to partition the free space and create it as vfat.
Both OS should be able to recognize it without problems.

---

### Post by samuel.rajesh on 2007-11-27
> **azizzle said:**
> Hi everybody! I just need some direction. I have recently done a fresh install of xp, and gutsy. My hdd is 320gb. First, I installed xp, and allocated 70gb to that os. Then, gutsy, with 50 gb. I would like to make a fat 32 partition for the rest of the hd, like the one i saw on the psychocats website, [http://img379.imageshack.us/my.php?image=partitioning3gs4.png](http://img379.imageshack.us/my.php?image=partitioning3gs4.png). 
I'm thinking I can and should do this with the ubuntu live cd? Will that work because I don't want to install another copy of ubuntu on the fat32? 
Also, when I do have that partition will ubuntu and windows automatically recognize it? What do I need to do to mount it on both systems? How do I save files onto this partition? Sorry for the noobish questions. I did search but I couldn't find something that answered my specific questions. Thanks, in advance.


u can format the partion within windows ,use either fat32 or ntfs ,gusty can read and write to both with no problems.

---

### Post by azizzle on 2007-11-27
> **samuel.rajesh said:**
> gusty can read and write to both with no problems.

is this true? 

Also, I'm in Gnome Partition Editor and it's telling me that my ext3 partition is 240gb. When I did the install I indicated  that only 50 gb was to be used. Whatever the case, is there a way that I can carve this partition back down to reformat it? The partition editor i'm using will only allow me to select the ntfs partition.

---

### Post by lespaul_rentals on 2007-11-27
> **samuel.rajesh said:**
> u can format the partion within windows ,use either fat32 or ntfs ,gusty can read and write to both with no problems.

That NTFS thing is a bad idea.

You cannot make changes to a hard drive that is mounted, and if you are running Ubuntu from your hard drive you will not be able to partition it.  Insert the LiveCD and make sure you have an Internet connection.  Install gparted, and run it with sudo privileges.  You should be able to see the unallocated space.  If so, format it with FAT32.

If you have already installed Ubuntu on the remaining space and treated it as one partition, you will have to resize the partition, then format the newly formed empty space.  Gparted is usually pretty good about protecting your data, so you don't really have much to worry about.

Your Windows should recognize it automatically.  Linux can be made to easily recognize it at boot by editing your fstab file.  Get the partitioning/formatting done first, then come back and I'll help you edit your fstab.

---

### Post by azizzle on 2007-11-27
> **lespaul_rentals said:**
> That NTFS thing is a bad idea.

You cannot make changes to a hard drive that is mounted, and if you are running Ubuntu from your hard drive you will not be able to partition it.  Insert the LiveCD and make sure you have an Internet connection.  Install gparted, and run it with sudo privileges.  You should be able to see the unallocated space.  If so, format it with FAT32.

If you have already installed Ubuntu on the remaining space and treated it as one partition, you will have to resize the partition, then format the newly formed empty space.  Gparted is usually pretty good about protecting your data, so you don't really have much to worry about.

Your Windows should recognize it automatically.  Linux can be made to easily recognize it at boot by editing your fstab file.  Get the partitioning/formatting done first, then come back and I'll help you edit your fstab.

I'm pretty sure that I have the gparted live cd... although I have no idea how to use it. Should I veer away from using that or should I try to learn how to do it? I'm not comfortable at all with command lines yet, and that seems to me the way that gparted works when i boot it up. So basically what I'm asking is: is gparted live easy to pick up and use, or should I go with the live cd method? Even if i did the live cd method, I have no idea how to run sudo privledges. I'm very new to this and pretty much have to be led by the nose:(

---

### Post by lespaul_rentals on 2007-11-27
> **azizzle said:**
> I'm pretty sure that I have the gparted live cd... although I have no idea how to use it. Should I veer away from using that or should I try to learn how to do it? I'm not comfortable at all with command lines yet, and that seems to me the way that gparted works when i boot it up. So basically what I'm asking is: is gparted live easy to pick up and use, or should I go with the live cd method? Even if i did the live cd method, I have no idea how to run sudo privledges. I'm very new to this and pretty much have to be led by the nose:(

Do you have an Ubuntu LiveCD?  So long as you have that and Internet access, you should be fine running gparted from the GUI.

And I understand your difficulties with the CLI.  It's very confusing sometimes!  You don't have to feel bad about it, I can help you out.

1. Insert the Ubuntu LiveCD, boot up, and when you get to the desktop, make sure you have an Internet connection.  Open Terminal (Gnome) or Konsole (KDE).

2. In the terminal, type the following:

```
sudo apt-get install gparted
```

3. Let it do its thing.  If it says *gparted is already installed*, great!  If it says *gparted will be installed, packages will be added, 128KB, yada yada yada, [Y/N]?* you will need to press Y then Enter.  This will tell your system, "Yes, I do want to install gparted!"

4. Once that's done, it's time to run gparted.  Type the following:

```
sudo gparted
```

You said you didn't know how to get sudo privileges.  The command "sudo" tells the system to do just that.  In the normal system you will have to enter your password, but since we are running from a LiveCD, that shouldn't be neccesary.  Basically, the sudo command tells the system to let you do whatever you want...sort of an important privilege to have if you are a making mass changes on a disk.

5. gparted should start, then you are ready to begin partitioning!  You should see the partitions.  From there, just select the one you want to format or adjust by right-clicking on it, and it should be pretty obvious from there.  When you're done, click the check mark to confirm changes.

Let me know if you need any more help.

---

