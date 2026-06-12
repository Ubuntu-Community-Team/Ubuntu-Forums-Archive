---
title: "How to Partition on PPC?"
date: 2008-03-29
forum: Apple PPC Users
---

### Post by Leopoguin on 2008-03-29
Hi all, I was hoping to dual boot my iMac G5. I was reading  [these instructions]("https://help.ubuntu.com/community/Installation/PowerPC") and at the part about partitioning, I wasn't sure if I should go with Ubuntu's partition editor or find another way.  Can it live partition my HD without damaging my Leopard install?  If I select the "use the largest continous free space" option will I have no space left on my Leopard partition?  I know there is a manual option for the partition editor but Linux's layout for that looks really unfamiliar to me.  Thanks for any tips.

---

### Post by stream303 on 2008-03-29
I've done a few dual-boot installations and tend to keep it simple since there are many ways to partition, so here are a few tips for what I do..  I'm sure others can explain it better than I can - still a bit shaky when it comes to partitioning myself.

For me the simplest way to dual-boot is to reinstall OSX, but use Apple's disk-utility on the setup disk to partition the drive in half prior to actually proceeding with the OSX install.  (Start the install, but go up to the menu bar and click on disk-utility, do your OSX partitioning, and then actually follow up with the install) Once OSX is installed onto half the drive, (or however much space you want to devote to OSX) I then install Ubuntu letting Ubuntu's guided partitioning to find the free space left.  Ubuntu will detect the OSX install automatically and include it in the boot menu.

If I want to resize the existing OSX partition without reinstalling it, I have used a commercial utility called iPartition to resize the hfs partition.  If you look for "resize hfs partitions for free" or something like that in the ppc forum here, you can do basically the same thing, although I haven't personally used this technique - many have reported success with it.  You then follow up with by letting Ubuntu again find free space.

At a minimum, Ubuntu will automatically create the four necessary partitions at a minimum needed to boot.  

It should look something like this:
```
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/sda3         Apple_UNIX_SVR2 untitled           303835938 @ 2018      (144.9G)  Linux native
/dev/sda4         Apple_UNIX_SVR2 swap                 8743852 @ 303837956 (  4.2G)  Linux swap

```

The sizes for the partition map and bootblock partitions are usually very near this size no matter what.  Your Linux native and swap will likely be much different depending on your drive and swap partition calculation.

(NOTE: early G3 iMac owners will want to keep the size of the Linux Native partition to under 8gb, preferably around 7.5gb.  This has thrown off a few owners that have had hard drive upgrades in those machines as the Ubuntu installer doesn't know about this Apple hardware limitation for those early iMacs.  Advanced early G3 iMac partitioners must be sure to keep everything up to the boot and root partitions no larger than 7.5gb if they slice and dice up their partitions for /home /tmp /log etc manually beyond 7.5 gb)

Advanced users can manually slice and dice up their Linux native into /usr /tmp /home etc for finer control.

For me, since my Macs are general purpose, I just use the very simplified method of trying to create free-disk space first by resizing any existing hfs partitions (or partition it myself for OSX up front), and then install Ubuntu afterwards by letting guided partitioning use free space and do it all automatically.

Lately though, I have weaned myself away from OSX and just let Ubuntu install to the entire disk, rather than use free space. :)

Whew, a little tongue-tied. :)  I'm sure others can point out more detailed info...

---

### Post by oswaldkelso on 2008-03-29
> **Leopoguin said:**
> Hi all, I was hoping to dual boot my iMac G5. I was reading  [these instructions]("https://help.ubuntu.com/community/Installation/PowerPC") and at the part about partitioning, I wasn't sure if I should go with Ubuntu's partition editor or find another way.  Can it live partition my HD without damaging my Leopard install?  If I select the "use the largest continous free space" option will I have no space left on my Leopard partition?  I know there is a manual option for the partition editor but Linux's layout for that looks really unfamiliar to me.  Thanks for any tips.

This is how I do it, I like this method as I know I have a copy of my data. 
[http://forums.debian.net/viewtopic.php?t=18193&highlight=](http://forums.debian.net/viewtopic.php?t=18193&highlight=)

---

### Post by stream303 on 2008-03-29
Ah,  interesting.  So let's see if I got this straight:

1) Use Carbon-Copy-Cloner to clone your OSX disk to an external firewire drive.

