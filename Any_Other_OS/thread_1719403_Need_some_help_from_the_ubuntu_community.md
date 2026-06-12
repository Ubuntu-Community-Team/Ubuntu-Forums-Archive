---
title: "Need some help from the ubuntu community"
date: 2011-04-01
forum: Any Other OS
---

### Post by linuxnewb2 on 2011-04-01
Guys having a real problem. Decided to cut ties with microsoft and get a respectable OS ... aka: linux. Needed something easy and people were saying linux mint, a close cousin to ubuntu was super user friendly.

Trying to get my gf, as well as myself to become a linux family. Needed something that had the look and feel of winblows. So installed linux mint in dual boot with XP home, SP3. Having some issues now and not sure what to do.

It's a strange situation. When I boot up linux mint 10.00 latest version. The hard drive light stays on. If I go to menu>quit>suspend ... Then let it go to suspend/standby. Hit the power button and let it fire up again. Then press any keyboard key ... it boots back up and the hard drive light works normally again.

Meaning goes off once the OS is loaded and stays off until something gets called up to get it working again.

Thing is this, think I made a mistake going with mint, after all the great things I'd heard about ubuntu. Wondering if it'd be possible to overwrite the mint install with ubuntu from the livecd. And just use it's partition to install ubuntu 10.10 ?

Already have a 700mb swap file set up for mint. Would this cause problems folks ? Would it be safe to let ubuntu overwrite mint and grub overwrite the one that was installed when I dual booted mint/xP ?

Would sure appreciate some help from the linux community on this. And the ubuntu community is famous for the help it offers newbs like me. Any recommendations would be much appreciated ... thanks.


d.

---

### Post by linuxnewb2 on 2011-04-01
Also, what about if I install ubuntu into the mix as well. Left a nice chuck of hard disk for it to occupy. Was planning on putting the 3 OS's side by side. XP home, linux mint and ubuntu and letting her decide which was the best one to get away from Micro$oft.

So what happens if I go ahead and install Ubuntu on the drive ? Will it's grub2 overwrite the existing linux mint grub and take over managing the disk ? Sighs ... again, just grasping at straws and hoping for a hand with this.

---

### Post by Lateralis on 2011-04-01
Hi there, and welcome to the "light" side! 

As for your second question, Linux distributions sit happily side-by-side, mainly because Grub is so flexible.  If you have two partitions, one with Linux Mint and one with Ubuntu you'll have two separate options in the Grub menu - one for Mint and one for Ubuntu.  (There is a slight caveat to this, but we'll ignore that until you decide what you want to do for definite.)  

Just for the record, if you did go down the root of having both Mint and Ubuntu, the one swap partition will work for both - a swap partition is not tied to any particular Linux distro. Also note that if you want suspend and hibernate to work properly it is a good idea to have your swap partition *at least* the same size as your RAM.  I seem to recall other people saying it should be twice the size, but off the top of my head I can't vouch for that.  (Google should be able to though, if someone else doesn't clarify this point for me.)

As for your primary question: of course it is possible to overwrite Mint with Ubuntu!  The Ubuntu install will overwrite everything on the partition in the same way that Mint probably overwrote everything on the previous NTFS (?) partition.  Ubuntu will also install Grub to the MBR and detect which OSs there are.  if there's just Ubuntu and XP then the Grub boot menu will have just these options at startup.

---

### Post by strafe_sawdoffe on 2011-04-01
Short answer to everything is: go for it.

I just tested this in a VM and there does'nt seem to be any problem. Boot the computer from the Ubuntu live CD, and after it asks you about your language, location and keyboard method, you'll get the choice to install Ubuntu over the entire disc, over a selected partition (use this if you want to get rid of Mint... just make sure you grab the Mint partition and not the Windows one, for now), or you can specify a side-by-side configuration. The Grub from Ubuntu will take over and, if everything works as designed, will let you chose between Windows, Mint, and Ubuntu.

---

### Post by strafe_sawdoffe on 2011-04-01
> **Lateralis said:**
> Hi there, and welcome to the "light" side! 

As for your second question, Linux distributions sit happily side-by-side, mainly because Grub is so flexible.  If you have two partitions, one with Linux Mint and one with Ubuntu you'll have two separate options in the Grub menu - one for Mint and one for Ubuntu.  (There is a slight caveat to this, but we'll ignore that until you decide what you want to do for definite.)  

Just for the record, if you did go down the root of having both Mint and Ubuntu, the one swap partition will work for both - a swap partition is not tied to any particular Linux distro. Also note that if you want suspend and hibernate to work properly it is a good idea to have your swap partition *at least* the same size as your RAM.  I seem to recall other people saying it should be twice the size, but off the top of my head I can't vouch for that.  (Google should be able to though, if someone else doesn't clarify this point for me.)

As for your primary question: of course it is possible to overwrite Mint with Ubuntu!  The Ubuntu install will overwrite everything on the partition in the same way that Mint probably overwrote everything on the previous NTFS (?) partition.  Ubuntu will also install Grub to the MBR and detect which OSs there are.  if there's just Ubuntu and XP then the Grub boot menu will have just these options at startup.

Lateralis beat me to it^

---

### Post by linuxnewb2 on 2011-04-01
You guys are awesome. I see the famous ubuntu support community lives up to it's name. Don't doubt the distro does too. Really appreciate the help. Sorry I didn't answer sooner. I've been sweating bullets wondering how to sort this out.

Just coming from M$tinks ... I'm out of my league with linux atm. Thanks again for clarifying for me. Time to overwrite mint. Can always put it back on another partition later. Should've went with my gut to begin with and installed ubuntu instead to begin with.

Just other people use the comp and are totally M$ dependent. Wanted to make it a distro that was as close as poss, so thought mint would be more user friendly for everyone involved.

Sighs ... you folks have given me the confidence to go ahead and try it ... ( crosses fingers )


d.

edit: Went with a 700mb swap. This PC has 512mb RAM. Thought about going with a swap the same size as the installed RAM. But googled somewhere about 1.5 times being a rule of thumb, sighs.

Anyway, thanks again for helping.

---

### Post by linuxnewb2 on 2011-04-02
Well everything survived. Reinstalled ubuntu, got a wild hair reinstalled mint over it. I have no idea what Im doing. But still prefer the ubuntu support forum crowd to the mint crew, lol. Oh well, ubuntu and mint are 1st cousins anyway .. right. :D

Not really  messing with it much until I have time to actually dig into linux. Got a little better handle on things this time around. Both operating systems running pretty much normally.

Still don't get why the HDD LED stays on in either ubuntu or mint ... Is beyond me ( linux newb.) Then once it starts up I hit the suspend, it spins down, press the start/power button, spins back up ... enter password .. then, no more LED problems. Weird, shrugs. This is an old comp. Tis my gf's, almost 10yrs old now. Hell things a senior citizen in computer years.

:D

---

### Post by matt_symes on 2011-04-02
Hi

The only issue with sharing a swap partition across distro's is a potential issue with hibernation as the memory is dumped to the swap partition during hibernation.

Kind regards

---

