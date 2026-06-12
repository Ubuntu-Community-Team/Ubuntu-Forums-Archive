---
title: "Easiest triple boot ever.  Leopard, Gutsy, Vista"
date: 2007-10-27
forum: Apple Intel Users
---

### Post by violajack on 2007-10-27
I just spent the day trying to set up a triple boot via various guides out there and found that there is an easier way, especially for those who don't want to partition from the command line.  

This is on a C2D Macbook.

I started from a clean install of Leopard on the whole disk.  Then I installed rEFIt, since I wanted to make sure that would work.  It didn't work from the installer, and I did have to venture into the terminal to fix it with the manual install commands:

cd /efi/refit
./enable.sh

Then I used Bootcamp Assistant to set up a 30G partition for Vista.  This is the one step that most guides tell you not to do, they all say you have to partition from the terminal using diskutil resizeVolume.  I just kept toasting my partition maps with that thing, and when I did get it right, the windows installer would complain and refuse to proceed.  Going straight from bootcamp was the only way I could get the windows install to cooperate.  

I completely installed Vista leaving me with OSX and Vista via plain old normal bootcamp.  Bootcamp changes your startup volume, so I had to hold Alt to get the option to boot into OSX again.  I reran the rEFIt enable.sh, but I'm not sure if that was really necessary.  I had to then change the startup volume back to the mac partition, which allowed it to boot into rEFIt again.

From OSX, I used the GUI Disk Utility from the Utilities folder.  If you click on the main disk (not on of the two partitions) you will have a tab option for Partition.  From the graphic of the two partitions, click the main OSX partition, then click the little plus sign and it will split the OSX partition into two.  You can then drag the space between to set the size of the new partition and name it whatever you want.  Disk Utility will only format it as HFS+, but the Ubuntu live CD will gladly reformat it to ext3 for you.  The partitions did not stay proportional size-wise in the GUI, but if you click on each, it should show the correct size in GB.  Yes, it resized my OSX partition, while booted, nondestructively, without breaking my ability to boot Windows.  

From there, I inserted the Ubuntu 7.10 live CD and restarted.  rEFIt came up and I chose the option to boot to the Linux CD.  I reformatted the new HFS partition as ext3 using the Partitioning tool, but I think it would have worked from in the installer as well.  I ran the installer as normal, choosing to partition manually.  It wanted to format the ext3 partition again to use it as root, so I let it.  It complained about not getting a swap partition, but that's normal.  The only thing to be careful of at this point is that in the last window of the installer, you have to click the "Advanced" button and tell it to install grub to the same partition as Linux, not hd0, or it will overwrite the Master Boot Record.  In my case (EFI system on 1, OSX on 2, Linux on 3, and Vista on 4) that meant installing to /dev/sda3.  

When that finished, I rebooted and hoped for the best.  rEFIt came up with three entries!  I have been able to boot all three OSes now just fine, with no partitioning from command line!

I hope this can help others out there looking for an easy way to cram all three OSes on a mac.

---

### Post by cyberdork33 on 2007-10-28
the disk utility in leopard has a cool little "add partition" function. This makes things much easier.

---

### Post by Subversive_One on 2007-10-28
Thanks for this terrific walk thru.  Your set up is exactly what I would like to do.  I'm basically brand new to Ubuntu, but I like the idea of having it on my machine.  As a total Linux Newb, I can follow almost everything you're saying... except this part:

> **violajack said:**
> ...I reformatted the new HFS partition as ext3 using the Partitioning tool, but I think it would have worked from in the installer as well.

Would you mind giving me a little more detail on how I use the Partitioning tool?


Also... Did you end up installing LILO instead of GRUB?  To be honest, I don't know the difference between either.  It's just that all of the guides seem to recommend LILO, for some reason.

Thanks again!

Sub

---

### Post by cyberdork33 on 2007-10-28
> **Subversive_One said:**
> Thanks for this terrific walk thru.  Your set up is exactly what I would like to do.  I'm basically brand new to Ubuntu, but I like the idea of having it on my machine.  As a total Linux Newb, I can follow almost everything you're saying... except this part:



Would you mind giving me a little more detail on how I use the Partitioning tool?


Also... Did you end up installing LILO instead of GRUB?  To be honest, I don't know the difference between either.  It's just that all of the guides seem to recommend LILO, for some reason.

Thanks again!

Sub

You change the partion type in the ubuntu installer...

you do not need to worry about lilo. Grub is the default and works fine.

---

### Post by Subversive_One on 2007-10-28
Got it working!

Thanks for the walk thru!

---

### Post by pxwpxw on 2007-10-28
> **violajack said:**
> 
<snip>
From OSX, I used the GUI Disk Utility from the Utilities folder.  If you click on the main disk (not on of the two partitions) you will have a tab option for Partition.  From the graphic of the two partitions, click the main OSX partition, then click the little plus sign and it will split the OSX partition into two.  You can then drag the space between to set the size of the new partition and name it whatever you want.  Disk Utility will only format it as HFS+, but the Ubuntu live CD will gladly reformat it to ext3 for you.  The partitions did not stay proportional size-wise in the GUI, but if you click on each, it should show the correct size in GB.  Yes, it resized my OSX partition, while booted, nondestructively, without breaking my ability to boot Windows.  
<snip>
.

That is a major improvement in Leopard GUI Disk Utility. Previously in Tiger, disk utility had to reformat the whole drive in order to change one partition.

Good howto.:)

---

### Post by violajack on 2007-10-29
Yeah, I was blown away when Disk Utility did the second partitioning for me.  I had it pounded into me back when my dad was showing me how to install 5 OSes on one of the home computers (95, NT, Solaris, and 2 different versions of Redhat) that you cannot resize a mounted partition.  Then again, I don't even remember if nondestructive shrinking was possible.  We managed to thoroughly zorch a hard drive with Partition Magic.  I guess I've always sucked at partitioning properly.  So it was so awesome to see Disk Utility do it for me.  I must have screwed up from the command line at least three times (requiring an erase disk and reinstall OSX each time) before I just tried that.  I'm so glad to hear that people are finding my post helpful.  

Some other things I've learned to add to the explanations:
Most of the guides say to use LILO.  Most of the guides were also written based on 6.10.  From what I've read, Grub had a bug that prevented it from working with EFI, so you had to use LILO instead.  Grub has since been fixed and the 7.10 version works just fine with rEFIt.

The Partitioning tool = gparted.  It can be run from the live CD by going into System > Administration > Partitioning (or something like that).  

Another cool thing about the macbook - Desktop Effects works at the highest setting out of the box.  I added Advanced Desktop Effects Settings and Emerald for a really nice looking setup.  I miss my old nVidia based Sony less and less all the time.

---

### Post by speedemonV12 on 2007-10-29
wow. That is a great tutorial. I am about to take the plunge. But one thing that I was wondering.
After doing all this, lets say I decide to stop using Ubuntu, what then happens to that partition? is it just stuck as a separate partition until i do a full disk partition? Or can i somehow get that partition to merge back with the os x partition?

---

### Post by cyberdork33 on 2007-10-29
> **violajack said:**
> Another cool thing about the macbook - Desktop Effects works at the highest setting out of the box.  I added Advanced Desktop Effects Settings and Emerald for a really nice looking setup.  I miss my old nVidia based Sony less and less all the time.

Intel graphics = works.

---

### Post by violajack on 2007-10-29
> **speedemonV12 said:**
> wow. That is a great tutorial. I am about to take the plunge. But one thing that I was wondering.
After doing all this, lets say I decide to stop using Ubuntu, what then happens to that partition? is it just stuck as a separate partition until i do a full disk partition? Or can i somehow get that partition to merge back with the os x partition?

