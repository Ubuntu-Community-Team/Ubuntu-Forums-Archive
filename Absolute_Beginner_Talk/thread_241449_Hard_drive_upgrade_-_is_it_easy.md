---
title: "Hard drive upgrade - is it easy?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by petersjm on 2006-08-22
Hi guys,

I'd like to buy a new HDD with more storage space than I currently have and I'm [thinking about getting this one](http://www.ebuyer.com/UK/product/59736) - although I've no idea about HDDs etc so not sure if 1) it's compatible with Ubuntu, and 2) it's compatible with my Dell Dimension 2400 Desktop PC. Anyone got any clues?

Now, before I buy it, this is what I want to do: I'd like to copy over everything from my current drive to the new drive and as far as I'm aware I need to make the new drive a slave? Whatever that means. Then I need to remove the original drive and make the new one the master (?) so it's the first-boot drive. These are all XP terms as far as I can tell, but is it a similar process in Ubuntu? Or maybe I can just plug the new one in and have Ubuntu recognise it immediately? I know I'll need to use gparted to format it as ext3, that's not a problem.

Can anyone offer any useful advice or help on this? Many thanks! :D

---

### Post by richardward101 on 2006-08-22
Ok, first compatability.
Interface wise, all hard disks are (for all practical purposes) identical. All HDD's work in ubuntu (unless you've got some funky scsi set up, in which case, who knows? This drive'll be fine and dandy in ubuntu. As for your PC, open it up, and if theres a spare IDE cable end then yes, you can use it (more than likely).

next, installing and tips.
I think you'll be pleasantly surprised by how easy it is. When your pc boots it looks through the HDDs until it finds one with a valid boot sector (IE one with grub installed). once it hits grub, grub will tell it to load the OS on the FIRST drive (by default, assuming you haven't manually messed about with grub). All you need to do is set the new drive to master and the old drive to slave, and all should be dandy (if you try to boot up like this grub should give you an error, don't worry, it won't after you move your files across).
Now for the copying. boot from your ubuntu live cd, and use GParted to format the new disk (which should be listed as hda).
next, open a terminal and type the following:
```
sudo mkdir /olddrive
sudo mkdir /newdrive
sudo mount /dev/hda1 /newdrive
sudo mount /dev/hdb1 /olddrive
sudo cp /olddrive/* /newdrive/
```
don't delete your old stuff till you know its worked!
Now reboot, remove the cd and, if your lucky, it should boot up just fine, as if nothing had happened. Just one thing, you should check once its booted that its still using the swap space, go into to the system monitor and see how much free swap space there is and make sure its using the swap partition. At this point you can delete the stuff on your old disk, but only once you know everythings working.
Hope that helps, if you need clarification on anything or if anything goes wrong then post back here.

---

### Post by petersjm on 2006-08-22
Many thanks, Richard. That all sounds straight-forward and easy! My only concern at the minute is:

> All you need to do is set the new drive to master and the old drive to slave

Is that a setting I do *within* Ubuntu, or a switch I need to flick on the side of the HDD? As you can tell, I'm a bit clueless! Thanks again!

---

### Post by aeon on 2006-08-22
there are switches/prongs on the back of the HDD that control wether a disk is master, slave or cable-selected. just have a look on the back of it, there'll probably be a schematic on the disk somewhere too, telling you how to set it for master/slave.

Don't worry, it's not that hard :wink:

---

### Post by petersjm on 2006-08-23
Thanks aeon. That's all I needed to know. As long as there's a straightforward way of doing something, I'm willing to roll my sleeves up and get stuck in...!

Right, as for formatting to ext3, should I boot up the 'puter once first to make it recognise the new disk, then boot again from gParted LiveCD to format? Or do I not need to boot first for recognition? Then I can boot again and copy files as explained by Richard above. Am I making sense?

---

