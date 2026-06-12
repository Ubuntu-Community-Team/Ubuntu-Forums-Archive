---
title: "So I NEED to install windows XP."
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Royal_Pwner on 2007-12-19
I need to run software in windows for a class. Don't worry, ubuntu, I still love you.

However, I also *need* to keep my current settings that I have on ubuntu.
I'm on a system 76 upgraded serval performance with a 200g 7200rpm harddrive. Only stuff on it is ubuntu and files that I put on. (programs, stuff for classes, media, etc.)

How do I go about doing this? I searched, but I need to be really really sure not to screw up.

---

### Post by Tux.Ice on 2007-12-19
dual boot i would think that way you can boot in to either windows xp or ubuntu

you need to install g parted

```
sudo apt-get install gparted
```

then run it

```
gparted
```

then rezize your current ubuntu partition and create a windows ntfs partition. then install windows on the ntfs partition and ubuntu should automatically figure it out and you will hav a choice of ubuntu or xp on bootup.

if you have any questions or problems message me.

---

### Post by Niniel on 2007-12-19
Use gparted to free up some hd space and then install XP into that. 20  - 30 GB ought to be enough.

---

### Post by dpar on 2007-12-19
Or run it in a virtualbox.

---

### Post by maybeway36 on 2007-12-19
VirtualBox is good. But if you need real Windows, it's easy enough to set it up to boot from GRUB.

---

### Post by RKCole on 2007-12-19
I second dpar, in that you could run Windows XP inside of VirtualBox.  I am a student also, and that is precisely what I do.  If you are not familiar with virtualization, ti si basically the ability to run an operating system (virtually) within your current operating system without having to install it onto your hard drive, thus dropping the necessity of installing it onto a separate partition.

