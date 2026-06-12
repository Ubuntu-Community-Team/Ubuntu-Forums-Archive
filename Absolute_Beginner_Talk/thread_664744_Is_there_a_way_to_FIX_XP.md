---
title: "Is there a way to FIX XP?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by neveragain on 2008-01-11
Alright, I really don't want Ubuntu on my computer.
I allowed my brother to mess around on it, having no idea that he was planning on installing it.

And there is a BIG problem.
Now that he loaded on Ubuntu with Live CD, I can't get to the XP welcome screen!
Which also means I can't log into anything on my computer.

I don't want Ubuntu.
Is there a way to rewind this back to how it was before?

Any help, is MUCH appreciated.

---

### Post by Niniel on 2008-01-11
If he didn't wipe the disk when he installed Ubuntu, you should be able to get back in by using the GRUB boot loader. Normally that creates a menu with XP in it as an option when it detects it.

If you don't have that you may have a problem...

---

### Post by dmitriyp13 on 2008-01-11
Can you be more specific as to what is happening with XP?  Is it giving you an error message or just freezing, etc.

---

### Post by Pevichaey5 on 2008-01-11
ask him to create a user for you on linux, if you use it for a bit, you actually discover some of the advantages of linux over windows, such as no viruses, no spyware, the list carries on

you can still run applications like Microsoft Office 2003 with a program called wine (i personally use 'cross over' but its a commercial thing) and you can still play most of the windows games using cedegar (again a commercal product)

---

### Post by neveragain on 2008-01-11
> **thexero said:**
> ask him to create a user for you on linux, if you use it for a bit, you actually discover some of the advantages of linux over windows, such as no viruses, no spyware, the list carries on

you can still run applications like Microsoft Office 2003 with a program called wine (i personally use 'cross over' but its a commercial thing) and you can still play most of the windows games using cedegar (again a commercal product)

Yes, I've heard this, but I prefer to have my XP system back on MY computer.
And he doesn't know how to rewind it back.

---

### Post by neveragain on 2008-01-11
> **Niniel said:**
> If he didn't wipe the disk when he installed Ubuntu, you should be able to get back in by using the GRUB boot loader. Normally that creates a menu with XP in it as an option when it detects it.

If you don't have that you may have a problem...

I don't think he wiped the disk.
From what he told me, all he did was load on the Live CD.

How do you view this GRUB boot loader?
I have NO experience with any Linux program, let alone Ubuntu.

---

### Post by neveragain on 2008-01-11
> **dmitriyp13 said:**
> Can you be more specific as to what is happening with XP?  Is it giving you an error message or just freezing, etc.

I reboot, it loads up (loading screen, etc...). But the screen where there should be the option to log in... welcome screen, etc.... doesn't ever load. It's just BLACK, like it should be loading, but ...?

---

### Post by Dodelijk on 2008-01-11
when you start up the computer do you get a screen asking you to choose between Ubuntu and Windows?

---

### Post by oldos2er on 2008-01-11
Grub should appear as a menu after POST. If configured correctly it should show you an entry to boot Windows.

 You can boot with your Win* install disk and run fixmbr; this would get you back to booting straight to Windows without Grub.

---

### Post by Niniel on 2008-01-11
Oh, ok, so you are starting to boot into Windows and then it freezes? Are you sure it's loading Windows? You don't get any sort of boot menu after you switch on the computer? What have you done yet? Deleted anything?

This is peculiar, installing Ubuntu shouldn't cripple Windows to the point where it starts but never gets to the login screen. Maybe your dear brother messed up more than he's admitting to...

---

### Post by gunashekar on 2008-01-11
I am not being rude but what I learned about linux is : the only way is " Go figure that out" 

You will find out a number of posts and sites about  GRUB if you search on a search engine. Grub is the bootloader that usually  appears when you start your computer. If your windows partion exists, you can also find out by viewing the partions on your hard disk using ubuntu Gparted or any partion manager CD. If you cant find any NTFS or Fat partition on your hard disk then your XP is gone.

