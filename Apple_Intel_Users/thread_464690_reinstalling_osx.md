---
title: "reinstalling osx"
date: 2007-06-04
forum: Apple Intel Users
---

### Post by fumanchu on 2007-06-04
I recently caused some irreparable permissions problems in osx (I changed the ownership of my entire mac hd after mounting it in ubuntu) and decided that the best thing to do would be a complete reinstall.  However, after erasing my osx partition and attempting to reinstall osx from the install disc, the installer returns with a message that it encountered errors during the installation and that I should try again; i did try again, and got the same message.  I also know that I don't just have a faulty install disc, because I got the same message when trying to install off of a disc that they had at my local apple store.  I think that the osx installer just doesn't like something about ubuntu and my partition setup.  Is there any way to solve this without erasing my whole hard drive and starting from scratch?

---

### Post by ronocdh on 2007-06-05
> **fumanchu said:**
> I recently caused some irreparable permissions problems in osx (I changed the ownership of my entire mac hd after mounting it in ubuntu) and decided that the best thing to do would be a complete reinstall.  However, after erasing my osx partition and attempting to reinstall osx from the install disc, the installer returns with a message that it encountered errors during the installation and that I should try again; i did try again, and got the same message.  I also know that I don't just have a faulty install disc, because I got the same message when trying to install off of a disc that they had at my local apple store.  I think that the osx installer just doesn't like something about ubuntu and my partition setup.  Is there any way to solve this without erasing my whole hard drive and starting from scratch?
Like Windows, I think OS X likes to be installed on an entire drive. Personally I always make sure OS X is installed and happily running before I mess with other partitions. As much as I may wipe or split the other partitions, I never touch the OS X one, because it's moody about being shoved around, and as you've seen, it doesn't much like to install with friends. =/

If anyone has succeeded in tricking OS X to install onto an already partitioned system, please post. I myself have always just caved and let it take up the entire drive.

---

### Post by fumanchu on 2007-06-05
thanks ronocdh, I'll see if I can find out anything more on the apple forums

---

### Post by ronocdh on 2007-06-05
> **fumanchu said:**
> thanks ronocdh, I'll see if I can find out anything more on the apple forums
Much luck to you, and please post back, whatever your results!

---

### Post by fumanchu on 2007-06-05
Ok well I've decided to just scrap osx for now, as there doesn't seem to be an easy solution to my problem.  So what would be the best way to reformat the osx partition and dedicate it to ubuntu?

---

### Post by fumanchu on 2007-06-06
Well I went ahead and used the gparted live cd to erase my hfs+ partition and resize the ext3 partition to fill the empty space, but now ubuntu won't boot anymore.  The computer doesn't even recognize it at startup.  Is this fixable or have I just lost both of my OSs?

---

### Post by ronocdh on 2007-06-06
> **fumanchu said:**
> Well I went ahead and used the gparted live cd to erase my hfs+ partition and resize the ext3 partition to fill the empty space, but now ubuntu won't boot anymore.  The computer doesn't even recognize it at startup.  Is this fixable or have I just lost both of my OSs?
You can try booting to the Ubuntu live CD and performing a rescue, but I believe you might be hosed. (Always always back up, especially when futzing with partitions! Hopefully your data is safe, at least.) I **believe** that the GParted CD isn't very useful on the Mactels because it doesn't handle GPT editing very well. That's why things like iPartition have become popular, but of course that's pay-for software.

At this stage in the game, I recommend wiping your drive by reinstalling OS X onto it, then partitioning from within OS X and installing Ubuntu. Remember that you can remove any unwanted software packages during the OS X installation procedure. (There will be a rather obscure "Options" button, in the lower left hand corner of the window, IIRC.)

---

### Post by ivesjd on 2007-06-06
I removed the extra languages in my install and it saved 1.1 Gbs. More room for mp3's!! :)

---

### Post by hellomatts on 2007-06-08
Once your all done, I would recommend using these apps to make images of both your mac side and your linux side...

Mac: super duper
Linux: Ghost for Linux (GFL)

---

### Post by tchorix on 2007-06-11
This message is a bit late, but I just wanted to give some more feedback.

I also tried to re-install macosx in one of the partition of my hard disk, but I always got the "funny and useless" message "error during instalation... try again"... he he he... not even a detail about what went wrong. As ronocdh said, it seems that macosx wants to manage the whole disc in order to perfrom an install.

About the other issue discussed here. I wouldn't get rid of the partition with macosx. One reason is because is the only way for getting framework updates. The other one, I don't fully understand it, but I can use my bluetooh keyboard during the selection of the operative system when rEFIt is launch. This means that some mac software is taking control of the machine in order to run rEFIt... this is probably why fumanchu was not able to boot Ubuntu after erasing macosx.

cheers
Tch

---

### Post by ronocdh on 2007-06-12
> **tchorix said:**
> This message is a bit late, but I just wanted to give some more feedback.

I also tried to re-install macosx in one of the partition of my hard disk, but I always got the "funny and useless" message "error during instalation... try again"... he he he... not even a detail about what went wrong. As ronocdh said, it seems that macosx wants to manage the whole disc in order to perfrom an install.

About the other issue discussed here. I wouldn't get rid of the partition with macosx. One reason is because is the only way for getting framework updates. The other one, I don't fully understand it, but I can use my bluetooh keyboard during the selection of the operative system when rEFIt is launch. This means that some mac software is taking control of the machine in order to run rEFIt... this is probably why fumanchu was not able to boot Ubuntu after erasing macosx.

cheers
Tch
I too recommend that everyone keep an OS X partition on the laptops, just because it adds a bit of security in a pinch (I lost my Madwifi support during a kernel update while I was away--my fault, I know, but still happened!). As tchorix said, it is indeed the only way to acquire firmware updates for your hardware. Nonetheless, there are many people here who boot Ubuntu solely on their machines, and they don't run into problems.

 I haven't read much about using Apple peripherals, such as the keyboard, in Ubuntu without OS X installed, but I doubt OS X is somehow providing functionality when it's not running. I too used the Apple bluetooth keyboard for a while, and I laughed out loud when I realized I was using it during the installation of WinXP--yes, on that horrid blue screen BIOS-esque interface! There are posts active here about using the Mighty Mouse (though the side buttons aren't working yet!), too, and I would bet that works with or without OS X installed on the system.

---

