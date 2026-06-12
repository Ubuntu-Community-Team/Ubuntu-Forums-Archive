---
title: "[SOLVED] 7.10 not booting after new installation. please help a newb!"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by h84ll1 on 2008-01-17
hi there,

after much reading and looking at what can be done with ubuntu on various sites i decided i wanted to install it.  moving away from windows can only be a benefit!
I'm entirely new to linux though, although my computer knowledge is not too bad.  Having said that i'm not familiar with using the command line interfaces i keep seeing code quoted for, hopefully i'll get used to it.

I need help getting the install to boot.  After sorting out the partitions manually, everything installed from the live CD and then i rebooted as advised.  When i reboot i just get the windows xp choices to boot (there are two because i have custom boot and logon screens for windows), but nothing at all mentioning Ubuntu as a choice to boot to.
I installed it on the same drive as windows, but on a separate partition.

What can i do to get my machine working as dual boot?? (the pages i've found relating to dual dont match what i've done)
I think it's just the setting up of what boots the OS list i need help with for the moment. Is there a program i can get to run in windows to sort this out??

hope you can help!!
thanks :)

---

### Post by pollywog on 2008-01-17
Can you tell if your bootloader in now the program "GRUB", or is the bootloader exactly the same as it was before you attempted to install Ubuntu? GRUB is a real "Plain Jane" text based interface, but it's fairly clearly marked as GRUB, so this should be obvious. If your bootloader is not GRUB, then the problem may be that GRUB was installed in the wrong location. This can happen if you have a 2nd hard drive installed. If that is the case you can probably get your system up and running by booting into your BIOs setup, and changing the boot order so that your other Hard Drive is booted earlier in the boot sequence. It's easy enough to switch back if that's not the case. There as a great free utility called "Super Grub" that can be freely downloaded and burned to disk, that will likely allow you to boot into your new OS directly, and/or repair a messed up boot loader.

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

 Also, you may have just gotten a bad install, which may have been a fluke, or been caused by a faulty CD. It's likely that if this was the case, you'd be dead in the water staring at a screen telling you "GRUB error 22" or something has happened. Hang in there and don't get discouraged, we can probably help you get your new system up and running-you'll be happy that you did.-P.W.

---

### Post by h84ll1 on 2008-01-17
thanks for that advice, nice and straight forward :)

I downloaded super grub incase i'll need it.  I restarted to check if there was any mention of GRUB in the loader i see, there wasn't so it must not be quite right.
When i was installing i did see an 'Advaced' option about where the boot loader would be installed, think it said hd0, but i was unsure of what that meant so left it well alone.
I do have a second hard drive so maybe it's been put there. will i need to remove it??!
the second one is on the primary IDE channel, the one i installed onto is SATA on the first SATA port on the motherboard so.

So where do i go now?
think i'll try looking in the bios as you suggested, then if no joy i'll burn super grub iso and try running that.

let you know how i get on.

on a side note, security wise will i need to install stuff on ubuntu for that? I'll probably need to update the OS once i have it booting so i want to be secure also. I can download what i might need on windows first?

thanks again!
don't be a stranger :)

---

### Post by h84ll1 on 2008-01-17
ok so now i'm back from experimenting.  I tried lookin in the bios first, the hard drives are set to boot in the right order.  Did you mean try booting to the one where the boot loader may have been put incorrectly? just that that disk won't have the actual stuff installed on it, since it on the other disk. hope you see what i mean with that.

anyway, i tried out a few things with Super GRUB.  My comp now boots to a different list (i guess this must be GRUB-list in a box, few choices) but none of the choices work.
Those related to Linux give me the error;  Error 22 partition doesn't exist (or something like that)

Those related to windows take me to a different error saying; NTLDR is missing. I then have to press ctrl+alt+del to restart (says this after the warning). then it just restarts and gets me to this menu (i think its GRUB) again.

