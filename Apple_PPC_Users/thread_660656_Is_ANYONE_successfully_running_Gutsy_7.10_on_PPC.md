---
title: "Is ANYONE successfully running Gutsy 7.10 on PPC?"
date: 2008-01-07
forum: Apple PPC Users
---

### Post by VidiotGeek on 2008-01-07
I installed Feisty on my 15" iMac with little to no issues (in that I actually got it to work) & had happily customized things to my liking, started figuring out how to install apps & work with Linux in general--the last 3 days are my first real experience of trying to use Linux after being a Mac user for about 5 years--and felt I was off to a great start. 

Then Add/Remove... told me that 7.10 was available for upgrade. I clicked it & let it run through the upgrade but after I restarted, it won't load the OS from my HD. It starts, gives me a jacked up boot splash (so did Feisty, I thought nothing of it) and it ultimately drops out to a kernel CLI prompt. Saying something to the effect of "I can't mount this drive".

I don't want to have to wipe my Linux partition & start over with a fresh install if I don't have to but I can't seem to find any recovery tools on this 7.04 Live CD, other than GParted. From what I've been able to find on the forum, it seems that alot of people are having trouble with Gutsy on the PPC platform. Maybe this is why the PPC distro is less prominently featured on the site? Any pointers are quite welcome & appreciated, This is a whole new world for me.

---

### Post by Twiggy003 on 2008-01-07
I personally have had little problems with Gutsy on a ibook G4 PPC, the only issues I had were the wireless, where I had to install them using a wired connection, and the sound which has a workaround on this forum.  I initially upgraded from feisty to gutsy using the updater and I ran into quite a few problems, a best bet would be to back up your stuff and do a fresh install of gutsy.

---

### Post by PapaNerd on 2008-01-07
I've had 6.06.1, 6.10, and 7.04 all running on the same PowerBook G4 with no problem (except for the DVI card driver which appears to be troubling a lot of other folks as well).  However, after doing the on-line upgrade to 7.10, the boot-up process appears to be normal, but the system then drops into BusyBox v1.1.3 with a "(initramfs)" prompt.  None of the drive partitions are listed in the /dev directory, so can't mount them, and there is no /etc/init.d directory to try and start things manually.

---

