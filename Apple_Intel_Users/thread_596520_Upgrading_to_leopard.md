---
title: "Upgrading to leopard"
date: 2007-10-29
forum: Apple Intel Users
---

### Post by schauerlich on 2007-10-29
Are there any known issues when upgrading OS X to Leopard on a dual boot machine?

---

### Post by aysiu on 2007-10-29
> **EDavidBurg said:**
> Are there any known issues when upgrading OS X to Leopard on a dual boot machine?
Yes. You might get a "blue screen of death."
[http://www.informationweek.com/blog/main/archives/2007/10/expect_the_wors.html](http://www.informationweek.com/blog/main/archives/2007/10/expect_the_wors.html)

---

### Post by Terc on 2007-10-29
The BSOD is not directly related to dual booting in my understanding, it's because of APE, get rid of it.  Regardless, here's the fix for the BSOD [http://docs.info.apple.com/article.html?artnum=306857]("http://docs.info.apple.com/article.html?artnum=306857")

---

### Post by cyberdork33 on 2007-10-29
> **EDavidBurg said:**
> Are there any known issues when upgrading OS X to Leopard on a dual boot machine?

It will kill rEFIt, but you just have to reinstall it.

---

### Post by schauerlich on 2007-10-29
Does this apply to a disk partitioned in Boot Camp?

---

### Post by Zaff on 2007-10-30
When you say you just need to reinstall rEFIt, do you need to reinstall it only in macos ?
Also I already posted this somewhere else but I'm asking here too : when I try to upgrade macos to leopard it seems it can't find macos and wants to erase my macos partition. Is that due to partitioning ? is there a way to not erase the disk ?
Thanks

---

### Post by cyberdork33 on 2007-10-30
> **Zaff said:**
> When you say you just need to reinstall rEFIt, do you need to reinstall it only in macos ?
Also I already posted this somewhere else but I'm asking here too : when I try to upgrade macos to leopard it seems it can't find macos and wants to erase my macos partition. Is that due to partitioning ? is there a way to not erase the disk ?
Thanks
I don't know how to fix that issue. It did it to me as well.
rEFIt is installed in OSX, yes.

---

### Post by Zaff on 2007-10-30
> **cyberdork33 said:**
> I don't know how to fix that issue. It did it to me as well.
rEFIt is installed in OSX, yes.

So all i need to do is just reinstall rEFIt in macosx and I'll get my ubuntu back the way it was ... thanks for that.
It's no big deal if I have to overwrite my mac os partition, I just wanted to know if this happened to everyone or just me. Cuz if it's just me maybe I have a weird partitionning system and I wouldn't feel too good in messing it up. I really don't want to have to reinstall ubuntu and put all my settings back together (it took me a while to get everything working).
Thanks

---

### Post by cyberdork33 on 2007-10-30
I think it is our custom partitioning that is causing the problem with upgrading. I initially got the message and thought maybe rEFIt had something to do with it, so I uninstalled it, and still got the issue. maybe it is GRUB? IDK.

Did anyone successfully install leopard on a dual boot machine without having to wipe the old partition out?

---

### Post by Zaff on 2007-10-30
So, just to be sure, even if I overwrite the macos partition, Ubuntu should remain untouched right ? All I'll need to do after that is just reinstall rEFIt in MacOs and it'll work ? I'm sorry if I'm making you repeat yourself I just wanna be sure (this is my work station)
Thanks again for your help, every time I have an issue you seem to be around.

---

### Post by cyberdork33 on 2007-10-30
> **Zaff said:**
> So, just to be sure, even if I overwrite the macos partition, Ubuntu should remain untouched right ? All I'll need to do after that is just reinstall rEFIt in MacOs and it'll work ? I'm sorry if I'm making you repeat yourself I just wanna be sure (this is my work station)
Thanks again for your help, every time I have an issue you seem to be around.

While I can't say I did this myself (I upgraded to 64-bit Ubuntu as well), I have a high amount of certainty that you can boot the leopard disc, open disk utility, use 'erase' on your current OSX partition, and then start the installer and choose to install to it. if you can't, then you might have to wipe the entire disk. I can't say that is not an outcome.

You should still be able to boot your Ubuntu system even without OSX or rEFIt (Hold alt on startup). If you get boot failures starting after the upgrade, I would guess something happened to grub, which is easily correctable by booting the Ubuntu CD and [installing natively]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html"). I can't see how the OSX installer would affect your Ubuntu install unless you told it to use the entire disk.

---

### Post by mustang on 2007-10-30
> **Zaff said:**
> So, just to be sure, even if I overwrite the macos partition, Ubuntu should remain untouched right ? All I'll need to do after that is just reinstall rEFIt in MacOs and it'll work ? I'm sorry if I'm making you repeat yourself I just wanna be sure (this is my work station)
Thanks again for your help, every time I have an issue you seem to be around.

Yes. I was dual booting Feisty + Tiger. I installed Leopard onto my mac partition (that is the only option you will be presented during install). That killed refit---no problem, reinstalled that. Everything was back to normal.

---

### Post by Zaff on 2007-10-30
> **mustang said:**
> Yes. I was dual booting Feisty + Tiger. I installed Leopard onto my mac partition (that is the only option you will be presented during install). That killed refit---no problem, reinstalled that. Everything was back to normal.

okay thanks for that, I shall upgrade tomorrow
Leopard looks nice ! I have to admit I'm only really upgrading to show off since I'm not using MacOs that much.
Thanks again for all the help.

---

### Post by cyberdork33 on 2007-10-30
> **mustang said:**
> Yes. I was dual booting Feisty + Tiger. I installed Leopard onto my mac partition (that is the only option you will be presented during install). That killed refit---no problem, reinstalled that. Everything was back to normal.

So did you 'upgrade' or did it say there was a problem with the partition and it needed to be erased (like we did).

---

### Post by mustang on 2007-10-31
I did not upgrade. I intended to wipe it from the beginning so I do not think I got that message you did.

---

### Post by ilmarw on 2007-10-31
I'm triple booting, but when trying to install Leopard, I get a yellow exclamation mark, and the installer telling me that I have to erase the disk. This is probably due to refit. Any way around this? Simply removing refit won't help, from what I've read. IF I decide to erase the disk, does someone know if this goes for the whole disk, or just the partition OSX is installed on?

ilmar

---

### Post by nowshining on 2007-10-31
never heard of a BSOD on a MAC until now on the MAC OS, so I'm guessing it's really an INTEL issue on the BSODS and the code they use in ther processor chips..

---

### Post by Zaff on 2007-10-31
> **ilmarw said:**
> I'm triple booting, but when trying to install Leopard, I get a yellow exclamation mark, and the installer telling me that I have to erase the disk. This is probably due to refit. Any way around this? Simply removing refit won't help, from what I've read. IF I decide to erase the disk, does someone know if this goes for the whole disk, or just the partition OSX is installed on?

ilmar

I had the same issue and MacOs only erase the MacOs partition when installing Leopard. All you need to do is reinstall rEFIt in MacOs afterwards and you'll get your system back as it was before. I don't know if there is a solution to that problem but I didn't have anything really important on my MacOs partition anyway.

---

### Post by cyberdork33 on 2007-10-31
> **Zaff said:**
> I had the same issue and MacOs only erase the MacOs partition when installing Leopard. All you need to do is reinstall rEFIt in MacOs afterwards and you'll get your system back as it was before. I don't know if there is a solution to that problem but I didn't have anything really important on my MacOs partition anyway.
I think he is asking if you choose to go ahead and let it erase, does it only erase the OSX partition or the whole disk. As I mentioned before, I did wipe my entire disk, but I meant to. Did it only wipe the OSX partition?

---

### Post by cyberdork33 on 2007-10-31
> **nowshining said:**
> never heard of a BSOD on a MAC until now on the MAC OS, so I'm guessing it's really an INTEL issue on the BSODS and the code they use in ther processor chips..It is related to having a certain application installed (Application Enhancer), and then trying to upgrade. [http://forums.macrumors.com/showthread.php?t=375444](http://forums.macrumors.com/showthread.php?t=375444)

---

### Post by Zaff on 2007-10-31
> **cyberdork33 said:**
> I think he is asking if you choose to go ahead and let it erase, does it only erase the OSX partition or the whole disk. As I mentioned before, I did wipe my entire disk, but I meant to. Did it only wipe the OSX partition?

It only erased my MacOS partition, my ubuntu partition was untouched. So no biggie really unless you really don't want to erase your MacOS partition.

---

### Post by jenhsun on 2007-10-31
And if you are a java programmer, welcome to check this out.

So Long Apple. The Party's Over
[http://www.javalobby.org/java/forums/t102936.html](http://www.javalobby.org/java/forums/t102936.html)

---

### Post by cyberdork33 on 2007-10-31
> **jenhsun said:**
> And if you are a java programmer, welcome to check this out.

So Long Apple. The Party's Over
[http://www.javalobby.org/java/forums/t102936.html](http://www.javalobby.org/java/forums/t102936.html)
Please start a new thread for something so off topic.

---

### Post by ilmarw on 2007-10-31
> **Zaff said:**
> I had the same issue and MacOs only erase the MacOs partition when installing Leopard. All you need to do is reinstall rEFIt in MacOs afterwards and you'll get your system back as it was before. I don't know if there is a solution to that problem but I didn't have anything really important on my MacOs partition anyway.

You re quite sure of that? I can loose my Mac partition, but not my Linux partition. Any way to move everything from Mac over, so that in a sense I do get an upgrade? How about the archiving option in the Leopard installer?

ilmar

---

### Post by goodsup on 2007-10-31
Hi at all.
I'm new ubuntu italian user, in my macbook i've installed tiger and ubuntu gutsy. All worked fine.
Then i install leopard, and now refit don't work...so ...just reinstall it on mac osx but....if i restart nothing happens...just leopard startup....

i wanna reinstall refit to have my dual boot with ubuntu. someone can help me? how can i check if refit work fine or not?

thanks

---

### Post by Zaff on 2007-10-31
> **ilmarw said:**
> You re quite sure of that? I can loose my Mac partition, but not my Linux partition. Any way to move everything from Mac over, so that in a sense I do get an upgrade? How about the archiving option in the Leopard installer?

ilmar

I got eactly the same thing you did : the yellow exclamation point and MacOS installer saying I needed to erase it. If you look at the drive icon it should tell you the size of the MacOS partition and not the total size of the disk. I erased that partition and ubuntu was untouched, so I am 99% sure this will do the same for you. I don't know how to move everything from mac over (not exactly sure what ou meant by that and I don't know what the archiving option in the installer is (didn't see it). But as far as I'm concerned if you're only worried about your linux partition, then you can just proceed with the install. Just don't forget to reinstall rEFIt afterwards if you want a boot menu at the start.

---

### Post by Zaff on 2007-10-31
> **goodsup said:**
> Hi at all.
I'm new ubuntu italian user, in my macbook i've installed tiger and ubuntu gutsy. All worked fine.
Then i install leopard, and now refit don't work...so ...just reinstall it on mac osx but....if i restart nothing happens...just leopard startup....

i wanna reinstall refit to have my dual boot with ubuntu. someone can help me? how can i check if refit work fine or not?

thanks

rEFIt is destroyed when you upgrade to leopard. you need to reinstall it in MacOS.
how many times did you restart your macbook and was it because you had an update done and MacOs was asking for it or did you choose to restart? I've noticed that if MacOs restarts itself it will skip rEFIt. Try restarting it from the apple menu.
Also try pressing down the Alt/option key at restart to see if you're given a "windows disk" choice. Your linux system should be on there.

---

### Post by cyberdork33 on 2007-10-31
> **goodsup said:**
> Hi at all.
I'm new ubuntu italian user, in my macbook i've installed tiger and ubuntu gutsy. All worked fine.
Then i install leopard, and now refit don't work...so ...just reinstall it on mac osx but....if i restart nothing happens...just leopard startup....

i wanna reinstall refit to have my dual boot with ubuntu. someone can help me? how can i check if refit work fine or not?

thanks
You have to install with the manual instructions. This happened to me too. The installer does not install properly anymore.
[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

---

### Post by ilmarw on 2007-10-31
> **cyberdork33 said:**
> You have to install with the manual instructions. This happened to me too. The installer does not install properly anymore.
[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

This manual installation method has a drawback that you should be aware of. Since you&#8217;re not using rEFItBlesser, Mac OS X updates will disable rEFIt, and the rEFIt menu will show up even when waking from Safe Sleep.

The above is a copy/ paste from those instructions. Maybe we should wait for a refit update. I noticed someone already requested this (leopard support).

ilmar

---

### Post by cyberdork33 on 2007-10-31
I have had no such issues... besides, it doesn't totally remove it, you would just have to run the script again to get it working. Also, you can install it to a CD or USB drive if you want to make sure you can always use it. 

None the less, it won't break anything..

---

### Post by mustang on 2007-10-31
> **goodsup said:**
> Hi at all.
I'm new ubuntu italian user, in my macbook i've installed tiger and ubuntu gutsy. All worked fine.
Then i install leopard, and now refit don't work...so ...just reinstall it on mac osx but....if i restart nothing happens...just leopard startup....

i wanna reinstall refit to have my dual boot with ubuntu. someone can help me? how can i check if refit work fine or not?

thanks

Try restarting it again yourself as opposed to refit restarting for you.

---

### Post by goodsup on 2007-10-31
So i don't know why...but i reinstall refit 0.8 and now all is ok!
Thanks at all!

:lolflag:

---

### Post by ilmarw on 2007-10-31
> **goodsup said:**
> So i don't know why...but i reinstall refit 0.8 and now all is ok!
Thanks at all!

:lolflag:

What do you mean? You downgraded refit to 0.8, and the leopard installer let you upgrade without giving a yellow exclamation mark?

ilmar

---

### Post by schauerlich on 2007-10-31
I used Bootcamp to partition my drive/select which partition to boot on startup. Will I have the same issues, and if not, what issues will I have?

---

### Post by cyberdork33 on 2007-10-31
> **EDavidBurg said:**
> I used Bootcamp to partition my drive/select which partition to boot on startup. Will I have the same issues, and if not, what issues will I have?

No idea. We don't know what is causing the problem.

---

### Post by Zaff on 2007-11-01
Okay I'm just gonna do a quick overview of what upgrading to Leopard seems to cause on a system with ubuntu dual boot. So far we've had the following issues :

- The Leopard installer does not recognize the MacOS partition properly and cannot upgrade it. It needs to be **ERASED** and the new system will install itself on it. The installer only seems to **"see"** the Mac OS partition. It just can't upgrade it. It **doesn't see** the Ubuntu partition. It displays a yellow exclamation point on the disk icon and tells you you have to erase it to use it for your new system. If you look on the disk icon it should tell you it's only the size of your MacOS partition and not the size of your entire disk.

- After installing Leopard, rEFIt will disappear and needs to be reinstalled in MacOS. For me it worked right away but apparently not for everyone. There is nothing that needs to be done in Ubuntu for it to work again.

As far as I can tell, there is no danger for the Ubuntu partition as the installer doesn't even know it's there.

Those are the only issues I encountered and I haven't heard of any other. The same precaution apply for upgrading on a regular system : some Tiger applications are not compatible with Leopard and may cause your system to crash on upgrade but this is not due to having dual boot. It is a know Mac OS issue (my sister's boyfriend's had this problem and is trying to reinstall everything and he only has Tiger on his computer).

So the bottom line is : if you're not sad about having to overwrite everything on you Mac OS partition, then everything should be fine for you. I don't know if this was tested on a Triple boot system (with windows for instance) so if anyone has done it, please let us know.
There you have it. I upgraded to Leopard and everything works fine for me now. I only really use Ubuntu anyway.

---

### Post by jslmg on 2007-12-26
After upgrading to Leopard---with the required erase-and-install--- I cannot load Ubuntu. I only get a grub prompt. The Leopard install did not erase the Linux partition, but Ubuntu won't load. I've made no other changes to my Ubuntu, and it booted fine just two days ago.

Any ideas?

---

### Post by jslmg on 2007-12-26
> **jslmg said:**
> After upgrading to Leopard---with the required erase-and-install--- I cannot load Ubuntu. I only get a grub prompt. The Leopard install did not erase the Linux partition, but Ubuntu won't load. I've made no other changes to my Ubuntu, and it booted fine just two days ago.

Any ideas?

After poking around a bit, I realized that the Leopard Installation changed my partition table around. When I originally made the partition table, the Linux swap was last, the with main Linux partition before that. 

The original order was:
EFI Protective (FAT)
Mac OS X HFS+
Linux basic data
Linux Swap

Now it's:
EFI Protective (FAT)
Mac OS X HFS+
Linux Swap 
Linux basic data

Could that switch be the culprit?

---

### Post by ilmarw on 2007-12-26
I experienced the same. So it should simply be a matter of changing the partition number in GRUB. Since you have a swap partition as well (I have triple boot on my machine, in addition to shared partition, so I only use a file for swapping), you probably need to adjust /etc/fstab.

ilmar

---

### Post by jslmg on 2007-12-26
> **ilmarw said:**
> I experienced the same. So it should simply be a matter of changing the partition number in GRUB. Since you have a swap partition as well (I have triple boot on my machine, in addition to shared partition, so I only use a file for swapping), you probably need to adjust /etc/fstab.

ilmar

So, how do we access /etc/fstab from the grub prompt?

---

### Post by jslmg on 2007-12-28
So, I just took the most obvious, direct measure: reinstall Ubuntu, and start... all... over.... again.
](*,)
Still, would be nice to know what to do next time this happens.

---

### Post by Zaff on 2007-12-28
sorry for the late answer, 
you probably could have modified the /etc/fstab from the live cd environment by mounting your partition and then just accessing it.
That's all I got anyway.

---

### Post by Katjum on 2008-01-01
I'd really like to update to Leopard without having to erase my MacOSX partition. I get the same error (yellow sign with an exclamation mark, only option is to erase and install) when I try to install that everyone else seems to have. 

I think the problem has to do with the way rEFIt changes the GPT when it synchronizes it with the MBR. After I used Boot Camp (several months ago with Tiger), I split the second partition it created to add a swap partition. I had to synchronize the GPT and MBR to the new partition would show up in MacOSX (under Disk Utility). 

I think rEFIt may have changed the order of the other partitions, and that might be why Leopard refuses to update the installation. I don't remember if any other partitions where different before I synchronized. Maybe a tool under Ubuntu (like parted) can fix the GPT.

Thanks!

This is what I get from the Partition Inspector included with rEFIt:

*** Report for internal hard disk ***
Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    323371047  Mac OS X HFS+
 3      323371048    386718750  Basic Data
 4      386718751    390721934  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    323371047  af  Mac OS X HFS+
 3      323371048    386718750  83  Linux
 4      386718751    390721934  82  Linux swap / Solaris

MBR contents:
Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 323371048:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 386718751:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

---

### Post by cyberdork33 on 2008-01-02
parted and gparted can read/write gpt

I think you are stuck deleting though as I believe that the issue is that it is not a single bootcamp partition that causes the problem.

---

### Post by Katjum on 2008-01-02
> **cyberdork33 said:**
> parted and gparted can read/write gpt

I think you are stuck deleting though as I believe that the issue is that it is not a single bootcamp partition that causes the problem.

If this is the case, couldn't I somehow eliminate my swap partition (since there's nothing on it and I have 3GB of RAM) temporarily to get Leopard to install? I know that if I use a tool that changes the MBR, rEFIt will correct the GPT for me. 

If I boot from a Linux disc, can I use fdisk to repartition and change the MBR?

What changes would I have to make in my Ubuntu install to do this (and make sure everything boots and is recognized right)? 

I have more I want to save in my MacOSX partition than in my Ubuntu one.

Can anyone confirm that it is multiple bootcamp partitions that are causing the problem?

---

### Post by cyberdork33 on 2008-01-02
> **Katjum said:**
> If I boot from a Linux disc, can I use fdisk to repartition and change the MBR?

I would just use gparted and update everything without needing to sync.

> **Katjum said:**
> What changes would I have to make in my Ubuntu install to do this (and make sure everything boots and is recognized right)? 
to do what? remove the swap?

> **Katjum said:**
>  Can anyone confirm that it is multiple bootcamp partitions that are causing the problem?You are misreading my statement. It is not "multiple bootcamp partitions", it is the fact that you have partitions that are not bootcamp partitions. i.e. all linux partitions. For some reason the linux partitions are throwing the updater off... I don't believe this is an issue when you have a normal bootcamp (windows) partition on the disk.

---

### Post by Katjum on 2008-01-02
> **cyberdork33 said:**
> I would just use gparted and update everything without needing to sync. 

I thought that would leave the MBR and GPT out of sync which would cause boot and/or other problems if I ever tried to partition or update either OS.

> **cyberdork33 said:**
> You are misreading my statement. It is not "multiple bootcamp partitions", it is the fact that you have partitions that are not bootcamp partitions. i.e. all linux partitions. For some reason the linux partitions are throwing the updater off... I don't believe this is an issue when you have a normal bootcamp (windows) partition on the disk.

You may be right that the mere presence of partitions in formats it does not read (Ext3 and Swap) causes the problem. I was hoping to find some way around the problem that did not involve erasing any partitions. 

I had thought about "moving" the partitions (or at least changing the GPT number, which I do not know how to do) back to the way they were before rEFIt changed them (which I also do not know) to synchronize the GPT with the MBR. I don't know if it will work, but I figured it was non-destructive and worth a shot.

Maybe if I reformat my Ubuntu and swap partitions into one FAT32 or NTFS partition (I think it will all fit in FAT32. That was how I did it in Bootcamp.), I can update MacOSX. All the data on my Ubuntu partition will fit on the MacOSX partition, and (with the help of the Ext2fs driver for MacOSX) I think I can make a disk image and then put the data back after I update to Leopard and repartition with the Ubuntu disk.

Does anyone know if this will work? If I get time, I'll give it a try. Thanks!

---

### Post by cyberdork33 on 2008-01-02
> **Katjum said:**
> I thought that would leave the MBR and GPT out of sync which would cause boot and/or other problems if I ever tried to partition or update either OS. No, fdisk will give this problem, since it is incapable of reading / updating the GPT... However, parted and it's dervatives (including gparted) can read/write GPT just fine and there is no "syncing" to do (as they would already be the same).

> **Katjum said:**
>  Maybe if I reformat my Ubuntu and swap partitions into one FAT32 or NTFS partition (I think it will all fit in FAT32. That was how I did it in Bootcamp.), I can update MacOSX. All the data on my Ubuntu partition will fit on the MacOSX partition, and (with the help of the Ext2fs driver for MacOSX) I think I can make a disk image and then put the data back after I update to Leopard and repartition with the Ubuntu disk.If you can image the Ubuntu root partition and restore it without losing anything this would probably work, but that is a process in itself. The problem with going through ext2fs is that permissions will likely not show up the same in OSX. you can boot off a livecd and tar the whole filesystem up (if you can write to the hfs+ partition). That would probably be a working solution.

What do you have in Ubuntu that you cannot lose? can you just backup the home directory or personal files and then reinstall later?

---

### Post by Katjum on 2008-01-02
> **cyberdork33 said:**
> No, fdisk will give this problem, since it is incapable of reading / updating the GPT... However, parted and it's dervatives (including gparted) can read/write GPT just fine and there is no "syncing" to do (as they would already be the same). 

I understand that, but rEFIt only works in one direction (MBR to GPT). If I update the GPT, I will have to manually update the MBR. I might be mistaken, but I think that is the point of rEFIt's syncing tool, to make it possible to use tools that do not recognize the GPT. Will gparted automatically fix the MBR too? I don't know if having the GPT and MBR unsynchronized could also keep Leopard from installing.

> **cyberdork33 said:**
> If you can image the Ubuntu root partition and restore it without losing anything this would probably work, but that is a process in itself. The problem with going through ext2fs is that permissions will likely not show up the same in OSX. you can boot off a livecd and tar the whole filesystem up (if you can write to the hfs+ partition). That would probably be a working solution.

I think I can write to the HFS+ partition if I disable journaling (and maybe something else, I don't know). With ext2fs, the linux filesystem (ext3) is read-only. I don't if that means the permissions are correct or not.

> **cyberdork33 said:**
> What do you have in Ubuntu that you cannot lose? can you just backup the home directory or personal files and then reinstall later?

I don't  have anything only in Ubuntu I can't lose. I have plenty of backups. It's just a pain in the neck to have to reinstall and reconfigure everything, especially if I still can't install Leopard.

I was looking for a "quick and dirty" way around the problem with having to erase anything, but I guess there really isn't one.

Anyway, I'll try erasing the Ubuntu partitions (and rEFIt) later tonight or tomorrow and see if that works.

Edit: Sorry, I didn't have a chance yesterday, but I will post results when I have them. Thanks for all your help!

Any other suggestions are welcome! Thanks! :)

---

### Post by cyberdork33 on 2008-01-03
> **Katjum said:**
> I understand that, but rEFIt only works in one direction (MBR to GPT). If I update the GPT, I will have to manually update the MBR. I might be mistaken, but I think that is the point of rEFIt's syncing tool, to make it possible to use tools that do not recognize the GPT. Will gparted automatically fix the MBR too? I don't know if having the GPT and MBR unsynchronized could also keep Leopard from installing.yes, parted updates both the MBR and GPT.

> **Katjum said:**
>  I think I can write to the HFS+ partition if I disable journaling (and maybe something else, I don't know). With ext2fs, the linux filesystem (ext3) is read-only. I don't if that means the permissions are correct or not.There is an option to ignore permissions, but it seems that there are problems with it still. It used to work fine for me but that was a long time ago. I know it hasn't worked since I upgraded to leopard...

> **Katjum said:**
>  I don't  have anything only in Ubuntu I can't lose. I have plenty of backups. It's just a pain in the neck to have to reinstall and reconfigure everything, especially if I still can't install Leopard.

I was looking for a "quick and dirty" way around the problem with having to erase anything, but I guess there really isn't one.
Good Luck.

---

### Post by ilmarw on 2008-01-04
I don't think I posted this workaround on this thread:
What I did was using a second Mac. First, I upgraded the Mac that did not contain any other partitions. When asked, I chose to transfer data from another Mac (my Mac, with five partitions). This worked fine. Then I continued upgrading my Mac, choosing to delete the Tiger partition. When asked, I chose to transfer everything from the temporary Mac to my Mac, and after resetting the temporary Mac, I achieved what I wanted. The total procedure took less then a couple of hours.

ilmar

---

### Post by Zaff on 2008-01-04
> **ilmarw said:**
> I don't think I posted this workaround on this thread:
What I did was using a second Mac. First, I upgraded the Mac that did not contain any other partitions. When asked, I chose to transfer data from another Mac (my Mac, with five partitions). This worked fine. Then I continued upgrading my Mac, choosing to delete the Tiger partition. When asked, I chose to transfer everything from the temporary Mac to my Mac, and after resetting the temporary Mac, I achieved what I wanted. The total procedure took less then a couple of hours.

ilmar

sounds like quite the workaround.
Unfortunately not all of us have an extra mac lying around :(
Thanks for that though

---

### Post by ilmarw on 2008-01-04
I know, that is quite a big catch. However, the hassle and time is much less then reinstalling (and setting up!) the entire Ubuntu partition all over again.

ilmar

---

### Post by Katjum on 2008-01-04
> **Zaff said:**
> sounds like quite the workaround.
Unfortunately not all of us have an extra mac lying around :(
Thanks for that though

I have a friend with a mac and large external drive. I am going to visit him today, so I may be able to try something like what ilmar suggested.

Thanks! :)

---

### Post by murphybailey79 on 2008-01-04
I've heard a lot of negative comments about Leopard but for me it works just perfectly. Thanks for your answers though because my friend had a similar problem on his Mac as well

---

### Post by Katjum on 2008-01-04
I got Leopard to upgrade-install. :KS

I had to erase both my both my root (Ubuntu) filesystem and swap partition to get it to work, but it did install! It can be done!

Thanks everyone for all your help!:)

---

### Post by cyberdork33 on 2008-01-05
> **Katjum said:**
> I had to erase both my both my root (Ubuntu) filesystem and swap partition to get it to work, but it did install! It can be done!Well, that is good info. It least we know that the partitions are the problem.

---

### Post by vikramsharma on 2008-02-04
> **Zaff said:**
> rEFIt is destroyed when you upgrade to leopard. you need to reinstall it in MacOS.
how many times did you restart your macbook and was it because you had an update done and MacOs was asking for it or did you choose to restart? I've noticed that if MacOs restarts itself it will skip rEFIt. Try restarting it from the apple menu.
Also try pressing down the Alt/option key at restart to see if you're given a "windows disk" choice. Your linux system should be on there.


I read the whole thread but there is still a doubt in my mind regarding the erase and install option of Leopard.  I have two partitions created on my iMac on one partitions have OS X and the other partition I created using bootcamp has Ubuntu 64 bit.  I have installed the Linux bootloader in the the partition created using bootcamp.  In other words only when I press the alt key and choose the Linux partition created using bootcamp do I get the Linux bootloader.  Would I also have to install rEFIt, where do I get rEFIt from.  I think in my case Linux and mac should be completely independent of each other as the boot loader for Linux is installed on a different partition.

---

### Post by cyberdork33 on 2008-02-04
> **vikramsharma said:**
> I read the whole thread but there is still a doubt in my mind regarding the erase and install option of Leopard. I have two partitions created on my iMac on one partitions have OS X and the other partition I created using bootcamp has Ubuntu 64 bit. I have installed the Linux bootloader in the the partition created using bootcamp. In other words only when I press the alt key and choose the Linux partition created using bootcamp do I get the Linux bootloader. Would I also have to install rEFIt, where do I get rEFIt from. I think in my case Linux and mac should be completely independent of each other as the boot loader for Linux is installed on a different partition.rEFIt is just a fancy menu for the EFI bootloader on your Mac. It actually has nothing to do with linux. You do not have to use it. Your functionality will be exactly the same after you upgrade. If you are interested, you install it in OSX, and you can download it and read more information about it at [http://refit.sourceforge.net](http://refit.sourceforge.net)

---

### Post by vikramsharma on 2008-02-04
> **cyberdork33 said:**
> rEFIt is just a fancy menu for the EFI bootloader on your Mac. It actually has nothing to do with linux. You do not have to use it. Your functionality will be exactly the same after you upgrade. If you are interested, you install it in OSX, and you can download it and read more information about it at [http://refit.sourceforge.net](http://refit.sourceforge.net)

Thanks for the reply, I guess doing erase and install would not be much of a hassle for me then.

---

### Post by vikramsharma on 2008-02-05
> **cyberdork33 said:**
> rEFIt is just a fancy menu for the EFI bootloader on your Mac. It actually has nothing to do with linux. You do not have to use it. Your functionality will be exactly the same after you upgrade. If you are interested, you install it in OSX, and you can download it and read more information about it at [http://refit.sourceforge.net](http://refit.sourceforge.net)

Thanks for your advice man, my iMac used to boot default into Linux prior to installing Leopard, now it boots into Leopard.  All I have to do is hold the option (alt) key while the computer boots (which is not a hassle btw), other than that everything went fine.

---

### Post by cyberdork33 on 2008-02-05
> **vikramsharma said:**
> Thanks for your advice man, my iMac used to boot default into Linux prior to installing Leopard, now it boots into Leopard.  All I have to do is hold the option (alt) key while the computer boots (which is not a hassle btw), other than that everything went fine.You can make either the default in rEFIt.

---

### Post by vikramsharma on 2008-02-05
> **cyberdork33 said:**
> You can make either the default in rEFIt.

Would do that, atleast my Linux install is independent of the Mac install which makes me less a less worried person.

---

