---
title: "partitioning advice please"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2005-09-02
Hello there,

(bit xp - but kubuntu relevant  :)  )

I hope someone can help. I'll try to explain the setup I have at the moment, the reason for the change, and then post my questions about how to do all this. Ok...

I have a (scratched and battered) toshiba laptop. It is a few years old now (2.4) I think, and I have recently pumped it up with some more ram. All is moving along at a bearable speed. The laptop has a harddrive of 40gig. It is partitioned as follows

hda1 xp home
hda2 kubuntu
hda3 linux swap
hda5 fat 32 shared partition

When I first installed XP and fired up cubase - everything was working fantastically. Now, that other stuff has creeped on their - it has slowed dramatically. I think Norton in particular is dragging things along. Well I do most of my music in linux - but occasionaly like to try out something in xp/cubase. So, I'd like to add another instance of XP to the above setup - one which I can keep scrubbed clean and studio software specific. Can I though - is there a primaries limit? if so would there be any way to combine the two linux file systems so they classed as one primary?

This gets more complicated. As Toshiba sold me a machine that has a damned recovery disk with the OS on, and not a XP installation disc. So I guess I'll have to copy the first partition - and then trim teh fat from it. Very annoying. Particularly as I have seen standard XP home installs amount to about 2.5 gig in space - and the (minimum) toshiba install bloats up to over 4 gig. That is space just being wasted. I can delete fonts and stuff, but where does nearly two gig come from?! So, thats the other issue. Any serious trimming tips and speed up links much appreciated.

This laptop connects through a dsl hub. Is there any way I could take the xp audio partition offline (short of removing the cable) - then I'd not have to both with the slow antivirus.

I am thinking of using the tools on BootIt NG to resize the FAT32 partition - and create in the new space a copy of the XP partition. Am not a linux ninja though, so any advice on how to update Grub also very much appreciated.

thanks in advace,
John

---

### Post by aysiu on 2005-09-02
If I were in your shoes, this is what I would do:

Back up everything--all your data, your emails, your music, your preferences.
Then, I'd use the Windows XP restore CD (unfortunately, if your restore CD is anything like mine, it'll just wipe out the entire hard drive).
Shrink the Windows partition to its smallest possible size.
Then reinstall Kubuntu.
You can probably, in the network setup in Windows, disable your ethernet connection without physically pulling out the cord. Poke around there and see what your options are.

If you are able to reinstall Windows without wiping the entire hard drive clean, you can then follow these instructions to reinstall Grub:

