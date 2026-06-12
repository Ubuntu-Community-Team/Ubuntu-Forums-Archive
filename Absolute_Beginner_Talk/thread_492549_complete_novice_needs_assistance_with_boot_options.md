---
title: "complete novice needs assistance with boot options"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by grate on 2007-07-04
Hello,

I just tried the Ubuntu live CD, and was super impressed.
I decided to install this operating system to my computer, along side with windows.

Upon completed installation, I was not presented with an option to boot to either Ubuntu or Windows, but simply Ubuntu loaded.

From my research, it looks like I need to configure Grub to allow for the option to load either windows or Ubuntu?

I presently have Ubuntu on a regular hard drive partition, while my windows installation is on a SATA drive.

I'd appreciate any advice or help anyone can provide with this problem.

Thanks so much in advance-

Grate

---

### Post by freebird54 on 2007-07-04
Under normal circumstances, the installer would have recognized the Windows installation and provided the necessary information in your Grub setup.  So - something was not 'right' at that time.  Did you have the Windows drive unplugges during install?

If not, then open up a Applications->Accessories->Terminal and type in:

```
sudo fdisk -l
```

and paste the output into your reply.  we'll need that info to being with, if the first thing I mentioned is not the case...

---

### Post by fumduck on 2007-07-04
to reinstall grub..

there is this  link
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by grate on 2007-07-04
First of all, thanks guys!

Heres the results from the sudo command:

```

Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         486     3903763+  83  Linux
/dev/sda2             638        9732    73055587+   7  HPFS/NTFS
/dev/sda3             487         637     1212907+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       14946   120045712+   f  W95 Ext'd (LBA)
/dev/sdb5               2       14946   120045681    7  HPFS/NTFS

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1275    10241406    7  HPFS/NTFS
/dev/sdc2            1276        4499    25896780    f  W95 Ext'd (LBA)
/dev/sdc5            1276        4499    25896748+   7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdd5               2       19457   156280288+   7  HPFS/NTFS


```

This is the windows partition that i would like to optionally boot into:

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1275    10241406    7  HPFS/NTFS





Thanks so much-

Grate

---

### Post by freebird54 on 2007-07-04
OK - what SHOULD work is to make some small edits (!) in the configuration file for Grub. So, in order....
Create backup of file

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst/backup070407
```

now open it in an editor

```
gksudo gedit /boot/grub/menu.lst
```

and find this line at the bottom

```

### END DEBIAN AUTOMAGIC KERNELS LIST
```

and replace it with this whole block
```


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title           Microsoft Windows XP Professional

root    (hd2,0)
savedefault
makeactive
chainloader     +1
```

Save,exit, and reboot to see if it worked.  If not - you'll have to copy the backup into place again..

```
sudo cp  /boot/grub/menu.lst/backup070407 /boot/grub/menu.lst
```

---

### Post by grate on 2007-07-04
Thanks Freebird, I really appreciate your help.

When I try to Save changes to the menu.lst file I get this error:

```

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.


```

It won't even let me make any directories or anything, its acting like I do not have any permissions,  do you know what is preventing this :(?

Thanks again-

Grate

---

### Post by coolen on 2007-07-04
> **grate said:**
> Thanks Freebird, I really appreciate your help.

When I try to Save changes to the menu.lst file I get this error:

```

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.


```

It won't even let me make any directories or anything, its acting like I do not have any permissions,  do you know what is preventing this :(?

Thanks again-

Grate

Did you type gksudo at the beginning of the line?
Try this:

sudo nano /boot/grub/menu.lst

See if that works.

---

### Post by freebird54 on 2007-07-04
Well - using ***gksudo*** in front of the gedit (editor) command should have prevented that problem!  Did you invoke those commands by pasting them directly into the terminal?  

*BTW - <shift><ctrl>V pastes in a terminal, <shift><ctrl>X cuts  <shift><ctrl>C copies....

---

### Post by atria on 2007-07-04
Did you follow the instructions exactly? Or to be more precise, make sure that menu.lst is opened with "gksudo" (if you're using gedit) or "sudo" if you're using a console editor like nano.

---

### Post by grate on 2007-07-04
Thanks so much for the fast replies.

When I paste your code in terminal:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst/backup070407

```