2) Use OSX install, and instead of installing, go up to disk-utility menu bar and just repartition the original drive to how large you want OSX to be, and leave the rest as free space.  Dump out of the OSX install.

3) Boot the firewire drive, and then run Carbon-Copy-Cloner from this drive, and clone itself back to the original disk, which now has the resized partition.

4) Install Ubuntu onto the free space.

That looks great!

---

### Post by Leopoguin on 2008-03-30
Posted from Firefox within Ubuntu!

I roughly followed the advice here, especially stream303's, although I chose not to reinstall Leopard because I already have it installed. Instead I used the Leopard installer's Disk Utility to live partition my HD (actually used the "free space" option rather than creating a new volume), and then trusted Ubuntu's installer to find this newly created free space.  And now I'm up and running.  

It was a little shaky booting up, though.  It didn't work at first and I'm not sure what I did differently, but I've proved I can boot into Linux or Mac OS X, so that's progress.  

I also don't have permissions to get into my own files on my Mac OS volume, which Ubuntu seems to think is read-only, and although I can read most files, it won't even let me open folders such as ~/Documents or ~/Pictures (on the Mac OS X partition).  Anyone know how to work around that?  Appreciate your comments.

---

### Post by oswaldkelso on 2008-03-30
> **stream303 said:**
> Ah,  interesting.  So let's see if I got this straight:

1) Use Carbon-Copy-Cloner to clone your OSX disk to an external firewire drive.

2) Use OSX install, and instead of installing, go up to disk-utility menu bar and just repartition the original drive to how large you want OSX to be, and leave the rest as free space.  Dump out of the OSX install.

3) Boot the firewire drive, and then run Carbon-Copy-Cloner from this drive, and clone itself back to the original disk, which now has the resized partition.

4) Install Ubuntu onto the free space.

That looks great!

You got it :) I always back up my vital data on to dvd as well also. Then if it does go awol I've only lost my settings. Works a treat.

---

### Post by stream303 on 2008-03-30
> **Leopoguin said:**
> I also don't have permissions to get into my own files on my Mac OS volume, which Ubuntu seems to think is read-only, and although I can read most files, it won't even let me open folders such as ~/Documents or ~/Pictures (on the Mac OS X partition).  Anyone know how to work around that?  Appreciate your comments.

Looks like a good thread here about osx file permissions and sharing with Ubuntu...

