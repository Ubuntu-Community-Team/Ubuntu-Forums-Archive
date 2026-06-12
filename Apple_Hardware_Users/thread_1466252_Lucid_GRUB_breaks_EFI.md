---
title: "Lucid: GRUB breaks EFI"
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by Zannek on 2010-04-30
In previous versions of Ubuntu, I had no issue installing the OS to my MacBook (5,1 model). In Lucid's installer, when clicking "Advanced" like instructed in the [generic Mactel installation guide]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation"), there is no /dev/sda3/ option. I sought advice by browsing these very forums and asking in #ubuntu on IRC. The general advice I got from both was to ignore what the intstructions said, and to install grub to /dev/sda/, as there was no way it could override my Mac's EFI.

I would like to announce now that this is quite likely the wrong course of action. Since attempting this method, my MacBook now no longer boots without me holding down the 'alt' key so that a list of bootable devices come up. This occurs even with rEFIt installed. Thankfully, both the OS X partition and Ubuntu boot just fine, with Grub appearing when choosing the Ubuntu partition.

I'm starting this thread for three purposes:


[LIST]
[*]To warn Mactel users that installing Grub to /dev/sda/ apparently borks your EFI.
[*]To find out what the correct method of installing Lucid to a Mac is.
[*]And, if it's not too much trouble, to find out how to fix my Mac (somehow, I don't think taking it to an Apple Store at this point in time would help much).
[/LIST]

---

### Post by johnystevenson on 2010-04-30
zannek

i am in the same situation with holding the alt key now, but because i deleted a partition too many during my lucid install.

I have no refit anymore and no osx but i need to get past the holding down the alt key.

will follow your post and see if i come up with anything myself to help

johny

---

### Post by zeroti on 2010-04-30
Zannek: are you sure that you didn't choose the "select startup disk" option in os x? if you do that, I think it borks your boot process. I think there's some way to reinstall something somewhere, (the bootstrap maybe?) but I'm not really experienced in that area.

---

### Post by Cygni on 2010-04-30
> **Zannek said:**
> 
[LIST]
[*]To find out what the correct method of installing Lucid to a Mac is.
[/LIST]
I used a boot manager, specifically Refit, and the installation was easy peasy.
Not sure if installing it now would make a difference, however, for your next install I highly recommend. :)

---

### Post by jacques4x4 on 2010-04-30
Cygni,  I also have used rEFIt for my boot manager and I can not get 10.04 to install.  I use bootcamp to resize the drive, then reboot using the Ubuntu 10.04 CD, then with gparted I delete the Fat 32 partition and let the installer partition the free space.  However on the last dialogue box of the installer when I choose the advanced button I cannot choose to install grub to dev/sda3

Any work arounds?

thanks

Jacques

---

### Post by Zannek on 2010-05-01
> **Cygni said:**
> I used a boot manager, specifically Refit, and the installation was easy peasy.
Not sure if installing it now would make a difference, however, for your next install I highly recommend. :)

I installed according to the generic Mac installation  instructions, which I link to in my first post. This means I had rEFIt  installed BEFORE I even booted up the live cd. Secondly, even with rEFIt  installed, I now have to hold down 'alt' to even boot rEFIt.

> **zeroti said:**
> Zannek: are you sure that you didn't choose the "select startup disk" option in os x? if you do that, I think it borks your boot process. I think there's some way to reinstall something somewhere, (the bootstrap maybe?) but I'm not really experienced in that area.

I have tried multiple times setting the startup disk in OS X's preference pane to no effect. I am quite certain that this is a side effect of Grub being installed to /dev/sda instead of /dev/sda3 as it is during a normal dual-boot installation of Ubuntu onto Mac.

---

### Post by xxander on 2010-05-01
I did exactly what Jacques4x4 did, and there is no /dev/sd3 option..

WHAT CAN WE DO??

---

### Post by zeroti on 2010-05-01
> **Zannek said:**
> I have tried multiple times setting the startup disk in OS X's preference pane...

I'm pretty sure that that's what you *don't* want to do. I don't know about GRUB, but it's a problem with yaboot (for older ppc machines):

[https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot)

you might want to try resetting your pram. if that doesn't work, you can prob. use some command in ubuntu to reset your GRUB installation.

---

### Post by Zannek on 2010-05-01
> **zeroti said:**
> I'm pretty sure that that's what you *don't* want to do. I don't know about GRUB, but it's a problem with yaboot (for older ppc machines):

[https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot)

you might want to try resetting your pram. if that doesn't work, you can prob. use some command in ubuntu to reset your GRUB installation.

It worked! Macbook now boots just dandy. I'd like to know, however, just where has Grub been installed to?  And in the inevitable future event that I need to remove the Ubuntu installation, how do I remove it?