however, if i use the option to do with booting Linux in Super GRUB 'Boot Directly' allows me to boot to the partition with Ubuntu on it, it loads up and i can log in and use it.  Thats good i guess but i want dual boot set up for easy use.

I can also boot to windows (hence me being able to write this) by using Super GRUB and the 'Boot Windows' option.  This brings me to the original choices i had before installing Ubuntu.

All a little confusing.  :confused:  I can boot to them both (using Super GRUB), but as far as having a working list load and choosing which OS i wish to load (which is what i want) that is not present.

What can i do to sort this??  If a fresh install of Ubuntu will help i don't mind that since i've not really used it yet. just need to know where i may have got it wrong.

Hope you can help further!

---

### Post by pollywog on 2008-01-17
I'd say that it is quite certain that you just got a bum install of GRUB. That "Super Grub" disk has some utilities to fix GRUB, but unless the problem is that GRUB has been overwritten after a reinstall of Windows- which will happen, and it will fix- I haven't had much real luck with fixing a messed up GRUB with this utility. My advice:
1) Try fixing GRUB with "Super Grub"- if that doesn't work

2) Use "Super Grub", tell it that you are using windows, and choose "fix boot of windows", which will erase GRUB, and reinstall windows bootloader

3) Use Gparted disk

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

or similar Partition Editor to delete the 2 partitions associated with this Ubuntu install (Ext3 & swap)

4) Open your computer case, unplug any other hard drives, leaving only the target drive connected.

5) Reinstall Ubuntu, choosing "install on largest continuous free space" option.

I'll bet that this will get you up and running. I'll send you some additional info about getting started directly to your private messages of your Ubuntu Forums profile. Good Luck-P.W.

---

### Post by h84ll1 on 2008-01-18
well, i have fixed the windows loader again (how you said to) so it now goes to the original booting screen i saw before installing ubuntu.

I'm getting gparted now to delete the installation and start fresh.  I'll do it with my other hard drive disconnected as you suggested, it makes things simpler!! great idea that i didnt think of when i first wanted to install.

I've done a little research into wifi, and believe i need something to allow my wifi card to work in ubuntu. i downloaded what i needed in windows (the offline version of it) and transfered to ubuntu using a usb device, but i couldn't unzip the file to then use it. my wifi card is BCM4318 so.

how can i update ubuntu to a point where i can use my wifi without having it connected to the internet via cable??

if i can get what i need to install downloaded in windows, then i'll just transfer that via usb and run in ubuntu. once i have the wifi sorted i can get everything updated within ubuntu. :confused:

this is confusing me some what! lol. if i dont have cable internet how can i update it!?

thanks again for all the help!

---

### Post by njparton on 2008-01-18
Your IDE drive will be hd0 and your sata drive will be sd0 so grub was installed to your ide drive and not your sd0 drive which is where you really wanted it.

Just change your bios to boot from the ide drive first to see grub (which should also include an option to boot windows as well as ubuntu).

---

### Post by h84ll1 on 2008-01-18
> **njparton said:**
> Your IDE drive will be hd0 and your sata drive will be sd0 so grub was installed to your ide drive and not your sd0 drive which is where you really wanted it.

Just change your bios to boot from the ide drive first to see grub (which should also include an option to boot windows as well as ubuntu).

thanks for chipping in with that. i thought it might work something like that.
i've re-installed ubuntu now. did it again entirely but with only the target drive attached.  it now boots to either like its supposed to and i've plugged the ide drive back in now (it doesnt have an adverse effect).  Hopefully it's booting from the drive with the installation on (it boots without the ide plugged in though so).
i couldnt get the liveCD of Gparted to get to a point where i could use it so i just decided reinstalling would prob be able to do the same thing i was after.

now, how about this wifi driver thing? any ideas? if i can get what i need though windows i would hope i could sort it. :confused:

thanks again for your help

---

### Post by pollywog on 2008-01-20
Try this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

It has a procedure for getting connected, on a non-internet enabled machine, though it still requires that you download a few packages on another machine that is internet capable, and transfer them manually.

---

