---
title: "A Picky Beginner (Lots of questions)"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by GepettoBR on 2007-09-18
This is probably going to be a very annoying post to whoever decides to answer, but I've heard nothing but compliments about the Ubuntu community so let's go for it.


I am a complete Linux newbie. I've been a Windows user ever since I first saw a computer. I have used every MS Windows home desktop distro since Windows 3.x, but nothing else, which means my CLI experience sums up to typing "c:/win" to boot the OS before Win95 came out. Having used Windows for so long, one does get tired of the BSOD and the increasing demand for resources with every new release (which you *have* to buy or the new versions of your software won't run). What do I do, then? I look for alternatives. Since around May this year I've been testing a few LiveCD distros and Googling alternatives to the software I use in Windows (except for OpenOffice, Firefox and Thunderbird, which I've already been using for quite a while).


I do a lot of video editing on my computer and Linux suffers from a terrible lack of good NLEs. For that reason, I can't fuly abandon Windows. Currently I have a Compaq Evo N1020 Laptop, but by the end of the year I"ll have moved to a bigger place and be able to actually have a tower PC.


So, to sum up all the unnecessary crap I wrote above, I'll be buying a fresh new computer, with a 400GB SATA HD and at least 2GB of RAM, and I intend to use Intel Core 2 Duo, but said computer doesn't exist yet, so hardware compatibility can be adressed. I plan to dual-boot Windows XP and Kubuntu 7.10 - this will be my first ever use of a non-LiveCD Linux distro.


With that in mind, here are my questions:

1)Which OS should I install first? Should I partition before or after installing the first OS, and in my specific case what would be the best tool to do it? I've found that there are quite a few.

2)How much space would each OS need for a partition, if I intend to keep my personal files on a third partition? This assuming that it's best to do so - if not, ignore this question.

3)Is there a stable and secure workaround to using a FAT32 partition for my files? the 4GB file limit is not an option when you work with uncompressed video (I've had under-five-minute segments mount up to 7-8 GB), and having to divide the whole thing into 32GB partitions because Windows is dumb with FAT32 doesn't help either. I need both Windows and Linux to safely write to my document partition, since I'll be using Premiere and VirtualDubMod under Windows to edit the video, but MEncoder under Linux to compress it (I expect the lighter OS to speed up the encoding process quite a bit, due to the extra free RAM and CPU cycles).

4)Since I enjoy the occasional gaming, I'd like my video card to be an nVidia GeForce series, which works great with DirectX, but I've heard there are problems with nVidia+Ubuntu+openGL. What are they?

5)I'm going with KDE but I don't want to rule out GNOME. Is it better to go ahead and install Ubuntu on a separate partition and triple-boot, or to just install the ubuntu-desktop package on Kubuntu when I feel like it? Or even, would it be better to install Ubuntu with the kubuntu-desktop package, and no Kubuntu at all?

6) I read on [this site (link)]("http://www.psychocats.net/ubuntu/") that it would be better to create separate partitions for certain directories, like /home, /boot and /usr. Knowing nothing about how the Linux filesystem works, how I'd have Kubuntu point to said partitions instead of creating the directories in the / partition and ignoring them, OR about resizing partitions if I ever need to do so, I'm just absolutely clueless about how I should distribute my partitions. Luckilly for me, 400GB is no small hard drive. Also on this subject, what the hell is a swap partition, why do I need it and how big should it be?


I know I'm demanding quite a lot, and there's probably a lot of unnecessary information up there, but it's better to sin for excess of information than lack of it. While I currently don't know anything about setting up Linux or using the CLI, I'll learn if I have to - if I intended to whine and bitch about stuff being hard, I'd have stayed with Windows or bought a Mac. I want to do this the best way possible, regardless of the learning curve (but please hold back on the jargon, I'm Linux-illiterate).

Once again, sorry for the trouble and thanks in advance to all those who answer.

---

### Post by eljoeb on 2007-09-18
> **GepettoBR said:**
> This is probably going to be a very annoying post to whoever decides to answer, but I've heard nothing but compliments about the Ubuntu community so let's go for it.


I am a complete Linux newbie. I've been a Windows user ever since I first saw a computer. I have used every MS Windows home desktop distro since Windows 3.x, but nothing else, which means my CLI experience sums up to typing "c:/win" to boot the OS before Win95 came out. Having used Windows for so long, one does get tired of the BSOD and the increasing demand for resources with every new release (which you *have* to buy or the new versions of your software won't run). What do I do, then? I look for alternatives. Since around May this year I've been testing a few LiveCD distros and Googling alternatives to the software I use in Windows (except for OpenOffice, Firefox and Thunderbird, which I've already been using for quite a while).


I do a lot of video editing on my computer and Linux suffers from a terrible lack of good NLEs. For that reason, I can't fuly abandon Windows. Currently I have a Compaq Evo N1020 Laptop, but by the end of the year I"ll have moved to a bigger place and be able to actually have a tower PC.


So, to sum up all the unnecessary crap I wrote above, I'll be buying a fresh new computer, with a 400GB SATA HD and at least 2GB of RAM, and I intend to use Intel Core 2 Duo, but said computer doesn't exist yet, so hardware compatibility can be adressed. I plan to dual-boot Windows XP and Kubuntu 7.10 - this will be my first ever use of a non-LiveCD Linux distro.


With that in mind, here are my questions:

1)Which OS should I install first? Should I partition before or after installing the first OS, and in my specific case what would be the best tool to do it? I've found that there are quite a few.

2)How much space would each OS need for a partition, if I intend to keep my personal files on a third partition? This assuming that it's best to do so - if not, ignore this question.

