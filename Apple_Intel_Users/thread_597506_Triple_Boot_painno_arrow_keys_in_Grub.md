---
title: "Triple Boot pain:no arrow keys in Grub"
date: 2007-10-30
forum: Apple Intel Users
---

### Post by ffooky on 2007-10-30
I've managed to get triple booting to work on my white 24" iMac, at least in theory. I have Leopard and XP (Boot Camp) installed on my internal HD and Ubuntu 7.10 on a USB drive. The Linux boot volume is on the internal and the root & swap partitions on the USB.

 Everything functions well but I've come up against what seems to be a firmware problem with my gen of iMac. I have rEFIt installed and the menu offering me the choice of the three OSes pops up but if I select either Linux or XP, once the Grub window appears the arrow keys are not recognised so I just have to allow it to boot into Gutsy and have now lost access to XP (yep, worse things definitely do happen at sea).

 I'm led to believe that this is a firmware issue as MacBooks that suffered the same were fixed by a firmware update...it's just a case that the keyboard hasn't been recognised by the time the Grub screen appears. I've tried all the workarounds I've come across i.e. unplugging the keyboard, waiting until rEFIt has run for 10-15 seconds, using the page down to select the OS in rEFIt but no dice.

 Is changing my Ubuntu installation so that it uses Lilo rather than Grub a possible solution ? If so how do I go about doing it ? I still get excited by running './configure' in Terminal so please make any solutions noob-friendly.

---

### Post by cyberdork33 on 2007-10-30
I too have once again lost keyboard functionality in grub, and replugging the USB keyboard no longer works either. I don't know what has changed. It was working after the firmware update.

To avoid grub to boot windows, you need to first install grub to the ubuntu partition rather than the MBR.
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

Then boot the windows install cd and go into the recovery console. Then use the fixmbr command to place the windows bootloader in the MBR. 

After that, selecting the icon in rEFIt should boot into the correct OS.

Can others confirm if the keyboard is dead again in grub / Ubuntu CD bootloaders?

---

### Post by pxwpxw on 2007-10-30
Is it Leopard?

---

### Post by cyberdork33 on 2007-10-30
> **pxwpxw said:**
> Is it Leopard?

Good question, but I am pretty sure that was not it.

Stopped working before I upgraded

---

### Post by pxwpxw on 2007-10-31
**cyberdork33**

No change here on MacBook c2d, menu selection all works fine. Using only macosx10.4 installation, no Leopard.

**ffooky**

I don't know if the EFI firmware update has been icluded with your iMac, this fixed the keys startup bug until now.
 
The firmware updates came from 4 weeks back:
  	
iMac EFI Firmware Update 1.2 - liberalist 
[http://ubuntuforums.org/showthread.php?t=563052](http://ubuntuforums.org/showthread.php?t=563052)

---

### Post by ffooky on 2007-10-31
**pxwpxw**

I'm at IM61.0093.B07 which is the correct revision for my model.

**cyberdork33**

Sorry to be so dim but I'm not quite sure from the link you posted exactly how to proceed. Do I need to create a GRUB boot disk ? The root directory for Ubuntu on my external drive is not the first partition so do I need to chain-load ? If you could give me a real dummies' guide I'd appreciate it greatly.

---

### Post by pxwpxw on 2007-10-31
> **ffooky said:**
> **pxwpxw**

I'm at IM61.0093.B07 which is the correct revision for my model.

**cyberdork33**

Sorry to be so dim but I'm not quite sure from the link you posted exactly how to proceed. Do I need to create a GRUB boot disk ? The root directory for Ubuntu on my external drive is not the first partition so do I need to chain-load ? If you could give me a real dummies' guide I'd appreciate it greatly.

**This assumes your linux boot partition is on the internal drive**, then you want to install the bootloader to that partition, say it is /dev/sda3.

You run the grub application from ubuntu terminal. 

It then should go like this, except for your partition numbers.
note that hd(0,2) = /dev/sda3 

```

$ sudo grub

 [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,2)

grub> root (hd0,2)
grub> setup (hd0,2)

#### it will report what it does

grub> quit

```
Then when that is done, the MBR needs to be fixed for Windows.

---

### Post by cyberdork33 on 2007-10-31
^Yep

BTW, it might be leopard still. I thought through the evidence I had better and made a realization. I might have to do some additional testing. It is not rEFIt that is for sure.

---

### Post by ffooky on 2007-10-31
When I run

grub> find /boot/grub/stage1

I get

Error 15: File not found

Is this because the boot partition is on the internal and the root files on the external ?

---

### Post by pxwpxw on 2007-10-31
> **ffooky said:**
> When I run

grub> find /boot/grub/stage1

I get

Error 15: File not found

Is this because the boot partition is on the internal and the root files on the external ?

Ah, try this way, what do you get, not sure how that affects the next procedure
```

grub> find /grub/stage1
 (hd0,3)

grub> 

```

---

### Post by cyberdork33 on 2007-10-31
> **pxwpxw said:**
> Ah, try this way, what do you get, not sure how that affects the next procedure
```

grub> find /grub/stage1
 (hd0,3)

grub> 

```
you don't need to do the find command if you know which partition to install to. Set the root with the root command, then install to the same partition.

Grub starts counting at 0, so sda = (hd0), sda1 = (hd0,0), sda2 = (hd0,1), sdb1 = (hd1,0), etc.

---

### Post by ffooky on 2007-10-31
Yes, I get exactly the result you predict above.

FWIW, my boot volume is on /dev/sda4 and my root files on /dev/sdb4 which I'm guessing are hd0,3 and hd1,3 respectively.

edit: I tried

grub> root (hd1,3)

grub> setup (hd1,3)

and got:

Error 15: File not found

---

### Post by pxwpxw on 2007-10-31
Explanation - that is as expected if you have a separate partition mounted as /boot. I had forgotten that. I have the same system here.

If you found /grub/stage1 at (hd0,3), should be safe to proceed with

root (hd0,3)
setup (hd0,3)

the setup messages will tell you the result

---

### Post by ffooky on 2007-10-31
pxwpxw's suggestion led to:

 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0,3)"... failed (this is not fatal)
 Running "embed /grub/e2fs_stage1_5 (hd0,3)"... failed (this is not fatal)
 Running "install /grub/stage1 (hd0,3) /grub/stage2 p /grub/menu.lst "... succe