I get the following result:

```

cp: accessing `/boot/grub/menu.lst/backup070407': Not a directory

```

What is even more bizarre is when I right click this drive  under Places/Computer/filesystem(drivename) It says that root is the owner and that the whole drive is read only, and that I do not have permission to change any properties :((.

Thanks-

Grate

---

### Post by freebird54 on 2007-07-04
**ARRGHHH!  Felled by the typo bug!!**  :oops:

Let's try that again....
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup070407
```

and later on.. (to restore if necessary)
```

sudo cp  /boot/grub/menu.lst.backup070407 /boot/grub/menu.lst
```

Yes, I know the keys are right next to each other - but I used to think I could READ!

---

### Post by coolen on 2007-07-04
Ignore me :)

---

### Post by grate on 2007-07-04
Thanks Freebird, I was able to edit the file now.

Windows Xp shows up in the boot list now, however when I select it to load from I just get the following message:

Starting up...
--

And nothing happens. Have we possibly specified the wrong location to boot XP from?

Thanks so much-

Grate

---

### Post by coolen on 2007-07-04
> **grate said:**
> Have we possibly specified the wrong location to boot XP from?

Thanks so much-

Grate

It was the first partition of that drive, yes?

---

### Post by grate on 2007-07-04
Thanks Coolean, as stated before this is the report:

[code]


Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sdc1               1        1275    10241406    7  HPFS/NTFS[/COLOR]
/dev/sdc2            1276        4499    25896780    f  W95 Ext'd (LBA)
/dev/sdc5            1276        4499    25896748+   7  HPFS/NTFS