3)Is there a stable and secure workaround to using a FAT32 partition for my files? the 4GB file limit is not an option when you work with uncompressed video (I've had under-five-minute segments mount up to 7-8 GB), and having to divide the whole thing into 32GB partitions because Windows is dumb with FAT32 doesn't help either. I need both Windows and Linux to safely write to my document partition, since I'll be using Premiere and VirtualDubMod under Windows to edit the video, but MEncoder under Linux to compress it (I expect the lighter OS to speed up the encoding process quite a bit, due to the extra free RAM and CPU cycles).

4)Since I enjoy the occasional gaming, I'd like my video card to be an nVidia GeForce series, which works great with DirectX, but I've heard there are problems with nVidia+Ubuntu+openGL. What are they?

5)I'm going with KDE but I don't want to rule out GNOME. Is it better to go ahead and install Ubuntu on a separate partition and triple-boot, or to just install the ubuntu-desktop package on Kubuntu when I feel like it? Or even, would it be better to install Ubuntu with the kubuntu-desktop package, and no Kubuntu at all?

6) I read on [this site (link)]("http://www.psychocats.net/ubuntu/") that it would be better to create separate partitions for certain directories, like /home, /boot and /usr. Knowing nothing about how the Linux filesystem works, how I'd have Kubuntu point to said partitions instead of creating the directories in the / partition and ignoring them, OR about resizing partitions if I ever need to do so, I'm just absolutely clueless about how I should distribute my partitions. Luckilly for me, 400GB is no small hard drive. Also on this subject, what the hell is a swap partition, why do I need it and how big should it be?


I know I'm demanding quite a lot, and there's probably a lot of unnecessary information up there, but it's better to sin for excess of information than lack of it. While I currently don't know anything about setting up Linux or using the CLI, I'll learn if I have to - if I intended to whine and bitch about stuff being hard, I'd have stayed with Windows or bought a Mac. I want to do this the best way possible, regardless of the learning curve (but please hold back on the jargon, I'm Linux-illiterate).

Once again, sorry for the trouble and thanks in advance to all those who answer.

Hi

As for what you heard about the community, they lied.  Now for questions.

1. Install Windows XP first.  It won't play nice if you do it second.
2. Not really necessary.  There are tools (ntfs-config) that let you see Windows partitions and vice versa.
3. NTFS works in Linux, but I had problems with it on external drives.  Mess with the files on the Windows partition and you shouldn't have a problem.
4. Games on Linux = Less fun.  Unless you like the idea of canoodling your settings for hours to run a game, I recommend passing and allocating more space to windows for games.  I had problems with my NVidia card, but nothing earth shattering.  ATI has the problematic drivers on Linux.
5. I would say don't triple boot.  You can install the Ubuntu desktop any time.  Just keep in mind that startup will take longer when they (GNOME and KDE) coexist.  They're like cats and dogs, I tell ya.
6. The swap partition can be automatically handled by the installer.  I had no problems with it and I have less real estate than you.

---

### Post by irish_flu on 2007-09-18
> **GepettoBR said:**
> 
1)Which OS should I install first? Should I partition before or after installing the first OS, and in my specific case what would be the best tool to do it? I've found that there are quite a few.

Windows.  The Windows Boot loader can be a little snarky if it's added second.
> 
2)How much space would each OS need for a partition, if I intend to keep my personal files on a third partition? This assuming that it's best to do so - if not, ignore this question.

It depends on how much RAM you have (because both OS will have a larger memory "swap" when you have more RAM) but since it's a new machine and Hard Drives are cheap, I'd say give both as much as you can.  Maybe 12 GB (minimum) each, if you want to keep your stuff somewhere else?  Keep in mind that a few games will eat that up fast.
> 
3)Is there a stable and secure workaround to using a FAT32 partition for my files? the 4GB file limit is not an option when you work with uncompressed video (I've had under-five-minute segments mount up to 7-8 GB), and having to divide the whole thing into 32GB partitions because Windows is dumb with FAT32 doesn't help either. I need both Windows and Linux to safely write to my document partition, since I'll be using Premiere and VirtualDubMod under Windows to edit the video, but MEncoder under Linux to compress it (I expect the lighter OS to speed up the encoding process quite a bit, due to the extra free RAM and CPU cycles).

Linux can easily *read* an NTFS partition, and there is (somewhat less robust) a driver to write NTFS as well.  There are also ext drivers for Windows, but I've never used them and don't know if they're any good.
> 
4)Since I enjoy the occasional gaming, I'd like my video card to be an nVidia GeForce series, which works great with DirectX, but I've heard there are problems with nVidia+Ubuntu+openGL. What are they?

IMHO Nvidia is by far the best choice for use with Ubuntu, as far as drivers go.
> 
5)I'm going with KDE but I don't want to rule out GNOME. Is it better to go ahead and install Ubuntu on a separate partition and triple-boot, or to just install the ubuntu-desktop package on Kubuntu when I feel like it? Or even, would it be better to install Ubuntu with the kubuntu-desktop package, and no Kubuntu at all?

Options two or three are equally awesome.  Run whichever one you want, and install the other package when you feel like it.  You'll be able to choose between KDE and Gnome at startup, after you have both "desktop" packages.
> 
6) I read on [this site (link)]("http://www.psychocats.net/ubuntu/") that it would be better to create separate partitions for certain directories, like /home, /boot and /usr. Knowing nothing about how the Linux filesystem works, how I'd have Kubuntu point to said partitions instead of creating the directories in the / partition and ignoring them, OR about resizing partitions if I ever need to do so, I'm just absolutely clueless about how I should distribute my partitions. Luckilly for me, 400GB is no small hard drive. Also on this subject, what the hell is a swap partition, why do I need it and how big should it be?