---

### Post by kosumi68 on 2010-05-01
> **Zannek said:**
> It worked! Macbook now boots just dandy. I'd like to know, however, just where has Grub been installed to?  And in the inevitable future event that I need to remove the Ubuntu installation, how do I remove it?

The grub is a string of bytes installed at the very beginning of the partition where you install Ubuntu. If you reformat or remove the partition, one would have to be into computer forensics to find out that Ubuntu was ever installed on it.

---

### Post by jacques4x4 on 2010-05-02
Zannek  I am a little unclear as to what you did to resolve this.  

Resetting your pram?  (parameter random access memory)???

Could you clarify?

thanks

---

### Post by Zannek on 2010-05-02
To reset PRAM (on an Intel machine) hold down Command+Alt+P+R on startup. It seemed to work sporadically however, as after booting back into OS X, the problem re-appeared. I have a feeling that GRUB did very much bork my EFI partition, but hopefully I can restore it somehow. :?

---

### Post by jacques4x4 on 2010-05-02
> I have a feeling that GRUB did very much bork my EFI partition, but hopefully I can restore it somehow.

It totaled mine..  I had to boot with the OSX install disk, use the disk utility to format the drive using the GUID partition table..

Then, thank goodness for the Time Machine, I restored the OS and my data..  

I believe this is the only way back

---

### Post by Zannek on 2010-05-02
> **jacques4x4 said:**
> It totaled mine..  I had to boot with the OSX install disk, use the disk utility to format the drive using the GUID partition table..

Then, thank goodness for the Time Machine, I restored the OS and my data..  

I believe this is the only way back

That's probably a good idea. I'll try it when I get the time. Thanks. :)

---

### Post by Nikos.Alexandris on 2010-05-03
> **xxander said:**
> I did exactly what Jacques4x4 did, and there is no /dev/sd3 option..

WHAT CAN WE DO??

I've seen this when I installed Kubuntu lately. I just let it install grub at **/dev/sda** and it worked!