[http://ubuntuforums.org/showthread.php?t=681483&highlight=seeing+osx+files](http://ubuntuforums.org/showthread.php?t=681483&highlight=seeing+osx+files)

Congrats on the new Ubuntu install!

---

### Post by oswaldkelso on 2008-03-30
Also see
[http://ubuntuforums.org/showthread.php?t=553628&highlight](http://ubuntuforums.org/showthread.php?t=553628&highlight)

and

[http://ubuntuforums.org/showthread.php?p=4105039&highlight](http://ubuntuforums.org/showthread.php?p=4105039&highlight)

---

### Post by wiggers on 2008-04-02
Hi

A new to all this although I have been playing with Linux for a few years just never made the jump.

I have been live running Gutsy on a PPC G5 tower and I would like to install it as dual boot for a proper test.

I have two drives in my machine which are SDB A and SDB B the SDB B is a 500 GB drive with 2 partitions at 250GB each

I have managed to turn off the journalling on the second parition of SDB B and I was trying last night to manually set up the partitions in the gutsy installer app.

Well I didn't complete as the process is a little guess work and even though I think I set up a mount point and a swap partition (As this was what the installer states I should do) when going forward it tells me I have not set up a neworld partition and a temp partition and I lost the feeling of control and or knowledge of what the installer was about to do and aborted the process!

Is there a web link to a how to for my installation (Tricky I know ) as I can't seem to find anyone who has shared the step by step instructions.  I can see that many have acheived the end dual boot goal but I need to know how (I am a G5 owner not and intel so boot camp is out)

Many thanks.

---

### Post by slacka-vt on 2008-04-02
Is there anything on the 500GB drive ?
You say it is partitioned into two 250GB volumes.

Assuming one of the 250GB volumes as no data on it,
Boot into an Ubuntu Live CD and
go to System > Administration > Partitioner
choose whatever partition you're going to use for your Ubuntu install.
And "Delete" the partition, this just leaves "Free Space"

Now when you Install, and the partitioner launches,
you can choose "Guided Partition" and select "Use Largest Free Space"

You can actually create the "Free Space" using the method mentioned above
using the partitioner during the installation also.

~s

---

### Post by stream303 on 2008-04-02
> **wiggers said:**
> I have two drives in my machine which are SDB A and SDB B the SDB B is a 500 GB drive with 2 partitions at 250GB each

These dual-drive machines have been tricky and there is a thread here somewhere I'd have to dig up.

I'm pretty sure that after install to either drive, you need to check or edit /etc/yaboot.conf, and also make sure that the /etc/fstab is pointing correctly to the right drive with the proper UUID.

If I remember correctly, most can manually edit the yaboot.conf right, but I'm not sure that the /etc/fstab was checked for proper UUID's.

I'd love to see this working on a dual-drive model.

---

### Post by wiggers on 2008-04-03
It is as you say two partitions one empty.

I installed it last night on a G4 iBook as an experiment.  I used a full auto install and it erased the drive in the iBook and installed.

I had anticipated this (backed up the iBook before) although when it tried to boot up again into Unbuntu all I got was a very white screen.  I have seen this before when using the live CD and I know how to boot with no-splashpowerpc but how do you force the boot up on a real install to do this?

I presume that you have to edit the boot up configuration file from the live cd version?

I will preservere but for now I will use my laptop as an sandbox I have reinstated the iBook back to OS X but partitioned the drive to 2 volumes one for OS X and the other for Unbuntu (Unix file system) and as you suggest I will use the largest free space option, but could you give me a guidance on the white screen issue?

Many thanks for the replys

---

### Post by stream303 on 2008-04-03
> **wiggers said:**
>  I have seen this before when using the live CD and I know how to boot with no-splashpowerpc but how do you force the boot up on a real install to do this?

I presume that you have to edit the boot up configuration file from the live cd version?

Ok, for now we'll stick to just the G4 install.  All we need to do is edit the **/etc/yaboot.conf** file, and add an append= line to it with the kernel parameters.  The trick is getting there. :)

You can do it several ways.  With a live-cd, you can boot like you normally would do, and pass the kernel parameters to avoid the white screen like usual to get it up and running.

From there, if you want to edit graphically, you can type in a terminal

```
gksudo gedit /etc/yaboot.conf 
```  
(edits the file with root priveleges)

and put in a line something like this into yaboot.conf depending on your kernel parameters you needed:

```
append="nosplash"
```
or
```
append="nosplash video=ofonly"
```

and save the file.  See below for the ybin command below to make the system aware of the change.

You can do the same thing from a terminal with the nano editor:

```
sudo nano -w /etc/yaboot.conf
```

Now that we've changed the file, we need to make the system aware of it:

```
sudo ybin -v -C /etc/yaboot.conf
```

and then reboot.

If you have just the "alternate" install disk, or if you have the live-cd but want to do it this way, you can boot the cd in single-user root rescue mode:

1). At the second stage of the boot prompt, hit -TAB- to stop the boot timeout from proceeding.  You should be presented with a few options, one of which is "rescue" (or rescue-64 for G5's etc).

2) Type rescue at the prompt, and the system will boot up and look similar to an install, but will leave you at a shell prompt, typically choose the environment for the root partition (ie, sda3 or whatever yours is) in which to use the shell.

3) Now, since you are operating as root, you can edit the /etc/yaboot.conf file without using sudo, since we are already root:

```
nano -w /etc/yaboot.conf
```

Sometimes this doesn't look good, so you may have to use the vi editor if you are comfortable with it..  In that case, you probably want to set up the terminal emulation to vt100 beforehand:

```
export TERM=vt100
```

and then proceed with vi /etc/yaboot.conf, and don't forget to make the system aware of it with the ybin command.

Reboot.

Let's see how far we get with this...

---