The Installer will help you with those partitions.
"Swap" is the same thing as in Windows; your RAM uses it to put stuff it's not currently using, or doesn't have enough room for.  IMHO it's best to let the installer pick the size (the best size depends on the amount of RAM you have).
[/QUOTE]
I know I'm demanding quite a lot, and there's probably a lot of unnecessary information up there, but it's better to sin for excess of information than lack of it. While I currently don't know anything about setting up Linux or using the CLI, I'll learn if I have to - if I intended to whine and bitch about stuff being hard, I'd have stayed with Windows or bought a Mac. I want to do this the best way possible, regardless of the learning curve (but please hold back on the jargon, I'm Linux-illiterate).

Once again, sorry for the trouble and thanks in advance to all those who answer.[/QUOTE]

Don't worry about it buddy, knowledge is power!  If anything I said confuses you, please tell me.  I'm sure others will chime in with opinions as well.

Good luck, and remember that we're here to help each other; if you get frustrated, ask here before you chuck your nice new PC out the Window!

---

### Post by GepettoBR on 2007-09-18
Wow, that was quick! Two great replies in record time!

Thanks a lot, you've cleared up everything but item 3. Is there really no 100% secure way to have a partition that both Windws and Kubuntu can write to? If not, and I have to tweak something around with a margin of insecurity, would it be better to make Linux write to an NTFS partition, or to make Windows write to an Ext3 partition? (and by "better", I mean "less likely to crash my HD and/or corrupt my data and/or hump my CPU")

A bucket full of thanks to both of you. They didn't lie. :D

---

### Post by rsambuca on 2007-09-18
I would partition the drives PRIOR to installing anything.  This way, you don't have to worry about the partitioner borking any of your systems.  Definitely install XP first, and on the first partition of the drive.

I would allocate 20GB for each (overkill, but you have tons of space).  Your swap will probably never be used by ubuntu if you have 2GB Ram, so 1 or 2GB is more than enough.  Ubuntu is much more efficient than XP at utilizing system resources.

I recommend putting the remainder of your drive as ext3 for common storage.  The [drivers]("http://www.fs-driver.org/") for Windows work very well.  You could just use ntfs if you really wanted to and use the ntfs-3g driver for Ubuntu, but NTFS is not nearly as good a filesystem.

You can use either method for trying both ubuntu and kubuntu.  I personally prefer separate partitions because other your menus get a little cluttered with all of the kde apps and gnome apps mixed together, but it doesn't affect anything.

---

### Post by prabbit237 on 2007-09-18
Just a few notes of my own.

> **eljoeb said:**
> Hi

As for what you heard about the community, they lied.  Now for questions.

1. Install Windows XP first.  It won't play nice if you do it second.

Agreed. Ubuntu will install grub for a bootloader that will see windows fine and add it to the list. But if you install windows AFTER grub, you'll kill grub.

> 2. Not really necessary.  There are tools (ntfs-config) that let you see Windows partitions and vice versa.

See [http://www.fs-driver.org/](http://www.fs-driver.org/) for drivers for windows to allow it to see ext2 partitions.

See [http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/) or [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/) for mounting windows drives in ubuntu.

> 6. The swap partition can be automatically handled by the installer.  I had no problems with it and I have less real estate than you.

If you have 2 gigs of ram, swap space is probably a wast of time. But if you really want it, I'd use maybe 2 gigs max.

---

### Post by rsambuca on 2007-09-18
> **GepettoBR said:**
> Wow, that was quick! Two great replies in record time!

Thanks a lot, you've cleared up everything but item 3. Is there really no 100% secure way to have a partition that both Windws and Kubuntu can write to? If not, and I have to tweak something around with a margin of insecurity, would it be better to make Linux write to an NTFS partition, or to make Windows write to an Ext3 partition? (and by "better", I mean "less likely to crash my HD and/or corrupt my data and/or hump my CPU")

A bucket full of thanks to both of you. They didn't lie. :D

I am not sure what you mean by 100% secure, but both the IFS driver for windows and the ntfs-3g driver for linux are considered stable.  I have certainly never had a problem.

Also, regarding the nvidia question, certainly the current situation is that nvidia is easier to use with linux, although not perfect.  That may change in the future, however, as new owner AMD has just announced last week regarding opensource initiatives for its videocard drivers.  Time will tell, I guess.

---

### Post by GepettoBR on 2007-09-19
> **irish_flu said:**
> Maybe 12 GB (minimum) each, if you want to keep your stuff somewhere else?  Keep in mind that a few games will eat that up fast.

> **rsambuca said:**
> I recommend putting the remainder of your drive as ext3 for common storage.  The [drivers]("http://www.fs-driver.org/") for Windows work very well.  You could just use ntfs if you really wanted to and use the ntfs-3g driver for Ubuntu, but NTFS is not nearly as good a filesystem.

If I installed the fs-drivers on Windows and installed the games in an Ext3 partition, they should run, right?

Also, the site [www.fs-driver.org](www.fs-driver.org) says that the driver is for Ext2, but also works with Ext3. It explains that the difference is "journaling" but I didn't really understand that part. In practice, what's the difference?

If both methods (NTFS in Linux and Ext3 in Windows) are deemed equally secure and NTFS is a proprietary filesystem which the ntfs-3g developers had restricted access to, then the Windows driver is the safest bet, no?

Finally, what software do you reccomend for partitioning my HD before installing Windows?

Another question combo o.o
Thanks again for all your replies! This is actually turning out a lot simpler than I first assumed :guitar:

Edit: Forgot to ask two more things. If I install Beryl or Compiz-Fusion, will Kubuntu still run faster than Windows XP (asuming a reasonable level of eye-candy) and if compatibility issues with my Windows video software ever leads me in to buying the dreaded resource-eating Vista (God forbid), will there be problems if I install it over Windows XP or to a separate location (since there will already be a different non-Microsoft OS on the system) ?

---

### Post by anemptygun on 2007-09-19
I would type up my list of recommendations... but, since it would be exactly what everyone else said this is what I will say.

I agree. :P

---

### Post by bobbocanfly on 2007-09-19
For partitioning prior to installing Windows, download the GParted live CD which will let you create your partitions very easily.

its a much better idea to use your free space as EXT3 as those Windows driver devs have unlimited access to the filesystem code etc. so can therefor make changes easier, unlike NTFs which they have to reverse engineer.

---

### Post by Duck2006 on 2007-09-19
Take a look at this it may help

[http://video.google.com/videoplay?docid=-6104490811311898236&q=label%3Aubuntu+linux+%2F+windows+dual+boot+instructional+vid](http://video.google.com/videoplay?docid=-6104490811311898236&q=label%3Aubuntu+linux+%2F+windows+dual+boot+instructional+vid)

---

### Post by newlinux on 2007-09-19
I second the FS-driver. That's what I used for my XP/Ubuntu dual boot machine. I also have kubuntu-desktop installed ontop of my ubuntu install, and it works fine. Some setting changes in one environment will affect the other one, but it works fine. I try to use both just to keep up on both KDE and Gnome.

In practice for OS use there isn't much of a difference between a journaling and a non journaling filesystem. A Journaling filesystem makes a drive a little more crash friendly. When you enable journaling on a disk, a continuous record of changes to files on the disk is maintained in the journal. If your computer stops because of a power failure or something, the journal is used to restore the disk to a known-good state when the server restarts. I have no idea how this affects fs-driver's interaction. I would guess it doesn't take advantage of the journaling.

I think Kubuntu/Ubuntu with compiz will still be faster. I rarely use compiz so I can't say for sure.

I think a problem you might have installing Vista is that it will probably destroy grub (The ubuntu boot loader), meaning you won't be able to boot to the other OS's. But you could restore that with the Ubuntu live disc. This is why all have recommended you install windows first. It doesn't play nice.

---

### Post by mysticmatrix on 2007-09-19
> **GepettoBR said:**
> 
Edit: Forgot to ask two more things. If I install Beryl or Compiz-Fusion, will Kubuntu still run faster than Windows XP (asuming a reasonable level of eye-candy) and if compatibility issues with my Windows video software ever leads me in to buying the dreaded resource-eating Vista (God forbid), will there be problems if I install it over Windows XP or to a separate location (since there will already be a different non-Microsoft OS on the system) ?

Hehe... Well good thing with Ubuntu is system never slows, no matter what amount of software you install. Linux software, unlike their windows counterpart, don't run crappy "services"/"background processes" which tends to slow down the system. More over, a software usually maintains its own setting, and without "Dll Hell" and a pathetic registry system, all software typically act independent of each other.

Coming back to Compiz-Fusion, it runs usually out of box when you have correct Nvidia drivers installed. The number of cards supported out of box usually are those that are released before release of particular version of Ubuntu. Therfore all cards of 7 series and below as well as 8800GTX is supported out of box. 
For other cards, you may either wait for Gutsy(includes support for all cards releases till September), or try Envy, a software that installs the latest Nvidia drivers for you automatically.
Also, performance of your card really matter how much fluidity you'll get. Compiz uses much less system resources than Vista crap. For e.g my Intel IGP gives me about 150 FPS with 2% CPU usage. You can find benchmarks for various cards here. [http://www.phoronix.com/scan.php?page=article&item=730&num=1](http://www.phoronix.com/scan.php?page=article&item=730&num=1)
The article is for Beryl, but Compiz Fusion, it's successor is almost 20% less intensive than Beryl in system resources. 

Now comparing with Vista, I have personally never used it but have heard that it requires atleast Shader Model 2, Geforece 6 series and above, while Beryl runs on even i845 IGP :guitar:

EDIT: By out of box, I meant that you have to perform three clicks to install correct drivers for your system after you have installed Ubuntu.

---

### Post by GepettoBR on 2007-09-19
> **newlinux said:**
> I think a problem you might have installing Vista is that it will probably destroy grub (The ubuntu boot loader), meaning you won't be able to boot to the other OS's. But you could restore that with the Ubuntu live disc. This is why all have recommended you install windows first. It doesn't play nice.

Is there another boot manager I could install that wouldn't have that problem?

I read somewhere that since partitions correspond to actual physical "pie slices" of the hard drive, the order in which I create them makes a big difference (I can't add space to the beginning of a partition, but can to the end - or something like that), so in what order should I create the partitions?

---

### Post by mysticmatrix on 2007-09-19
> **GepettoBR said:**
> Is there another boot manager I could install that wouldn't have that problem?

I read somewhere that since partitions correspond to actual physical "pie slices" of the hard drive, the order in which I create them makes a big difference (I can't add space to the beginning of a partition, but can to the end - or something like that), so in what order should I create the partitions?

Vista doesn't like any other OS. That's it. Use any boot manager, and reinstall of XP/Vista would kill it, As simple as that.

Also, partitions do correspond to Physical pie chart, but with Spin rates well above 7200 RPM(that means your drive spins 120 times a second, insane speed indeed), it matters very little now how you partition.

---

### Post by dondad on 2007-09-19
> **GepettoBR said:**
> This is probably going to be a very annoying post to whoever decides to answer, but I've heard nothing but compliments about the Ubuntu community so let's go for it.


I am a complete Linux newbie. I've been a Windows user ever since I first saw a computer. I have used every MS Windows home desktop distro since Windows 3.x, but nothing else, which means my CLI experience sums up to typing "c:/win" to boot the OS before Win95 came out. Having used Windows for so long, one does get tired of the BSOD and the increasing demand for resources with every new release (which you *have* to buy or the new versions of your software won't run). What do I do, then? I look for alternatives. Since around May this year I've been testing a few LiveCD distros and Googling alternatives to the software I use in Windows (except for OpenOffice, Firefox and Thunderbird, which I've already been using for quite a while).


I do a lot of video editing on my computer and Linux suffers from a terrible lack of good NLEs. For that reason, I can't fuly abandon Windows. Currently I have a Compaq Evo N1020 Laptop, but by the end of the year I"ll have moved to a bigger place and be able to actually have a tower PC.


So, to sum up all the unnecessary crap I wrote above, I'll be buying a fresh new computer, with a 400GB SATA HD and at least 2GB of RAM, and I intend to use Intel Core 2 Duo, but said computer doesn't exist yet, so hardware compatibility can be adressed. I plan to dual-boot Windows XP and Kubuntu 7.10 - this will be my first ever use of a non-LiveCD Linux distro.


With that in mind, here are my questions:

1)Which OS should I install first? Should I partition before or after installing the first OS, and in my specific case what would be the best tool to do it? I've found that there are quite a few.

2)How much space would each OS need for a partition, if I intend to keep my personal files on a third partition? This assuming that it's best to do so - if not, ignore this question.

3)Is there a stable and secure workaround to using a FAT32 partition for my files? the 4GB file limit is not an option when you work with uncompressed video (I've had under-five-minute segments mount up to 7-8 GB), and having to divide the whole thing into 32GB partitions because Windows is dumb with FAT32 doesn't help either. I need both Windows and Linux to safely write to my document partition, since I'll be using Premiere and VirtualDubMod under Windows to edit the video, but MEncoder under Linux to compress it (I expect the lighter OS to speed up the encoding process quite a bit, due to the extra free RAM and CPU cycles).

4)Since I enjoy the occasional gaming, I'd like my video card to be an nVidia GeForce series, which works great with DirectX, but I've heard there are problems with nVidia+Ubuntu+openGL. What are they?