### Post by anaconda on 2006-08-23
cp /olddrive/* /newdrive/

won't copy everything!! You have to use -R switch so that all directories, AND also their subdirectories are copied.

I would suggest, that put the new hdd (master) in, install ubuntu from CD to the new hdd, and THEN copy everything you need  from your old hdd... and install all the aplications you need..

It is only good to re-install your operating system sometimes.

And no you don't have to boot it first for regognition..

Just copying the files wont make your new hard-disk bootable! Maybe if you copy all the files, and then install GRUB to the new disk.. (it has to be installed, copying wont do. )

---

### Post by iampoch on 2006-08-23
I'm interested with this topic as I'll also be upgrading my HDD.  I'd like to ask if Norton Ghost's disk imaging utility can help transfer my current HDD setting (OS's, partitions, files, etc.) to the new hard drive.  I plan to upgrade to a SATA 300GB HDD and my current one is an IDE 160GB. Will these affect the transfer in any way? And is what I'm thinking of possible?

---

### Post by petersjm on 2006-08-23
> **anaconda said:**
> cp /olddrive/* /newdrive/

won't copy everything!! You have to use -R switch so that all directories, AND also their subdirectories are copied.

I would suggest, that put the new hdd (master) in, install ubuntu from CD to the new hdd, and THEN copy everything you need  from your old hdd... and install all the aplications you need..

It is only good to re-install your operating system sometimes.

And no you don't have to boot it first for regognition..

Just copying the files wont make your new hard-disk bootable! Maybe if you copy all the files, and then install GRUB to the new disk.. (it has to be installed, copying wont do. )

Thanks, Anaconda. I guess, then, it's probably easier to drop the old drive out, boot the new drive, install Ubuntu and all my additional programs, then -- can I? -- pick up the old drive again as master and make the new one slave, then simply copy across my /home folder and personal folders. Then drop the old one again and make the new one the master and only drive...

---

### Post by szf on 2006-08-23
I've had a problem with mixed-manufacturer hard drives and the 'cable select' setting. I recommend using 'master/slave' - although you may have to pull the current hard drive to check the default setting. 

For comparison, this is my setup:

/dev/hda = dvd/master
/dev/hdb = hdd/slave
/dev/hdc = hdd/master

---

### Post by jimcooncat on 2006-08-23
Most computers come with two IDE cables -- either flat ribbons or big round cables with large flat connectors. There are three connectors usually, the one on the long side plugs into your motherboard or a special card. The other two connectors go to your hard drive or cd/dvd drive.

Look closely before plugging in. There's one pin missing on the motherboard, and one hole filled in on the cable. Make sure they match up, or you might be straightening out the pins with pliers if you push too hard.

If you need to buy new cables, or are playing with drives and have a little money anyway, swap out your flat cables for round ones. The round ones will let air circulate around the case better. Sometimes though computers are made for the flat cables, snaking them through small rectagular holes. Should be easy to see if swapping makes sense.

Make sure you blow the dust bunnies out of the case and power supply with a can of compressed air. Don't use a vaccuum unless the nozzle is specially grounded -- or you can blow your motherboard with static electricity.

For best performance, if you use two drives at the same time,  put them on different cables if you can. For instance, if you copy a lot of stuff from the CD to the main hard disk, put the CD on one cable and main HD on the other, and your other drives on the second connectors. 

When adding drives, always set them to either master or slave. Cable select only seems to work a quarter of the time for me, and I don't bother anymore -- I set them all manually. For each cable, set one drive to master and one to slave, it doesn't matter which one. 

Usually there's a diagram on the drive's case that shows you how, and sometimes you have to remove another piece of metal to see the diagram. Sometimes the diagram is upside down, so you might have to look for letters or numbers next to the jumper pins to know which way they mean is "up".

What this shows you is where to move the jumper, a little plastic piece with a metal connector inside. Be careful not to drop this on the floor, if you lose it you'll have to go to the computer junkyard and get another! Pull the jumper straight out, and place it over the pins you want, and slide it on gently. Don't force, this means you're doing something wrong.

Old duffers like me may need strong reading glasses or magnifying lens handy before starting. Hope this helps!

---

### Post by seshomaru samma on 2006-08-23
> **iampoch said:**
> I'm interested with this topic as I'll also be upgrading my HDD.  I'd like to ask if Norton Ghost's disk imaging utility can help transfer my current HDD setting (OS's, partitions, files, etc.) to the new hard drive.  I plan to upgrade to a SATA 300GB HDD and my current one is an IDE 160GB. Will these affect the transfer in any way? And is what I'm thinking of possible?

I used Norton Ghost to clone copies of Xubuntu, it worked well , except I usually had to reinstall Grub. I reinstalled Grub with Ubuntu live CD but now i found a faster way with [this ]("http://www.sysresccd.org/Main_Page") , it also has  Partimage which is Linux' version of Ghost.

---

### Post by jimcooncat on 2006-08-23
> **seshomaru samma said:**
> I used Norton Ghost to clone copies of Xubuntu, it worked well , except I usually had to reinstall Grub. I reinstalled Grub with Ubuntu live CD but now i found a faster way with [this ]("http://www.sysresccd.org/Main_Page") , it also has  Partimage which is Linux' version of Ghost.

He's talking about the System Rescue CD, and it's worked for me well. If you're using LVM, it's got backup tools for your partitioning scheme, too!

---

### Post by robins_web on 2006-08-23
If you've got an empty USB port, you can go the lazy route--which is what I'm about to do with my laptop: buy an external USB drive and plug it into the USB port. You'll still have your original hard disk, and you can format the USB drive any old way your heart desires!

I decided to go this route because I have 2 laptops running Ubuntu and I would like extra storage space on both of them. With a USB drive, I'll be able to switch it back and forth between systems whenever I want. Also a great way to keep my files in sync on both machines.

---

### Post by richardward101 on 2006-08-24
> **anaconda said:**
> ```
cp /olddrive/* /newdrive/
```
won't copy everything!! You have to use -R switch so that all directories, AND also their subdirectories are copied.
Yeah, sorry, my bad.

> **anaconda said:**
> Just copying the files wont make your new hard-disk bootable! Maybe if you copy all the files, and then install GRUB to the new disk.. (it has to be installed, copying wont do. )
In my defence, yes it would work if my instructions were followed and the old drive stayed in permanently (tho don't worry about this if you're re-installing!) because the boot would fall back to the old drive and it would boot the stuff on the new drive fine.

> **petersjm said:**
> Thanks, Anaconda. I guess, then, it's probably easier to drop the old drive out, boot the new drive, install Ubuntu and all my additional programs, then -- can I? -- pick up the old drive again as master and make the new one slave, then simply copy across my /home folder and personal folders. Then drop the old one again and make the new one the master and only drive...
It may indeed be a good idea to install it all again, It'd make things simpler in the long run I suspect.
However, if you do reinstall rather than just copy, It'd probably be easier  to put the new one in as master from step one. my advice, Keep it simple;
1, take old drive out.
2, put new one in (set as master).
3, install ubuntu.
4, insert old disk (as slave).
5, copy files.
6, dispose of old drive if thats what you want (or better still use it for backup purposes)

If you need help mounting the old drive to copy the old drive for copying (and indeed longer term use) do come back and ask.

---

### Post by Tom Brokaw on 2006-08-24
> **jimcooncat said:**
> Make sure you blow the dust bunnies out of the case and power supply with a can of compressed air. Don't use a vaccuum unless the nozzle is specially grounded -- or you can blow your motherboard with static electricity.

Don't neglect this step - dust can cause your cooling devices to stop working and can have serious consequences.

> For best performance, if you use two drives at the same time,  put them on different cables if you can. For instance, if you copy a lot of stuff from the CD to the main hard disk, put the CD on one cable and main HD on the other, and your other drives on the second connectors. 

To clarify, you won't want to mix optical and hard drives on the same cable.  Optical drives run at a significantly slower speed, and the cables default to the slowest device's speed.  To get technical, optical drives use the ATA33 standard, whereas hard drives use ATA100 or sometimes ATA133.  That means that mixing them will bring about a reduction to a third or even a quarter of possible speed.

> When adding drives, always set them to either master or slave. Cable select only seems to work a quarter of the time for me, and I don't bother anymore -- I set them all manually. For each cable, set one drive to master and one to slave, it doesn't matter which one. 

That's funny, I've had the exact opposite experience.  I've had incorrectly set jumpers cause all kinds of boot problems.  Well, one kind of boot problem - wouldn't boot!  Rule of thumb: 

end of cable = master
middle of cable = slave

> Usually there's a diagram on the drive's case that shows you how, and sometimes you have to remove another piece of metal to see the diagram. Sometimes the diagram is upside down, so you might have to look for letters or numbers next to the jumper pins to know which way they mean is "up".

What this shows you is where to move the jumper, a little plastic piece with a metal connector inside. Be careful not to drop this on the floor, if you lose it you'll have to go to the computer junkyard and get another! Pull the jumper straight out, and place it over the pins you want, and slide it on gently. Don't force, this means you're doing something wrong.

Old duffers like me may need strong reading glasses or magnifying lens handy before starting. Hope this helps!

What he said.

---

### Post by petersjm on 2006-08-24
Well, all I can say is thank you to each and every one of you! You're all amazing! :D

I'm no real dummy when it comes to computers, but I'm more of a software kinda guy rather'n hardware.

Anyway, I'll be ordering the new HDD tomorrow (pay day! Yay!), and thanks to you guys I know what I'm doing now!

Oh, but one more thing... (there always is, isn't there?!) Once i'm set up with the new drive as master and the old one as slave, I've reinstalled Ubuntu on the new one, when I copy across the /home folder, will it pick up and use my themes, colours, Firefox profiles etc, as well?

---

### Post by jimcooncat on 2006-08-26
> **Tom Brokaw said:**
> To clarify, you won't want to mix optical and hard drives on the same cable.  Optical drives run at a significantly slower speed, and the cables default to the slowest device's speed.  To get technical, optical drives use the ATA33 standard, whereas hard drives use ATA100 or sometimes ATA133.  That means that mixing them will bring about a reduction to a third or even a quarter of possible speed.

I didn't realize that! I am just about to put in a second hard drive in one of my machines, and following my own advice I would have done it poorly, by making it a slave of the CD instead of the first hard disk. Thanks for commenting on my post.

---

### Post by richardward101 on 2006-08-27
> **petersjm said:**
> will it pick up and use my themes, colours, Firefox profiles etc, as well?

YES

Thats the best part, ALL configuration files for more or less everything are stored in home, in hidden folders (ones starting with a full-stop). When your copying the files, make sure you copy the hidden ones too, and it'll (hopefully) all work out fine.

The only things that wont be copied are things that you had to enter your password to change, eg shared folders, login screen themes, etc.

the only caveat is, make sure that the files still belong to you once you've copied them across. File permissions are done by user id number (not name), so it'll probably be fine of both the old and new home directories belong to the first account created (the one it make automatically on install). If not, you can always chown them so that they are correct:
```
 sudo chown your-username ~/ -R

```

---