### Post by PapaNerd on 2008-01-07
Oops, spoke too soon ... found the workaround (to at least my problem) on [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by jmo1687 on 2008-01-07
I was running Gusty on my 14" iBook G4 up until an hour ago, where I downgraded to Feisty. It worked pretty well for me, with a few problems (small black bars on top bar, weird black lines when starting up and shutting down) and I didn't even have an option in Gusty for my computer to sleep (suspend to ram), and I needed that to work. In Feisty, so far sleep works fine, and things are generally running smoother.

With my experiences with Gusty, I would recommend sticking to Feisty, as it seems there are less issues with PPC.

---

### Post by VidiotGeek on 2008-01-08
> **PapaNerd said:**
> I've had 6.06.1, 6.10, and 7.04 all running on the same PowerBook G4 with no problem (except for the DVI card driver which appears to be troubling a lot of other folks as well).  However, after doing the on-line upgrade to 7.10, the boot-up process appears to be normal, but the system then drops into BusyBox v1.1.3 with a "(initramfs)" prompt.  None of the drive partitions are listed in the /dev directory, so can't mount them, and there is no /etc/init.d directory to try and start things manually.

That is precisely the issue I am having. I guess there are worse fates than having to download a 7.10 ISO & reinstall with that. At least I still have some disks. I should probably start using CD-RW's though at this rate.

---

### Post by VidiotGeek on 2008-01-08
> **jmo1687 said:**
> I was running Gusty on my 14" iBook G4 up until an hour ago, where I downgraded to Feisty. It worked pretty well for me, with a few problems (small black bars on top bar, weird black lines when starting up and shutting down) and I didn't even have an option in Gusty for my computer to sleep (suspend to ram), and I needed that to work. In Feisty, so far sleep works fine, and things are generally running smoother.

With my experiences with Gusty, I would recommend sticking to Feisty, as it seems there are less issues with PPC.

Interesting...it definitely seemed people were having issues on PPC with it. The urge to upgrade is strong but if it's going to cause problems, it's not worth it. Does the online upgrade option *usually* work fine? Is this just an issue with this release?

---

### Post by driven1 on 2008-01-09
The link provided by papanerd 

> **PapaNerd said:**
> Oops, spoke too soon ... found the workaround (to at least my problem) on [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

and this one [https://wiki.ubuntu.com/PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ") will solve most of your issues with running Gutsy on PPC and especially on a Powerbook. There is an issue with sound on the TiPowerbooks, but it's a fairly easy fix. The solution can be found on this forum.  I've been very happy with Gutsy so far.

---

### Post by fouba on 2008-01-09
I have now Xubuntu 7.10 on my iBook G3 and I can tell it wasn't easy to get it to this. First i installed Xubuntu 6.06 and than changed gutsy to the /etc/apt/sources.list replacing dapper. Than I just wrote apt-get update and apt-get dist-upgrade, I had to use to -f (force) in atleast one time.. There was some problems with the xorg-thing, but I solved that. So I have the latest version of Xubuntu on my very old laptop iBook G3 PPC and I'm pretty proud that I got it working.. Just keep on trying, most of the time the Xubuntu gives the best advices, when the situation isn't looking too good.

---

### Post by havoc_joe on 2008-01-13
I am new to ubuntuforums, but I am an experienced GNU/Linux user and administrator. I have to say that I am impressed with how easy it was to install Ubuntu 7.10 on my ~7 year old G3 dual-usb ibook. A simple "modprobe ide-core" at the initramfs prompt and away I went. The only issues that I had were minor: gnome sound daemon kept dieing (not a big deal honestly) and I had some issues connecting to WPA encrypted networks. I believe the latter problem is due to hardware limitations however as the Airport card (not extreme) has known issues in this regard no matter which Linux Distro one chooses. In fact, AES (as apposed to TKIP) encryption doesn't work at all even in OSX with this card from my experience.

Ubuntu has been the easiest install for me on this platform. I've tried Fedora 8 and Gentoo 2007.0, both successfully, but Fedora is just a bit too bloated for my tastes and I couldn't get X support working at all in Gentoo for some reason, even when using the same driver and config that worked in Fedora. With Ubuntu, I had no problems with X at all. It is a great pleasure not to have to mess with that for a change, though I must admit that I don't really need to have X. It's just nice from time to time.

---

### Post by VidiotGeek on 2008-01-13
> **havoc_joe said:**
> I am new to ubuntuforums, but I am an experienced GNU/Linux user and administrator. I have to say that I am impressed with how easy it was to install Ubuntu 7.10 on my ~7 year old G3 dual-usb ibook. A simple "modprobe ide-core" at the initramfs prompt and away I went.
....
Ubuntu has been the easiest install for me on this platform. I've tried Fedora 8 and Gentoo 2007.0, both successfully, but Fedora is just a bit too bloated for my tastes and I couldn't get X support working at all in Gentoo for some reason.........though I must admit that I don't really need to have X. It's just nice from time to time. 

I'd consider myself a bit of a modest power user on Mac OS X or Windows. I'm fairly knowledgeable & end up being the goto geek for alot of people I know. But I don't know how to do much on the command line of either OS. As for Linux, I'm definitely here as a hobby. I'd love to learn my way around bash beyond the basics of cd, pwd, ls, cp, mv, rm, etc, especially since alot of that will translate to OS X, but I'm kind of testing the waters with it to see how easy it is for an average computer user as much as I am playing with it to learn the ins & outs. Ease of use is probably the number one obstacle to mainstream (home desktop for Mom & Dad) acceptance of Linux still. Ubuntu's great so far, this is the first version of Linux I've ever been able to actually install without a CLI & I tried a handful of others. But if I can avoid it, I want to keep the system running with as little command line magic as possible. My last attempt at Gutsy didn't fit well with that goal. ](*,)

**I should note that I have since reinstalled Feisty & everything is working very happily now. :-)

---

### Post by havoc_joe on 2008-01-13
I completely understand your situation. It wasn't long ago that I was new to Linux and the whole open source scene myself, but as a CS major, programmer, and sysadmin, I really appreciate the freedoms and power that Linux and open source software provides me. IMHO, there is no better platform for development, administration tasks, or just plain old getting real work done (not that there isn't a lot of fun that can be had either).

My biggest advice for you if you want to seriously become a "power user" is to keep on working through the community and read the man pages/documentation for EVERYTHING. Once you see the general way things work, it becomes a lot easier. Then again, there is nothing like trying things out for yourself. Depending on the situation, I've found that the best way to learn is to try something and look at the results. Sure, it can be dangerous, but when your running a free OS, there is virtually nothing that you can do that can't be fixed. If you're afraid of losing data, back up things either regularly or before you run some strange command/code.

It's true that people learn Linux by using it. Keep that in mind.

---

### Post by woopud on 2008-01-14
Yes, I succesfully installed 7.10 on my B/W G3.  I had tried different LiveCD's like Ubuntu, Vine, Gentoo and Fedora, all with no succes, they all gave errors while booting, i found out that when I disconnected my internal Zip drive they would boot but no working graphics.   Then I downloaded the 7.10 alternate CD and installation was flawless, everything works, I can now dual boot between 7.10 and OS X.

Bert

---

### Post by Kerry_M on 2008-01-16
Yes! :)