5)I'm going with KDE but I don't want to rule out GNOME. Is it better to go ahead and install Ubuntu on a separate partition and triple-boot, or to just install the ubuntu-desktop package on Kubuntu when I feel like it? Or even, would it be better to install Ubuntu with the kubuntu-desktop package, and no Kubuntu at all?

6) I read on [this site (link)]("http://www.psychocats.net/ubuntu/") that it would be better to create separate partitions for certain directories, like /home, /boot and /usr. Knowing nothing about how the Linux filesystem works, how I'd have Kubuntu point to said partitions instead of creating the directories in the / partition and ignoring them, OR about resizing partitions if I ever need to do so, I'm just absolutely clueless about how I should distribute my partitions. Luckilly for me, 400GB is no small hard drive. Also on this subject, what the hell is a swap partition, why do I need it and how big should it be?


I know I'm demanding quite a lot, and there's probably a lot of unnecessary information up there, but it's better to sin for excess of information than lack of it. While I currently don't know anything about setting up Linux or using the CLI, I'll learn if I have to - if I intended to whine and bitch about stuff being hard, I'd have stayed with Windows or bought a Mac. I want to do this the best way possible, regardless of the learning curve (but please hold back on the jargon, I'm Linux-illiterate).

Once again, sorry for the trouble and thanks in advance to all those who answer.

The other questions have all been answered, but for number 6, when you do the install, it will give you the option of what to do with each partition. You can select which one will be the root, which one for /home, and the swap partition. It is best to have the /home especially in a separate partition because if (when, if you like to tinker ;-))you break your system while learning what to do and not do, you can reinstall without touching your personal files.