eded
Done.

Good or bad ?

---

### Post by pxwpxw on 2007-10-31
Good, carry on

Edit sorry - have finger trouble here, need check overlapping posts.

OK, now I have read properly. All in order, you have installed the grub stage1 on the boot sector of sda4. At ths stage you should still boot ubuntu as before because grub stage1 is also on the MBR, but when you fix the MBR, you will be able to boot linux from the refit screen,if you have rEFIt installed.

Are you OK to fixmbr now, 
Err, you have XP, it does FIXMBR.

---

### Post by cyberdork33 on 2007-10-31
> **ffooky said:**
> Yes, I get exactly the result you predict above.

FWIW, my boot volume is on /dev/sda4 and my root files on /dev/sdb4 which I'm guessing are hd0,3 and hd1,3 respectively.

edit: I tried

grub> root (hd1,3)

grub> setup (hd1,3)

and got:

Error 15: File not found

Except you wanted the boot partition, not the root filesystem. I know that is confusing... It is asking for the root for grub to boot. The grub config file (menu.lst) specifies things such as where your kernel is, and where the root filesystem is located.

It looks like you got it right in your next posts. You can use FIXMBR now.

---

### Post by ffooky on 2007-10-31
All seemed to go well, no GRUB screen after rEFIt but Windows is giving me:

Windows could not start because the following file is missing
or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file.

I vaguely remember reading about this somewhere but I'll search around.

Thanks very much to the pair of you for your excellent advice and sorry for being such a dunce.

---

### Post by ffooky on 2007-10-31
Bugger, bugger, bugger.

 I tried literally every method I could find to rectify the hal.dll problem before reluctantly accepting a complete reinstall of Windows as the only solution. Boot Camp wouldn't let me reinstall as there's more than two partitions on the drive so I opted to simply install from the XP disc onto the previous Windows partition. It installed and then after the reboot Windows threw an error about an unmountable volume. I tried booting XP in safe mode but came up against the same bloody problem of an unresponsive keyboard so I couldn't try tinkering with running FIXMBR again. I'm almost prepared to try cloning my Leopard volume, formatting, reinstalling, repartitioning with Boot Camp and installing Gutsy again, maybe all three on the internal drive this time but I fear the same result will be inevitable.

 I think, short of a firmware update I'm just going to have to choose between XP and Ubuntu as my dual boot option. How very dispiriting.

---

### Post by cyberdork33 on 2007-10-31
> **ffooky said:**
> Bugger, bugger, bugger.

 I tried literally every method I could find to rectify the hal.dll problem before reluctantly accepting a complete reinstall of Windows as the only solution. Boot Camp wouldn't let me reinstall as there's more than two partitions on the drive so I opted to simply install from the XP disc onto the previous Windows partition. It installed and then after the reboot Windows threw an error about an unmountable volume. I tried booting XP in safe mode but came up against the same bloody problem of an unresponsive keyboard so I couldn't try tinkering with running FIXMBR again. I'm almost prepared to try cloning my Leopard volume, formatting, reinstalling, repartitioning with Boot Camp and installing Gutsy again, maybe all three on the internal drive this time but I fear the same result will be inevitable.

 I think, short of a firmware update I'm just going to have to choose between XP and Ubuntu as my dual boot option. How very dispiriting.