My first time linux installation, but I still managed to get xubuntu 7.10 running on an old G3 imac. Definitely could not have done it without looking up the issues on this forum. I used the alternate install disk and had the problem described in the [PowerPCKnownIssues]("https://wiki.ubuntu.com/PowerPCKnownIssues").

I had to type:

modprobe ide-core

exit

on first boot after waiting for the busybox prompt to come up, then edit the "modules" file in etc/initramfs-tools/ using the Terminal.

The modules file looks like this now:

```
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
ide-core
# sd_mod
```

After typing "sudo update-initramfs -u" at the Terminal prompt the system boots properly.

I found using vi awkward as I had never used it, but there is probably a way to change the file using mousepad (not sure as I don't yet entirely understand how users and permissions work in ubuntu).

[IMG]http://members.shaw.ca/jeepster101/Screenshot_7_10.jpg[/IMG]

[IMG]http://members.shaw.ca/jeepster101/Screenshot3.jpg[/IMG]

---

### Post by VidiotGeek on 2008-01-16
> **woopud said:**
> Yes, I succesfully installed 7.10 on my B/W G3.  I had tried different LiveCD's like Ubuntu, Vine, Gentoo and Fedora, all with no succes, they all gave errors while booting, i found out that when I disconnected my internal Zip drive they would boot but no working graphics.   Then I downloaded the 7.10 alternate CD and installation was flawless, everything works, I can now dual boot between 7.10 and OS X.

Bert

Great reply's by everyone. I may yet make another attempt at getting Ubuntu Gutsy up & running in the next few weeks. I'll definitely have to lay out my game plan ahead of time though. I've got a 7.10 disk burned & a PC laptop in case I have to check the forums again mid process. I almost feel obligated to get it working with all the tips & advice everyone has offered. :)

As for backing up, the only thing I've done so far in Linux has been download cursors, themes, backgrounds, GDM themes, & miscellaneous binaries. Other than using Apt-on-CD, which seems like a great way to quickly reinstall all my software on a fresh system, what sort of backup software can anyone recommend? On Mac OS X, I've been kind of spoiled by SuperDuper. I make a bootable clone & proceed with reckless abandon. :-)

If I can, I'd like to do the same with my Ubuntu install. Is there anything on Linux that could accomplish the same thing? I'd have to be able to edit the partition map on my FW HD without erasing the second partition. Currently, it has one backup partition for the OS X boot drive & the rest is chocked full of crucial data. I'd be splitting up the first partition on the external to clone the Mac & Linux partitions.

---

### Post by hananias on 2008-02-01
i had no problem upgrading feisty to gutsy.  i have no knowledge of linux what so ever, but it was pretty smooth upgrade...even got compiz fusion working great.  you shouldn't have so much problems.

---