Also, since you haven't bought or built the system yet, I would add a second hard drive (since they are cheap these days), put Windows on one, and linux on the other. In linux, you can mount any partition anywhere you like, so it will be totally transparent that it is a second drive.

---

### Post by GepettoBR on 2007-09-19
> **mysticmatrix said:**
> Vista doesn't like any other OS. That's it. Use any boot manager, and reinstall of XP/Vista would kill it, As simple as that.

Also, partitions do correspond to Physical pie chart, but with Spin rates well above 7200 RPM(that means your drive spins 120 times a second, insane speed indeed), it matters very little now how you partition.
So I can partition in any order, like Swap>Windows>Ubuntu>Files or Ubuntu>Files>Swap>Windows or any other one of the 24 variations of four partitions? 

> **dondad said:**
> It is best to have the /home especially in a separate partition because if (when, if you like to tinker ;-))you break your system while learning what to do and not do, you can reinstall without touching your personal files.
Oh, so the /home directory is for my personal files? In that case, wouldn't mine be the same as the larger partition that I want both Windows and Linux to access? If so, then Ext3 is surely the way to go. If not, what exactly is /home for, and around how big should I make it?

> **dondad said:**
> Also, since you haven't bought or built the system yet, I would add a second hard drive (since they are cheap these days), put Windows on one, and linux on the other. In linux, you can mount any partition anywhere you like, so it will be totally transparent that it is a second drive.
Actually, the reason I'm dishing out for a 400GB hard drive is that in Brazil right now, due to all those boring market numbers and statistics, larger hard drives are cheaper and smaller hard drives are more expensive (I can get about 1.3GB per R$1 on a larger drive, but only 0.7GB per R$1 on a smaller one). I don't have the cash to buy two 400GB HDs, and to buy a smaller one isn't (to use one of my least favourite terms in the English language) feasable. I'll keep your suggestion in mind, though, since the prices will come down eventually.


I keep remembering new things to ask :oops: Do Ext3 partitions require defragging as much as NTFS or (God no) FAT32 partitions do? If so, Kubuntu must come with a tool (or a Terminal/Konsole command) that does that, right? Or should I use the Windows Disk Defragmenter after I've installed the FS-driver?

---

### Post by rsambuca on 2007-09-19
> **GepettoBR said:**
> So I can partition in any order, like Swap>Windows>Ubuntu>Files or Ubuntu>Files>Swap>Windows or any other one of the 24 variations of four partitions? 