The 10GB portion highlighted in red is the windows partition I would like to be able to optionally load. :(

Thanks-
Grate

---

### Post by coolen on 2007-07-04
> **grate said:**
> Thanks Coolean, as stated before this is the report:

[code]


Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sdc1               1        1275    10241406    7  HPFS/NTFS[/COLOR]
/dev/sdc2            1276        4499    25896780    f  W95 Ext'd (LBA)
/dev/sdc5            1276        4499    25896748+   7  HPFS/NTFS


The 10GB portion highlighted in red is the windows partition I would like to be able to optionally load. :(

Thanks-
Grate

Unless something's gone wrong with your Windows partition/MBR, I don't know what's wrong. The instructions above should work.
Try using the option from the Ubuntu CD to boot from the first hard drive. At least then we can narrow down the problem.

---

### Post by freebird54 on 2007-07-04
Well - we specified that partition - but if it won't come up, perhaps it is another one!  You might want to try changing the line:
```

root    (hd2,0)
```

into 

```
root    (hd0,1)
```

just on case that's the 'real' one... :)

In fact, the system is that you need a table of equivalents:
```

sda1 = hd0,0
sdb3 = hd1,2
sdd2 = hd3,1
```

if you see how that goes.  ONE of those NTFS entries must be the one!

---

### Post by bradmayne on 2007-07-04
hey I had the same problem with my toshiba.  I had to turn the dvd over and use the older version that was more stable.  Then my vista came up on grub with no other problems

---

### Post by grate on 2007-07-04
Thanks all for the suggestions/help.

Freebird, root    (hd0,1) generates an ntldr error and requests alt+ctrl+del to restart.

I'll try the other provided suggestions.

Thanks again.

---

### Post by grate on 2007-07-04
0,0 abd 3,1 generate the following error:

invalid or unsupported executable format

1,2 reports:

no such partition


ugh :(, any other suggestions?

---

### Post by grate on 2007-07-04
> **coolen said:**
> Unless something's gone wrong with your Windows partition/MBR, I don't know what's wrong. The instructions above should work.
Try using the option from the Ubuntu CD to boot from the first hard drive. At least then we can narrow down the problem.

Booting from the 'first hard drive' loads my current installation of Ubuntu.

Dunno if this is useful, thanks though.

---

### Post by jimmygoon on 2007-07-05
Just to point out from the fdisk output:
```
Partition table entries are not in disk order
```I imagine that might be important? I'm not sure though. I get confused with all the sdX stuff.

Actually I might have thought it to be 2,0 since its the third(-1) drive and the first(-1) partition... Maybe try "root (hd2,0)"... maybe?

but the fact that "root    (hd0,1) generates an ntldr error" is something since a ntldr error means you're in the XP partition... Can you give a more precise ntldr error. thanks!

---

### Post by freebird54 on 2007-07-05
Those particular values were examples of how the numbering system works.  Basically, fdisk starts with a and 1, where grub uses 0 and 0.

So - all the NTFS partitions you have listed on what you sent me were:

```
sda2  (hd0,1)
sdb5 (hd1,4)
sdc1 (hd2,0)
sdc5 (hd2,4)
sdd5 (hd3,4)
```

I was thinking you should try those values - though I still would have thought hd0,1 was the most likely offhand.  Why are there so many NTFS partitions/drives on your system? Are you running Win3.1, 95, 98, XP and Vista all together? :)

Another thing we might try if you continue to have difficulty is to mount the drives and actually LOOK at their contents... that should tell us more about what's going on if necessary....

---

### Post by jimmygoon on 2007-07-05
[COLOR=Silver]Um, sdc1 is what he wants (right???) which would be root(hd2,0) which i don't believe he's tried yet

[COLOR=DarkSlateGray]Oops, just kidding. But, I still say take a look at that NTLDR error more... that is indicative of progress...[/COLOR]
[/COLOR]

---

### Post by grate on 2007-07-05
Argh--------------


In a last ditch effort I tried to let windows repair the MBR.

I've made a huge mistake.

All my boot information is now gone.

I've had to reinstall windows, and sure enough windows doesn't play nice with the Ubuntu boot information so it has flagged it as inactive.

So now I am stuck with a bare bones installation of windows, I have Ubuntu still installed on the other drive, but windows ignores it.

Is there any hope for resolving this from the Windows side now?

It is absolutely frustrating that both of these operating systems are being so oblivious to each other.

---

### Post by coolen on 2007-07-05
> **grate said:**
> Argh--------------


In a last ditch effort I tried to let windows repair the MBR.

I've made a huge mistake.

All my boot information is now gone.

I've had to reinstall windows, and sure enough windows doesn't play nice with the Ubuntu boot information so it has flagged it as inactive.

So now I am stuck with a bare bones installation of windows, I have Ubuntu still installed on the other drive, but windows ignores it.

Is there any hope for resolving this from the Windows side now?

It is absolutely frustrating that both of these operating systems are being so oblivious to each other.

You could grab the Super GRUB disc...it's come in handy for me in the past. From there, you have tools to repair a GRUB installation (or Windows MBR, if need be).
The good news is, your Windows partition seems fine. I had similar problems with an older computer not long ago, and it turned out the entire hard drive was dead.
The GRUB disc might also get you back into Ubuntu (you may need to use the shell for this. It should be your previous GRUB entry for booting Ubuntu in succession).
Don't worry, you're not stuck with Windows. Ubuntu's still there...you just need to find a way back :)

---

### Post by grate on 2007-07-05
> **coolen said:**
> You could grab the Super GRUB disc...it's come in handy for me in the past. From there, you have tools to repair a GRUB installation (or Windows MBR, if need be).
The good news is, your Windows partition seems fine. I had similar problems with an older computer not long ago, and it turned out the entire hard drive was dead.
The GRUB disc might also get you back into Ubuntu (you may need to use the shell for this. It should be your previous GRUB entry for booting Ubuntu in succession).
Don't worry, you're not stuck with Windows. Ubuntu's still there...you just need to find a way back :)

I would like to get out of Windows, do you have any more details/instructions for the Super/Grub disk?

Or does anyone know how to tell the windows boot loader to add the ubuntu installation as an option ? :(

---

### Post by freebird54 on 2007-07-05
Been done before :)

Anyway - the fix is doable from the Live CD.  Windows is pretty much oblivious to the existence of anything else - except, in some cases, other versions of itself.  If you follow [this link](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub), it will show you how to get Grub going once again, - hopefully with Win recognized this time!

---

### Post by coolen on 2007-07-05
> **grate said:**
> I would like to get out of Windows, do you have any more details/instructions for the Super/Grub disk?

Or does anyone know how to tell the windows boot loader to add the ubuntu installation as an option ? :(

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Link to their website. Not sure if that'll get you the same disc I got (it seemed to have an ad for a Spanish tourist resort...), but you should be greeted by some text explaining the basic options. Select one, and you'll be taken to a new menu, and shown more information on the options it contains before you get there.
You'll probably want to fix GNU/Linux Grub, or something like that. You could always choose to simply boot GNU/Linux (if you've wiped your previous GRUB install by accident, this may not work...but I think it should).
You can, as mentioned, repair from the disc, or get back to Ubuntu for some help along the way. As you've seen, accidentally wiping your boot loader is a startling experience...but not the end.

---

### Post by grate on 2007-07-05
Progress, I think?

Thanks Coolen and Freebird for your suggestions.

Heres where I stand now.

Using Super Grub I can boot the ISO and browse to my Linux partition and launch it without any problems.

However, when I try to launch Windows from SGRUB, even trying the boot from secondary hard drive partition option, I just get errors.

So where I stand now is, I have a method of booting into Ubuntu with the Grub CD, however its rather tedious as I have to [enter] through about 5 menus and prompts to launch the partition.

Is there an easy way to get SGRUB to detect both partions and run them simultaneously without headaches? I'd rather throw this computer out the second story window then reinstall windows again due to some erroneous mix up.

---

### Post by coolen on 2007-07-05
So, Windows works without the disc, and Ubuntu works with it?
That means each is bootable. Have you tried running the Grub install option from the disc, or perhaps from Ubuntu itself?
If you get truly desperate, you could always make yourself a custom Grub disc/floppy/USB. Pop it in and restart, you wind up in Ubuntu, take it out and restart again, you've got Windows.

---

### Post by grate on 2007-07-05
> **coolen said:**
> So, Windows works without the disc, and Ubuntu works with it?


Do you have detailed instructions for doing this either with Super GRUB or through Ubuntu?

Ubuntu did this on its own before, and ended up not including the Windows boot information which lead to me having to reinstall that operating system, and losing a number of unrecoverable files. I guess I shouldn't be too worried about it now, as what is gone is gone. :(

---

### Post by coolen on 2007-07-05
I can test it on my laptop...but I've no Windows install on there. Hopefully the failure to recognise Windows was a problem with the installer, not Grub itself.
Okay, on the main menu, you should see a few options. Under GNU/Linux, there's an option to Fix Boot of GNU/Linux (GRUB). That should be what you need.
Actually, this option seems to restore a previous Grub install...that should at least get you back to the state you were in at the beginning of this post. I think reinstalling Grub from Ubuntu may be the best way to go. I believe the ability to detect other OSs is provided by Debian scripts.

---

### Post by grate on 2007-07-05
Cased closed guys.

Thanks all for your help.

Using super grub disk I was able to find the real windows boot partition.
From there, I repaired Grub using SGD, and then added the real partition 0,2 via Freebirds manual instuctions.

Thanks a bunch for all of your help.   :KS:KS:KS::popcorn::KS:KS:KS

---

### Post by freebird54 on 2007-07-05
OK - would be good to mark the thread "RESOLVED'  though - you can set that by editing your original post, and choosing ADVANCED -> mark resolved..

Glad we got you going!

---