Here is a guide if you are interested:
[http://doc.gwos.org/doku.php/doc:office:virtualbox?s=virtualbox](http://doc.gwos.org/doku.php/doc:office:virtualbox?s=virtualbox)

---

### Post by rickycodie on 2007-12-19
i will third dpar, but it doesn't work if you need directx

---

### Post by bodhi.zazen on 2007-12-19
> **Tux.Ice said:**
> dual boot i would think that way you can boot in to either windows xp or ubuntu

you need to install g parted

```
sudo apt-get install gparted
```

then run it

```
gparted
```

then rezize your current ubuntu partition and create a windows ntfs partition. then install windows on the ntfs partition and ubuntu should automatically figure it out and you will hav a choice of ubuntu or xp on bootup.

if you have any questions or problems message me.

Ummmm .... No

Please do not do that. 

You can not resize a mounted partition, so to resize your Ubuntu root partition you will need to boot a live CD

Gparted is on the Ubuntu Desktop CD

The only other tricks you may need to know is :

1. Windows needs to be installed into a PRIMARY partition

2. After installing Windows you will need to restore GRUB :

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by Royal_Pwner on 2007-12-19
Is there an easy way to virtualize xp without using an install cd?

Also, will it take a performance drop by using virtualization? I'd very much like to be able to game on windows and do everything else on ubuntu. Ubuntu is severelly lacking in the gaming departement.

---

### Post by bodhi.zazen on 2007-12-19
There are ways to convert you window install to a virtual machine.

However, games do not work so well in virtual machines.

Try this link : [http://gaming.gwos.org/news.php](http://gaming.gwos.org/news.php)

---

### Post by Royal_Pwner on 2007-12-19
> **bodhi.zazen said:**
> There are ways to convert you window install to a virtual machine.

However, games do not work so well in virtual machines.

Try this link : [http://gaming.gwos.org/news.php](http://gaming.gwos.org/news.php)

Care to elaborate on the games thing? It's essentially not worth it to me to virtualize if my games take a performance hit. I've got kick-*** hardware (for a laptop) and I want to use it.

---

### Post by bodhi.zazen on 2007-12-19
Virtual machines will not use your hardware directly. Active X will not work for example.

---

### Post by Royal_Pwner on 2007-12-19
oh, then I need to do a dual boot.
ugh.
any advice?
is it hard to do?

---

### Post by bodhi.zazen on 2007-12-19
Dual booting is easy. After installing Ubuntu you will get the grub menu which will allow you to select the OS you want to run.

Alternates include wine and cedega, see the link I gave you earlier.

---

### Post by jken146 on 2007-12-19
Dual booting is not that hard to do.  You'll need one partition for Windows, probably 20 gigs at least.

It's a good idea to back up your files before messing around with partitions!

---

### Post by Royal_Pwner on 2007-12-19
I've installed ubuntu already.
I already know about WINE/Cedega.

How do I go about backing up my stuff?

---

### Post by jken146 on 2007-12-19
> **Royal_Pwner said:**
> How do I go about backing up my stuff?

Another hard drive (be it internal or external), another PC via a network, CD/DVDs, anything else you can think of... it really doesn't matter.

---

### Post by Royal_Pwner on 2007-12-19
But, what exact process would I go about doing it by?
is there a 'backup-maker"?

---

### Post by Royal_Pwner on 2007-12-19
Also, how much harder would it be to do this if the copy of windows was possibly...how should I say this...not..."legit".?

---

### Post by jken146 on 2007-12-19
> **Royal_Pwner said:**
> But, what exact process would I go about doing it by?
is there a 'backup-maker"?
What I would do is just copy the files you want to keep to your backup media.  What more do you need?

> Also, how much harder would it be to do this if the copy of windows was possibly...how should I say this...not..."legit".?
I can't give you any advice on pirating Windows.

---

### Post by dpar on 2007-12-19
> **Royal_Pwner said:**
> Also, how much harder would it be to do this if the copy of windows was possibly...how should I say this...not..."legit".?

Oooops, you just asked the wrong question.

---

### Post by Royal_Pwner on 2007-12-19
I didn't mean pirated.
I meant that the disc would be borrowed, so I can't know for sure if it's legit or not.

---

### Post by dpar on 2007-12-19
If you read the EULA, I think that you would find that it would not be legit.

---

### Post by Tux.Ice on 2007-12-20
admin-
thank you for pointing that out forgot to mention you need to be on a live cd.

gparted is already installed on gutsy????
whoa. never knew that

---

### Post by Frank Golden on 2007-12-20
> **Royal_Pwner said:**
> I didn't mean pirated.
I meant that the disc would be borrowed, so I can't know for sure if it's legit or not.
You will still need to activate XP. If the disk isn't "legit" borrowed or not and is already installed on another machine MS will know that and refuse to activate. Activation is new with beginning with XP as part of MS's antipiracy campaign.

You would have fewer headaches if you purchased an OEM version of XP and installed that. An OEM version is usually cheaper than a retail version and usually requires a hardware purchase. My copy was delivered with an ATA cable to satisfy this license requirement. It is identical to a retail version but priced less for use by computer builders.

See link below for a very reasonably priced OEM copy of XP Home SP2.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16832116056](http://www.newegg.com/Product/Product.aspx?Item=N82E16832116056)

There may be other cheaper sources out there, Google for them. I myself use a tripple boot setup (Ubuntu 7.10 and PCLinuxOS 2007 with XP Pro) and am very happy about it.

---

### Post by Yoke &amp; Chung on 2007-12-20
> **Royal_Pwner said:**
> But, what exact process would I go about doing it by?
is there a 'backup-maker"?

You can backup the whole partition using Partimage. 
I am currently using Clonezilla, with capability of backing both NTFS and ext3 partitions.

Regards

---

### Post by Royal_Pwner on 2007-12-20
however, I can't figure out which part of the hardrive is what I use.
sda1? sda2? sda5? /dev/mapper/ubuntu-root?

I just don't know.

also, partimaged won't save because my partition is mounted. I can't unmount it.

---

### Post by Royal_Pwner on 2007-12-20
bump

---

### Post by Royal_Pwner on 2007-12-20
double bump.

how do I partition?
Please help.

---

### Post by bodhi.zazen on 2007-12-20
You can partition with gparted from the live CD

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by Royal_Pwner on 2007-12-20
I tried that.
Under the 4 boot options I've tried, it always hangs at
io scheduler cfg register

---

### Post by Royal_Pwner on 2007-12-20
Please help.

---

### Post by kf4mat on 2007-12-20
Hey all,

Reading this with interest because I also need XP to run the Basic Stamp IDE software. I have a restore CD of XP and was going to reload it after I had to replace a destroyed hard drive but downloaded ubuntu instead. 

Since i'm not a techie i don't have a clue about making partitions but want to know more about the virtual option.  I followed RKCole's link on how to do it but the link seems to be dead. Anyone have another tutorial that might help me out.

Thanks in advance,

Tom

---

### Post by bodhi.zazen on 2007-12-20
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

@Royal_Pwner ??? gparted is on the Ubuntu Live (desktop) CD.

---

### Post by Royal_Pwner on 2007-12-20
I guess I'll just use the ubuntu livecd. The gparted livecd doesn't work.

---

### Post by Royal_Pwner on 2007-12-20
I'll post what happens when I run gparted.
I can't modify either of the large drives.
Even if I could, I don't know which I *would* modify.
Screenies attached.

---

### Post by mc4man on 2007-12-21
> Under the 4 boot options I've tried, it always hangs at
The gparted livecd doesn't work
force vesa is what normally works (8th option)
looks like you might want to do a little more reading up on partitions(ing) and a little less clicking around  in a partitioner

---

### Post by Yoke &amp; Chung on 2007-12-21
> **Royal_Pwner said:**
> however, I can't figure out which part of the hardrive is what I use.
sda1? sda2? sda5? /dev/mapper/ubuntu-root?

I just don't know.

also, partimaged won't save because my partition is mounted. I can't unmount it.

You may download a live rescue CD, think you can get the link from Partimage web page. Boot up from the disk, and in there, there is gparted and partimage. This way your hard disk will not be mounted.

Regards

---

### Post by mukul_d on 2007-12-21
Reading all these replies I would say, there is no way you can retain your existing settings in Ubuntu if you want to install Windows XP in the existing setup. Windows does not like any other operating system running on the computer it is going to run and it will delete the MBR regardless and won't give you any other option. It is hard enough to make dual boot machines with different flavours of Windows let alone Linux.

The way to go would be to use Windows in a virtual environment if you cannot do without keeping you existing settings. Under normal circumstances Linux should be installed AFTER windows has been installed and configured.

---

### Post by bodhi.zazen on 2007-12-21
> **mukul_d said:**
> Reading all these replies I would say, there is no way you can retain your existing settings in Ubuntu if you want to install Windows XP in the existing setup. Windows does not like any other operating system running on the computer it is going to run and it will delete the MBR regardless and won't give you any other option. It is hard enough to make dual boot machines with different flavours of Windows let alone Linux.

The way to go would be to use Windows in a virtual environment if you cannot do without keeping you existing settings. Under normal circumstances Linux should be installed AFTER windows has been installed and configured.

No, that is not true.

All that needs be done is :

1. Boot a live CD

2. Resize the ubuntu root partition.

3. Make a new primary partition.

4. Install Windows into the new primary partition.

5. Restore grub.

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]


The OP is trying to do this, but the exact hold up is not clear to me.

---

### Post by Royal_Pwner on 2007-12-21
how do I make a new primary partition?

The hold up is that I don't know what to resize. see my above post for the different partitions on my drive.

---

### Post by bodhi.zazen on 2007-12-21
Can you be more specific ? What part of the documentation do you not understand ?

This how - to is detailed and includes screen shots :

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

As does this :

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

---

### Post by Royal_Pwner on 2007-12-21
I'm being as specific as I can.

Look at the screenshots I attached in my previous post on the previous page.
I currently have 3 partitions.
I don't know which one to resize.
I understand how to resize, etc.
I just don't know which one.

---

### Post by iammeagain on 2007-12-21
> **Royal_Pwner said:**
> I'm being as specific as I can.

Look at the screenshots I attached in my previous post on the previous page.
I currently have 3 partitions.
I don't know which one to resize.
I understand how to resize, etc.
I just don't know which one.

I looked at the screen shots, I dont understand why you opened /dev/mapper/ubuntu-root or /dev/mapper/ubuntu-swap_1

The /dev/sda screenshot displays your partitions. It looks like you need to resize /dev/sda5 . You just select it and click the resize button on top.
ALSO since windows wants a primary partition you will likely need to resize the extended partition /dev/sda2 that sda5 is within. I believe you are only allowed like 4 primary partitions per hard drive which is why they have extended partitions.

The windows partition may need to be fairly big if you are going to use it for gaming. Since games can take up a lot of space.


Another option is the virtualization, using vmware which CAN run directx. I run some video games that way. I'll see if I can find a link, I had it bookmarked but I'm not on my computer. Got it, [http://ubuntuforums.org/showthread.php?t=372928](http://ubuntuforums.org/showthread.php?t=372928)  that should get the idea across of how to setup vmware. Only I believe you just need the VMware workstation to set up Windows, after that you can just use VMware player to run Windows. 

Hope this helps

---

### Post by Royal_Pwner on 2007-12-21
I just don't know what /dev/mapper/ubuntu-root is.
What is it?

It's what it opened to when I started the program.
I'm going to just delete the swap partition.

---

### Post by Royal_Pwner on 2007-12-21
Also, Windows needs to be on a primary partition in ntfs, correct?

dev/sda5 is not primary, correct?
it also won't be formatted in ntfs. the option is greyed out.

---

### Post by bodhi.zazen on 2007-12-21
Windows will format the partition as part of the install process so don't worry about that.

You need to know what is in your partitions. If you are not sure, mount them and take a look.

---

### Post by iammeagain on 2007-12-21
I dont know if gparted can format in ntfs, but windows xp will run on ntfs or fat32. I think only XP Pro will run on ntfs though. I may be wrong. Yes I believe it needs to be primary.

Correct /dev/sda5 is not primary it is under the extended partition /dev/sda2. 

You dont wanna format anything unless it is free space, or you are sure you dont want the info contained in that partition. If you resize sda5 it should leave free space. But dont format that free space yet, you need to resize sda2 to fit around the new sda5. Then that free space that is NOT under sda2 will be able to be primary partition that you can format. 

Once formatted it will likely be labeled sda3. The sda1 to sda4 i believe are always primary, then sda5 and on will be under extended partitions.

---

### Post by Royal_Pwner on 2007-12-21
I need to know what /dev/mapper/ubuntu-root is before I do anything.

What is it?

---

### Post by iammeagain on 2007-12-21
> **Royal_Pwner said:**
> I need to know what /dev/mapper/ubuntu-root is before I do anything.

What is it?

I don't know for sure, it appears to that its just another way of the computer identifying the ubuntu partition. Like another name for it, maybe some program or another needs to identify it that way. I don't really know. The sda stuff is what you should be messing with though.

---

### Post by Royal_Pwner on 2007-12-21
alright.
so, review time.
here's what I do:
Leave the /boot (sda1) alone.
delete the swap partition.
shrink down the /ubuntu-root by 35 gigs.
format that leftover space as ntfs.
install windows in the ntfs space.
recover grub.
right?

---

### Post by iammeagain on 2007-12-21
> **Royal_Pwner said:**
> alright.
so, review time.
here's what I do:
Leave the /boot (sda1) alone.
delete the swap partition.
shrink down the /ubuntu-root by 35 gigs.
format that leftover space as ntfs.
install windows in the ntfs space.
recover grub.
right?

Why bother deleting swap? No real reason to is there? You can though.

I don't know what ubuntu-root is, it should be the same as sda5. But it would likely be safer actually resizing sda5.

There is no need to format it, windows install will format it either way. It is repetitive. (Make sure that the free space is out of sda2, so it can be primary.)

Do you know how to recover grub?

---

### Post by iammeagain on 2007-12-21
Heres a little on how to do grub. Its from an old crudy how to of mine.

Install Grub:

Info Windows erased the Master Boot Record (MBR) so now we have to fix that.

First Boot into (K)Ubuntu live Cd again

Second Open up a terminal, and type in " sudo grub "

Third Type " root (hd0,1) " Replacing the 0,1 with the appropriate #'s. (You need to know what partition (K)Ubuntu is on. If you can't remember opening a new terminal and typing " sudo fdisk -l ", which will list your partitions. So hda1=hd0,0 and hda2=hd0,1 and hdb1=hd1,0 I hope that makes sense its a little tricky to explain.)

Fourth Type in " setup (hd0) " (But replace it with the same thing it was above for you.)

Fifth Type " quit " and reboot everything should be setup. (Once you learn how its not nearly as hard as it seems.)

Sixth OK you need to edit your grub menu to include Windows. I totally forgot that part. I dont have the tiem to add it now but i will later

---

### Post by blueridgedog on 2007-12-21
Are you certain the software you need to run will not run in wine?  I have found all of the windows applications that I needed worked well in wine.

---

### Post by DeloNIdaho on 2007-12-21
Hey guys. I just installed Ubuntu today. I'm really starting to like it... One question though. After I install xp on a virtual drive do I need to install my Virus> AVG AD AWARE AND SPYBOT and stuff? Quick explination. Does it access the internet through a firewall in ubuntu???

---

### Post by iammeagain on 2007-12-21
> **DeloNIdaho said:**
> Hey guys. I just installed Ubuntu today. I'm really starting to like it... One question though. After I install xp on a virtual drive do I need to install my Virus> AVG AD AWARE AND SPYBOT and stuff? Quick explination. Does it access the internet through a firewall in ubuntu???

I don't know a 100% answer on how it access the internet, even if it did the firewall probably wouldn't stop everything that is windows related since its for Linux. Also the firewall can't stop you from downloading a virus when you think your trying out MS software.
Either way when it comes down to it, Windows is still vulnerable to viruses, and you should probably have anti-virus even in the virtual system. Although i think you can take a snapshot of the system and restore it if you do get a virus.

---

### Post by DeloNIdaho on 2007-12-21
Sweet good call man.

---

### Post by Royal_Pwner on 2007-12-22
Yeah, I know it doesn't work in wine.

I'm worried about the /dev/mapper/ubuntu-root thing though.
I think that's what I need to resize. It's the only one that accurately portrays my usage.

---

### Post by Royal_Pwner on 2007-12-22
any insight?

---

### Post by Royal_Pwner on 2007-12-22
please?

---

### Post by mc4man on 2007-12-22
some reading
[http://ubuntuforums.org/showthread.php?t=627550](http://ubuntuforums.org/showthread.php?t=627550)
[https://bugs.launchpad.net/system76/+bug/123077](https://bugs.launchpad.net/system76/+bug/123077)
plus there's a system 76 forum to browse/post
and if you totally bork things [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

---

### Post by Zenthes on 2007-12-22
How about you just try using wine? what exactily are the sort of programs that you NEED to run for class?

---

### Post by Royal_Pwner on 2007-12-22
Programs like Solid Works.

also, gaming of all sorts.

---

### Post by Royal_Pwner on 2007-12-23
Bump

---

### Post by iammeagain on 2007-12-23
back everything important up and just go for it. I don't know if there is anymore info you can get now.

---

### Post by Royal_Pwner on 2007-12-23
Yeah....
I seem to be unable to back up my stuff though. It's just not working...
meh.
This is getting so problematic.

---

### Post by iammeagain on 2007-12-23
Just burn what you want to keep to a DVD or CD, thats how I back up my info.

---

### Post by Royal_Pwner on 2007-12-23
Yeah, but is there a way to backup your entire system?
Like, settings and stuff?
Meh.
I think I'll just burn the files, deal with the other stuff when I need to.
I need the system76 drivers though...

---

### Post by 99bluefoxx on 2007-12-23
i was wondering, is it possible for the SATA controller on a mobo to burn out and the rest still work? cause i cant get a seagate barracuda 7000.10 80 GB to detect properly in my BIOS, it shows up as a "X0-0001" 270 GB, and linux refuses to mount it
and i know its not the drive b/c i took it back and they tested it, and the replacement one
i want to know cause i cant put a second PATA drive at the moment, and i want to backup data and install winblows[dont like it but need it], ubuntu, and also try out debian/slax/puppy, and a few others [pent-boot?lol]

---

### Post by iammeagain on 2007-12-25
> **Royal_Pwner said:**
> Yeah, but is there a way to backup your entire system?
Like, settings and stuff?
Meh.
I think I'll just burn the files, deal with the other stuff when I need to.
I need the system76 drivers though...

I think all your settings are saved under your /home/username directory, but are hidden. I'm not sure of the extent of if this is all or just some of your settings and what else is there. Like tomboy notes are saved in a hidden directory in your /home/username

---

### Post by rosslaird on 2007-12-26
> **iammeagain said:**
> I think all your settings are saved under your /home/username directory, but are hidden. I'm not sure of the extent of if this is all or just some of your settings and what else is there. Like tomboy notes are saved in a hidden directory in your /home/username

Only some (but most) of the settings are in the home directory (and some are indeed hidden by a dot prefix). For these types of files, backing up using rsync is an excellent option:

```
rsync -varuzP /home/me/ /destination/me/
```

The trailing slashes are important. Search the forums for the rsync tutorial(s).

There are also some settings files that are not in the home directory, such as xorg.conf, which can be a crucial file to save. It's in /etc/X11.

Ross

---

### Post by Royal_Pwner on 2007-12-26
Well, I tried it, and it got messed up.
Whatever.
I'm back up and running now though, so it's all good.
Thanks for the help.

---