Oh, so the /home directory is for my personal files? In that case, wouldn't mine be the same as the larger partition that I want both Windows and Linux to access? If so, then Ext3 is surely the way to go. If not, what exactly is /home for, and around how big should I make it?


Actually, the reason I'm dishing out for a 400GB hard drive is that in Brazil right now, due to all those boring market numbers and statistics, larger hard drives are cheaper and smaller hard drives are more expensive (I can get about 1.3GB per R$1 on a larger drive, but only 0.7GB per R$1 on a smaller one). I don't have the cash to buy two 400GB HDs, and to buy a smaller one isn't (to use one of my least favourite terms in the English language) feasable. I'll keep your suggestion in mind, though, since the prices will come down eventually.


I keep remembering new things to ask :oops: Do Ext3 partitions require defragging as much as NTFS or (God no) FAT32 partitions do? If so, Kubuntu must come with a tool (or a Terminal/Konsole command) that does that, right? Or should I use the Windows Disk Defragmenter after I've installed the FS-driver?

Windows does best on the first partition, so I would go Windows-Ubuntu-Files-Swap

Yes, /home is kinda like the My Documents folder from Windows.

Ext3 does not require any defragmenting.  It doesn't try to squeeze everything into one section of the drive, so it spaces the files out and it automatically gets defragged just by using it.

---

### Post by timzak on 2007-09-19
Not that you'll need to conserve space with 400 gigs, but I have found on my system with 1 gig of ram that my swap partition never gets touched.  I have it sized to 500 MB (way smaller than what the installer suggested).

Even on an older computer with only 256 MB of ram, I've never seen the swap partition get filled more than 50 MB.

Good luck!

---

### Post by dondad on 2007-09-19
> **GepettoBR said:**
> So I can partition in any order, like Swap>Windows>Ubuntu>Files or Ubuntu>Files>Swap>Windows or any other one of the 24 variations of four partitions? 


Oh, so the /home directory is for my personal files? In that case, wouldn't mine be the same as the larger partition that I want both Windows and Linux to access? If so, then Ext3 is surely the way to go. If not, what exactly is /home for, and around how big should I make it?


Actually, the reason I'm dishing out for a 400GB hard drive is that in Brazil right now, due to all those boring market numbers and statistics, larger hard drives are cheaper and smaller hard drives are more expensive (I can get about 1.3GB per R$1 on a larger drive, but only 0.7GB per R$1 on a smaller one). I don't have the cash to buy two 400GB HDs, and to buy a smaller one isn't (to use one of my least favourite terms in the English language) feasable. I'll keep your suggestion in mind, though, since the prices will come down eventually.


I keep remembering new things to ask :oops: Do Ext3 partitions require defragging as much as NTFS or (God no) FAT32 partitions do? If so, Kubuntu must come with a tool (or a Terminal/Konsole command) that does that, right? Or should I use the Windows Disk Defragmenter after I've installed the FS-driver?

The order on the drive for the partitions doesn't technically matter, but the Windows install should be on the first one. Your /home directory is basically the equivalent of your my_documents directory in Windows except that it also contains some hidden files with configuration info and some applications. Ext3 systems do not require defragging, so that is one thing that you won't have to worry about. If it is ext3, I wouldn't let the windows defragger anywhere close to it ;-)

Sorry, I didn't realize that you were in Brazil. If and when the prices come down, an extra hard drive is a good way to go. 
Where are you in Brazil? I used to go to Sao Paolo a couple of times a year for business, but it has been a few years.

---

### Post by GepettoBR on 2007-09-19
So just for clarification, my /home directory is where I'll keep all my files, including the ones I want Windows to read? In other words, the big ol' chunk of hard drive that's left after I separate the swap partition and the OS partitions?

> **timzak said:**
> Not that you'll need to conserve space with 400 gigs, but I have found on my system with 1 gig of ram that my swap partition never gets touched.  I have it sized to 500 MB (way smaller than what the installer suggested).

Even on an older computer with only 256 MB of ram, I've never seen the swap partition get filled more than 50 MB.

Good luck!
If the Windows swap file is any reference, I'll need it big. Video compression really pounds on the RAM under Windows, and it shouldn't be that much different under Linux, since it's still the same algorythms, just running on a different OS. My confusion with the swap directory was that Windows doesn't create a partition, but a file in each partition, so I thought it wasn't the same thing. Apparently it is, so I think I got it. Thanks to everyone for your great explanations!

> **dondad said:**
> Sorry, I didn't realize that you were in Brazil. If and when the prices come down, an extra hard drive is a good way to go. 
Where are you in Brazil? I used to go to Sao Paolo a couple of times a year for business, but it has been a few years.
I Live in Minas Gerais, that's the state directly north and northwest of São Paulo. We have a few big cities, but it's more of a rural state. You shouldn't come over just for business, we have kickass beaches and over half of the Amazon Rainforest for everyone's touring pleasure. Just don't litter ;)

---

### Post by oomingmak on 2007-09-19
> **GepettoBR said:**
> So just for clarification, my /home directory is where I'll keep all my files, including the ones I want Windows to read?
Not necessarily.

The /home folder also contains all your configuration and settings files for your user account, (so the home folder is somewhat like the 'Application Data' folder in Windows). Ubuntu does default to storing user created files in /home, but it doesn't have to be that way, you may wish to keep your files (e.g. your letters, music, photo's etc.) separate from all these configuration settings. 

If you choose to do this, it means that if you upgrade your OS, or if have problems with your account settings, that you can restore or overwrite your /home partition without having to move all your mp3s etc. It also means that you can use disk images to quickly back up and restore your home partition, because the size will be much more manageable than if you are also having to image your entire music collection just because it happens to be in the same folder.