I do believe that Windows like to be the last partition on the drive too.

---

### Post by pxwpxw on 2007-11-01
> **ffooky said:**
> Bugger, bugger, bugger.

 I'm almost prepared to try cloning my Leopard volume, formatting, reinstalling, repartitioning with Boot Camp and installing Gutsy again, maybe all three on the internal drive this time but I fear the same result will be inevitable.

 I think, short of a firmware update I'm just going to have to choose between XP and Ubuntu as my dual boot option. How very dispiriting.

If you are doing a ful reinstall (sounds like a good idea), look at this thread.
Easiest triple boot ever. Leopard, Gutsy, Vista  (Multi-page thread 1 2)
violajack 
[http://ubuntuforums.org/showpost.php?p=3649551&postcount=1](http://ubuntuforums.org/showpost.php?p=3649551&postcount=1)
In particular, Vista gets installed 2nd, but finishes up as partition 4.

I cant see any difference between having a full linux root on the internal, or just having the /boot partition as you did before - either way its just an ext3 boot partition with grub and kernel files as seen by rEFIt and efi booting. 
An external /home partition is another option.

---

### Post by cyberdork33 on 2007-11-01
> **pxwpxw said:**
> An external /home partition is another option.Any separate home partition is always a good way to go. makes upgrades very easy.

---

### Post by ffooky on 2007-11-01
> **pxwpxw said:**
> If you are doing a ful reinstall (sounds like a good idea), look at this thread.
Easiest triple boot ever. Leopard, Gutsy, Vista  (Multi-page thread 1 2)
violajack 
[http://ubuntuforums.org/showpost.php?p=3649551&postcount=1](http://ubuntuforums.org/showpost.php?p=3649551&postcount=1)
In particular, Vista gets installed 2nd, but finishes up as partition 4.

I cant see any difference between having a full linux root on the internal, or just having the /boot partition as you did before - either way its just an ext3 boot partition with grub and kernel files as seen by rEFIt and efi booting. 
An external /home partition is another option.For the time being I just installed Gutsy on my old Boot Camp-created Windows partition, which I also divided with the Gutsy installer into a 30 gig root and ~800MB swap.

 In thie tutorial you link to, is there any reason why at this point> From OSX, I used the GUI Disk Utility from the Utilities folder. If you click on the main disk (not on of the two partitions) you will have a tab option for Partition. From the graphic of the two partitions, click the main OSX partition, then click the little plus sign and it will split the OSX partition into two.you couldn't create two partitions, thus allowing one to be available for swap ?

---

### Post by pxwpxw on 2007-11-01
> **ffooky said:**
> For the time being I just installed Gutsy on my old Boot Camp-created Windows partition, which I also divided with the Gutsy installer into a 30 gig root and ~800MB swap.

 In thie tutorial you link to, is there any reason why at this pointyou couldn't create two partitions, thus allowing one to be available for swap ?

That is a function of the Leopard disk utility I cant comment on, as I dont have it.
 I assume you could create 2 partitions, question is whether that would upset windows and the booting.
It might be possible, only way would be to try it.
It seems that it is wise to keep windows in the last of 4 primary partitions, therefore the extra partition cannot be a primary as seen by windows.

You would be departing from the 4 partition idea, all bets off.

However, if you _started_ a complete re install with Leopard in 1 partition, leaving space at the end, then proceed as for the tutorial, not touching the space, you should then have that space available to linux or macosx for any number of partitions. 

If it worked.

---

### Post by cyberdork33 on 2007-11-01
> **ffooky said:**
> For the time being I just installed Gutsy on my old Boot Camp-created Windows partition, which I also divided with the Gutsy installer into a 30 gig root and ~800MB swap.

 In thie tutorial you link to, is there any reason why at this pointyou couldn't create two partitions, thus allowing one to be available for swap ?

You could make multiple partitions with disk utility, but you can't create a swap partition in diskutility, which means you would still have to use the partitioner in Ubuntu to use the partition the way you wanted anyway.

You can work around the 4 partition limit issue quite easily since Windows is really the only problem with that. Leopard (or other OSX partitions), as well as 'other' ubuntu partitions (home, swap) can be beyond #4 and work fine. In fact some people find that you can even have the main Ubuntu partition beyond #4 as long as grub is installed on one of the first 4 partitions. You only need to put the partitions that you want Windows to 'see' in the first 4. That is getting a bit complicated though now.

---