That's a really good question.  That's the problem I kept running into when I messed up my partitioning.  I tried to use Disk Utility to delete the partitions I didn't want and then expand the main OSX partition to whole drive, but it never worked.  It would say that the OSX partition was the full size of the drive in Disk Utility, gparted, and even in Disk Utility from the OSX install CD.  But the finder told me I only had free space that lined up with the smaller partition size, and the bootcamp partitioner said the same.  That's why I kept going back to erase disk and reinstall when it didn't work.  There's more discussion here: [http://ubuntuforums.org/showthread.php?t=590525](http://ubuntuforums.org/showthread.php?t=590525) about resizing mac partitions.  There's an interesting way to do it with the bootcamp assistant, but I think that would require killing all the partitions that aren't the main OSX partition. 

I guess I never thought about removing Ubuntu.  I was with just OSX and Vista for a while, while I got used to using OSX, but with a new Ubuntu out, I just had to put it on again.  I am so happy to be using linux again.  The only thing that might change for me would be giving more space to linux.

---

### Post by cyberdork33 on 2007-10-29
> **violajack said:**
> That's a really good question.  That's the problem I kept running into when I messed up my partitioning.  I tried to use Disk Utility to delete the partitions I didn't want and then expand the main OSX partition to whole drive, but it never worked.  It would say that the OSX partition was the full size of the drive in Disk Utility, gparted, and even in Disk Utility from the OSX install CD.  But the finder told me I only had free space that lined up with the smaller partition size, and the bootcamp partitioner said the same.  That's why I kept going back to erase disk and reinstall when it didn't work.  There's more discussion here: [http://ubuntuforums.org/showthread.php?t=590525](http://ubuntuforums.org/showthread.php?t=590525) about resizing mac partitions.  There's an interesting way to do it with the bootcamp assistant, but I think that would require killing all the partitions that aren't the main OSX partition. 

I guess I never thought about removing Ubuntu.  I was with just OSX and Vista for a while, while I got used to using OSX, but with a new Ubuntu out, I just had to put it on again.  I am so happy to be using linux again.  The only thing that might change for me would be giving more space to linux.

The bootcamp thing was really the only way to do it previously as there are not any utilities to grow hfs+. However, in Disk Utility in Leopard, there is a little '-' beside the '+', I would try that first.

---

### Post by violajack on 2007-10-29
But that's what I did and it kept not working.  If the windows installer complained about its partition, I would go back into OSX, use the - button to remove the extra partitions, then drag the OSX partition to refill the drive, then clicked Apply.  It looked like it was doing things, but it didn't really expand the main HFS+ partition.  It would look like that partition filled the drive from Disk Utilities on the drive, Disk Utilities on the OSX disk, and gparted on the live CD.  However, finder showed free space that matched the smaller OSX partition, as did bootcamp.  Apparently, Disk Utilities tempts with promises of growing your OSX partition, but fails to deliver.  That's part of why I was so amazed that it could correctly shrink the booted partition for me without screwing anything up.  

Also, when I booted from the OSX install CD and tried to repair the volume, it would either fail completely, or mention that the header needed minor repair, claim to repair it, but still result in a screwed up drive.  

That little + button might do wonders for adding partitions, but I would not trust Disk Utilities to properly reclaim space.

---

### Post by cyberdork33 on 2007-10-30
> **violajack said:**
> But that's what I did and it kept not working.  If the windows installer complained about its partition, I would go back into OSX, use the - button to remove the extra partitions, then drag the OSX partition to refill the drive, then clicked Apply.  It looked like it was doing things, but it didn't really expand the main HFS+ partition.  It would look like that partition filled the drive from Disk Utilities on the drive, Disk Utilities on the OSX disk, and gparted on the live CD.  However, finder showed free space that matched the smaller OSX partition, as did bootcamp.  Apparently, Disk Utilities tempts with promises of growing your OSX partition, but fails to deliver.  That's part of why I was so amazed that it could correctly shrink the booted partition for me without screwing anything up.  

Also, when I booted from the OSX install CD and tried to repair the volume, it would either fail completely, or mention that the header needed minor repair, claim to repair it, but still result in a screwed up drive.  

That little + button might do wonders for adding partitions, but I would not trust Disk Utilities to properly reclaim space.
Well that is too bad. The good news I guess is that you could create a separate hfs+ partition to make the space useable at least.

---

### Post by stevie_velvet on 2007-10-30
well done
Going for a QUAD-Boot on my laptop of Vista, Solaris, Ubunutu..and....
Almost got their on My dev box

You neve know!

---

### Post by cyberdork33 on 2007-10-30
> **stevie_velvet said:**
> well done
Going for a QUAD-Boot on my laptop of Vista, Solaris, Ubunutu..and....
Almost got their on My dev box

You neve know!

This should be easily attainable. Hint: OSX doesn't have to be one of the first 4 partitions since it boots natively from EFI.

Also, check out this thread. Someone seems to have a very thorough understanding of partitioning and booting on a Mac.
[http://ubuntuforums.org/showthread.php?t=432281](http://ubuntuforums.org/showthread.php?t=432281)

---

### Post by mcvaughan on 2007-11-02
Any thoughts on problems installing rEFIt and re-partitioning AFTER I've already setup Windows via Boot Camp?  I want to re-partition my Mac OS for Ubuntu, but will I destroy the ability to boot to Leopard if I already have this setup?

---

### Post by jtwadsworth on 2007-11-05
Did Vista work ok for you ?  I have a brand new 24" iMac and Leopard...installed Vista via Bootcamp with no problems and now I'm repartitioning for Gutsy...but my Vista install, although it works, lacks accurate detection of video card and sound...sound doesnt' work at all and I'm stuck with regular VGA mode.  I had to install manually the newest ATI drivers for the iMac's vidcard.

I still get scores of '1' on Vista's experience-o-meter thingie.  It also doesnt' recognize the Bluetooth or Isight camera, but that's not a big deal.

I would like to make sure I get sound and video right tho.  Could it be because Vista is 32bit copy and the iMac is 64 bit?

jtw

---

### Post by cyberdork33 on 2007-11-05
> **jtwadsworth said:**
> Could it be because Vista is 32bit copy and the iMac is 64 bit?no

---

### Post by violajack on 2007-11-06
> **mcvaughan said:**
> Any thoughts on problems installing rEFIt and re-partitioning AFTER I've already setup Windows via Boot Camp?  I want to re-partition my Mac OS for Ubuntu, but will I destroy the ability to boot to Leopard if I already have this setup?

Shouldn't cause any problems.  My first step was to install Vista with the regular boot camp method.  After I had that set up, I used diskutil to resize the OSX partition and then installed Ubuntu to the newly created partition.  rEFIt just works.  It scans everything looking for anything that can be booted, so as soon as you install it, it should give you the option to boot from anything that is already bootable on your machine.  I tested rEFIt with my Tiger/Vista dual boot before wiping everything for Leopard.  It saw both partitions and booted each one just fine.  I also installed rEFIt right after Leopard and it worked giving me just the one option to boot Leopard.  There was no configuration required with rEFIt along the way, each time I installed something new, or had a bootable CD in the drive, it would just show me all of my options.  It's a pretty amazing little utility. 

The only thing that confuses it is when I have my external hard drive plugged in.  I just got the startup chime over and over again.

---

### Post by jtwadsworth on 2007-11-06
> **cyberdork33 said:**
> no

Any ideas as to why I don't have sound/correct video then in Vista?

jtw

---

### Post by cyberdork33 on 2007-11-06
> **jtwadsworth said:**
> Any ideas as to why I don't have sound/correct video then in Vista?

jtw

Not really... It's windows, something is corrupted. Did you resize the Vista partition? That may have messed something up. Whatever it is, it sounds pretty bad.

---

### Post by mcvaughan on 2007-11-06
OK, I got it all installed, but I have a problem with Windows.  When I try to go into Windows I get a BSOD.  It won't even let me into safe mode.

Any thoughts?

---

### Post by jtwadsworth on 2007-11-06
> **cyberdork33 said:**
> Not really... It's windows, something is corrupted. Did you resize the Vista partition? That may have messed something up. Whatever it is, it sounds pretty bad.

It seems to be with driver recognition since neither the vidcard nor the soundcard are recognized accurately, and therefore drivers not accurately installed.  Wouldn't there be a problem if there were not 64bit drivers in the 32bit system of Vista given that the machine is 64bit?

Not sure what else could be the answer.

Also as a side note, after using this technique listed here for partitioning, I am left with a 3GB partition on the 'top' of my driver that I cannot move in Disk Utility in Leopard.  I never resized the Mac partition downward to allow for free space on the top of the partition tables.  It's weird.  There is no way for me to reclaim this space through Disk Utility anyway.

jtw

---

### Post by cyberdork33 on 2007-11-06
> **jtwadsworth said:**
> Wouldn't there be a problem if there were not 64bit drivers in the 32bit system of Vista given that the machine is 64bit?
It is not 64bit, it is x86_64. Meaning that you can run 32bit or 64bit code on it. Also, you only use 64bit drivers in a 64bit OS.

> Also as a side note, after using this technique listed here for partitioning, I am left with a 3GB partition on the 'top' of my driver that I cannot move in Disk Utility in Leopard.  I never resized the Mac partition downward to allow for free space on the top of the partition tables.  It's weird.  There is no way for me to reclaim this space through Disk Utility anyway.

Apple likes to add free space everywhere. I don't know why. This seems like a lot though since it is usually on the order of 100MB. You can probably use gparted to put a new partition in the space if you really wanted. (Small shared partition perhaps?) Can you give the output of 'diskutil list' in OSX?

You never really answered my question. Did you resize the Vista partition? If you did, I think that is likely that the resizing messed up the filesystem, which is why you are having issues. Probably best to reinstall as there is no way to really determine what is missing or corrupted.

---

### Post by jtwadsworth on 2007-11-06
> **cyberdork33 said:**
> It is not 64bit, it is x86_64. Meaning that you can run 32bit or 64bit code on it. Also, you only use 64bit drivers in a 64bit OS.

Ok thanks for clearing me up on that.

> Apple likes to add free space everywhere. I don't know why. This seems like a lot though since it is usually on the order of 100MB. You can probably use gparted to put a new partition in the space if you really wanted. (Small shared partition perhaps?) Can you give the output of 'diskutil list' in OSX?

Will do when I get home and follow up with this.

> You never really answered my question. Did you resize the Vista partition? If you did, I think that is likely that the resizing messed up the filesystem, which is why you are having issues. Probably best to reinstall as there is no way to really determine what is missing or corrupted.

Sorry, didn't meant to ignore the question.  Here is what I did....1TB original MacOSX drive...used BOOTCAMP Manager to create a partition 150GB and installed Vista.  Then booted into Vista and the sound/vidcard issue was apparent.  No resizing was done of the BOOTCAMP partition.  Then pressed ALT during reboot to get back to MacOSX...then resized the MacOSX partition to make room for Ubuntu at 50GB.  Did this on the fly with apparently no problems.  Rebooting now brings up rEFIt's boot drive selection screen.  Have yet to install Ubuntu into it's now reserved partition but will do that next.

Now on the partition table in Disk Utility, it shows a blank 3GB partition in front/on top of the MacOSX partition.  Not sure how it got there or what it's for but it's blank and I cannot move it.  Perhaps a better partitioning program like gparted or some such instead of Disk Utility.

I can start from scratch if I must with not big headache when I get time on the weekend but since things are running relatively ok, it's more an annoyance and challenge to get it right that's driving me now.

jtw

---

### Post by jtwadsworth on 2007-11-06
> **cyberdork33 said:**
> It is not 64bit, it is x86_64. Meaning that you can run 32bit or 64bit code on it. Also, you only use 64bit drivers in a 64bit OS.

Apple likes to add free space everywhere. I don't know why. This seems like a lot though since it is usually on the order of 100MB. You can probably use gparted to put a new partition in the space if you really wanted. (Small shared partition perhaps?) Can you give the output of 'diskutil list' in OSX?

You never really answered my question. Did you resize the Vista partition? If you did, I think that is likely that the resizing messed up the filesystem, which is why you are having issues. Probably best to reinstall as there is no way to really determine what is missing or corrupted.

Here is the output:

```
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *931.5 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS iMac                    726.7 Gi   disk0s2
   3:                  Apple_HFS Ubuntu                  50.0 Gi    disk0s3
   4:       Microsoft Basic Data                         151.3 Gi   disk0s4

```

Strange how that 3GB top partition doesn't show.

jtw

---

### Post by jtwadsworth on 2007-11-06
Just intalled Ubuntu 7.10 and rEFIt does great at allowing choosing which partition to boot.  Linux has the same problem that my VISTA install does...no sound and no accelerated graphics.  For some reason both VIsta and Ubuntu installs fail to detect/install drivers correctly for these devices.

my machine:

iMac 24" Aluminum
4GB RAM
1TB HDD
2.8GHz Core Duo

grr

jtw

---

### Post by cyberdork33 on 2007-11-06
> **jtwadsworth said:**
> Just intalled Ubuntu 7.10 and rEFIt does great at allowing choosing which partition to boot.  Linux has the same problem that my VISTA install does...no sound and no accelerated graphics.  For some reason both VIsta and Ubuntu installs fail to detect/install drivers correctly for these devices.

my machine:

iMac 24" Aluminum
4GB RAM
1TB HDD
2.8GHz Core Duo

grr

jtw

Your problem with video and sound in linux is not the same. That is due to the fact that support for your machine is not completely available yet in Ubuntu by default. You need to install a newer version of fglrx for the 3D graphics and get a patch for ALSA to get the sound working.
[http://ubuntuforums.org/showthread.php?t=598725](http://ubuntuforums.org/showthread.php?t=598725)

It appears that your Ubuntu partition is not being recognized correctly (or it really is HFS+ format, which is highly unrecommended for linux). that command wouldn't show the 3GB space since it is likely 'free' space (no partition).

I think it would be best to delete the windows and ubuntu partitions and start from there. (really I would just repartition the entire drive, but I assume that you cannot do that easily).

Let me know what you decide you want to do and I will try to give a better guide for whichever.

---

### Post by jtwadsworth on 2007-11-06
> **cyberdork33 said:**
> Your problem with video and sound in linux is not the same. That is due to the fact that support for your machine is not completely available yet in Ubuntu by default. You need to install a newer version of fglrx for the 3D graphics and get a patch for ALSA to get the sound working.
[http://ubuntuforums.org/showthread.php?t=598725](http://ubuntuforums.org/showthread.php?t=598725)

It appears that your Ubuntu partition is not being recognized correctly (or it really is HFS+ format, which is highly unrecommended for linux). that command wouldn't show the 3GB space since it is likely 'free' space (no partition).

I think it would be best to delete the windows and ubuntu partitions and start from there. (really I would just repartition the entire drive, but I assume that you cannot do that easily).

Let me know what you decide you want to do and I will try to give a better guide for whichever.

The listing was done just before I installed Ubuntu, so I had formatted that partition by now as ext3.

I installed a patch for the ALSA drivers, perhaps not as updated as the link you sent, but still from Ubuntuforums and now it's working fine from the internal speakers on the iMac.

I had thought the fglrx drivers were up to date for ATI cards by now...I chose Radeon drivers from the setup "screens and graphics preferences" but no luck.  Thanks so much for all your help...which is the fastest way to get the right graphics driver to allow for Compiz?

jtw

---

### Post by cyberdork33 on 2007-11-06
> **jtwadsworth said:**
> The listing was done just before I installed Ubuntu, so I had formatted that partition by now as ext3.

I installed a patch for the ALSA drivers, perhaps not as updated as the link you sent, but still from Ubuntuforums and now it's working fine from the internal speakers on the iMac.

I had thought the fglrx drivers were up to date for ATI cards by now...I chose Radeon drivers from the setup "screens and graphics preferences" but no luck.  Thanks so much for all your help...which is the fastest way to get the right graphics driver to allow for Compiz?

jtw
The HD series cards were not supported until very recently, and this newer driver has not made it into the Ubuntu repos yet.

You can get the latest driver from ATI's website. If you installed 64bit Ubuntu, there is a bug in the latest drivers that gives an error, but you can get fixed packages on my website:
[http://www.rickycampbell.com/2007/10/24/fglrx-8423-in-64bit-gutsy/](http://www.rickycampbell.com/2007/10/24/fglrx-8423-in-64bit-gutsy/)

---

### Post by jtwadsworth on 2007-11-06
> **cyberdork33 said:**
> The HD series cards were not supported until very recently, and this newer driver has not made it into the Ubuntu repos yet.

You can get the latest driver from ATI's website. If you installed 64bit Ubuntu, there is a bug in the latest drivers that gives an error, but you can get fixed packages on my website:
[http://www.rickycampbell.com/2007/10/24/fglrx-8423-in-64bit-gutsy/](http://www.rickycampbell.com/2007/10/24/fglrx-8423-in-64bit-gutsy/)

Ok, now I've learned a bit from you and reading tons...going to start completely over with repartiioning everything and reinstalling...will let you know later in the week how it goes.

jtw

---

### Post by jtwadsworth on 2007-11-07
Partial update just because it may help others and to prove what an idiot I am...the Vista problems were simply because I failed to run the BOOTCAMP program on the Leopard DVD while booted into Vista...this program installs all the drivers needed for the iMac hardware into Vista...now Vista boots and functions perfectly...now if only fixing the M$ nagging about activation of a product I've already bought but installed on another computer was so easy.

More to come on the Ubuntu install and functions but I hope this may help someone who also neglected to install BOOTCAMP from within Vista...there may be at least one other person out who was impatient during the setup like me.

jtw

---

### Post by cyberdork33 on 2007-11-07
> **jtwadsworth said:**
> More to come on the Ubuntu install and functions but I hope this may help someone who also neglected to install BOOTCAMP from within Vista...there may be at least one other person out who was impatient during the setup like me.

Well, that makes more sense now... :) I assumed you had already used the drivers cd.

---

### Post by ChardFi on 2007-11-07
Well i'm on my third attempt at this tripple boot nonsenseon my spanking new MacBook Pro :-(

- The first time i did it i foolishly forgot to change the boot loader to the Ubuntu installation drive. This resulted in all systems still booting but whenever i loaded windows i got a ubuntu boot screen.

- The second time i decided that not only would i have the thee main partitions, also i would add an extra partition in fat32 that i could use to put all my files in. This all worked ok until i installed ubuntu (this time specifying sda3 for bootloader) where neither windows or ubuntu would boot.

This time i am going back to the first plan of installing each os on their own partition and see how that turns out!

Might need some help later Chaps.

Chard

---

### Post by ChardFi on 2007-11-07
Ok, I re-did everything. I've installed all three of the sods and they all boot (Yay).

Anyway, i booted ubuntu and things were looking pretty good. Graphics were nice and i could connect to the internet via my Ethernet. However, I didn't have wifi, the touch pad is a nightmare and i'm paranoid she's running too hot. Oh and no back light but i'll deal with that later.

So, i followed a couple of tutorials at [https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa) and i can now see the wifi card, although i can't connect to my WPA2 protected wifi but i'm sure i'll figure that one out at some point. The next tutorial i followed was the X.org adjustments to sort out the touch pad and now all my lovely graphics are screwed up. I went to recover from my backup of xorg.conf but it's too late as i have managed to delete it by making a tired mistake. Can anyone help me sort this out as all graphics tutorials seem to be for the  ATI drivers?

Here's my config

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600M GT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600M GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1440x1440"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Thanks

---

### Post by cyberdork33 on 2007-11-07
You need to enable the proprietary nvidia driver.

---

### Post by ChardFi on 2007-11-07
Thanks for the advice CyberDork. I am really new to ubuntu though so do you think you could provide more details on how?

Cheers

---

### Post by cyberdork33 on 2007-11-07
> **ChardFi said:**
> Thanks for the advice CyberDork. I am really new to ubuntu though so do you think you could provide more details on how?

Cheers
The restricted drivers manager should suggest it to you. System > Administration > Restricted Drivers Manager

If it does not have an option, the package is nvidia-glx-new as in the wiki page you posted.

---

### Post by ChardFi on 2007-11-08
I spotted this one last night and spent ages trying to get something to work but the screen seemed to still be shot to pieces. However, this morning when i booted her up she was loving it!

...Must have needed a couple of reboots. Only Temperature, Mouse, Back Light,and the iSight camera to go.

Cheers for all the help so far :-)

C

---

### Post by cyberdork33 on 2007-11-08
> **ChardFi said:**
> I spotted this one last night and spent ages trying to get something to work but the screen seemed to still be shot to pieces. However, this morning when i booted her up she was loving it!

...Must have needed a couple of reboots. Only Temperature, Mouse, Back Light,and the iSight camera to go.

Cheers for all the help so far :-)

C
iSight should be working out-of-the-box on Gutsy (not necessarily in the app you want, but drivers are there). 

Test with:
```
gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink
```

For the backlight, I think you need pommed:

---

### Post by ChardFi on 2007-11-08
Thanks Cyberdork33 you've been really helpful so far, hope you don't mind if i pick your brains some more;

As i understand it Xorg.conf is the file that runs at start up and contains all the relevant subs to configure system components. At present my touch pad is crap as in it is uber sensitive and i can only get a right click from a three finger finger tap :-( I've followed a few tutorials to copy a new xorg.conf to my system to try and make it work but nothing sems to work.

The part that i don't understand is this;

I've been googlng like made and found a config that relates to debian. I backed up my existing config and this time only copied over the subs that appeared to be the mouse setup. However, when i reboot all the graphics are screwed up again and the mouse still isn't working.

Why does only changing the subs about the mouse affect the graphics on my system and how can i sort this touch pad out?

Please help me :-( If posted what i copied below

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Option         "RTCornerButton" "3"
    Option         "RBCornerButton" "2"
    Identifier     "Apple Touchpad"
    Driver         "synaptics"
    Option	   "CorePointer"
    Option         "GrabEventDevice" "1" # use device exclusively
    Option         "Device" "/dev/input/by-id/usb-Apple_Computer_Apple_Internal_Keyboard_._Trackpad-event-mouse"
    Option         "Protocol" "auto-dev"
    Option         "SHMConfig" "on"
# Touchpad geometry 
    Option         "TopEdge" "50"
    Option         "BottomEdge" "330"
    Option         "LeftEdge" "50"
    Option         "RightEdge" "1100"
    Option         "AccelFactor" "0.2"
    Option         "MinSpeed" "0.4"
    Option         "MaxSpeed" "1.5"
    Option         "FingerLow" "5"
    Option         "FingerHigh" "25"
# button2 = twofingertap, button3 = threefingertap
    Option         "TapButton2" "0"
    Option         "TapButton3" "0"
# don't mistake moving for tapping
    Option         "MaxTapMove" "20"
    Option         "MaxTapTime" "100"
# don't wait too long for double-clicks..
    Option         "SingleTapTimeout" "100"
# Scrolling
    Option         "VertEdgeScroll" "1"
    Option         "HorizEdgeScroll" "0"
    Option	   "CornerCoasting" "1"
    Option	   "CoastingSpeed" "10"
    Option         "VertTwoFingerScroll" "0"
    Option         "HorizTwoFingerScroll" "0"
    Option         "VertScrollDelta" "20"
    Option         "HorizScrollDelta" "0"
# CornerButtons
EndSection

---

### Post by cyberdork33 on 2007-11-08
These options adjust the sensitivity (both sensitivity to touch and mov't):
```
Option         "AccelFactor" "0.2"
Option         "MinSpeed" "0.4"
Option         "MaxSpeed" "1.5"
Option         "FingerLow" "5"
Option         "FingerHigh" "25"
```It is assuming you have 3 buttons you want to use, and thus the 3rd finger is right click, middle is middle click, and first is left click. You can swap those with:
```
Option "TapButton2" "3"
Option "TapButton3" "2"
```This will make 3-finger a middle click, and 2-finger a right click.

You can see all the synaptics options and how to set them by doing 'man synaptics' at the commandline.

---

### Post by jtwadsworth on 2007-11-08
> **cyberdork33 said:**
> Well, that makes more sense now... :) I assumed you had already used the drivers cd.

Followed your website to the letter...all went well it seems with no errors...after reboot I am still unable to enable video effects.  The driver is listed as fglrx.

But fglrxinfo yields the Mesa GLX Indrect driver and things are actually slower with the way scrolling in windows is.  

Where did I flub?

jtw

---

### Post by cyberdork33 on 2007-11-09
> **jtwadsworth said:**
> Followed your website to the letter...all went well it seems with no errors...after reboot I am still unable to enable video effects.  The driver is listed as fglrx.

But fglrxinfo yields the Mesa GLX Indrect driver and things are actually slower with the way scrolling in windows is.  

Where did I flub?

jtw

Not sure, but if you get mesa, you are not getting 3D acceleration. Did you completely reboot your machine? I was getting strange things happening until I completely reloaded the kernel.

You might try this too:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying)

---

### Post by ChardFi on 2007-11-09
> **cyberdork33 said:**
> These options adjust the sensitivity (both sensitivity to touch and mov't):
```
Option         "AccelFactor" "0.2"
Option         "MinSpeed" "0.4"
Option         "MaxSpeed" "1.5"
Option         "FingerLow" "5"
Option         "FingerHigh" "25"
```It is assuming you have 3 buttons you want to use, and thus the 3rd finger is right click, middle is middle click, and first is left click. You can swap those with:
```
Option "TapButton2" "3"
Option "TapButton3" "2"
```This will make 3-finger a middle click, and 2-finger a right click.

You can see all the synaptics options and how to set them by doing 'man synaptics' at the commandline.


BRILLIANT!

I copied these to my config, my graphics isn't screwed up and my touch pad works properly! Much, much appreciation to you for making that post.

I even managed to get the backlight working by installing pommed!

..Man, I love ubuntu it is wicked fast and i'm starting to find my way around it now. So many great and free apps. If i can put my mind at ease about the temperature i think i might ditch Leopoard all together!

---

### Post by cyberdork33 on 2007-11-09
> **ChardFi said:**
> BRILLIANT!

I copied these to my config, my graphics isn't screwed up and my touch pad works properly! Much, much appreciation to you for making that post.

I even managed to get the backlight working by installing pommed!

..Man, I love ubuntu it is wicked fast and i'm starting to find my way around it now. So many great and free apps. If i can put my mind at ease about the temperature i think i might ditch Leopoard all together!
See if this works for your fans:
[http://ubuntuforums.org/showpost.php?p=3710810&postcount=103](http://ubuntuforums.org/showpost.php?p=3710810&postcount=103)
You might need to leave out the '.768' when typing the command as that is only added with the very latest patches.

---

### Post by ChardFi on 2007-11-09
Won't this just set the fans flat out all the time?

How can i put the fans back as they are if this doesn't help?

---

### Post by cyberdork33 on 2007-11-09
> **ChardFi said:**
> Won't this just set the fans flat out all the time?

How can i put the fans back as they are if this doesn't help?

yes, but better than frying your laptop.

You can turn off manual control by using the first set of commands again, but using 0 (false) instead of 1 (true)

```
echo 0 > /sys/devices/platform/applesmc.768/fan1_manual
echo 0 > /sys/devices/platform/applesmc.768/fan2_manual
```

---

### Post by jtwadsworth on 2007-11-09
> **cyberdork33 said:**
> Not sure, but if you get mesa, you are not getting 3D acceleration. Did you completely reboot your machine? I was getting strange things happening until I completely reloaded the kernel.

You might try this too:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying)

I remember now another reason I was angry with Apple for putting ATI cards in the iMac.  I've done everything on your website walkthrough by cut and paste and in order getting no errors, but I'm still stuck with the Mesa driver which is slower than the default.

jtw

---

### Post by cyberdork33 on 2007-11-09
> **jtwadsworth said:**
> I remember now another reason I was angry with Apple for putting ATI cards in the iMac.  I've done everything on your website walkthrough by cut and paste and in order getting no errors, but I'm still stuck with the Mesa driver which is slower than the default.

jtw

It's not slower, it just is not supposed to be used with fglrx.

Just fyi the latest ATI drivers are fishy anyway so don't feel too bad about it. can you post your current xorg.conf?

---

### Post by ChardFi on 2007-11-09
> **cyberdork33 said:**
> yes, but better than frying your laptop.

You can turn off manual control by using the first set of commands again, but using 0 (false) instead of 1 (true)

```
echo 0 > /sys/devices/platform/applesmc.768/fan1_manual
echo 0 > /sys/devices/platform/applesmc.768/fan2_manual
```

Fair comment.

When running these commands i'm getting a permission denied error, even if i stick a sudo in from of it :-( is this because the file is in use? 

> How can i work around this?

---

### Post by cyberdork33 on 2007-11-09
> **ChardFi said:**
> Fair comment.

When running these commands i'm getting a permission denied error, even if i stick a sudo in from of it :-( is this because the file is in use? 

> How can i work around this?

Did you take the .768 out? If so, then I don't know. It may not even be available for you unless you [recompile your kernel]("http://ubuntuforums.org/showthread.php?t=442941") with the mactel patches. Oh, make sure the applesmc module is actually loaded as well:
```
sudo modprobe applesmc 
```

I think there is still a way to do it, but I do not know how.

---

### Post by jtwadsworth on 2007-11-09
> **cyberdork33 said:**
> It's not slower, it just is not supposed to be used with fglrx.

Just fyi the latest ATI drivers are fishy anyway so don't feel too bad about it. can you post your current xorg.conf?

I went through the Wiki steps and now have it working somehow...I used the default ATI package and although I got 1 error it apparently still took since now I am compositing.

Hopefully the next time I reinstall Ubuntu it will play more nicely with ATI and visa versa.  Where is the compiz config tool?

Also, I have an extra screen hooked up to the iMac...does Ubuntu recognize dual screens?  So far my 2nd one is just mirroring the first.

jtw

---

### Post by cyberdork33 on 2007-11-09
> **jtwadsworth said:**
> I went through the Wiki steps and now have it working somehow...I used the default ATI package and although I got 1 error it apparently still took since now I am compositing.
whatever works. Did you use the 32bit debs on my site previously? maybe they are not working correctly (they are not mine).

> **jtwadsworth said:**
>  Hopefully the next time I reinstall Ubuntu it will play more nicely with ATI and visa versa.  Where is the compiz config tool?

System > Preferences > Advanced Desktop Configuration tool (something like that)

> **jtwadsworth said:**
>  Also, I have an extra screen hooked up to the iMac...does Ubuntu recognize dual screens?  So far my 2nd one is just mirroring the first.You can attempt to use the "Screens and Resolutions" tool in the admin menu, but that is kind of hit-or-miss for most people. Otherwise there are instructions in the Gutsy Release Notes under "Dual-head (multi-screen) setups":
[https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes](https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes)

---

### Post by jtwadsworth on 2007-11-09
> **cyberdork33 said:**
> 
System > Preferences > Advanced Desktop Configuration tool (something like that)


This was helpful [http://ubuntu-tutorials.com/2007/10/04/compiz-fusion-on-ubuntu-710-gutsy-gibbin/](http://ubuntu-tutorials.com/2007/10/04/compiz-fusion-on-ubuntu-710-gutsy-gibbin/)

THanks for all your help...will work on the dual head stuff now.

jtw

---

### Post by hardawayd on 2007-12-05
I just got my MBP and have tried with no success to install Ubuntu 7.10 using both the live cd-64 and the alternate 7.10 cd-64. During the installation it keeps indicating corrupt file error messages for some of the files and at the end of the base installation it says it failed. Have no idea what the problem is.

---

### Post by cyberdork33 on 2007-12-05
> **hardawayd said:**
> I just got my MBP and have tried with no success to install Ubuntu 7.10 using both the live cd-64 and the alternate 7.10 cd-64. During the installation it keeps indicating corrupt file error messages for some of the files and at the end of the base installation it says it failed. Have no idea what the problem is.

bad download / burn

---

### Post by framerate on 2007-12-29
> **violajack said:**
>  The only thing to be careful of at this point is that in the last window of the installer, you have to click the "Advanced" button and tell it to install grub to the same partition as Linux, not hd0, or it will overwrite the Master Boot Record.  In my case (EFI system on 1, OSX on 2, Linux on 3, and Vista on 4) that meant installing to /dev/sda3.  

Great post, but the GRUB syntax always confuses me. 

If I want to install to /dev/sda3... and the "Advanced Tag" wants it in the form (hd0)... what is the proper syntax?

I was hoping I could just list a device, so I tried /dev/sda3 and got an error :(

Thanks!

---

### Post by ethien on 2007-12-30
> **violajack said:**
> From OSX, I used the GUI Disk Utility from the Utilities folder.  If you click on the main disk (not on of the two partitions) you will have a tab option for Partition.  From the graphic of the two partitions, click the main OSX partition, then click the little plus sign and it will split the OSX partition into two.  You can then drag the space between to set the size of the new partition and name it whatever you want.  Disk Utility will only format it as HFS+, but the Ubuntu live CD will gladly reformat it to ext3 for you.  The partitions did not stay proportional size-wise in the GUI, but if you click on each, it should show the correct size in GB.  Yes, it resized my OSX partition, while booted, nondestructively, without breaking my ability to boot Windows. 

Hi there,
I tried this twice, but Disk Utility hangs when I try to cut the OSX partition in two to make room for Ubuntu. (I get "Modifying Partition Map" spinning forever). The only difference I can think of is the fact I'm installing Windows XP in lieu of Vista, but as far as I know this shouldn't make any difference to disk partioning anyway, right?

The first time I force quit Disk Utility and tried to partition using GParted, but Windows did not start after installing Ubuntu (missing a dll or something windows-ish of the sort). I did notice that GParted created an ext3 partition on /dev/sda4 and not sda3.

I tried it all again from scratch, zeroing the drive to make sure I started with a clean slate. All went smoothingly, but Disk Utility is still hanging as I type this, making it a solid 25-30 minutes now.


Any ideas?
Cheers



MacBook Pro 2.16
MacOS X 10.5
Windows XP SP2
Ubuntu 7.10




[EDIT] Just retried (3-4th time) and it worked. I don't know exactly what I did right this time. The only thing I can think of is I did not erase the name this time around.

---

### Post by framerate on 2007-12-30
> **ethien said:**
> 

[EDIT] Just retried (3-4th time) and it worked. I don't know exactly what I did right this time. The only thing I can think of is I did not erase the name this time around.

I'd be worried about the harddrive being faulty? Maybe not, but seems odd.


Anyone have any idea on my GRUB issue? I don't want to mess around with my laptop as I need OS X functioning, and this How To specifically said DO NOT install to (hd0)

Thanks!

edit: found a wiki post that said to do hd(0,2) (well they said 0,3 but my partition sets sda3 as my linux partition). Once again I got a fatal error running "grub install(hd0,2) and the install failed.

Any help would be amazing.

---

### Post by cyberdork33 on 2008-01-02
> **framerate said:**
> Great post, but the GRUB syntax always confuses me. 

If I want to install to /dev/sda3... and the "Advanced Tag" wants it in the form (hd0)... what is the proper syntax?

I was hoping I could just list a device, so I tried /dev/sda3 and got an error :(

Thanks!

should be (hd0,2)

You are going to have to give more information about how your partitions are setup if you need help.

---

### Post by framerate on 2008-01-02
> **cyberdork33 said:**
> should be (hd0,2)

You are going to have to give more information about how your partitions are setup if you need help.

My partitions were setup exactly like the original post.

EFI
OSX
Linux (made with disk utils)
Windows

weird that hd(0,2) gave me an error, but I'll try it again.

---

### Post by cyberdork33 on 2008-01-02
> **framerate said:**
> My partitions were setup exactly like the original post.

EFI
OSX
Linux (made with disk utils)
Windows

weird that hd(0,2) gave me an error, but I'll try it again.
please give the output of:
```
sudo parted /dev/sda print
```

---

### Post by violajack on 2008-01-04
> **framerate said:**
> Great post, but the GRUB syntax always confuses me. 

If I want to install to /dev/sda3... and the "Advanced Tag" wants it in the form (hd0)... what is the proper syntax?

I was hoping I could just list a device, so I tried /dev/sda3 and got an error :(

Thanks!

I'm not sure if you're still working on this or not (I don't check this thread often enough any more), but I really did just click the Advanced button at the very last screen, which pops up another little window, and typed in /dev/sda3 in place of the default hd0,0 and it installed with grub going to the beginning of the linux partition.  Are you still having trouble?  What error does it give you?  I remember having some errors the first time around too due to mistyping and trying /dev/hda3.  If the grub install fails, but the rest of the install went okay, I think there's a way to do just the grub install from the live CD so you don't have to do the whole install over again, but I didn't bother to look it up.  When I screwed up the first time, I just did the whole install over again, but making sure I had /dev/sda3 in the Advanced pop up of the last install screen.

---

### Post by hardawayd on 2008-01-05
In installing Gusty and Hardy on my MBP (santa rosa) what i have found is that using partitions above 4 is better since the boot loader Grub is gpt aware but not fully engineered to work with it.  Why they do not have a version that is fully compatible is beyond me.  I understand that elilo is supposed to be compatible with the efi/gpt stuff on the new Macs but have not tried it.  I would hope that Ubuntu would have its installed detect if the Machine is a efi/gpt and if so to use a bootloader that would work properly and ignore the MBR.

---

### Post by cyberdork33 on 2008-01-05
> **hardawayd said:**
> In installing Gusty and Hardy on my MBP (santa rosa) what i have found is that using partitions above 4 is better since the boot loader Grub is gpt aware but not fully engineered to work with it.  Why they do not have a version that is fully compatible is beyond me.  I understand that elilo is supposed to be compatible with the efi/gpt stuff on the new Macs but have not tried it.  I would hope that Ubuntu would have its installed detect if the Machine is a efi/gpt and if so to use a bootloader that would work properly and ignore the MBR.

We are forcing to load the OS in legacy mode because there is still a way to go to get eveything working for a native EFI boot... I don't think it is a problem with grub, but more a problem with the how the MBR is emulated on your Mac...

---

### Post by grazie on 2008-01-08
For some strange reason I'm having lots of problems with this. Several times now I've got as far getting OS X installed followed by XP with bootcamp, followed by rEFIt and finally resizing the OS X partition. I've also installed both Parallels and VMWare Fusion to use XP under virtualization and everything works fine. However, as soon as I add extra partitions for Linux to the free space created on resizing OS X, both with OS X Diskutill or Linux gparted, the XP installation becomes unbootable. Also, something that seems rather odd is that gparted will let me add as many primary partitions as I like, rather than a maximum of four. I don't think it's significant, but the machine is the latest MacBook with Santa Rosa.

---

### Post by violajack on 2008-01-08
> **grazie said:**
> For some strange reason I'm having lots of problems with this. Several times now I've got as far getting OS X installed followed by XP with bootcamp, followed by rEFIt and finally resizing the OS X partition. I've also installed both Parallels and VMWare Fusion to use XP under virtualization and everything works fine. However, as soon as I add extra partitions for Linux to the free space created on resizing OS X, both with OS X Diskutill or Linux gparted, the XP installation becomes unbootable. Also, something that seems rather odd is that gparted will let me add as many primary partitions as I like, rather than a maximum of four. I don't think it's significant, but the machine is the latest MacBook with Santa Rosa.

How are you going about adding partitions to the free space?  The way that worked for me was to use the graphical DiskUtil in OSX to split the main HFS+ partition into two HFS+ partitions.  The only thing I changed after I clicked the + button was to drag the separater to get the sizes I wanted.  I left the second partition as HFS+.  The only other time I touched the partitions was in the installer on the live CD of Ubuntu.  I used that to delete the second HFS+ partition and then to create one big ext3 partition for linux in that space.  You can only add that one partition.  I found that every time I tried to touch the partitions from the command line, or do any deleting from OSX, they blew up.  No amount of trying to resync the partition tables in rEFIt fixed it.  The only tool that would reliably create the linux partitions for me was the installer from the live CD.

---

### Post by cyberdork33 on 2008-01-08
> **grazie said:**
> For some strange reason I'm having lots of problems with this. Several times now I've got as far getting OS X installed followed by XP with bootcamp, followed by rEFIt and finally resizing the OS X partition. I've also installed both Parallels and VMWare Fusion to use XP under virtualization and everything works fine. However, as soon as I add extra partitions for Linux to the free space created on resizing OS X, both with OS X Diskutill or Linux gparted, the XP installation becomes unbootable. Also, something that seems rather odd is that gparted will let me add as many primary partitions as I like, rather than a maximum of four. I don't think it's significant, but the machine is the latest MacBook with Santa Rosa.you are not limited to four partitions on the disk, the emulated bios is just limited to seeing the the first four partitions (which means that windows is also since it can only use the MBR partition table and cannot use the real GPT).

what kind of error are you getting from windows? If you install windows and then change the partitions, you will sometimes get boot errors. Try this if you are getting the hal.dll error:
[http://ubuntuforums.org/showthread.php?t=327386](http://ubuntuforums.org/showthread.php?t=327386)

---

### Post by grazie on 2008-01-08
violajack,

I hadn't realised you were restricting yourself to four partitions, which also explains your comment about not using a swap partition. This is where what I've done has been different and is certainly why I am getting problems that you didn't.

cyberdork33,

I remember getting the hal.dll error in an earlier try, but that's not what I've got now. When booting Windows (and virtual Windows using Parallels) I get the following error.
```
No bootable device - insert boot disk and press any key
```
However, using VMWare gives a more useful error message as follows
```
Cannot open the disk '/Users/grazie/...' blah blah

Reason: The partition table on the physical disk has changed since the disk was created. 
        Remove the physical disk from the virtual machine, then add it again.
```
I could try looking at the MBR and see if can be hacked, but I'd rather not. If you know of an easier solution, it would be much appreciated. And I still can't figure out why gparted lets me create lots of primary partitions. I'm sure it should complain if you try creating more than four and on the same disk. It must be to do with the way GPT works, which I know nothing about (yet).

Thanks for both of your replies.

---

### Post by cyberdork33 on 2008-01-08
> **grazie said:**
> When booting Windows (and virtual Windows using Parallels) I get the following error.
```
No bootable device - insert boot disk and press any key
```However, using VMWare gives a more useful error message as follows
```
Cannot open the disk '/Users/grazie/...' blah blah

Reason: The partition table on the physical disk has changed since the disk was created. 
        Remove the physical disk from the virtual machine, then add it again.
```I could try looking at the MBR and see if can be hacked, but I'd rather not. If you know of an easier solution, it would be much appreciated. And I still can't figure out why gparted lets me create lots of primary partitions. I'm sure it should complain if you try creating more than four and on the same disk. It must be to do with the way GPT works, which I know nothing about (yet).
from the vmware error message it may be more related to the same issue as the hal.dll error. I would try that solution anyway. You are changing the partition layout after install. Windows doesn't like this. Why do you not just create all your needed partitions up front, then install Windows...

Again, you ARE NOT limited to 4 partitions. This is a point of confusion. gparted directly reads and partitions via the GPT. As a form of legacy compatibility (for Operating Systems such as windows, that cannot read the GPT), the first 4 partitions in the GPT *appear* as a MBR partition table. Partitioning with gparted directly affects the GPT and syncs the psuedo-MBR with the GPT.

So the rules for partitioning are:[LIST]
[*]Windows will be limited to seeing the first 4 partitions on the disk, therefore, the windows partition as well as any partitions that you want windows to be able to access need to be within the first four partitions.
[*]Since OSX is booted directly from EFI, and is unaffected by the state of the MBR, you can put your OSX partition ANYWHERE on the disk... This includes partitions AFTER number 4.
[*]I have seen evidence that you do not have to have any Linux partitions within the first 4, but I would keep at least the initial boot partition within the first 4 to make it easy on yourself. (this means /boot or the entire / partition if you do not separate /boot on it's own). Once Linux is loaded, it can read the GPT and interact with partitions beyond 4, meaning you can have a separate /home partition, swap partition, or whatever greater than 4 with no problem...[/LIST]So... You just need to taylor you partitions to suit windows (and one for Ubuntu) and you should not have issues.

---

### Post by grazie on 2008-01-09
> Why do you not just create all your needed partitions up front, then install Windows...
Because I want to use virtual Windows with either Parallels or VMWare Fusion from OS X. I could be wrong, but it's my understanding that in order to use a real Windows disk image with either of these tools then Windows needs to be installed via Bootcamp. The problem with Bootcamp is that you can only have two partitions. You then have to shrink either OS X or Windows to make room for Linux or whatever else you fancy. However shrinking OS X results with the Windows partition outside the first four partitions if you create more than one partition in the free space, which is why I've got the problems described . If you shrink the Windows parition, as I did initially, you end up with the hal.dll error (or maybe others) cyberdork33 mentions. Also, I'm pretty sure that shrinking Vista (using Vista, not Linux) wouldn't work well if at all. However, as I believe Vista supports GPT then shrinking it wouldn't be needed - you'd shrink the OS X partition instead.

There's no confusion with DOS disks and MBR records on my part. You are limited to four primary partitions with this type of disk. If more partitions are needed then an extended partition is used. However, it's now clear to me that GPT does not have these restrictions.

I'll give Bootcamp one more try by going back to shrinking the Windows partition to make room for Linux. Otherwise, I think the only solution is not to use Bootcamp.

---

### Post by cyberdork33 on 2008-01-09
> **grazie said:**
> Because I want to use virtual Windows with either Parallels or VMWare Fusion from OS X. I could be wrong, but it's my understanding that in order to use a real Windows disk image with either of these tools then Windows needs to be installed via Bootcamp.
I wouldn't really say that you have to you bootcamp, but the VM setup expects there only to be one other partition (for Windows). I also think you are over-valuing Bootcamp... all it does for you is partition a disk... you can do that without Bootcamp.

> The problem with Bootcamp is that you can only have two partitions. You then have to shrink either OS X or Windows to make room for Linux or whatever else you fancy. However shrinking OS X results with the Windows partition outside the first four partitions if you create more than one partition in the free space, which is why I've got the problems described . If you shrink the Windows parition, as I did initially, you end up with the hal.dll error (or maybe others) cyberdork33 mentions.However, the hal.dll error might be the better situation since it has a known fix!

> Also, I'm pretty sure that shrinking Vista (using Vista, not Linux) wouldn't work well if at all. However, as I believe Vista supports GPT then shrinking it wouldn't be needed - you'd shrink the OS X partition instead.I am sure there are windows partitioning tools that can shrink Vista partitions (NTFS)... and I KNOW that gparted can, (I just did this the other day). Also Vista does NOT support GPT. I think there are some server editions of windows that can read gpt, but nothing consumer-grade. (I believe it is only Windows for Itanium-based systems.) I believe it REALLY has to do with the fact that you can't boot Windows from EFI... yet.

> There's no confusion with DOS disks and MBR records on my part. You are limited to four primary partitions with this type of disk. If more partitions are needed then an extended partition is used. However, it's now clear to me that GPT does not have these restrictions.Correct. Unfortunately, the legacy compatibility on your Mac does not allow for logical/extended partitions. That would make things much easier (At least nobody has figured out how to do it yet).

Good Luck!

EDIT: I just remembered that you do have another option. You can format the entire disk in DOS MBR format (not GPT). OSX will not install to such a disk, but you can restore an image of a partition to the legacy disk and it will boot and run fine. There are a few threads about this in the forum here, but basically, you clone the OSX install to the MBR disk from an external drive.

---

### Post by grazie on 2008-01-15
I'm afraid I failed to achieve what I tried to do. What I really wanted was to install as many Linux distros as I felt like (though in reality it would probably be no more than two) and install Windows XP along with OS X. I also wanted to be able to use the Window image from OS X using virtualization software. However, as soon as you add another OS to the already installed OS X and Windows, the virtualization apps go belly up. 

I've still got the hal.dll error on booting Windows and all the solutions I've seen to this problem involve editing the partition numbers in the Windows boot.ini file. Editing this file didn't work for me. However, one thing about my installation that may be  causing problems is that although the Windows partition is the last physical partition on the disk, it is /dev/sda3 and Linux is /dev/sda4. Maybe I could try renumbering the partitions, which I've done before for Apple Partition Table disks, but I've no  idea whether it's possible on GPT disks. Or maybe I'm missing something obvious.

About the best reference I found was [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp).

One thing that I did do that I wouldn't recommend was to change to my OS X UID and GID to match Linux. I then ended up with lots of disk permission problems and actually losing use of the CD-ROM, despite using chown to change file ownerships. I've been using OS X 10.5 (Leopard) BTW.

EDIT: I should have added that changing the partition numbers in boot.ini from 3 to 2 made Windows bootable and fixed the hal.dll missing problem, but it still doesn't boot to completion. The message I now get after the Windows splash screen is UNMOUNTABLE_BOOT_VOLUME,etc . Booting up in Safe Mode shows that the boot gets as far as loading drivers the last one being agp440.sys. I've not been able to find any solution to this problem.

---

### Post by LiamTreacy on 2008-01-15
OK I tried this and the only part that didn't work is the XP installation. It's incomplete and won't boot right after the main installation. So it's either boot from CD orDisk Error.

---

### Post by LiamTreacy on 2008-01-23
Having tried this, my advice is not to use Disk Utility to partition your disks. It worked to partition for Windows, but the second partition for Linux would not work. It failed about three times, saying it had lost control of the disk (!). The fourth time it failed with "resource not available," after it had freed the space but before it had formatted it. Now I'm left with 30GB of unusable free space that Disk Utility refuses to deal with. I'm trying to find an alternative way of reclaiming this space without buying iPartition.

---

### Post by cyberdork33 on 2008-01-23
> **LiamTreacy said:**
> Having tried this, my advice is not to use Disk Utility to partition your disks. It worked to partition for Windows, but the second partition for Linux would not work. It failed about three times, saying it had lost control of the disk (!). The fourth time it failed with "resource not available," after it had freed the space but before it had formatted it. Now I'm left with 30GB of unusable free space that Disk Utility refuses to deal with. I'm trying to find an alternative way of reclaiming this space without buying iPartition.
It doesn't matter if it is formatted or not, you are just going to reformat it during the Ubuntu install. 

Boot the Ubuntu LiveCD and run the partition editor. You can then alter the partition / free space however you like (you cannot increase the size of your OSX partition though), but if you can get it into a working partition, you can use disk utility to remove it.

---

### Post by macuser2000 on 2008-01-23
You know, I have a triple boot setup too on my iMac. I use Apple's EFI boot loader to select the Leopard or windows partitions. When I boot into the windows partition, I use the GRUB boot loader to boot into ubuntu or windows vista.

---

### Post by LiamTreacy on 2008-01-24
> **cyberdork33 said:**
> It doesn't matter if it is formatted or not, you are just going to reformat it during the Ubuntu install. 

Boot the Ubuntu LiveCD and run the partition editor. You can then alter the partition / free space however you like (you cannot increase the size of your OSX partition though), but if you can get it into a working partition, you can use disk utility to remove it.
Well I just did that, and it seemed to work, formatting the free space to ext3. When I restarted in OS X, I find I still have 30.8GB Empty Space, 86.2 iMac HD, 31.9 NTFS for Windows WHICH SHOWS UP AS FORMATTED AND NOW WON'T BOOT TO WINDOWS, and a new entry, DISKOS4, 30.8GB FAT. 

This last entry is obviously wrong, as I never created a FAT partition. It's the same size as the Empty Space so Disk Utility is duplicating the Empty Space in its list of partitions. The total for all 4 partitions is 180GB. It's a 160GB drive!

I'll think I'll have to buy iParition and try to repair this mess before it goes any more wrong.

Edit: The Windows partition is still there on the OS X desktop, thankfully. It's just not bootable anymore. Disk Utility still thinks it's formatted. Disk Utility stinks, I'm thinking.

---

### Post by Djesse on 2008-01-24
This doesn't work for me, I don't know why every time when I add a partition I get a warning from the Disk utility saying "Changing the partition map may make the Boot Camp partition unbootable." I thought that was fine so I continued, but after I added a new partition, I won't be able to boot Windows XP again, does it work for the Vista Only? The problem is it seems to be fine when I was booting into Windows, I can see the Windows Logo, but before I can see the Welcome screen it shows a blue screen, and that was so fast sometimes I can't even see the blue screen, my computer(MacBook Pro 2.33Ghz) will restart immediately. And it just keep happening. Does anyone has the same???

Thanks!

---

### Post by cyberdork33 on 2008-01-24
> **LiamTreacy said:**
> I'll think I'll have to buy iParition and try to repair this mess before it goes any more wrong.Well, good luck. I don't really know how you got your GPT so messed up. I think your Windows install is fine, you just can't boot it because the windows bootloader is not in the MBR and/or the boot sectors on the partition got messed up. This can be fixed from the windows recovery console (on the install disc) using the FIXMBR and FIXBOOT commands respectively. It may not work until you get your partition table problems situated though.

---

### Post by LiamTreacy on 2008-01-24
> **cyberdork33 said:**
> Well, good luck. I don't really know how you got your GPT so messed up. I think your Windows install is fine, you just can't boot it because the windows bootloader is not int he MBR and/or the boot sectors on the partition got messed up. This can be fixed from the windows recovery console (on the install disc) using the FIXMBR and FIXBOOT commands respectively. It may not work until you get your partition table problems situated though.
I think Windows not booting was a rEFIt problem. Because I've deleted the intended Linux partition using iParition and it's back to 3 partitions: Empty Space, Mac, XP - and Mac and XP both boot again with rEFIt.

I think the best thing to do is simply ignore what I see in Disk Utility, because it has a completely different view of the partitions than iPartition and Ubuntu. I'll try to enlarge the HFS partition to take in the Empty Space and repartition again. If that fails I'll try install Linux on the Empty Space partition and configure rEFIt to boot all 3 OSes correctly. Thanks for your help.

---

### Post by cyberdork33 on 2008-01-24
> **LiamTreacy said:**
> I'll try to enlarge the HFS partition to take in the Empty Space and repartition again. That may be all it takes. Rewriting the partition table might fix whatever issues the GPT has in it...

---

### Post by LiamTreacy on 2008-01-28
iParition resized the HFS partition so I'm back to HFS and Windows. I tried again to partition the HFS volume but now I get "MediaKit reports partition (map) too small." I don't know if this is a symptom of a problem left over from the previous failed partitions or just a shortcoming in Disk Utility. If it's the latter I'd partition using another tool.

---

### Post by cyberdork33 on 2008-01-28
> **LiamTreacy said:**
> iParition resized the HFS partition so I'm back to HFS and Windows. I tried again to partition the HFS volume but now I get "MediaKit reports partition (map) too small." I don't know if this is a symptom of a problem left over from the previous failed partitions or just a shortcoming in Disk Utility. If it's the latter I'd partition using another tool.
You might want to do a disk repair from the install dvd to make sure everything is as it should be after doing all the resizing.

---

### Post by LiamTreacy on 2008-01-31
I ran the Disk Utility tools and they found no problems. I then partitioned with iPartition. It looks all messed up in Disk Utility but I didn't mind that. Now both OS X and Ubuntu are booting, thanks very much. XP is now giving me the hal.dll treatment.

Could I be directed to the solution to the hal.dll problem? I have 

/dev/sda1 EFI
/dev/sda2 HFS
/dev/sda4 ext3
/dev/sda3 NTFS

---

### Post by cyberdork33 on 2008-01-31
[http://ubuntuforums.org/showthread.php?t=327386](http://ubuntuforums.org/showthread.php?t=327386)

---

### Post by LiamTreacy on 2008-02-02
Thanks. I assume I should change Partition(3) to Partition(4) in boot.ini. Doesn't seem to work, though. I'm still getting hal.dll error.

The partitions are
/dev/sda1 EFI
/dev/sda2 HFS
/dev/sda4 ext3
/dev/sda3 NTFS

Edit: When set to Partition(2), Windows boots, but stops now at a blue screen, which flashes, then restarts. This looks like the restart loop which happens with almost every XP installation at some time in a computer's lifetime.

---

### Post by LiamTreacy on 2008-02-08
Trying to install XP again but I can't. The installation won't resume after the restart. I just get hal.dll.

Is it possible to reinstall Windows to anything but the last partition? In other words, am I going to have to overwrite the Ubuntu partition with XP, then put XP in Ubuntu's current partition? All help appreciated.

Edit: I also tried disabling rEFIt and reinstalling XP. Again, I can hold down Option to select Windows HD, but the installation will not resume after the restart. The boot.ini has three entries, 2 of which give hal.dll, while the other gives the blue screen.

---

### Post by darkstr2o4 on 2008-02-23
How big should the linux partition be? Will I have access to files on other partitions?

---

### Post by LiamTreacy on 2008-02-29
I think I have this sorted out now by creating both new FAT/NTFS Data partitions, with the "Visible in Windows" option ticked, before installing Windows or Ubuntu. So far Windows has installed properly to the last partition. 

But the bluetooth keyboard won't work in the Ubuntu liveCD. I'm sure I had this working before, but I forget how!? I know it's those Bluez-Utils that are preventing bluetooth from working. I'd use the Alternate CD but that doesn't give an option to install grub anywhere but the MBR.

---

### Post by lex1 on 2008-02-29
how isit possible to see the OSX drive while in windows?

lex1:popcorn:

---

### Post by FerdinandoPucci on 2008-03-08
> **grazie said:**
> EDIT: I should have added that changing the partition numbers in boot.ini from 3 to 2 made Windows bootable and fixed the hal.dll missing problem, but it still doesn't boot to completion. The message I now get after the Windows splash screen is UNMOUNTABLE_BOOT_VOLUME,etc . Booting up in Safe Mode shows that the boot gets as far as loading drivers the last one being agp440.sys. I've not been able to find any solution to this problem.

Hi, I have just bought a macbook and installed windows and kubuntu, in this order. I use rEFIt. Win has the last partition but after linux installed win doesn't boot anymore. I tryed everything guys suggest on the web, fixmbr, chkdsk, edit boot.ini, reinstall, but the best I can get is the UNMOUNTABLE_BOOT_VOLUME error. 

Did you get to fix it? How?

thanks in advance
Ferdinando

---

### Post by elliott69 on 2008-03-08
hi, i am a complete newbie to this. i have followed the guide but i'm having problems partitioning my macintosh hd. when i make the new partition "ubuntu" the disk utility seems to work, but once the process is complete, i cannot see the new partition "ubuntu". however the disk space has been used up. if i try to install ubuntu the only partition i can see is the big macintosh partition and the smaller windows partition .i obviously dont want to install onto the mac partition. please help, i have an imac 24" 2.33ghz 500gb hard drive

---

### Post by fredscripts on 2008-03-08
Hi! I'm trying to triple boot on my macbook too, but I don't know what to do now I have Mac OS and windows XP in order to install Ubuntu, if someone could take a look at the post called " Macbook problem:Cannot use more than 3 partitions?"  on the same page of this oneI'll be very grateful! Thanks!

---

### Post by cyberdork33 on 2008-03-08
disk utility cannot make a partition that Ubuntu can use. 

Bootup the Ubuntu LiveCD and run gparted (System > Administration > Partition Editor). There you should be able to see all the partitions on your disk. Delete the intended Ubuntu partition and create an ext3 partition in it's place, after exiting you can install ubuntu to the ext3 partition. 

You may have to install windows again still unfortunately.

---

### Post by LiamTreacy on 2008-03-09
> **FerdinandoPucci said:**
> Hi, I have just bought a macbook and installed windows and kubuntu, in this order. I use rEFIt. Win has the last partition but after linux installed win doesn't boot anymore. I tryed everything guys suggest on the web, fixmbr, chkdsk, edit boot.ini, reinstall, but the best I can get is the UNMOUNTABLE_BOOT_VOLUME error. 

Did you try creating both new partitions before you installed Windows?

---

### Post by emaildepot on 2008-03-29
Hi there! I'm a newbie.
I have a laptop, and i want to have 3 OS's on it. Vista, Ubuntu and Leopard.
I only have 1 HDD and i want to put them altogether there through partition. Is it possible? 'coz i tried doing Vista and leopard, but stil having no luck at all. :-(

I downloaded the Ubuntu live and will try to it now. 

Here is my laptop specs:

MSI VR320x
Core Duo 2 (T5200)
256 ATI Radeon xpress 200m
120g HDD SATA
ATI® RC410ME + SB450 - chipset
2 GB
13.3" WXGA ACV(Amazing Crystal Vision) Display
SoundBlaster compatible
120GB SATA (5400RPM)
COMBO/DVD Super Multi
Built-in 10/100Mbps Ethernet LAN and Modem Module
Built-in 802.11b/g WLAN Card
USB2.0 Port X 3
Mic-in Port X 1
Line-in Port x 1
Headphone Output X 1
Modem Port X 1
LAN Port X 1
PCI Express Card X 1

---

### Post by cyberdork33 on 2008-03-29
This is a support forum for Apple hardware.

---

### Post by hackersmovie on 2008-03-31
Hello all,

 Just a note and question.

1) Great thread and HOW TO: I tried this method by following it to a "T" on my Macbook 2.0Ghz, 4GB RAM Core2Duo and ran into a few little hiccups.

  a) everything went as planned until I rebooted for the first time after having installed and update each OS. (updated right after installing - note to self,  DON'T DO THAT! install them, then go back and update to save time!) I first booted Windows XPSP2, it came up with an error saying it couldn't boot because of disk errors to reinstall some file, so I booted from the CD, deleted the partition, reinstalled XPSP2, all when well, now when I boot into Windows I have to select which kernel or installation to boot into? weird considering I deleted the partition. No biggie, I only use XP to stream Netflix movies. But, any ideas?

 b) After reinstalling XPSP2, I get the same thin when booting Ubuntu. I have to select the kernel to boot into. In both cases, there are only two, and only the first one will boot, so again no biggie, but, I hate it not just booting right into the OS, is there anyway, besides reinstalling both of them, to remove this "other" kernel or installation?

I had no issues what so ever with my CoreDuo iMac.

Lastly, I've read that the audio should work "out of the box" with Gutsy and I believe Hardy, I've tried both (amd64 alternate CD versions) neither of them did the audio work. And the worst is everything I've tried hasn't worked. I can get everything else working, but with no sound, what's the point?

Sorry for the lengthy post, I digress. . .

---

### Post by cyberdork33 on 2008-04-01
> **hackersmovie said:**
> now when I boot into Windows I have to select which kernel or installation to boot into? weird considering I deleted the partition. No biggie, I only use XP to stream Netflix movies. But, any ideas?are you sure this is not the grub menu? 

 > **hackersmovie said:**
> After reinstalling XPSP2, I get the same thin when booting Ubuntu. I have to select the kernel to boot into. In both cases, there are only two, and only the first one will boot, so again no biggie, but, I hate it not just booting right into the OS, is there anyway, besides reinstalling both of them, to remove this "other" kernel or installation?

Ok, I am sure it is grub now. This is a part of your Ubuntu install. Grub overwrote the Windows bootloader (as is the standard method for most machines). You can use the FIXMBR command on the Windows rescue cd to get windows booting directly, and reinstall grub to the Ubuntu partition rather than the MBR. See the link in my signature about multibooting. It will give full instrcutions to correct that.

As for the request to "skip" the grub menu altogether, I would not suggest do that. If /When you upgrade a kernel and something breaks, you will want to be able to boot from the older kernel (that works) (or maybe into safe mode). Grub (or another bootloader) is REQUIRED to load the linux kernel so you cannot get rid of it. You can however, edit the delay for the grub menu in the configuration file:
/boot/grub/menu.lst

> **hackersmovie said:**
> Lastly, I've read that the audio should work "out of the box" with Gutsy and I believe Hardy, I've tried both (amd64 alternate CD versions) neither of them did the audio work. And the worst is everything I've tried hasn't worked. I can get everything else working, but with no sound, what's the point?i would run alsamixer first to make sure it is not just a muted channel... but the issue is probably fixed via the following:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-6a2f3399bd41e87c39ff69ff7a48a1953db51cdd](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-6a2f3399bd41e87c39ff69ff7a48a1953db51cdd)

---

### Post by hackersmovie on 2008-04-01
> **cyberdork33 said:**
> are you sure this is not the grub menu? 

 

Ok, I am sure it is grub now. This is a part of your Ubuntu install. Grub overwrote the Windows bootloader (as is the standard method for most machines). You can use the FIXMBR command on the Windows rescue cd to get windows booting directly, and reinstall grub to the Ubuntu partition rather than the MBR. See the link in my signature about multibooting. It will give full instrcutions to correct that.

As for the request to "skip" the grub menu altogether, I would not suggest do that. If /When you upgrade a kernel and something breaks, you will want to be able to boot from the older kernel (that works) (or maybe into safe mode). Grub (or another bootloader) is REQUIRED to load the linux kernel so you cannot get rid of it. You can however, edit the delay for the grub menu in the configuration file:
/boot/grub/menu.lst

i would run alsamixer first to make sure it is not just a muted channel... but the issue is probably fixed via the following:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-6a2f3399bd41e87c39ff69ff7a48a1953db51cdd](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-6a2f3399bd41e87c39ff69ff7a48a1953db51cdd)

One question, When I was dual booting I would see 

```
GRUB Loading. . . .

Please wait. . . .
```
Or something like that, now I still see but, only after selecting the kernel to boot in both windows and Ubuntu. If I select, say the second "Windows XP Professional" in the text menu when booting, I'll get the XP Loading screen but, it will fail to boot. I'm only asking to be sure it is in fact a "GRUB" deal because I told Ubuntu to install GRUB on the same partition as Ubuntu (dev/sda3) hoping to elude this issue. . . .

---

### Post by cyberdork33 on 2008-04-01
> **hackersmovie said:**
> One question, When I was dual booting I would see 

```
GRUB Loading. . . .

Please wait. . . .
```Or something like that, now I still see but, only after selecting the kernel to boot in both windows and Ubuntu. If I select, say the second "Windows XP Professional" in the text menu when booting, I'll get the XP Loading screen but, it will fail to boot. I'm only asking to be sure it is in fact a "GRUB" deal because I told Ubuntu to install GRUB on the same partition as Ubuntu (dev/sda3) hoping to elude this issue. . . .
That indeed sounds odd. Try just doing the FIXMBR command from the windows cd. That should overwrite any install of grub in the MBR and make sure that the Windows loader is there. if you still have an issue, it might be the windows bootlaoder giving the issue and you will have to modify the boot.ini file to remove additional entries (that don't work).

---

### Post by hackersmovie on 2008-04-02
This is a few PM's between Cyberdork33 and myself, we felt it would benefit others! Enjoy!


[B]Cyberdork33,

Thank you for your help and insight! I'm not quite sure I explained in the thread the "issue". So here's what I've done.

Cleanly installed OS X Leopard (did the 10.5.2 update)
Used BootCamp to partition my hard drive
Installed rEFIt
Installed Windows XP SP2 (installed Apple's drivers via OS X disc, updated Windows, etc.)
Back in OS X, used Disk Utility to repartition my OS X partition to make room for Ubuntu
Booted from Ubuntu disc
Installed Ubuntu on the newly created partition (used the Alternate CD amd 64 version)
Told GRUB to install on dev/sda3 (my ext3 partition, mount point /, NO SWAP Partition at all)
went back to OS X, from Terminal re "blessed" the rEFIt folder (don't know why but, I had to do this every time)
restarted, see the rEFIt menu. . . all would seem o.k. -

from rEFIt, if I select Linux it begins to boot but then shows a text screen prompting me to select from one of these:
```
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-gerneric (recovery mode)
Ubuntu 7.10, memtest86+
Other operating systems:
Microsoft Windows XP Professional
```
I select the first one and it boots right into Ubuntu, no isses. This never showed when I was only dual booting .. . 

Now Windows I see this when selected from the rEFIt menu:
```
Please select the operating system to start:

Microsoft Windows XP Professional
Microsoft Windows XP Professional

Use the up and down arrow keys to move the highlight to your choice.
Press ENTER to choose.
```
Only the first one will boot, if I choose the second one, it says there is a file missing and I should reinstall it from the XP CD. Again, I never saw this when only dual booting.

What did I do wrong? It all works, just not the way I think it's suppose to. Or is it?

Thanks so much,

-Hackersmovie




His response:

When you choose "Linux" from rEFIt, you will get the grub screen where you can select what kernel to load. This is completely normal and is part of Ubuntu. You can edit the "delay" that used before the default is booted by editting the parameter in the menu.lst file. Check it out, it is not too hard to figure out what to edit. You can also remove the windows entry from this list as it is not needed here.
```
sudo gedit /boot/grub/menu.lst
```
The screen you see when selecting windows is the windows bootloader. It seems to have added a second entry because you changed the partition layout after you had already installed windows. You can remove the non-working item from the list by:
Right Click on My Computer and select properties. Go to the advanced tab and click the button that says "Settings" under "Startup and Recovery".

Here there are options for selecting how long the menu is shown, and you can click the Edit button and remove the "bad" line from the file under "[operating systems]" then it should not show the menu at all.

I hope this helps. [/B]


It did! Perfectly! Thanks so much! BTW, I reduced the delay in GRUB to 2 seconds, and deleted the "Windows" entry, saved, exited, rebooted, all is well. In Windows, did exactly as you stated, it boots straight to Windows now! Most excellent! Thanks once again, greatly appreciated!

---

### Post by cyberdork33 on 2008-04-02
> **hackersmovie said:**
> It did! Perfectly! Thanks so much! BTW, I reduced the delay in GRUB to 2 seconds, Excellent.

Grub also has a "Hidden Menu" option that will just show a message about hitting ESC to show the menu for a couple of seconds instead of showing the kernel chooser, but it really won't save you any time either way.

---

### Post by lat2005 on 2008-04-19
Success!
I used the directions on the first page and succeeded in installing Leopard,Ubuntu, and WinXP.
Reinstalling OS X was my first step since my parititions were messed up from an earlier attempt.
I let my OSX partition be quite large to be able to hold Ubuntu (I made it 120GB so that I have 60GB for OS X and 60GB for Ubuntu.
I tried other tutorials out there and they all failed.
I have a new March 2008 Macbook Pro.

My windows did fail after installing ubuntu, it gave me a blue screen that I guess is the UNMOUNTABLE BOOT VOLUME error(something like that), kinda hard to see since it automatically restarted.

In the Ubuntu installation I used /dev/sda3  like the tutorial said and I had no problems. This I think was something I was missing in all the other walkthroughts.

Because of this I simply reinstalled windows. It added another windows to the boot list( there are 2 win xp, this is the boot list you get after selecting windows in reFIT.
This is easily eliminated by editing the boot.ini in any way(editing the file or using windows).

All OSes work, although I have to take care of the drivers and make sure the swap file works.


Thanks a lot to everybody and especially to the guy who posted this thread.

---

### Post by dmlc133 on 2008-05-16
thanks for the tips here.

one thing I found when following the first post was that for some reason I can't persuade disk utility to make partitions smaller than 30GB which is more than I want for either XP or Ubuntu. I haven't found any reference to this issue on the web so maybe I'm missing something.

---

### Post by cyberdork33 on 2008-05-16
> **dmlc133 said:**
> thanks for the tips here.

one thing I found when following the first post was that for some reason I can't persuade disk utility to make partitions smaller than 30GB which is more than I want for either XP or Ubuntu. I haven't found any reference to this issue on the web so maybe I'm missing something.
I would suggest just making one large new partition for both Ubuntu and XP, then you can boot the Ubuntu Live CD and use gparted to delete it (leaving free space) and create your Windows and Ubuntu root/swap partitions in the free space. THe critical part is reducing the size of your OSX partition  without harming it.

If you need further advice, I would suggest posting the new Apple forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by dmlc133 on 2008-05-18
Actually I figured it out - I had to resize the Mac HD partition first to leave the amount of free space I wanted for Ubuntu, then create a new partition, which filled this space with a new ext3 partition.

When I tried splitting the bootcamp partition at the point of installing Windows it didn't work - that is I could split the partition but once Windows was installed it wouldn't boot that partition, giving an error about hal.dll being missing or corrupt which usually means a problem with the mbr.

---

### Post by cyberdork33 on 2008-05-18
> **dmlc133 said:**
> When I tried splitting the bootcamp partition at the point of installing Windows it didn't work - that is I could split the partition but once Windows was installed it wouldn't boot that partition, giving an error about hal.dll being missing or corrupt which usually means a problem with the mbr.
yea windows doesn't like it if you change the partitions up after installing.

---

### Post by dmlc133 on 2008-05-19
I was having a problem if I split the partition using the Windows CD partitioner before Windows was installed.

Anyway it's all working now, really helpful how to and advice on this thread, thanks.

Only think now is that scrolling on the mighty mouse doesn't seem to be working, so I'm having a fiddle with that.

---

### Post by cyberdork33 on 2008-05-19
> **dmlc133 said:**
> Only think now is that scrolling on the mighty mouse doesn't seem to be working, so I'm having a fiddle with that.

There is a discussion on that in the new Apple Forum here:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

Discussion should be carried there.

---

### Post by BlackRaven on 2008-05-20
Thank you **violajack** for the guide!! 
It's been a big help.  I've tried many guides out there and could never get it any of them to work.  Tried your guide and got it to work the first try.

Thanks for sharing! :)

---