### Post by casbahdk on 2008-02-15
I have made attempts at running Ubuntu earlier, but there has always been mega problems with the PPC version. It has a different feel that it is now community supported. Some of the community have stepped up to the plate and written HowTos and there doesn't seem to be the sense of being ignored when a problem arises anymore, just because the hardware is PPC.

In practical terms, this has also meant that Gutsy is the best running Ubuntu I have yet experienced on my G5. I have noted a number of major bug issues for Gutsy and PPC hardware, but I haven't been affected as of yet (knock on wood).

---

### Post by Co.Sinecure on 2008-03-03
Hi All..sharing my experiences installing Gutsy..

I recently retired an old G3 iBook from its internet-gateway-and-dialer duties (upgraded to 3G broadband after waiting for several years for ADSL to reach our area - a whole 'nother story), and found that I couldn't install many of the programs I'd hoped to use it for (dmg error 95, anyone?), so decided to install Ubuntu instead.

Its a G3 700Mhz dual USB iBook.

I found the Gutsy live CD image for PPC, and prepared several tabs of forum posts just in case I needed them. It was mostly fairly straight forward...

Booting live CD required:
```
live-nosplash video=ofonly break=top
```
and at the initramfs prompt:
```
(inintramfs) > modprobe ide-core
(inintramfs) > exit
```

Installing from the live CD was too easy. I did a clean install over the entire disk (only 20gb. If it were more I would have made a seperate /home partition).

Alas, it didn't boot. :( Just gave a black screen with a non-blinking cursor.

Reading the [wiki (PowerPC Known Issues)]("https://wiki.ubuntu.com/PowerPCKnownIssues") I realised I needed modify /etc/initramfs-tools/modules.

I learnt a trick a while back from [a different issue]("http://ubuntuforums.org/showthread.php?t=409345&page=2#20") to gain root access to your installed system via the live CD:
```
sudo mount /dev/hda3 /media/root
sudo mount -t proc /media/root/proc
sudo mount -o bind /dev /media/root/dev
sudo chroot /media/root
```
Then at the new prompt you're presented with:
```
gksu gedit /etc/initramfs-tools/modules
```
and when you've finished and saved:
```
sudo update-initramfs -u
```

It boots fine now with the default sequence! Although I don't think it's showing the splash screen like it should.

There's still a few bugs with the settings-daemon I think, but it runs. Now to install a bunch of stuff!!

---

### Post by kavanayy on 2008-03-04
This is how I do on my ibook g4
when you come to the yaboot screen
*live-nosplash-powerpc video=ofonly*
when buzybox
[I]modprobe ide-core
exit[/I]
This can make you get in the livecd and finish your installation,
Before you restart your ibook.
Mount your install volume, so that you can access your /media/disk/etc/yaboot.conf.

*sudo vi /media/disk/etc/yaboot.conf*
Remove splash from all append = lines.

Then run ybin to update yaboot on your new file

*sudo ybin -C /media/disk/etc/yaboot.conf*

**And**
edit the "modules" file in etc/initramfs-tools/ using the Terminal.
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
**ide-core**
# sd_mod
After typing "sudo update-initramfs -u" at the Terminal prompt the system boots properly.


[http://wiki.ubuntu.org.cn/index.php?title=%E5%BF%AB%E9%80%9F%E8%AE%BE%E7%BD%AE%E6%8C%87%E5%8D%97/GutsyGibbon&variant=zh-cn](http://wiki.ubuntu.org.cn/index.php?title=%E5%BF%AB%E9%80%9F%E8%AE%BE%E7%BD%AE%E6%8C%87%E5%8D%97/GutsyGibbon&variant=zh-cn)

---

### Post by kavanayy on 2008-03-10
I tried many times, it works fine.

---

### Post by ljonesj on 2008-03-11
i have a ? i just picked up 2 g4 power macs one is a 440mhz or close or more to that and it has 1.12gb of ram i have another one that i dont know what its specs are but i did not get a keyboard or mouse with these 2 computers how do i get it to boot from a cd from a different usb keyboard and mouse

---

### Post by st0n3cutt3r on 2008-03-11
```

modprobe ide-core
exit
```

will get my system to boot (400 MHz G3 iMac with 512MB RAM), and to load the desktop after installing with the alternate CD, but the GNOME Settings Daemon crashes on log-in every time, also the sound crashes on log-in.  I can't open System < Preferences < Sound either, because it just won't load.   

```
sudo killall esd
``` just returns ```
esd: no process killed
```

I've got no clue beyond that......

---

### Post by st0n3cutt3r on 2008-03-11
> **ljonesj said:**
> i have a ? i just picked up 2 g4 power macs one is a 440mhz or close or more to that and it has 1.12gb of ram i have another one that i dont know what its specs are but i did not get a keyboard or mouse with these 2 computers how do i get it to boot from a cd from a different usb keyboard and mouse

any mouse and keyboard should work fine.  Doesn't have to be apple brand.

Hold C when the computer starts to get it to boot from CD

---

### Post by ljonesj on 2008-03-11
now how do i get it to boot off the cd

---

### Post by st0n3cutt3r on 2008-03-11
Hold C when the computer starts, and then you will probably be prompted to press c to boot from CD.  press c again if that happens 
(small text at the top that'll say 
```
press _ to boot from _____ 
press c to boot from CD
```

---

### Post by ljonesj on 2008-03-11
now i have another problem sorry i am using an old dell moniter for the apple i have it running a ram disk by what it said on the screen then the screen went blank and went into power save mode what have i done i dont have an apple moniter as this worked when the computer was using os9.2

---

### Post by st0n3cutt3r on 2008-03-11
What CD are you using?  7.10 has a lot of issues installing to PPC.
You might try the 7.04 or even 6.06 alternate CDs.

when it starts from CD it will ask you for what you want to do, hit Tab and it will display your options.

I recommend attempting with 
```
nosplash-powerpc
```

and if that doesn't work try with
```
nosplash-powerpc video=ofonly
```

**you type those in as your boot choice, then hit enter.

AFAIK, monitors going to powersave mode is a monitor issue, and not a computer issue.  Generally an automatic thing that happens after X seconds of receiving no signal from the computer.

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by ljonesj on 2008-03-11
using 6.06 alt disc

---

### Post by stream303 on 2008-03-11
Can you get to a virtual terminal, ie by doing CTRL-ALT-F2 ?

If so, we can edit some config files, specifically /etc/xorg.conf to match the specs of your monitor.  What brand / size / crt-lcd is your monitor?

---

### Post by st0n3cutt3r on 2008-03-11
Ctrl+Alt+F1

---

### Post by p1tst0p on 2008-03-12
Interesting,
I have a 24" Dell monitor connected to a Dual 2gh G5.. if i boot with nosplash-powerpc video=ofonly the monitor just goes into hibernation.

I tried CTRL+ALT+F1 to F7, but it didnt switch to terminal, just stayed in power save mode..

Im downloading the 7.04 version to give that a go later.

---

### Post by st0n3cutt3r on 2008-03-12
have you tried just booting it with powerpc and without nosplash/video=ofonly?   I'm really not even sure what got my G3 online anymore with 7.10, except that I KNOW I was using an alternate cd.  The live CDs just force a reboot after about 4 seconds.

I *think* that nosplash-powerpc is what I used to install 7.10alternate on my G3 most recently, but that has a lot of issues that I've been fighting with.  Details here:

[http://ubuntuforums.org/showthread.php?t=719048](http://ubuntuforums.org/showthread.php?t=719048)

---

### Post by ljonesj on 2008-03-16
well sad to say i crashed my system putting that line in the initramfs-tools section  but i think i am going to use the modprobe ide-core as a security feature

---

### Post by tjniels on 2008-03-18
> I personally have had little problems with Gutsy on a ibook G4 PPC, the only issues I had were the wireless, where I had to install them using a wired connection, and the sound which has a workaround on this forum. I initially upgraded from feisty to gutsy using the updater and I ran into quite a few problems, a best bet would be to back up your stuff and do a fresh install of gutsy.

Does your iBook do sleep mode properly?  Does it wake from sleep?  I'm thinking about 7.10 on my iBook G4/800, but I need to be sure it can sleep for several hours per day instead of constantly booting when I need to use it.  I can boot with the live 7.10 CD, does anyone know if the live CD works for installation on the G4 ibooks?

Thanks!

---