Of course you should have a backup of everything (don't you?) before trying it out. Be warned that I really have no idea why it did not work (with the Ubuntu installer) pointing at **/dev/sda3**.

Regards

---

### Post by pafufta503 on 2010-05-03
i need a bit of clarification.  what i've gathered is, the installation will cause damage to the EFI partition?  is this because you are installing it to the same harddrive as OS X?  if i install everything to a seperate hard drive, will grub still bork things up?

the overriding question is, is it safe for me to install lucid on my in macpro, or will it break my boot process?

---

### Post by gdgtfiend on 2010-05-04
> **pafufta503 said:**
> i need a bit of clarification.  what i've gathered is, the installation will cause damage to the EFI partition?  is this because you are installing it to the same harddrive as OS X?  if i install everything to a seperate hard drive, will grub still bork things up?

the overriding question is, is it safe for me to install lucid on my in macpro, or will it break my boot process?


I would wait to install 10.04 until we know that it is 100% safe. If there is a NEW install article on the Mactel Wiki you can try to do that.

As of now it is not particularly safe. So if you do it, BACK UP YOUR HDD!

If anyone has any info on the subject please write back. You can also msg me on irc @ n06 on freenode.

Speaking of irc, is anyone interested in oping a mactel support irc? I don't have the expertise to do it, but it would be nice to have one.

EDIT: I just found this info, I'm not very good in command line, so I thought someone who has some chops might try this [http://www.ehmac.ca/anything-mac/43204-restore-efi-partition-proper-bootcamp-operation.html](http://www.ehmac.ca/anything-mac/43204-restore-efi-partition-proper-bootcamp-operation.html)


Thanks,
-gdgtfiend

---

### Post by jacques4x4 on 2010-05-04
> EDIT: I just found this info, I'm not very good in command line, so I thought someone who has some chops might try this [http://www.ehmac.ca/anything-mac/432...operation.html](http://www.ehmac.ca/anything-mac/432...operation.html)

Wow...  Zannek this could potentially save you a lot of time..

---

### Post by bean123 on 2010-05-05
Yeah, I have seen this before, grub2 seems to mess up GPT partition when running from the installer. One solution is to skip the boot loader step. After reboot, use live CD to open a rescue shell on the root device, and run this manually:

```

grub-install --force /dev/sda
update-grub

```

---

### Post by thomas.clark on 2010-05-21
Ugh.  For a first-ever ubuntu install, this was a nasty surprise.

I don't know squat about any of this, but I managed to trick my system, I think, into booting back into OS X.

Not only did I have to hold down alt, but my Mac HD wasn't even an option to select as a Startup disk.  So, having booted into OS X via the hold alt method, I then set the Startup Disk to network.  I then tried to reboot without my network cable plugged in, which brought up the spinning earth as it tried to boot via the network, and eventually defaulted into OS X.  I'd accidentally done this once before for another reason, and found that it did successfully bring back the Mac HD as an option for Startup Disk.  I selected it to rebless, then dumped all the rEFIt folders.  Now I'm booting directly into OS X.

I haven't a clue what GRUB is or what it's doing or not doing in my EFI partition, but I'm hoping I don't find out.  Should have stopped and backtracked when there was no sda3 option for the boot loader.  Darn impatience.

In the meantime I'm going to retry with 9.04.  I do want to get into this ubuntu thing.

---

### Post by hybridcore on 2010-05-22
Maybe it will help: I've spent last few days on installing and reinstalling couple of ubuntu distributions.
I had strange problem: all of live cd's did work (not perfectly but worked :)) but after install I got black screen after choosing ubuntu from grub list.
The very first thing I did before installing linux was getting rEFIt, as mactel wiki says so. Then I tried to install 10.04 (got the same partition choosing issue) and 9.10 (got black screen too).
Time has come for 9.04 and it did work and, not without my surprise, it worked quite good (including recognising my airport).
The target distribution was 10.04 because of its LTS. So I upgraded system to 9.10 first. There appeared a graphic issue then (with the first boot after upgrade), which was fixed with restarting gdm from console. After that I did two steps: enabling nvidia driver and upgrading to 10.04.
I know that it takes some time (and maybe it's not a pro solution) but it was the only way I could get my macbook+10.04 duet working I've known of.
My mac is 5.2 revision.
Everything works according to the mactel wiki list. No problems with grub.

---

### Post by jamesixgun on 2010-05-22
Ok. I had the same problem with GRUB grubbing up EFI, but fixed it thanks to another thread in this forum. 

Rather than link directly, I'll post the workaround here, though your mileage may vary.

1. Start out by backing up your mac to an external drive. 
2. Install rEFIt. (restart two times, and it will take effect).
3. Open Boot Camp and set up a windows partition.
4. Shut down and boot into the Lucid install disk.
5. Select the option to try linux without installing (ie. boot into the live CD).
6. Open gparted (System --> Administration)
7. Use gparted to delete the boot camp partition. 
8. Remain in gparted, and create a tiny partition just after the mac partition (512M should be plenty). Name it BOOTCAMP or something memorable and set the file system as NTFS.
9. Apply changes. (BE SURE TO APPLY CHANGES.) Then exit gparted.
10. Start the Lucid installer from the desktop. Follow the locations and language and whatnot. When it asks you to prepare the disk, choose "Specify partitions manually."
11. Select the partition you just created (which should be /dev/sda3) , choose Change --> use as NTFS. At Check Format choose mount point = /windows. 
12. Select the free space. You'll need to create two partitions here, one for Ubuntu, and one for Swap at the end. I set upFor the first partition, choose Use as Ext4, mount point = / . In the remaining section (I used 4096 bytes, ie. 4 Gig) choose Add --> use as Swap. Click ok.

If everything worked as expected, you'll have 5 partitions: sda1 (EFI); sda2 (OSX); sda3 (NTFS); sda4 (where Ubuntu will go); and sda5 (the swap).

13. Go through the rest of the installation. On the last screen (screen 8, iirc) click the Advanced button and choose to install the boot loader to /dev/sda3, which should now appear. 

Click Install and wait 20 or 30 minutes while Ubuntu installs.

14. when the installation is complete, restart. In the rEFIt menu, choose the partition tool and resync. 
15. Power down your computer.
16. Power up and you should be just fine. rEFIt will present OSX and Lucid and allow you to choose.

If you're not dual-booting, you should still choose to set up a special partition for GRUB, since it will whack out your EFI even if Ubuntu is the only thing there. (Get into the live CD, go gparted, wipe the drive, set up a partition for GRUB, one for Ubuntu, and one for the swap, and be sure to install GRUB in dev/sda2/ instead.)

Good luck! I hope this works out for everyone. It worked brilliantly on my revA Macbook (1,1), and I'm typing this from the Mac side just now. Good times.


Oh. And I just realized that I have my notes from my install, and they include a link to [the thread]("http://ubuntuforums.org/showthread.php?t=1468240&page=5") where I originally found this. 

All credit goes to Jacques4x4 who originally developed this method.



Edit: I'm now on the Ubuntu partition, and realized that I forgot to  mention one small thing. When you start up Ubuntu via rEFIt, the GRUB  will assert itself and give you some additional boot options (straight  Linux, safe Linux, shutdown, OSX, and something else, if I recall). GRUB  will automatically boot into Ubuntu after 10 seconds, or you can just  hit 'return' and boot right into Ubuntu. Not a big deal, to me, but  those of you who really value your boot up times may want to search for a  way to teach GRUB to shut up.

---

### Post by thomas.clark on 2010-05-22
> **jamesixgun said:**
> 
If everything worked as expected, you'll have 5 partitions: sda1 (EFI); sda2 (OSX); sda3 (NTFS); sda4 (where Ubuntu will go); and sda5 (the swap).

13. Go through the rest of the installation. On the last screen (screen 8, iirc) click the Advanced button and choose to install the boot loader to /dev/sda3, which should now appear. 


Is is not necessary to install the boot loader to the same partition as Ubuntu?  What's the difference/advantage of doing this this way?  Is it simply a trick to create an available partition because there's no way to work with the installer to actually put the boot loader on the same partition as Ubuntu?

Seems like if you're using the installer to specify the partitions manually, then creating the NTFS partition is redundant.  Can't just create a larger parition for Ubuntu in sda3 and then a swap as sda4?

(I'd test it myself, but I'm chicken)

Also, how does this de-break having previously installed the boot loader to /dev/sda ?

forgive me if these are super basic questions.  I'm way new to this.

---

### Post by jarinlonia on 2010-05-23
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=arial]Long story short, a flaw in my 9.04 live CD has caused a GRUB file to disappear. My Ubuntu live cd's stopped working, Puppy Linux live CD can't find GRUB in my computer, and a Fedora live CD can't even boot. I've tried everything I can think of to fix it, but nothing's worked. Any ideas?

[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by jamesixgun on 2010-05-23
> **thomas.clark said:**
> Is is not necessary to install the boot loader to the same partition as Ubuntu?  What's the difference/advantage of doing this this way?  Is it simply a trick to create an available partition because there's no way to work with the installer to actually put the boot loader on the same partition as Ubuntu?

For me, the boot loader would never install to the same partition as Ubuntu (ie. sda3, though sda3 never existed without this trick). Without building a special little partition for GRUB, it will create a pseudo-partition that extends from the very beginning of the drive (sda1, where EFI lives), over OSX, and through a little grubby space it built for itself, and then give Ubuntu and swap spots at the end. 

> Seems like if you're using the installer to specify the partitions manually, then creating the NTFS partition is redundant.  Can't just create a larger parition for Ubuntu in sda3 and then a swap as sda4?

As noted above, unless you build a tiny little partition expressly for GRUB, GRUB will bork your EFI. For some reason, without a specified partition, created expressly for GRUB, GRUB will create a box for itself that covers EFI and OSX. It will bork your EFI, leave Ubuntu in a strange, non-functional-but-still-written-to-disk netherworld, and force you to load OSX via the alt key at startup.

> Also, how does this de-break having previously installed the boot loader to /dev/sda ?

Sorry, but this does not de-break anything. For that, you'll need to wipe your drive with Disk Utility on your OSX disk (specifying GUID partition table), then reinstall everything via a backup. Sorry, but I've not seen another work-around.

> forgive me if these are super basic questions.  I'm way new to this.

And no worries. I'm very new myself and just trying to share a trick that worked for me. Maybe it will work for you too?

---

### Post by jamesixgun on 2010-05-23
@jarinlonia: you could try downloading a new 9.04 iso, and creating a new install disk? Beyond that, I've got no idea.

Edit: I mean, I guess you'd have to wipe your hd and start again with a fresh GRUB and all. Hopefully some others will have better options.

---

### Post by thomas.clark on 2010-05-23
@[COLOR=Black]jamesixgun

Thanks for the explanation.  Will continue to play around and reinstall OS X if necessary.  
[/COLOR]

---

### Post by thomas.clark on 2010-05-24
There is a FIX!!!  Fix your GRUB and mbr w/o reinstalling OS X.  Simple.  Elegant.

[http://ubuntuforums.org/showthread.php?p=9350233#post9350233](http://ubuntuforums.org/showthread.php?p=9350233#post9350233)

Worked for me, no problems.  Proceed at your own risk.

---

### Post by bheussler on 2010-05-25
> **jacques4x4 said:**
> Cygni,  I also have used rEFIt for my boot manager and I can not get 10.04 to install.  I use bootcamp to resize the drive, then reboot using the Ubuntu 10.04 CD, then with gparted I delete the Fat 32 partition and let the installer partition the free space.  However on the last dialogue box of the installer when I choose the advanced button I cannot choose to install grub to dev/sda3

Any work arounds?

thanks

Jacques

Make sure your computer shuts down all the way before you try and reboot.  Sometimes if you don't and you just restart rEFIt doesn't work the first time

---

