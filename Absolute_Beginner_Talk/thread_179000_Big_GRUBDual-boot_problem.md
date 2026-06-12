---
title: "Big GRUB/Dual-boot problem"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by stevenash on 2006-05-18
Please help if you can.  First of all, I have 2 hard drives, one is a 40GB drive with Windows on it.  The other is a 250GB drive with Ubuntu 5.10 on it (which I am using now).  Due to a problem with installation (very long story), I was forced to unplug my Windows drive in order to install Ubuntu.

Now, I need help getting my computer set up to dual-boot after I plug my Windows drive back in.  I am a complete n00b to Linux, so could someone please give me step by step instructions?

Thank you very much.

---

### Post by Mr Fat Bat on 2006-05-18
You can do the first part of an Ubuntu install again, up until just after it installs grub.... there was a similar post involving removing SuSE where MasterChief gave an example of how to update grub using the ubuntu install disk without doing a full re-install:

[http://ubuntuforums.org/showpost.php?p=1031068&postcount=3]("http://ubuntuforums.org/showpost.php?p=1031068&postcount=3")

Hope it helps!

---

### Post by stevenash on 2006-05-18
[QUOTE=Mr Fat Bat]You can do the first part of an Ubuntu install again, up until just after it installs grub.... there was a similar post involving removing SuSE where MasterChief gave an example of how to update grub using the ubuntu install disk without doing a full re-install:

[http://ubuntuforums.org/showpost.php?p=1031068&postcount=3]("http://ubuntuforums.org/showpost.php?p=1031068&postcount=3")

Hope it helps![/QUOTE]
Unfortunately that won't help me.  The reason I had to unplug the Windows drive in the first place is because my Ubuntu installation was hanging when it got to "Starting Partitioner".  So I can't even get to the partitioner stage when I plug in my Windows drive.  Thanks though.

Any other suggestions?

---

### Post by catlett on 2006-05-18
This is pretty easy. First you'll have to open up the grub menu in a text file you can edit. Enter this in the terminal; (applications<accessories<terminal)```
sudo gedit /boot/grub/menu.lst
```
Once it is open hit enter a couple of times to get some space between the last entry and the one I'm going to give you. Next enter this in the text.
```
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
Hit save on the applications window. When you reboot grub will have an option to bot to it, This will work if windows is on the first hard drive and is in the first partition.


P.S. If windows isn't your master drive let me know and we'll work out which partition and drive it is on. But if it is your master drive and it has nothing else on it, this will work.

---

### Post by tuxcantfly on 2006-05-18
at the root section, the 1st number is the hard drive number, and the second is the partition number, so (hd0,0) is hard drive 1, partition 1. for something like hard drive 2, partition 3, it would be (hd1,2)

---

### Post by stevenash on 2006-05-18
Okay, thanks guys I will try this.  Stupid question: Do I need to insert the code after this line or before this line - ### END DEBIAN AUTOMAGIC KERNELS LIST  ??

---

### Post by Mr Fat Bat on 2006-05-18
You can stick it after if you want, or before, I don't think it will matter.  Everytime you do an automatic kernel update through apt it will add all of your kernels back in along with that line ;)

---

### Post by stevenash on 2006-05-18
Also in my current menu.list, it has all of the Ubuntu kernels set up like this:

```
title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot
```

All of the roots are set as (hd0,0).  Should I probably set the the Windows one as (hd1,0)?

---

### Post by catlett on 2006-05-18
Yes. If windows is the slave you are right. Grub starts with 0. So 2nd hard drive first partition is hd1,0. Just enter it like this 
```
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```
Enter it at the end of any other text. It actually doesn't matter. A "#" in front of a line of text makes grub ignore it. It will only recognise a line without a "#". So as long as you enter it without a #, grub will see it anywhere.

---

### Post by stevenash on 2006-05-18
Well, Windows is supposed to be the Master drive.  However, I took the jumpers off both drives in order to install Ubuntu.  I guess now Grub thinks that Ubuntu is the Master drive (hd0)??  So should I switch the jumpers around and make Windows the slave and Ubuntu the Master?  Or will Grub update itself?

---

### Post by catlett on 2006-05-18
Grub doesn't care about those numbers. It is in the MBR section of the 250gb drive. When you boot to that drive it will be there. BUT, YOU HAVE TO KEEP THE 250gb UBUNTU DRIVE THE MASTER. If you put the windows to master it will not have grub and will load windows. (sorry I didin't read your post careful enough and put this in earlier)
You have to keep Ubuntu's drive with Grub on it as master and put windows as the slave with the edit of hd1,0 in the grub list. All should be fine then.

---

### Post by stevenash on 2006-05-18
Grub only loaded up Ubuntu when I rebooted my computer.  It happened quickly...I believe it said something about pressing ESC to cancel, and it counted down quickly and then loaded Ubuntu.

---

### Post by catlett on 2006-05-18
What was listed in the grub menu? If it didn't have a menu it might be the new version of grub. In the new version it will only show the default option. You have to press any key (or maybe esc in your case) to get to the menu. The menu will have the options listed in the list. If you edited the list and saved it, the entry is there. Even if you put the wrong hd0,0 the entry would be there, It would just come up with an error when it tried to boot,
Do 2 things. Open up your grub list and make sure you saved the changes. Next when your computer boots press a key to get to the menu. That should be it. Post if there is a problem

---

### Post by stevenash on 2006-05-18
[QUOTE=catlett]What was listed in the grub menu? If it didn't have a menu it might be the new version of grub. In the new version it will only show the default option. You have to press any key (or maybe esc in your case) to get to the menu. The menu will have the options listed in the list. If you edited the list and saved it, the entry is there. Even if you put the wrong hd0,0 the entry would be there, It would just come up with an error when it tried to boot,
Do 2 things. Open up your grub list and make sure you saved the changes. Next when your computer boots press a key to get to the menu. That should be it. Post if there is a problem[/QUOTE]
Okay, BIG problems.  First, I changed the title from "Microsoft Windows XP Professional" to "Windows NT/2000/XP (loader)", and this time I pressed Escape and got to the Menu.  I selected Windows NT/2000/XP from the list, and it gave me an error saying that it wasn't found or something.

When I restarted the computer, the GRUB loader gave me an Error 17.  It continues to do this.  I had to go into BIOS and turn the Ubuntu drive off and I managed to get into Windows (which is where I am now).  I'm not sure what to do.  In BIOS the Ubuntu drive was set as Primary Drive 0 and the Windows was set as Primary Drive 1.  I don't know how to get back into Ubuntu to fix anything.

Help.

---

### Post by catlett on 2006-05-18
OK things are getting complicated. First the title doesn't mean anything to grub. It is for your reference when in the menu. All the entry does is tell grub what to put in the menu as text.
Error 17 usually means grub can't find itself. Did you switch the drives around?
If you just put the Ubuntu disk in alone does it boot?
If nothing works look at the bottom of my posts. You will see a link "drivers to access Ext2/3 partitions (your ubuntu partition) in windows". Hit on that link. Download and install the program. This will let you see the ubuntu partition.
Read the directuions but quickly when you install go to the comtrol panel/ "switch to classic view" then you will see the est2fs icon. Hit on it. You will have a drop down box in the ubuntu partition. Hit it and pick a letter . close. Go to "my computer" the ubuntu partition will be next to windows C or local disk.
You can get into ther grub list again by navigating to the boot folder and then the grub folder. You might have to start by entering the root folder. then the boot folder. then the grub folder. double click on menu.lst. Make sure you entered everything correctly. Check the hd1,0 again.
I have to turn in so I won't be back until tomorrow. For now I'm going to post my list as an example. My list has alot of entries but just check the wording for windows and ubuntu. (you might have different kernels so the numbers after the kernel might be different. But it is more about the set up of it. 
```

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.15-18-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-18-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-18-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-18-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-18-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-18-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Debian GNU/Linux, kernel 2.6.15-1-486 (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-1-486 root=/dev/hda7 ro 
initrd		/boot/initrd.img-2.6.15-1-486
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Debian GNU/Linux, kernel 2.6.15-1-486 (recovery mode) (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-1-486 root=/dev/hda7 ro single 
initrd		/boot/initrd.img-2.6.15-1-486
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by fornix on 2006-05-18
I havent tried editing linux files in windows. Though i doubt it will give rise to some complications. Windows Puts a CR/LF after each line. so files saved as text in windows may cause problems with linux.

**@Stevenash**
Additionally i think you might have to change boot.ini in C:\ 
My contents of boot.ini are
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

You will have to change the rdisk(0) to rdisk(1)
I am not sure you need to do this though.

---

### Post by confused57 on 2006-05-19
Check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper)

Basically, set your Ubuntu drive as the master drive and windows as the slave.
When you boot up you computer should boot to Ubuntu, check out the entry to place in grub for windows...it's how I have my system set up.

I'm assuming windows mbr doesn't have Grub installed to it...if it does, you could boot up with the windows install cd and "fixmbr", then set it up the way described in the link(see the instructions by "lha").

Just another option for you to consider.

---

### Post by stevenash on 2006-05-19
Thanks confused, I will keep that in mind.

Let me walk through how my hard drives were setup and partitioned through this entire process to make sure that the GRUB menu.lst file is set up correctly.

First, before I ever installed Ubuntu, I had my 40GB Windows drive set as Master and the 250GB drive set as Slave.  The Ubuntu installation wouldn't work with it set up like this (long story).

To install Ubuntu, I unplugged the IDE and power cables from my 40GB Windows drive, and then took the jumper pin off of the 250GB "Ubuntu" drive.

I installed Ubuntu easily, and the menu.lst file had all of my Ubuntu kernels as (hd0,0) because it assumed that my 250GB drive was the Master (and the root directory was my first partition).

I changed menu.lst and added Windows to the bottom, setting its root as (hd1,0).  I plugged my Windows drive back in, and changed its jumper to Slave.  I put the pin back on my 250GB Ubuntu drive, and put the jumper pin to Master this time, istead of slave.

When I chose Windows from the GRUB menu list, it would not load (saying something about a loader not being found), and then everytime my computer reloaded, Grub gave an Error 17 when trying to load Ubuntu.

It looks to me like to get Grub to load I may have to set my HD's up the way it was when I installed (no pin on the 250GB drive, unplug Windows).  I haven't had time to open my computer and try it, but I will.

For now, I need to figure out how to set up Grub's menu.lst.  I noticed that on my Windows drive, there is actually a small FAT partition before the large Windows partition.  Does anyone think that I should set Windows root to be (hd1,1)?  I'm also assuming that I will have to do something to the Windows boot loader.

Well, there's an account of my problem to date.  I have to work all day and will be unable to post or mess with my computer until tonight or even next weekend, but if anyone can offer any suggestions on exactly how I should set up Grub, I would appreciate it.  Thank you.

---

### Post by confused57 on 2006-05-19
I don't have much time, 9:00 tee time for golf.  Read back over the link I gave you...it looks like grub is on the 250G Ubuntu drive, that's good.
What I'd do is set the 250G as master, and the 40G as slave.  The trick is the windows entry in your Grub menu.lst:
         For now, yes I believe the windows root would probably be (hd1,1)...what's important is the mapping command part...it fools windows into thinking it is the 1st drive.   
     The windows entry in menu.lst would be the like the one shown in the link I mentioned, except change the root to (hd1,1).  Worth a shot.

Got to run...

---

### Post by stevenash on 2006-05-19
Okay, still problems.

I am in Windows and was able to get into the Linux partition and edit the menu.lst file.  I just completely took out any changes I had made to it, so it is exactly how it was when I first installed.

I unplugged my Windows drive and took the jumper pin off the Linux drive and tried booting up.  This setup is exactly how I had it when I installed Ubuntu and everything was working fine.  I still got an Error 17.  

Any suggestions?  I feel like a completely new install of Ubuntu is coming. :(

---

### Post by catlett on 2006-05-19
If you don't have anything valuable in Ubuntu I would reinstall. If there is anything you want. Copy it over from within windows.
What was the original error when you tried to install with the 250 gb as slave?

---

### Post by confused57 on 2006-05-19
You could try to restore Grub on your Ubuntu disk(maybe disconnect the windows, just in case):

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Once you get Ubuntu working, then you could try some of your other options.

Does your mobo bios support "cable select", if so, I'd just use that for both drives?

---

### Post by stevenash on 2006-05-20
[QUOTE=confused57]You could try to restore Grub on your Ubuntu disk(maybe disconnect the windows, just in case):

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Once you get Ubuntu working, then you could try some of your other options.

Does your mobo bios support "cable select", if so, I'd just use that for both drives?[/QUOTE]
I will try this first, and if it doesn't work I will just reinstall.

I'm not sure if my bios has cable select but I will check when I get home.

One thing I never thought of...What if I unplug my Windows drive to get to the partitioner (which was my original problem, I couldn't reach the partitioner stage with it plugged in) and then before GRUB installs, I open my computer up and plug it back in.  Would that work?

Here's a link to my original problem:  

[http://www.ubuntuforums.org/showthread.php?t=178575](http://www.ubuntuforums.org/showthread.php?t=178575)

Thanks again.

---

### Post by confused57 on 2006-05-20
Here's what I'd suggest:

Read back over the link that I first gave you about dual booting.

Set your Ubuntu drive as master and windows drive as slave.  Disconnect your windows drive and just have your Ubuntu drive connected as master.

You can try to restore Grub, if you're successful, then I'd delete your windows entry in Grub(if it's there after restore).  It might be best to just reinstall Ubuntu with just the one drive connected.

After you're able to get Ubuntu up and running, connect your windows drive as the slave drive.  When you restart your computer, it'll boot up into Ubuntu...then you can add the windows entry suggested by "lha" in the link to your menu.lst.  Read over how your can increase the timeout and also show the Grub menu without having to press "Esc".

Then reboot your computer and the grub menu should come up with the option to boot windows or Grub.

Just my suggestions... you may want to try (hd1,1) or (hd1,0) as the root for windows...

I don't want to assume anything and please forgive me if it sounds like I'm talking down to you, but make sure the end of the IDE cable is attached to the Ubuntu drive with the jumper set as master.  I'm sure you already know this, but I know what assuming can sometimes do...

---

### Post by catlett on 2006-05-20
[QUOTE=stevenash]I will try this first, and if it doesn't work I will just reinstall.

I'm not sure if my bios has cable select but I will check when I get home.

One thing I never thought of...What if I unplug my Windows drive to get to the partitioner (which was my original problem, I couldn't reach the partitioner stage with it plugged in) and then before GRUB installs, I open my computer up and plug it back in.  Would that work?

Here's a link to my original problem:  

[http://www.ubuntuforums.org/showthread.php?t=178575](http://www.ubuntuforums.org/showthread.php?t=178575)

Thanks again.[/QUOTE]
I think that has possibilities. You don't need the windows drive for anything to do with the install. You would only need it to be detected during grubs installation.
I'd try that because it can easily be turned into confused's directions. Meaning if it doesn't work, add it by his instructions. You will have an Ubuntu master  with  a windows slave setup left if it doesn't work. And his instructions should work.

---

### Post by gmcle454 on 2006-05-20
[QUOTE=catlett]This is pretty easy. First you'll have to open up the grub menu in a text file you can edit. Enter this in the terminal; (applications<accessories<terminal)```
sudo gedit /boot/grub/menu.lst
```
Once it is open hit enter a couple of times to get some space between the last entry and the one I'm going to give you. Next enter this in the text.
```
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
Hit save on the applications window. When you reboot grub will have an option to bot to it, This will work if windows is on the first hard drive and is in the first partition.


P.S. If windows isn't your master drive let me know and we'll work out which partition and drive it is on. But if it is your master drive and it has nothing else on it, this will work.[/QUOTE]

I hate to jump into some one else's support thread, but when I followed these instructions, grub returned a "filesystem type unknown partition type 0x7" error when I tried to boot XP. Any Ideas?

---

### Post by catlett on 2006-05-20
Is XP on the first partition of the first hard drive?
You can also try rootnoverify instead of root for a starter.

F.Y.I. That is a copy of my windows entry that boots my computer into XP with grub. My XP is installed on the first partition of the first hard drive.

---

### Post by gmcle454 on 2006-05-20
no, its is on the first partition of the slave. 

I used this:
```

title           Windows XP
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by gmcle454 on 2006-05-20
I tried using rootnoverify, but the grub just hangs when it tries to load xp.

---

### Post by confused57 on 2006-05-20
[QUOTE=gmcle454]no, its is on the first partition of the slave. 

I used this:
```

title           Windows XP
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```[/QUOTE]

How is your system set up, meaning which drive & partition is Linux installed on...

Sorry stevenash, we're getting a little sidetracked here...

---

### Post by gmcle454 on 2006-05-20
I have Linux on the master (a 80gb drive); I now have Windows XP (which used to be the machine's only dirve) as the slave (a 60gb drive). Windows is the only thing on the slave drive and it only has one partition.

stevenash also deserves my appologies . . .

---

### Post by catlett on 2006-05-20
stevenash is off reinstalling I don't think he'd mind. Does this link have the setup for a slave drive posted? Let me search and I'll post. Just wanted to tell you about stevenash

---

### Post by catlett on 2006-05-20
This is what I was looking for. It comes from confused's post earlier in the thread.
```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```
Try that. There is also a mention in that thread to try rootnoveriry instead of root in this setup as well

---

### Post by gmcle454 on 2006-05-20
I just feel bad jumping into the middle of a support thread.

I noticed that all the linux entries end with "boot" but the windows one ends with "chainloader +1".  Does the chainloader replace boot for non-linux entries, or should I add "boot" to the end ofthe entry?

---

### Post by confused57 on 2006-05-20
[QUOTE=gmcle454]I have Linux on the master (a 80gb drive); I now have Windows XP (which used to be the machine's only dirve) as the slave (a 60gb drive). Windows is the only thing on the slave drive and it only has one partition.

stevenash also deserves my appologies . . .[/QUOTE]

No problem, sounds like steve's busy anyway...
If you installed Linux on the master drive with the windows slave drive disconnected, then you'll just need to change the entry in Grub on the master drive to access the windows slave.  If that is the case read these two threads with the instructions by "lha" for the windows Grub entry:

[http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)
[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper)

Thanks catlett, that's the entry...can't keep up here.

I personally think this method of dual-booting should be written up as a "HowTo" dual boot Ubuntu/Windows using 2 harddrives without installing Grub to the mbr of windows.  As a beginner, I was afraid of installing Grub to windows and was lucky enough to find the excellent instructions by "lha".  I think this would be a much-needed "HowTo" for an alternate dual-boot with windows.

Update: Check out the "HowTo" section if you need to refer someone to a link with these instructions for dualbooting.

---

### Post by gmcle454 on 2006-05-20
[QUOTE=catlett]This is what I was looking for. It comes from confused's post earlier in the thread.
```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```
Try that. There is also a mention in that thread to try rootnoveriry instead of root in this setup as well[/QUOTE]


Thanks! That did the trick. :D 

I get the idea of mapping the master to the slave. That makes sence, but I don't understand why reversing the map on the next line works.:-k

BTW, confused57 good links. Thanks. I realy appreciate the help from both of you. steveash, good luck and thanks for letting me jump in the middle of your thread.

---

### Post by catlett on 2006-05-21
[QUOTE=gmcle454]I just feel bad jumping into the middle of a support thread.

I noticed that all the linux entries end with "boot" but the windows one ends with "chainloader +1".  Does the chainloader replace boot for non-linux entries, or should I add "boot" to the end ofthe entry?[/QUOTE]
The chaimloader is a generic way for grub to boot a partition. If you know there is an os on the partition you just point grub at it and let it chain load. If you had a linux distro on the 2nd drive it would be easy but windows likes to be on the first partition of the first drive.
This entry would work for an os on the 2nd driv 1st partition. (The title doesn't mean anything to grub. It is for the user so he can tell which option is which.
```
title        any os
rootnoverify (hd1,0)
chainloader  +1
```

P.S. The server went down on me. I didn't see your reply. I don't know why the second line. I just copied the entry from another thread. It has something to do with tricking the windows drive into thinking it's in the 1st partiton of the 1st drive. Anyways who cares along as it worked. Stevenash didn't get in his windows but at least his effort lead to your success.

---

### Post by gmcle454 on 2006-05-21
Thanks. It always better to learn what is going on, than to just fix the problem. I appreciate the explination, this is my first time out with grub--I've used lilo for the past three years(no real reason, just what someone recomended back then). So far grub seems more user friendly.

---

### Post by confused57 on 2006-05-21
Here's a little info about Grub:

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

It says the mapping is a virtual swap to fool windows into thinking it's the 1st hard drive...

---

### Post by stevenash on 2006-05-21
Hey guys I'm back!

First of all, no problem with taking over this thread.  You deserve help just as much as anyone, and I've been out of town and unable to post my status.

Second, I was about to try and get Grubto work again, but before I did I decided to try one last time to get Ubuntu to install with both hard drives plugged in.  This time, I had the 250GB drive as the master, and the 40gb drive as the slave.  Guess what?  It worked.  The partitioner loaded up and showed both drives.  I formatted the 250GB drive and installed Ubuntu over again.  Grub detected Windows and the dual-boot is working perfectly.  So, problem solved.

Thanks again to all of you all who helped me work through it.  Now that I've got Ubuntu running, I may be calling on your help again to get some other things working.

---

### Post by Mustard on 2006-05-21
Good news.  Welcome to the world of Ubuntu. :)

---

### Post by catlett on 2006-05-21
[QUOTE=stevenash]Hey guys I'm back!

First of all, no problem with taking over this thread.  You deserve help just as much as anyone, and I've been out of town and unable to post my status.

Second, I was about to try and get Grubto work again, but before I did I decided to try one last time to get Ubuntu to install with both hard drives plugged in.  This time, I had the 250GB drive as the master, and the 40gb drive as the slave.  Guess what?  It worked.  The partitioner loaded up and showed both drives.  I formatted the 250GB drive and installed Ubuntu over again.  Grub detected Windows and the dual-boot is working perfectly.  So, problem solved.

Thanks again to all of you all who helped me work through it.  Now that I've got Ubuntu running, I may be calling on your help again to get some other things working.[/QUOTE]
It's crazy like that sometimes. You do something and you have all kinds of errors. You don't really do anything different and things work. Glad you ran into one of the times it just worked. Just for sake of curiosity, did you craete a /home partition. I say this because people really should. I never did because when I first installed I was happy to get it to partition my partition of choice. But with upgrading coming up  a /home is important.If you have seperate root and home partitions  you can reinstall the filesystem and leave /home alone. Only the root partition will be formatted. See you around.

---

### Post by stevenash on 2006-05-21
Yes, I created a /home directory.  I did a lot of research pre-installation and learned that a /home directory is definitely recommended.  This whole process of getting Ubuntu has been extremely long and challenging but it was a lot of fun and I learned a lot.  Like I said though, I still have A LOT more to learn, so I will see you all around the boards.

---

### Post by confused57 on 2006-05-22
[QUOTE=stevenash]
Second, I was about to try and get Grubto work again, but before I did I decided to try one last time to get Ubuntu to install with both hard drives plugged in.  This time, I had the 250GB drive as the master, and the 40gb drive as the slave.  Guess what?  It worked.  The partitioner loaded up and showed both drives.  I formatted the 250GB drive and installed Ubuntu over again.  Grub detected Windows and the dual-boot is working perfectly.  So, problem solved.
[/QUOTE]

Good to hear you got it working...you're learning things pretty fast.
I was wondering if you had to modify the Grub menu.lst Windows entry after you installed Ubuntu to the master with both drives connected, i.e. did you add the mapping commands after installing Ubuntu?

---

### Post by stevenash on 2006-05-22
[QUOTE=confused57]Good to hear you got it working...you're learning things pretty fast.
I was wondering if you had to modify the Grub menu.lst Windows entry after you installed Ubuntu to the master with both drives connected, i.e. did you add the mapping commands after installing Ubuntu?[/QUOTE]
Actually, when I saw that both drives were working I just completely wiped my first installtion of Ubuntu off and started over.  When it went through the installation again Grub set everything up on it's own and both systems boot perfectly.  Never touched menu.lst.  It went from being a major pain in the rear to a textbook install with just the switch of some jumpers.  Again, thanks for all your help.

---

### Post by gmcle454 on 2006-06-14
[QUOTE=gmcle454]Thanks! That did the trick. :D 

I get the idea of mapping the master to the slave. That makes sence, but I don't understand why reversing the map on the next line works.:-k
[/QUOTE]

Just an update for anyone reading  this tread. 

It dawned on me the other night. If you map drive hd1 to pretend to be hd0 then you have to map what is hd0 to be something else, otherwise grub thinks there are two drives that are both hd0 and it won't know which one to write to. Essentially it would cause a logic problem. 

It is realy simple, I don't know why I didn't realize that earlier.

---