Your brother when he installed Ubuntu over XP must have changed the install option to use the entire hard disk. Normally the Live CD offers to resize the windows partition and offers to boot windows as an option  (GRUB does this).

---

### Post by ajgreeny on 2008-01-11
Let's check what is on the hard disk.
Get or borrow the ubuntu liveCD from your brother and boot from that.  It should go into the gnome desktop after booting up.  From there go to the Programs>Accessories>Terminal in the menu at the top and in the terminal that pops up type ```
sudo fdisk -l
```Hit enter and let us know what the output is.  Hopefully it will include something a bit like 
```
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd44cd44c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5229    42001911    7  HPFS/NTFS
/dev/hda2            5230       19747   116615835   83  Linux
/dev/hda3           19748       19929     1461915    5  Extended
/dev/hda5           19748       19929     1461883+  82  Linux swap / Solaris
```though if he did not actually install ubuntu to the hard disk the bottom three lines will not be there, just the line ending HPFS/NTFS, which is your windows installation.

If that is there, shutdown ubuntu and restart with the windows XP CD in the drive and go to the recovery module (I can't remember exactly what it is called, but something like that) and use the fixmbr command, which will restore your windows mbr to how it was before your brother messed it up.
I do agree with thexero's comments, however.  Give ubuntu a good try.  You may find you like it and can get away from dependence upon microsoft.

---

### Post by neveragain on 2008-01-11
> **Dodelijk said:**
> when you start up the computer do you get a screen asking you to choose between Ubuntu and Windows?

Nope, no choices or anything. This has me puzzled.

---

### Post by dstew on 2008-01-11
It is possible that the XP partition was deleted during the Ubuntu installation, and that grub was not installed. In such a case, you would not be able to boot anything. I agree with the advice of ajgreeny. It is the Windows Recovery Console that has the fixmbr command. Of course, that will only work if the Windows partition is still intact. You will be able to tell this by the fdisk output.

---

### Post by Dr Small on 2008-01-11
> **neveragain said:**
> Nope, no choices or anything. This has me puzzled.
Spam the ESC key to get the GRUB menu if it doesn't show.

---

### Post by Niniel on 2008-01-11
Yes, try the live CD to find out if your Windows is still there anymore. Still, strange that it's not booting something, not even Ubuntu.

---

### Post by neveragain on 2008-01-11
> **Niniel said:**
> Oh, ok, so you are starting to boot into Windows and then it freezes? Are you sure it's loading Windows? You don't get any sort of boot menu after you switch on the computer? What have you done yet? Deleted anything?

This is peculiar, installing Ubuntu shouldn't cripple Windows to the point where it starts but never gets to the login screen. Maybe your dear brother messed up more than he's admitting to...

Well, it doesn't actually ever freeze... it just doesn't do anything. 
The light on my computer flickers, like it's doing something, but it never shows anything on the screen.
It's black.

I don't get a boot menu or anything. No options on what to switch into.
Even though Live CD has been loaded on here.

The only thing I can think of, is that on XP I have also been using a program called Fly A Kite OSX...?
That tweaks some of the Windows XP system files.

---

### Post by Niniel on 2008-01-11
It is possible that something got messed up, but I think it's more likely that your computer can't find anything to boot. You really need to run the live CD and then the partition editor to see what you have on your disk.

---

### Post by Kimm on 2008-01-11
This is probably a stupid question. But have you removed the LiveCD?
In case you have, then your brother probably did something he shouldn't have and is now afraid to admit it, which means that your Windows installation is gone.

Your only choice, if you really cant live without the files you stored on your HDD, is to try and recover them (something that takes a very long time, and doesn't always restore everything). I used [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") to restore pictures and videos on my digital camera once, which worked fairly well. It works for all kinds of files.
You should also know what the filenames will be gone... so the recovered files will have names generated by the recovery program (which makes it hard to tell which file is which).

---

### Post by neveragain on 2008-01-11
> **ajgreeny said:**
> Let's check what is on the hard disk.
Get or borrow the ubuntu liveCD from your brother and boot from that.  It should go into the gnome desktop after booting up.  From there go to the Programs>Accessories>Terminal in the menu at the top and in the terminal that pops up type ```
sudo fdisk -l
```Hit enter and let us know what the output is.  Hopefully it will include something a bit like 
```
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd44cd44c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5229    42001911    7  HPFS/NTFS
/dev/hda2            5230       19747   116615835   83  Linux
/dev/hda3           19748       19929     1461915    5  Extended
/dev/hda5           19748       19929     1461883+  82  Linux swap / Solaris
```though if he did not actually install ubuntu to the hard disk the bottom three lines will not be there, just the line ending HPFS/NTFS, which is your windows installation.

If that is there, shutdown ubuntu and restart with the windows XP CD in the drive and go to the recovery module (I can't remember exactly what it is called, but something like that) and use the fixmbr command, which will restore your windows mbr to how it was before your brother messed it up.
I do agree with thexero's comments, however.  Give ubuntu a good try.  You may find you like it and can get away from dependence upon microsoft.

Well, here is what I get!

```

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK    change partition table
            fdisk -l [-b SZZ] [-u] DISK  list partition table(s)
            fdisk -s PARTITION           give partition size(s) in blocks
            fdisk -v                              give fdisk version

Here DISK is something like /dev/hdb or /dev/sda
and PARTIOTION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: for vertain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$
```

I am not really sure what all that means, but hopefully someone does?
Thanks for your help up to this point, I appreciate your time.

---

### Post by amingv on 2008-01-11
> **neveragain said:**
> I reboot, it loads up (loading screen, etc...). But the screen where there should be the option to log in... welcome screen, etc.... doesn't ever load. It's just BLACK, like it should be loading, but ...?

According to this, windows seems to be there. This happened to me some time ago while trying a Mandriva LiveCD. The fix for me was to load in the XP disk and enter into recovery mode (press 'r' after the disk loads). Log in with your username && password and type this into the console:

```
chkdsk /f c:
```

Assuming C:\ is your main drive.

Also, I have never heard of such a program as "Fly a Kite", but you need to be very careful when playing with the system, especially in windows (unless you're somewhat like me, and have nothing to lose).

---

### Post by eolson on 2008-01-11
that should be a lower case L after fdisk instead of a 1.

---

### Post by Kimm on 2008-01-11
you wrote the wrong command

it is not: -1 it is -l (Low cap. L)

---

### Post by neveragain on 2008-01-11
Whoops!
Alright.

```

dusj /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 selectors/track, 12161 cylinders
Units = cylinders or 16065 * 512 8225280 bytes

Device         Boot   Start        End           Blocks     Id          System
/dev/hdal1       *      606    12160   92815537+     7    HPFS/NTFS
/dev/hda2                    1        605       4859631      b   W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device         Boot     Start    End       Blocks          Id     System
/dev/hdb1        *        1       19547   156288321   7   HPFS/NTFS
```

Not sure what to do after that.

---

### Post by Niniel on 2008-01-11
Looks like your NTFS (Windows) partitions are still there... good. The next thing I would try is to restore the master boot record of my first drive. You can use the Windows installation CD for that; I think somebody posted earlier how do do that.

---

### Post by neveragain on 2008-01-11
> **Niniel said:**
> Looks like your NTFS (Windows) partitions are still there... good. The next thing I would try is to restore the master boot record of my first drive. You can use the Windows installation CD for that; I think somebody posted earlier how do do that.

This is via Windows set up, correct?

---

### Post by jerrykenny on 2008-01-11
If you dont have the xp install cd, i think you can use the smart-boot facilities on the system rescue cd

[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

have a read at their documentation b4 you download it . . . . . its probably around 700mb

There is definitely a floppy version of a smart boot manager, i definitely recall using one 2 years back, you can maybe google to try find it.

---

### Post by Niniel on 2008-01-11
Not exactly via Setup, you want the Recovery Console, which is essentially a command line interface. There you'll have to type the command fixmbr, hit Enter, and that's it. Restart, and hopefully it'll boot into Windows again.

[This explains this a bit]("http://pcsupport.about.com/od/termsf/p/fixmbr.htm").

---

### Post by neveragain on 2008-01-11
> **Niniel said:**
> Not exactly via Setup, you want the Recovery Console, which is essentially a command line interface. There you'll have to type the command fixmbr, hit Enter, and that's it. Restart, and hopefully it'll boot into Windows again.

[This explains this a bit]("http://pcsupport.about.com/od/termsf/p/fixmbr.htm").

Oh, I could kiss you!
Thanks so much everyone, it's working again!!!!!!!

---

### Post by Niniel on 2008-01-11
Excellent, I'm glad you got your computer back.

Now be nice and give Ubuntu a try when you have time, you may actually like it. :)

---

### Post by neveragain on 2008-01-11
> **Niniel said:**
> Excellent, I'm glad you got your computer back.

Now be nice and give Ubuntu a try when you have time, you may actually like it. :)

... the important thing: Does Photoshop, Dreamweaver, Flash and InDesign CS3 work on Ubuntu?

---

### Post by Niniel on 2008-01-11
Not sure, to be honest.

I did get Photosphop 6.0 to work under Wine without any problems at all - it even feels faster than under XP - but I guess you have newer versions which may not work. A good idea would be to search the web for something like "Photoshop CS3 Wine" etc.
As for the rest of your software, there may be similar Linux programs available, but then again, maybe with your requirements it's best you just stick to Windows since your software works and you know how to use it.

But, maybe one day you'll be ready to check out Linux.

Good luck.

---

### Post by tc10b on 2008-01-11
As was mentioned earlier you can get programs such as Crossover or Wine to run these programs for you in Linux. Otherwise there are a host of similar/clone programs you can download.

---

### Post by vivekchaurasia on 2008-01-14
open Ubuntu and take backup of your whole data and then boot from windows xp cd and reinstall windows xp....the easiest solution :)

---

### Post by Paqman on 2008-01-14
> **neveragain said:**
> ... the important thing: Does Photoshop, Dreamweaver, Flash and InDesign CS3 work on Ubuntu?

Ubuntu comes with GIMP, which I personally prefer to Photoshop, but I know a lot of people would disagree with me on that.

Dreamweaver is one thing I still boot into Windows to use. There are some decent Linux html editors, but they're nowhere near as good as Dreamweaver. Mostly I find they don't handle PHP very well.

No idea about Flash or InDesign. Tbh, for web design, Linux isn't such a good platform. But it sure is pretty!

---

### Post by Niniel on 2008-01-14
There is,  by the way, [a GIMP modification that turns Gimp into a true PS clone]("http://www.gimpshop.com/"). I haven't used it myself yet though so I cannot say how well this works.

---

### Post by quandary on 2008-01-14
> **Paqman said:**
> 
Ubuntu comes with GIMP, which I personally prefer to Photoshop, but I know a lot of people would disagree with me on that.

Dreamweaver is one thing I still boot into Windows to use. There are some decent Linux html editors, but they're nowhere near as good as Dreamweaver. Mostly I find they don't handle PHP very well.

No idea about Flash or InDesign. Tbh, for web design, Linux isn't such a good platform. But it sure is pretty!


First, I wouldn't say Ubuntu isn't a good platform just because Dreamweaver and Flash have no Linux port. It's Dreamweaver and Flash that is bad in this case ! ! !

Second: What do you need Dreamweaver for? HTML you normally create via a text editor. No need for Dreamweaver then, and you get what you want then, unlike using Dreamweaver...

As about Flash and InDesign, you anyway shouldn't use them, because if you create a website entirely in Flash, nothing will be found via Google or other search engines, because they search HTML, and not Flash... not to mention how bad Flash is for visual impaired/blind computer users...

As for Linux Dreamweaver equivalents, maybe you should browse the repository first, because if you do, you will find out that there is at least one Linux HTML-editor that is better than Dreamweaver and Frontpage. Well, the later isn't that difficult...

So, now if you really don't want to learn HTML and use Bluefish Editor (then you shouldn't create Webpages, too), then try a wysiwyg-Editor:
[SIZE="7"]**sudo apt-get install kompozer**[/SIZE]

---

