---
title: "xp/ubuntu problem!"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by striker4678 on 2007-06-19
Alright so last night I installed ubuntu on my laptop and I made a very big mistake!

I was currently running windows xp and when I went through the process of installing ubuntu I think I partitioned it wrong and now I believe I've deleted my xp.

Well I don't have my original system restore disk for my compaq laptop, but I do have one that came with a dell desktop, will that work fine?

Can I even re-install windows by using a system already running ubuntu?

How should I go about installing it, and how should I partition it?

and how can i make sure I deleted xp?

---

### Post by p_quarles on 2007-06-19
To be absolutely sure that XP is gone, you can press escape during the grub-loading process, and see if it's there. That said, Ubuntu should automatically mount any Windows partitions that exist on the drive, so if you're not seeing something like "Windows" or "Compaq" underneath a hard-drive icon, it's probably gone. 

And, unfortunately, you do need to install Windows prior to Ubuntu. The correct option to choose, when installing Ubuntu, is "Guided partition - use partial disk." 

As for installing your Dell XP on the Compaq: not legally. You might be able to buy a set of recovery disks from Compaq, though.

---

### Post by striker4678 on 2007-06-19
thanks...I guess windows is probably gone...any way i can recover any of my music or anything?

and if i use the dell xp would it still work?

---

### Post by striker4678 on 2007-06-19
and just so i don't mess up again

how should I go about uninstalling ubuntu and reinstalling xp and everything

---

### Post by confused57 on 2007-06-19
> **striker4678 said:**
> and just so i don't mess up again

how should I go about uninstalling ubuntu and reinstalling xp and everything

You can see if you might still have Windows by opening a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a small "L"

You can do this from the live cd, also.

---

### Post by p_quarles on 2007-06-19
I've never tried to use recovery disks for one system on another one, so I honestly have no idea if it will work. I'm guessing not, though.

Your Windows files are probably gone . . . you might try looking for a data recovery tool, but since Linux reformatted your entire drive, I wouldn't get too optimistic.

If you are able to reinstall XP, though, you won't need to do anything special. The reason you have to install that before Ubuntu is because Windows installations tend to automatically take over the entire drive, without you needing to uninstall anything. When you're ready to reload Ubuntu, just make read all the install options carefully, and don't select the "Guided partitioning -- use entire disk" option.

---

### Post by buuntuu! on 2007-06-19
you don't necessarily have to install xp first, there are some threads about installing it after ubuntu. it's doable, but a bit messy, i think, though i never tried it.
you can use the dell discs to retrieve the files you need for an xp-install (the i386 folder is all you need for a clean xp-disc)  n-lite will help you to create an install-disc. just the drivers for your box and any programs that compaq preinstalled will be missing, but IMO it's always best not to have such stuff (preinstalled progs, not drivers ;)), it's almost certainly bloated crap...
 just google around a bit, it can be done and you will learn quite a bit :)

---

### Post by striker4678 on 2007-06-19
sweet thanks, the drivers though...will i need those?  I'm guessing I will...

---

### Post by striker4678 on 2007-06-19
sweet thanks, the drivers though...will i need those?  I'm guessing I will...
how should I go about that?

are my music files lost?

and what is n-lite?
how can i get the files i need for the clean install?

---

### Post by buuntuu! on 2007-06-19
you guessed right.
 you can download them from compaq.

edit: have you tried confused57s command?? this will tell you if the xp partition is still there...

---

### Post by p_quarles on 2007-06-19
Most of the big manufacturers host Windows drivers for their components on their web sites. You should be able to find everything you need at Compaq's support page.

---

### Post by iceportal on 2007-06-19
If your Ubuntu install is fresh (with no special configurations since you installed) or if any changes you've made are minor, it would probably be best to reinstall XP (the XP disk from Dell should be fine, since usually they include pure XP and not some custom version specific to the hardware) before installing Ubuntu again.

It's possible to install XP dual-boot, but the process is, as stated before, quite messy.

One possible option:

Download gparted LiveCD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) and burn to disk, then use it to resize your Ubuntu partition to about half what it is now. Once that's done, reboot with the XP install disk in, and be sure to have it install on the unformatted space (not wipe the whole drive, just the part that you freed with gparted). Then, it should install a bootloader (like grub, but different) that will have "Windows XP" and "Other OS" in the boot menu (or something like that).

It's not as clean or pretty as GRUB, nor will it be as pretty as just installing XP then Ubuntu again, but it's workable.

Note: I've only done this a few times, so... Proceed with caution.

---

### Post by buuntuu! on 2007-06-19
i agree wiht iceportal,as your install is fresh it would be best to wipe clean the harddisc, reinstall xp and then ubuntu...

---

### Post by p_quarles on 2007-06-19
I think you can run gparted off the Ubuntu live CD as well (right?), so you might not need to download anything. In other words, try that first.

---

### Post by striker4678 on 2007-06-19
im at work right now..my summer job...and i actually work with computers which is kind of cool...and i'm on my work laptop..so i have to wait until tonight to do all of this i'm just trying to figure out and plan what to do tonight...

---

### Post by striker4678 on 2007-06-19
ok so should i use like this boot and nuke disk i have?
and then just start fresh, install windows using the dell cd
go online and get the driver stuff from compaq(im not sure exactly what stuff to get)
re-install ubuntu
and be sure and not use the partition whole disk option?

---

### Post by buuntuu! on 2007-06-19
then download gparted if you can at work. you can run it from the live cd alright, but at gparted's homepage you will get the latest version. partitioning is one of the more "dangerous" things to do to your hd, it pays to be up to date...

