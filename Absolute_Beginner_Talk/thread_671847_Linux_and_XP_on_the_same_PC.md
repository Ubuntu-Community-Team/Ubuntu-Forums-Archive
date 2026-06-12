---
title: "Linux and XP on the same PC"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by mereidmo on 2008-01-19
I really am at a loss here. I tried linux a few years ago and found it very frustrating, but I want to give it another try after seeing the "xubuntu compiz fusion" video on youtube. I believe this will breathe new life into my old computer.

However, I'm not ready to give up windows xp. I have a lot of programs that I use that I still want to run when I need them, so I think the solution is being able to choose (when I boot the pc) whether to boot into linux or windows xp.

Will this be possible with only one hard drive? If so, could someone please point me to a complete tutorial?
The edition (if you can call it that) Of ubuntu that i am using is the umm.. "gutsy gibbon 7.10" something like that..  I would be so grateful for your help!!!!

Thank you very much,
Reid

---

### Post by dcast on 2008-01-19
That should be no problem at all. Try looking here: 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Good luck,

Dcast.

---

### Post by argraff on 2008-01-19
dcast has you on the right track. 

Just FYI, "Gutsy Gibbon" is the friendly name for Ubuntu 7.10. "7.10" refers to it coming out in October ( 10 ) of '07. Each release has it's own animal name and the date of it's release, the next one being Ubuntu 8.04 ( April 08 ) "Hardy Heron."

Welcome! :)

---

### Post by mereidmo on 2008-01-19
oh man thank you for the help! someone else told me i needed to get qparted and then just left me on my own.. heh

---

### Post by z-itou16 on 2008-01-19
hi everyone.
well first of all sorry if my grammar is a little bad here, i am not a native English speaker. mereidmo I know how you about getting into linux, it is a little hard at the beginning since you have to get use to the terminal, compile, bash and other things that with the time and the proper practice you get use to it. this is the BEST tutorial i found and indeed it help me. well i gave me the idea. it take more steps but trust me the results are secure and you will be a happy camper.

here the link [http://www.apcmag.com/node/5162/](http://www.apcmag.com/node/5162/)

have  good day and if anything go ahead and post it and we will try the best to respond in the time mane. :)

---

### Post by HermanAB on 2008-01-19
Well, Ubuntu is not the easiest Linux around - it is kinda intermediate.  If you want a version of Linux that is very easy to install, plays nice in groups and allows you to do everything at the click of a mouse, then you should consider Mandriva, or its step-child PCLOS instead.

---

### Post by mereidmo on 2008-01-19
Well I don't know what the hell to do.. I'm sorry if my frustration comes out here but I burned the iso of xubuntu 7.10 and upon trying to start the live cd i got some error saying something was wrong with my disc.. 

so then.. i just went back to this thing called wubi.. it did its thing and i can boot into xubuntu 7.04, but i have no internet, media is unplayable in ginexine, and at one point my keyboard became unresponsive. on top of that, performance is slow..

i dont know wtf to do.

---

### Post by Aurora@FleetBuzz on 2008-01-19
mereidmo, did you verify the CD after downloading, and before burning the .iso file to the CD?  You may have got a bad download.  See here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Ub1476 on 2008-01-19
I suggest installing through the CD. Wubi is in beta so it is actually dangerous to install if you don't want to experience, and it's using the previous Ubuntu version, which has outdated drivers. On the CD menu, you can check the CD for errors. If there are errors, burn a new CD (and do a check sum) on slowest speed possible. If there are no corrupted files on the CD, post the error message here.

---

### Post by angry_johnnie on 2008-01-20
Hi there.  You most likely don't want to install it through wubi.  It's easy, yes.  But, since it uses the alternate iso, it'll be installing a lot less things.  As for the "unplayable" media, what exactly do you mean?  Mp3 and the like?  That is actually going to happen in all versions of Ubuntu  (you know K, X, G, Flux and so on), because they make it a point to include only free and open source software --no proprietary codecs.  You won't be able to get any of that until you enable the medibuntu repositories.  Go to [www.medibuntu.org](www.medibuntu.org)  for more information.  If you want a linux/ubuntu system that is fully functional out of the box, I would suggest using one that is more "newbie-friendly."  Try Linux Mint.  You'll get all your codecs and drivers and whatnot, as well as compiz-fusion. You'll find more info at [www.linuxmint.com](www.linuxmint.com).  (and just for the record, you might want to download the Gnome Main Edition).  Go ahead and download the iso.   But be sure to check it for errors before you burn it.  And, when you do, make sure you burn it a a low speed.  Somewhere in the vicinity of 4x will do just fine.  As for the dual boot.  Well, that's another story, but it's, really, not as difficult as one might think. First of all, you want to defrag your windows installation.  Then you can load the cd and reboot.  Once you boot into the live session you'll see some icons on the desktop.  One of them says install.  Click on it and answer a few questions regarding your language and keyboard layout.  Partitioning your hard drive is the tricky part.  The easiest way to go is to choose the option that says "resize existing partition and use remaining space."  That will shrink your windows partition.  So, when you choose the new size, keep in mind it'll be the size of your windows (not linux) partition.  After that it's all pretty straight forward.  If it asks you whether you want the bootloader, answer yes.  That will install GRUB, which will allow you to choose either linux or windows.  And, by the way, the next time you boot into windows, it will have to check your disk for erros, but there should be no problem.  I've done this a couple of times, and nothing happened.  So don't panic.  Just let it check whatever it has to check.  And, it's basically the same for any distro.  I've just recommended linux mint because it's easier to handle if you haven't used linux before, and because you wont have any problems regarding proprietary drivers.  It's ubuntu-based, and that means that any answers you see here, will probably help you as well.  And, don't freak out if you can't get something done.  You'll get the hang of it soon enough!:guitar:

