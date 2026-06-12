---
title: "What do i use to get Ubuntu on my mac but sitll keep osx?"
date: 2009-01-01
forum: Apple Hardware Users
---

### Post by mattpenguin09 on 2009-01-01
Hello people,Im going to get ubuntu and i want to run it on my mac.But i sitll want to keep osx tiger how can i do this? o and while im here will ubuntu run well on these sepcs imac g4 700MhzSpeed/768MbMemory/80Gb HDD Please help a user that is new to linux.Thaks alot for any help :)

---

### Post by mkvnmtr on 2009-01-02
You will need to use disk utility on the mac install disk to resize the partition that the Mac os is in to give you room to install Ubuntu. I always defrag my mac system with Drive Genius first but some say it is not important. Then you should have the Ubuntu install disk, I would recommend 8.04 for a first install. Put in the disk and restart holding down the "c" key. Hold down the key until first the mac icon comes up and then the linux icon comes up. Click on the linux icon and then the arrow and you should start to boot. When the first words show on the screen quickly press the "Tab" key. At that point I need to type in live-nosplash-powerpc and press enter. On your machine it might be something else. You will see a list of options including the one I use. If mine doesn't work for you restart with the same procedure and try another option.This should get you to a desktop and allow you to see the install icon. Play around on the desktop to see if you like Ubuntu and when you are ready to install double click the install icon. Up until you are asked to format the partition you can back out to the desktop and use Firefox to come to the forums to ask questions.

---

### Post by lse123 on 2009-01-02
yes/no
May use a MAC MINI with kubuntu or ubuntu by "resize the partition that the Mac os is in to give you room to install one of these" ? 
May I rather also run one of these from usb flash drive(bootable) or cd live(bootable) , from a MAC MINI ?
ALL Linux distributions run on the MAC ?

---

### Post by lse123 on 2009-01-02
yes/no
May use a MAC MINI with kubuntu or ubuntu by "resize the partition that the Mac os is in to give you room to install one of these" ? 
May I rather also run one of these from usb flash drive(bootable) or cd live(bootable) , from a MAC MINI ?
ALL Linux distributions run on the MAC ?

---

### Post by mkvnmtr on 2009-01-02
lse123 you might need to start your own thread to get answers. It will also help you if you tell what mac mini you have.

---

### Post by stream303 on 2009-01-02
The easiest way is to dual-boot.

But first you'll need to make room for Ubuntu.  You do this by either shrinking your existing OSX partition (see the tips here and in the ppc archive on how to do it) , or you can use a commercial utility such as ipartition:

[http://www.coriolis-systems.com/iPartition.php](http://www.coriolis-systems.com/iPartition.php)

The other way is to reinstall OSX to say perhaps half your drive, and leave the other half as free space.

All you do is boot with the OSX install disks, but just before you install, go to the top menu bar, and activate disk-utility.  With disk utility, you can repartition the drive typically by sliding the bottom part of the vertical partitioning window upwards, say about half-way.  The top partition should be dedicated to OSX (uncheck the os9 capability if you aren't using that), and the "bottom" partition window should be just left as free space.

To make it easier, grab the "combo-update" from Apple from 10.4.  That way once osx is installed you can just apply the combo update to bring you up to 10.4.11 in one shot.  You'll still need to update all the rest, but osx will tell you if you don't want to reinstall the other things by yourself.

Then when it comes time for the Ubuntu install, just let guided partitioning know to "use free space".

Once Ubuntu is installed, at the second stage boot: prompt, you can take your pick of either osx by hitting the "X" key, or Ubuntu with the "L" key for Linux.  The second-stage will automatically time out, so if you need more time to make a decision, just hit TAB and that will stop the countdown and await your decision.

---

### Post by lse123 on 2009-01-02
To ALL Questions answer is "yes" ...?

May I also run one of these from usb flash drive(bootable) or cd live(bootable) , from a MAC MINI(I plan buy an intel 2 one_2.0GHz_latest) ?
ALL Linux distributions run on the MAC ?

---

### Post by stream303 on 2009-01-03
mattpenguion09: With your G4 reference, that is a PPC architecture, and the answer is yes with a caveat - you have enough ram to run the live desktop installer, BUT you might end up having to manually modify your /etc/X11/xorg.conf anyway - so in this case it would be best to use the "alternate" text-based installer initially.

Also, a lot depends on exactly what you want to do with it.  Run a server?  Fully-blown desktop?  Image / audio editing?  Know that in the case of PPC, flash and 3D are problematic.

At the very least, look at the stickies and check out the faqs to see what you might be getting into.  Unfortunately, for many ppc boxes, it isn't plug n play.

Lse123: Your reference to buying an Intel mac-mini is best answered by the Intel faq and other threads here by the excellent Intel Mac group.  Again, it may not just be a drop-in installation and you'll have to rely on your own searching and other community support - again all depending on exactly what you want to do with it.

Eek - I see you have been answered already in another thread.

---