edit: get the drivers beforehand! if you can't get online for some reason with your fresh install (eg. because of  missing drivers;)) you will be happy to have them...

---

### Post by striker4678 on 2007-06-19
what exactly does gparted use..and how should i use it?  
what should i do with it i mean?

---

### Post by buuntuu! on 2007-06-19
gparted is a partitioning program. you can wipe your hd with it and format it with a windows filesystem, then install xp and so on...
it has got a gui, so it's quite self explaining...
read [this]("http://users.bigpond.net.au/hermanzone/") before you start, it will provide you with the necessary info on what you want to do.
have fun

---

### Post by striker4678 on 2007-06-19
i downloaded the live usb
could you tell me step by step how to go about getting closest to xp and feisty dual boot from what i have now
which is the ubuntu feisty

---

### Post by striker4678 on 2007-06-19
haha thanks i'll try i hope i don't mess up

does it erase the hd too?

---

### Post by buuntuu! on 2007-06-19
phew, it has been a while since i did my last install, so my step-by-step-ability is limited;)
but read [here]("http://www.psychocats.net/ubuntu/index.php") as well as the link from my last post and you will do fine!

but first things first!
1.wipe with gparted and format for windows (fat32 or ntfs, it's up to you -find out which is best for you thoug!)
2.install with your dell-discs (hope iceportal was right about the dell-discs, if not you'll have to create your own install-disc)
3. install ubuntu, this time without wiping xp;) 
the links i provided will inform you about the details!
4. have fun dual booting. you'll soon be a happy linux user, i'm sure!

---

### Post by striker4678 on 2007-06-19
thank you!
i may have to PM you later tonight! 
thanks for helping me with all my annoying questions! haha

---

### Post by buuntuu! on 2007-06-19
you're welcome!
it has not been long since it was i who "annoyed" others... just returning the favour to the community:KS

---

### Post by niglch on 2007-06-19
You've got to be pretty careful to avoid data loss when repartitioning hard drives. I remember being scared to death of messing it up and deleting everything because my computer didn't come with a recovery CD. Instead it came with a second partition for restoration. In my opinion, this makes no sense because one partition is as vulnerable as the other to damage, and the purpose is defeated. For future reference, I have also heard it's a really good idea to defragment any Windows partitions if you are going to repartition to avoid any stray or possibly important files from getting whacked.

One alternative solution is to install Ubuntu on another hard drive if you are willing to spend a little bit of money. I installed mine on a 160GB External HD connected to my computer via USB. If you have a newer computer, this is great because you will be able to install the GRUB bootloader on the external HD and you won't even need to touch the internal HD. This helps because if you decide you want to uninstall Ubuntu, you won't need to deal with restoring your master boot record. All you need to do is set your USB drives or second HD ahead of your internal HD and you will get a grub menu as long as the external HD is on. If it isn't, you get Windows. If you have an older computer like I do and your BIOS won't directly boot from USB drives, you can still install grub on the interal HD with little risk to the windows partition itself. The disadvantage is that your external HD must be on before you start your computer or else you will get a lovely "error 21". However, you will still have Linux and Windows on totally separate drives.

As for your music collection, if you got your songs from CDs you'll be fine because you can simply re-rip it. I know it's time consuming, but sound tends to be better on Linux than Windows for some reason. If you downloaded your songs from iTunes or another store that uses DRM, be warned that it probably won't play on LInux simply because of the DRM. However, I don't think you will be able to simply recover your music collection since the HD was reformatted completely. Sorry, but you might find Ubuntu worth the trouble (I almost never use Windows anymore, especially with WINE around).

---

### Post by p_quarles on 2007-06-19
niglch: A lot of computers come with recovery partitions, but I've found that they usually have a tool that allows you to make a set of disks that replace the need for the partition. 

Yeah, partitioning can be risky, but that's why you need to make backups of everything important before attempting it.

---

### Post by buuntuu! on 2007-06-19
> **niglch said:**
> You've got to be pretty careful to avoid data loss when repartitioning hard drives. I remember being scared to death of messing it up and deleting everything

what is there to be lost if all is already lost?? (read the first posts!)
but you've made a point about the recovery-partition...
striker4678: maybe there is still a hidden recovery partition on your hd from which you can reset xp to the factory settings... if ```
sudo fdisk -l
```shows you an additional partition you did not know of, (maybe around 5gig big) it may very well be a recovery partition. read your box's manual on this...

---

### Post by p_quarles on 2007-06-19
> **buuntuu! said:**
> what is there to be lost if all is already lost?? (read the first posts!)
but you've made a point about the recovery-partition...
striker4678: maybe there is still a hidden recovery partition on your hd from which you can reset xp to the factory settings... if ```
sudo fdisk -l
```shows you an additional partition you did not know of, (maybe around 5gig big) it may very well be a recovery partition. read your box's manual on this...
I doubt it. When I (intentionally) wiped a Windows drive with gparted, it reformatted the entire thing. On my dual-boot desktop, however, the recovery partition automounts in Ubuntu on startup. If it were still there, he would have seen it.

---

### Post by buuntuu! on 2007-06-19
wow, the "hidden" partition automounts? didn't know it as i wiped mine before installing

---

### Post by p_quarles on 2007-06-19
Yeah. I've found that a lot of things that are hidden in Windows show up very clearly on a dual-boot setup. I guess that the techniques MS uses to hide things are very OS-dependent.

---

### Post by thefoolisme on 2007-06-19
> **p_quarles said:**
>  Yeah, partitioning can be risky, but that's why you need to make backups of everything important before attempting it.

You can't have that quote enough on here!!!!  Backup your stuff people!!!!!  

And a little knowledge of what you're doing prior to messing with partitions is also good.  :-)

---