I forgot to mention this. :-)  You may or may not know this, but when gparted "shrinks" your windows partition, it'll also shrink the files in it.  So, fear not.

---

### Post by mereidmo on 2008-01-20
I think Linux Mint will be best for me especially if it has alot with it and comes with compiz fusion. i have also decided to format my system. however i do have one concern:  when i format my system with my windows disc and it asks me about the partitions i want, will that be a sufficient partitioning? also, after i get windows up and running, do i just run the linux mint live cd and install from there? will it give me an option to install the bootloader?

---

### Post by Smelly Avocado on 2008-01-20
if you format it you will delete all the data. i would reccomend following the steps from
[http://www.apcmag.com/6101/dualboot_windows_xp_and_ubuntu]("http://www.apcmag.com/6101/dualboot_windows_xp_and_ubuntu")
except using linux mint.
im pretty sure it will work. 
just backup all of your data to be safe.

---

### Post by mereidmo on 2008-01-20
i want to format.. i've formatted before, i know how to do it. i have my xp disc and i'll just add a partition when i format.. i want to start fresh and have been thinking about doing it for awhile anyway. disc defragmenter does not work very well on here. i'd have to run it many times.. so i'll just format and that way if i screw up anything i'll have everything backed up and it wont matter.

---

### Post by angry_johnnie on 2008-01-21
If you create your partitions using a windows cd, then you'll still have some more partitioning to do.  After you get windows up and running, load the linux cd, and reboot into the live session.  Go to your menu and find an option that says 'partition editor.'  That will open a window showing your existing partitions.  At this point, I'd figure you'll have only two.  One will be your windows installation, and the other one, the one you want for linux.  If your soon-to-be linux partition is formatted already as NTFS, then right-click on it, and choose 'delete.'  Then click the button that says 'apply.'  Deleting and creating new partitions is faster than formatting already existing ones, especially if they're big.  After it has been deleted, you should see your windows partition, and a gray block that says 'unallocated.'  Right click on it again and choose 'new.'   That will bring forth another window where you can choose the size of the new partition.  Make it about twice as big as your ram, at least.  Then, where it says 'file system,' choose linux-swap.  Right click on the 'unallocated' space again and create another partition.  The file system should be ext3.  You could use all of the remaining space for this one, but it would be much better to create yet another ext3 partition.  The reason for this is that one of them is going to be your root partition, and the other one is going to be home.  Home is where all your personal files are stored.  If you should have to install the system again, you would only need to format your root partition, leaving your home partition and, thus, your personal files, untouched.  I'd say 5-6 Gb is ok for a root partition.  Two will do, but then you might run out of space pretty soon.  The rest of it goes to home. When you're done, click on apply.


When you're finally done with your partitioning frenzy, you can go ahead and install.  Again, click on the desktop icon, answer a few questions about your language, keyboard, timezone and so on.  But, when it asks you how you want to install it, you want to go for the 'manual' option.


It will ask you to choose a swap partition and a root partition.  You've already created swap, so all you have to do is click on the partition you want to be root.  Then click on the button that says 'edit partition.'  Go to where it says 'mount point,'  scroll down and find '/'  (just a slash).  Select that and click ok.  Then select the partition you want to be home.  Click on 'edit'  and choose '/home' as the mount point.  Before you go on, make sure the box under 'Format?'  is checked for both.  After that, just click forward.  When it asks about the bootloader answer yes.  You may want to go into 'advanced options' just to make sure GRUB will be installed on hd0.  If it is, don't tinker with it.


And that's pretty much it.  Just go grab a cup of coffee while the system is being installed.  If you have an internet connection (you can, in fact, log on to a wireless network from the live cd) it will download a couple of things, such as language packs and the like.  When it's done, it will ask you to reboot.  And you're done :-)

---

### Post by hwheeler43 on 2008-01-21
:) I have a desktop and a laptop running both Ubuntu 7.10 and Windows XP in a dual boot setup.  Both already had XP installed and I simply installed Ubuntu from the live CD.  Both systems are working great. I simply let Ubuntu use and format the free space it needed on my drives.  I have no problems booting in to either system.  I did initially have a problem with Large Fonts on my Username and password screens in Ubuntu.  Fixed that with a search in these forums.  

If you are going to start from scratch,  I would recommend installing Windows XP first,  then install from the Live CD and let Ubuntu do what it needs to do.

---