I would suggest that you make a separate partition for your data and then you can either use mounting or symlinks to have access to this data partition from within your /home folder (so it will be a bit like using Windows "shortcuts" to get easy access to  files that are stored elsewhere). If you use a mount point, you won't even be able to tell that files are stored elsewhere, it will look as if the folders are within /home itself (if that's what you want).

Size wise, the home folder settings on their own (without user files like music and movies) is not very big at all. It's mainly a collection of very small text configuration files. I'd say that 20GB would be a very generous amount to allocate to your home folder (which you can afford to do as you will have a 400GB HD). I'd then allocate the majority of your storage space to your data partition and put all your documents, photos, movies, music etc on that partition which can then be easily accessed from Windows without having to wade through a bunch of useless (at least to Windows) configuration dot files.

---

### Post by GepettoBR on 2007-09-19
Do you mean 20GB for just the /home directory, or also the *buntu installation?

---

### Post by oomingmak on 2007-09-19
> **GepettoBR said:**
> Do you mean 20GB for just the /home directory, or also the *buntu installation? 
I meant just for /home. 
 
But as I said, that is being **very** generous (you could easily get away with giving only 3 to 4GB to your /home partition if you wanted to). 

However, with a hard drive of 400GB you might as well allow some "growing room" to cover every possible eventuality (for example if you continue using the same install for a couple of years and decide to install loads of backgrounds, themes, fonts and other software, or if you decide to add more user accounts - each of which will go into the home partition). Also the .Trash folder is stored in /home (i.e. the Recycle Bin equivalent) so if you delete lots of stuff and don't keep emptying the wastebasket, then this takes up space in the /home folder too.  

It's probably better to slightly over estimate your usage than to discover later that you are running out of space and therefore have to resize your partitions to borrow some space from elsewhere (and then shuffle everything about to allow for the change).

My current Ubuntu install is a test install, so I use it to try out anything that takes my interest (which means I have installed **lots** of different things). After several months of usage my /home folder is using just over 500MB (out of a 10GB /home partition) so that's only 5% of my /home folder used. So you could easily get away with using much less than 20GB for your home if you wanted to allocate the space elsewhere.

Here's how I have laid out my test install:

[IMG]http://i219.photobucket.com/albums/cc48/0omingmak/594ace54.png[/IMG]

I've allowed 50GB for Ubuntu, that's the OS itself (i.e. root "/"), the /home partition,  and a dedicated Data partition for my Ubuntu user files (e.g. pictures, documents etc). I gave 4GB to swap, which is probably way more than is necessary, but I just chose that figure because it's how much RAM I have (and I'm not exactly short of HD space). 

The rest of the unallocated space I intend to give to Windows (which is my main OS) to use for storage when editing video footage.

Hopefully this will give you a bit more of an idea about what kind of partition sizes might work best for you.

---

### Post by Shazaam on 2007-09-19
A swap file is for temporarily storing stuff that won't fit in your physical RAM (which you already know).
Simple swap file comparison=

Windows uses the whole drive to put little bits of files in every nook and cranny (sometimes corrupting everything else) causing file fragmentation and eventual system slowdown.

Linux swap is a dedicated partition, nothing else goes in there.

---

### Post by rsambuca on 2007-09-19
> **oomingmak said:**
> Here's how I have laid out my test install:

[IMG]http://i219.photobucket.com/albums/cc48/0omingmak/594ace54.png[/IMG]

I've allowed 50GB for Ubuntu, that's the OS itself (i.e. root "/"), the /home partition,  and a 25GB dedicated Data partition for my Ubuntu user files (e.g. pictures, documents etc). I gave 4Gb to swap, which is probably way more than is necessary, but I just chose that figure because it's how much RAM I have (and I'm not exactly short of HD space). 

The rest of the unallocated space I intend to give to Windows (which is my main OS) to use for storage when editing video footage.

Hopefully this will gives you a bit more of an idea about what kind of partition sizes might work best for you.
Gepetto, the problem with getting all of this info regarding partition schemes is that if you ask 10 people, you are likely to get 10 different answers.  I think you will find that the above scheme is very atypical usage for a standard linux installation.  The majority of users who actually use a dedicated /home partition will make that the largest partition, as that is usually where they end up chucking all of the user data files, media, video, music, etc.  If you ever have to re-install for some silly reason, then you just reformat the root partition and keep your existing /home, which contains all of the settings and miscellaneous storage.

The above partitioning scheme simply will not work because you can only have 4 primary partitions on one hard drive, so I don't know how oomingmak is going to actually use the unallocated space, since no partitions can be added to the above scheme.

---

### Post by rsambuca on 2007-09-19
I would recommend something more like this partitioning scheme, from the psychocats ubuntu site:[IMG]http://img379.imageshack.us/img379/2128/partitioning5bu8.png[/IMG]

---

### Post by oomingmak on 2007-09-20
> **rsambuca said:**
> The above partitioning scheme simply will not work because you can only have 4 primary partitions on one hard drive, so I don't know how oomingmak is going to actually use the unallocated space, since no partitions can be added to the above scheme.
As I said in my post, the unallocated area on my disk is going to be used only for video file storage (this is because my Windows OS and Data are on separate drives). The video storage area does not need to be bootable and so an extended partition will be set up to contain the logical partitions for Data and for Video storage). I have not bothered to do this yet because I've just done a clean Windows install and don't have my editing suite up and running yet (hence why the largest section of this disk is not even formatted). In the mean time I am using that drive as a test bed for Ubuntu, which I can happily test to destruction because any data I have created while using Ubuntu is on its own partition. So I just re-image the root and home to fix any irreparable problems that I have created while not losing my data.

I was not suggesting that Gepetto copy the **exact** layout of the screenshot, because obviously he does not need **2** data storage areas, and my layout doesn't allow for Windows to exist on the same drive (because I don't need it to). The screenshot was shown so that he could see how much *space* was actually being used by my root and home partitions, to help him gauge how much space he might wish to allocate on his own setup.