[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by Hobbsee on 2005-09-02
I was in the a similar situation as you - toshiba laptop (A10 Satellite 40 gig HD), wanting to reinstall windows.

What you will find is that the toshiba recovery disk will not overwrite your MBR - I was amazed at this, but it's true - feel free to test it, if you really want to.

Got no idea what the extra rubbish is on the toshiba CD - maybe a lot of the toshiba config tools?

I'd probably suggest that you trash your current windows, and reinstall it on that partition - toshiba restore cd will let you do it, as long as it thinks the partition is not too small. ie. 10 gig.  Unfortuanetly, when i tried that, i found that the toshiba rescue cd couldnt count, and thought that the 16 gig windows partition was less than 10 gig - go figure.

If you do decide to trash it, then make sure you have a backup of all your windows stuff - any AV/Firewall install files you have, the serial numbers for them (as you want to get them running as soon as possible), your windows and or office activation, if you dont want to reactivate them over the internet (i find it's quicker to reactivate them than copy the files, particularly for windows activation), and backup all your documents on both operating systems...

The reason for suggesting you trash your current windows:  you'd need at least 10 gig of space for each windows, and you are only likely to boot to the new, faster one, effectively leaving you with 10 gig unusable space...

---

### Post by pompeyjohn on 2005-09-03
Thanks for the replies. Am not too worried about the mbr being overriden because Grub can be installed at anytime right? and then that would overwrite whatever XP did yeah? Or am I way off on this.

The problem I now have is that the toshiba recovery disk will only wipe the entire disk; no matter how it is partitioned. It see's 40 gig and wants to ghost the entire drive. grrr. (It's an A15 btw)

Have stripped out everything Toshiba (config tool and other) wise from the install and still have just under 3 gig. Remarkable. Very good advice on backing up and noting serial numbers!! Thank you.

Ok, I think this is what I'll have to do;

1. backup everything.
2. use recoverydisk to install bloated toshiba xp install - this will wipe all drive
3. repartition drive to say 30 gig free space
4. copy xp partition to hda2 - leaving 20 gig - and a music and home xp instance
5. resize again to create fat32 partition in hda3
6. install ubuntu
7. install grub to mbr

That sounds like madness - but it is the only way I can see this working with this damned recovery disk.

Would grub pick up both XP partitions? I am concerned that there is a four primaries limit I read about somewhere.

I didnt know that I could disable the ethernet port in network setup. That would effectively take the studio offline and mean no need for av. Just a thought, I could run av on the home instance and have it check the studio one couldnt I? Both instances would see each others 'c drive.' I wonder how secure that is though.

Thanks for the tip on reinstalling Grub. I'll print that out, it might come in handy if I can get around the limitations of this damned recovery disk.

Right, I am gonna start this in about an hour - so any last minutes tips advice - or reassurance on the grub/limit primaries question - very much appreciated.

John

---

### Post by bjweeks on 2005-09-03
You could shell out 80 bucks for a real copy of XP. It would make it a 2 step process. 1. Intall XP 2. Install Ubuntu.

---

### Post by pompeyjohn on 2005-09-03
No way, I already own one version - I refuse to buy another because the QA department at Toshiba is awful.

---

### Post by bjweeks on 2005-09-03
Yep, most major computer manufacturers are just giving you Restore cd because they get a discount form Microsoft. There so excuse for all the crap they put on your cd there is just no need. But some people just have to 3 media players.  :rolleyes:

---

### Post by Hobbsee on 2005-09-03
[QUOTE=pompeyjohn]
Ok, I think this is what I'll have to do;

1. backup everything.
2. use recoverydisk to install bloated toshiba xp install - this will wipe all drive
3. repartition drive to say 30 gig free space
4. copy xp partition to hda2 - leaving 20 gig - and a music and home xp instance
5. resize again to create fat32 partition in hda3
6. install ubuntu
7. install grub to mbr

That sounds like madness - but it is the only way I can see this working with this damned recovery disk.
[/QUOTE]

I hope i'm not too late in this...dinner gets in the way sometimes...

Ah, yes, i've remembered.

The trick is to delete your windows partition with something like gparted.  (Yes, your MBR will have a windows entry that it cant boot to, but that's ok - it will get reinstalled).  Then, put in the toshiba recovery cd, and get it to ghost/install (whatever you want to call it) on the empty partition.

Then run your ubuntu installer, and partition the hard drives the way you want them - i guess you'd have to leave 10 gb free space for the second copy of windows, although i dont see why you'd want two, then you'd copy it with gparted.  Create all the other partions using ubuntu installer.  Continue the installation, installing grub to the mbr...

But then how do you boot to the second version of windows - someone will have to tell you how to edit your grub list...

All in all, it seems way easier to only have one windows partition!

---

### Post by pompeyjohn on 2005-09-03
Ok, I am back up and running now. In the end I scrubbed the drive, copied the toshiba image so there are now two xp partitions. Then, used the ubuntu partitioning tool to create a fat32 drive, and to install automatically in the remaing empty space.



[QUOTE=Hobbsee]....But then how do you boot to the second version of windows - someone will have to tell you how to edit your grub list...[/QUOTE]

and that is exactly where I am upto now!! I have two xp partitions and both entries in Grub are loading the same partition. I'll hunt around now for some grub editing tips. 

[QUOTE=Hobbsee]All in all, it seems way easier to only have one windows partition![/QUOTE]

Ha ha ..... it looks like xp needs two instances to do what Linux can do in one....  ;-) 

If any one has any tips on grub editing - please shout. If I find anything, I'll post it here.

Thanks all,
John

---

### Post by pompeyjohn on 2005-09-03
ok, still stumped by this.

The 2 XP instances are hd0,0 and hd0,1. Yet both load the same damn instance. Is there an XP config file that I have missed here? There must be something. This just is not making sense.

---

### Post by aysiu on 2005-09-03
[QUOTE=pompeyjohn]ok, still stumped by this.

The 2 XP instances are hd0,0 and hd0,1. Yet both load the same damn instance. Is there an XP config file that I have missed here? There must be something. This just is not making sense.[/QUOTE] Do they both say "chainloader +1" under them? How about posting your /boot/grub/menu.lst file up here?

---

### Post by pompeyjohn on 2005-09-03
yup, both have chainloader +1.

menu.lst ....
```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		XP Studio
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		XP Home
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

That all looks cool to me. I think I might have found the problem!! I just had a look at the partitions in gparted - and only one of the XP partitions (hd0,0) has a bootable flag. So, I wonder if when Grub tries to load (hd0,1) but cant find a bootable flag, it loads the other one. 

So now I am going to look into how bootable flags are set - and then try to set one against the second XP instance. (I have no idea how to do that!)

thanks all  :smile:

---

### Post by xequence on 2005-09-03
[QUOTE=pompeyjohn]Hello there,

(bit xp - but kubuntu relevant  :)  )

I hope someone can help. I'll try to explain the setup I have at the moment, the reason for the change, and then post my questions about how to do all this. Ok...

I have a (scratched and battered) toshiba laptop. It is a few years old now (2.4) I think, and I have recently pumped it up with some more ram. All is moving along at a bearable speed. The laptop has a harddrive of 40gig. It is partitioned as follows

hda1 xp home
hda2 kubuntu
hda3 linux swap
hda5 fat 32 shared partition

When I first installed XP and fired up cubase - everything was working fantastically. Now, that other stuff has creeped on their - it has slowed dramatically. I think Norton in particular is dragging things along. Well I do most of my music in linux - but occasionaly like to try out something in xp/cubase. So, I'd like to add another instance of XP to the above setup - one which I can keep scrubbed clean and studio software specific. Can I though - is there a primaries limit? if so would there be any way to combine the two linux file systems so they classed as one primary?

This gets more complicated. As Toshiba sold me a machine that has a damned recovery disk with the OS on, and not a XP installation disc. So I guess I'll have to copy the first partition - and then trim teh fat from it. Very annoying. Particularly as I have seen standard XP home installs amount to about 2.5 gig in space - and the (minimum) toshiba install bloats up to over 4 gig. That is space just being wasted. I can delete fonts and stuff, but where does nearly two gig come from?! So, thats the other issue. Any serious trimming tips and speed up links much appreciated.

This laptop connects through a dsl hub. Is there any way I could take the xp audio partition offline (short of removing the cable) - then I'd not have to both with the slow antivirus.

I am thinking of using the tools on BootIt NG to resize the FAT32 partition - and create in the new space a copy of the XP partition. Am not a linux ninja though, so any advice on how to update Grub also very much appreciated.

thanks in advace,
John[/QUOTE]


About the size of the installer, you can get some "lite" versions of XP on some bittorent sites if you dont mind the fact its illegal. Downloaded they are 200 or so MB and installed they are 600. They get rid of many things like media player but keep others like internet explorer (so you can download firefox :P). Just make sure you have the drivers...

---

### Post by pompeyjohn on 2005-09-03
Someone suggested on hardwareanlysis.com that a torrent xp would be legal as long as I used my purchased serial number. Something to consider.

I have tried to use the partition tool in the ubuntu setup to set the second xp partition boot flag - but no joy. It seems that setting one, clears the other. 

So, now I am wondering if that is because they are next to each other on the drive. Would sliding the second XP partition to the end of the drive solve that.

I'm stumped by this. Surely there is a way to do this!

---

### Post by Hobbsee on 2005-09-03
[QUOTE=pompeyjohn]
So, now I am wondering if that is because they are next to each other on the drive. Would sliding the second XP partition to the end of the drive solve that.

I'm stumped by this. Surely there is a way to do this![/QUOTE]

I seem to recall that windows must be the first partition on the drive, directly after the MBR, or it has a small hissy fit :P

I'm afraid i'm not much help on the rest though!  That bittorrent idea sounds attractive...

---

### Post by xequence on 2005-09-03
> Someone suggested on hardwareanlysis.com that a torrent xp would be legal as long as I used my purchased serial number. Something to consider.

I have tried to use the partition tool in the ubuntu setup to set the second xp partition boot flag - but no joy. It seems that setting one, clears the other. 

So, now I am wondering if that is because they are next to each other on the drive. Would sliding the second XP partition to the end of the drive solve that.

I'm stumped by this. Surely there is a way to do this! 

I dont know how legal it would be, what I do know is many XP torrents are the professional corporate edition, you dont have to use a serial.

> I seem to recall that windows must be the first partition on the drive, directly after the MBR, or it has a small hissy fit :P
 

I heard that too...

> I'm afraid i'm not much help on the rest though! That bittorrent idea sounds attractive... 

Always does :)

---

### Post by bjweeks on 2005-09-03
No, It is not legal, you own a licence to Windows XP OEM. So anyway you do it you are breaking the law by downloading it from bittorrnent in the US.

---

### Post by Hobbsee on 2005-09-03
[QUOTE=bjweeks]No, It is not legal, you own a licence to Windows XP OEM. So anyway you do it you are breaking the law by downloading it from bittorrnent in the US.[/QUOTE]
 to be fair though, windows is a lot smaller without all the security fixes - assuming you arent going to let it connect to any networks or internet...if it's a pure gaming machine, that would make it pretty small...

---

### Post by pompeyjohn on 2005-09-04
Right, I have tried everything I can think of. All partition tools only set one of the xp instance as bootable. I think bootit NG might be able to set both to bootable if I install it into the MBR. So, I might give that a go. But I kinda like Grub, and will miss it. I guess this is a limit of MBR managers who do not go the EMBR route. Oh man this is frustrating.... and there seems to be so little info about this online. 

thanks all for the help and advice,

John

---