In his setup he would have Windows and Kubuntu as primary partitions and then have home and data as logical partitions.

---

### Post by rsambuca on 2007-09-20
Well, like I said earlier, ask 10 people, get 10 different answers! As long as it works for you, that is the important thing.

I still think it is rather shortsighted of you to install Ubuntu (or any OS) onto a drive that you know you will be needing in the future.  It would have been much easier to just set up the logical partitions in the first place.  Who knows, maybe you will like Ubuntu so much you don't want to get rid of it?

---

### Post by oomingmak on 2007-09-20
> **rsambuca said:**
> Who knows, maybe you will like Ubuntu so much you don't want to get rid of it?
Well I knew that it was going to be wiped whatever happened (because It has always been my intention to do a clean install when Gutsy comes out next month) and given the hell that I've put this  existing Feisty test install through, then there's no way that I'd  want to keep it on disk long term.

But as you say, each to their own.

---

### Post by Skidpad on 2007-09-20
> **GepettoBR said:**
> I Live in Minas Gerais, that's the state directly north and northwest of São Paulo.
Coffee growing country.  :)
Welcome aboard!

/hijack

---

### Post by GepettoBR on 2007-09-20
> **Skidpad said:**
> Coffee growing country.  :)
Welcome aboard!

/hijack

Damn good coffee too.

Thanks a lot for the example, oomingmak. It's good reference, since I"ll also use my computer a lot for video editing (running Premiere and AE on 512 RAM is killing me, can't wait to get the new machine running)  I think I'll keep /home smaller and use the shared partition for storage, though... It won't be affected by a reinstall either, and I'd rather not risk Windows do anything stupid to my config files. 

Last question, since this seemed very important in rsambuca's post. What's the difference between a primary partition and a logical partition? I'll want both my OSes on primaries, I assume, but what about Swap, /home and the other one?

---

### Post by rsambuca on 2007-09-20
> **GepettoBR said:**
> Last question, since this seemed very important in rsambuca's post. What's the difference between a primary partition and a logical partition? I'll want both my OSes on primaries, I assume, but what about Swap, /home and the other one?
Basically there are 3 types of partitions you can make on your hard drive.  Primary partitions, Extended partitions, and Logical Partitions.  I am not sure what the technical reasons are, but you can only have 4 main partitions on one hard drive.  Three of these can be Primary, and you can then add one Extended Partition.  An extended partition can then be further 'subdivided' into a bunch of Logical partitions.  The logical partitions within an extended partition is basically an easy method of getting around the 4 partition limitation.

One problem of the logical partitions is that Windows doesn't like to run from them, so the main OS should be in its own dedicated Primary Partition.  Linux Os's don't really care whether they are in a primary or logical partition.

For instance, if you look at the attached partition structure of one of my drives, you can see a bunch of logical partitions inside of one extended partition.  Each one of these contains a different linux distrobution.  There is also a shared swap for all of the distros, and then a media storage partition at the end.

The reason I questioned oomingmak's own partitioning scheme is that it contains four primary partitions in addition to the unallocated space, so there is no method of **adding** another partition to use the space.  As oomingmak indicated though, it is because they knew this wasn't a permanent setup.

Sorry for the long post!

---

### Post by GepettoBR on 2007-09-20
No need for apologies! Your post was very informative, thank you!

I guess that wraps up my initial questions about assembling the system. Thanks to everyone for your great (and too quick) responses. Next I'll do some research on 64bit VS dual-core 32bit, and if I have any questions I'll stop by here again.

---

### Post by rsambuca on 2007-09-20
> **GepettoBR said:**
> No need for apologies! Your post was very informative, thank you!

I guess that wraps up my initial questions about assembling the system. Thanks to everyone for your great (and too quick) responses. Next I'll do some research on 64bit VS dual-core 32bit, and if I have any questions I'll stop by here again.

I am an advocate of using 64bit, by the way.  You will see a lot of posts that discourage 64bit Ubuntu because of... <insert problem here>, but frankly, most of that is outdated information.  The only 'snags' if you call them that, is with proprietary components like flash and java plugins, but scripts have been written to install these things with a simple mouse click.

The difference in the packages available between 32bit and 64bit is very small (less than 1%, currently), so if you are having trouble finding a program, it is not likely to be due to 64bit vs. 32bit.

The bottom line is that linux is linux.  It can be hit or miss depending on your hardware, and that is not the fault of Ubuntu or linux.  It is due to lack of support from the hardware manufacturers.  With any luck, things will go smoothly, but if you do have rough spots, it likely won't be any different whether you are using 32bit or 64bit ubuntu.  Because of this, you may as well take advantage of your system capabilities and use the 64bit system.

---

### Post by timzak on 2007-09-20
If you are aware of how hard disks work, the fastest portion is at the front of the drive.  In my opinion, (especially since you will likely be making frequent use of the swap partition), you should create the swap partition first so that it is on the fastest portion of the hard disk.  Then, create the root and home partitions (so they are adjacent to the swap), followed by the XP partition.  Someone correct me if I'm wrong, but can't you still install XP first once you create the partitions as such, then later install Ubuntu on the partitions you've reserved for root and home?

My thinking is to keep the Ubuntu and swap partitions close to each other so that the hard disk actuator has less physical distance to move back and forth when going from your data to the swap.  The absolute worst situation would be to put Ubuntu at the front and the swap at the end of your drive, as it would be sweeping across 400 GB of space each time it has to access the swap.

Of course, on the XP partition, create your swap file on the same partition as your work files to minimize actuator travel there as well.

---

### Post by ncappel1 on 2007-09-20
here is another site that may be helpful to you, it covers lots of issues and talks about dual booting in great detail: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

let us know if it is helpful.

---

