---
title: "Need Alternative CD for No-CD boot PowerBook"
date: 2007-07-14
forum: Apple PPC Users
---

### Post by fl1pper on 2007-07-14
Went to one of the ubuntu sites and it said, “If you need an alternative because you can’t boot from a CD, go here” and it gives an URL to the main ‘Download’ page and there is no PPC choice, only i386 and a defunct Solaris, etc.

Now what? My internal SuperDrive is dead, and my external firewire drive (a 52x LaCie drive) will absolutely not boot anything. When I did a recent install of OS X at an Apple Store, even they had to use my drive booted in Target Mode, to access it, rather than booting my laptop from their installer. It’s a pain in the *** that I’ve learned to live with pending my having $300 for a hardware rebuild (and a one-week turnaround time) from Apple.

So, where is this ‘alternative’ CD downloadable from? And is it even possible to install ubuntu on a laptop that does not have a bootable CD/DVD drive, at all?

Thanks a bunch,
~flipper

---

### Post by stmiller on 2007-07-14
Check out the sticky at the top of this forum section. There are links for the download.

---

### Post by fl1pper on 2007-07-15
Thanks for the tip. I'm not sure how I missed that, but I did. I had Ubuntu running on an old Ti-Book about three years ago, and I see that spanned desktops are still an issue, but what's really worrying me is the fact that the Airport Extreme has to be enabled by a further (non-builtin) download. I'm on wireless only, no Internet at home, at all, so, no Ethernet router. I know zero people here in Syracuse, so I'm thinking that even in the initial CD-based install the installer is going to want to be 'connected' to the Web, right?

Is there any way to just use the Mac Terminal to get the initial wireless files and then run from there on out through the Ubuntu installation, or is that just way beyond what's possible? I'm pretty sure I can at least access the Linux installation while booted into Mac OS, so I'm thinking I could just move files to their correct locations, and go from there, once the initial install is done. Does that sound feasible?

Thanks for any advice.

---

### Post by pxwpxw on 2007-07-15
Might be easier to do an hd-media install, where you can donwload the CD iso to Macos and then get a basic Linux install done, without using the network during the install. I think that would work. Then sort out the wireless config by transferring whats needed from Macos to Linux. But that would depend on how you have Macos set up, and what version Mac you have, and how to make room for ubuntu partitions. You need to be carefull not to demolish the Macos during the ubuntu install.

---

### Post by stmiller on 2007-07-15
> **fl1pper said:**
> Thanks for the tip. I'm not sure how I missed that, but I did. I had Ubuntu running on an old Ti-Book about three years ago, and I see that spanned desktops are still an issue, but what's really worrying me is the fact that the Airport Extreme has to be enabled by a further (non-builtin) download. I'm on wireless only, no Internet at home, at all, so, no Ethernet router. I know zero people here in Syracuse, so I'm thinking that even in the initial CD-based install the installer is going to want to be 'connected' to the Web, right?

Is there any way to just use the Mac Terminal to get the initial wireless files and then run from there on out through the Ubuntu installation, or is that just way beyond what's possible? I'm pretty sure I can at least access the Linux installation while booted into Mac OS, so I'm thinking I could just move files to their correct locations, and go from there, once the initial install is done. Does that sound feasible?

Thanks for any advice.

Do you have a dual boot going, with usable wireless with OS X for the time being? You can extract the firmware from the Airport Express driver from Apple. See this old gentoo thread: [http://forums.gentoo.org/viewtopic-p-2933009.html#2933009](http://forums.gentoo.org/viewtopic-p-2933009.html#2933009)

Basically the firmware files need to be put into /lib/firmware
and the wireless will work.

---

### Post by fl1pper on 2007-07-16
Thanks. That sounds very doable. I'm in an updated Mac OS environment (10.4.10), and have aqn extra partition on the internal drive, set aside for a Linux install. As I recall from several years ago, I had four files (yaboot, the yaboot config file, etc) that were probably on the partition that was getting the ubuntu install, but my memory is hazy on that. I'm assuming that when doing the hd-media install I can point the installer at any partition I want and it will go through the usual "choose a partitioning scheme' or let me go manual. Last time I just created a swap partition within the set aside partition, and a small (500KB or so) partition for the boot, and had the installer do the rest of the set aside partition as an ext. system.

It worked great. I never should have messed with it. (I lunched my main Mac OS somehow, and decided that since the install was so easy on the Linux side, to just wipe the drive, but the SuperDrive died at the same time, so not being able to do the simplified net install, I downloaded all of a Debian install and goofed up, ending up with a big mess of small partitions and could never boot into the Debian install after the first, initially successful reboot.)

I'll research the ins-and-outs of the hd-media install, before posting any further, but if you do have, or stumble upon some critical advice/caution, and have the time, please let me know. Thanks again for being so helpful.

All the best,
~flipper

---

### Post by fl1pper on 2007-07-17
I read through the documentation for the hd-media boot, and am obviously in way over my head. It was all a lot simpler two or three years ago. I never had to think about using partd or any of that stuff, just load the CD and pick the volume/partition, select a file system, and it was OK, OK, OK, OK, OK, OK, reboot. Done.

Now they're talking about setting aside boot partitions that are 'high enough' in the file structure and all this other jazz that is not my strong suit. Dragging the four files: yaboot, yaboot.conf, vmlinux, and initrd.gz... to, where? the /C drive? WTF? They mean the root of the main drive? I only have one drive internally with two partitions, my startup partition and another 15GB 'empty" and I have no idea where they're talking about, or how they expect a Mac to boot from an ISO, or any of it. greek.

---

### Post by pxwpxw on 2007-07-18
Sounds like you have been looking at old PC intel stuff. 
Try this summary for ppc
[ **Net/hd-media-install**]("http://ubuntuforums.org/showpost.php?p=2887410&postcount=4")

You just put all 4 files (or 5 with hd-media) in your Mac startup partition root, then boot yaboot from open firmware to the installer, the installer automatically finds the iso. After that it looks much the same as an install from CD. The 4 installer files for hd-media and netinstall are different thats all. 

When you cant boot a rescue or re-install from a CD it becomes critical to make sure you have an alternative boot (netboot, macos or a usb stick) depending on your system specs. Macos is at risk during partitioning for ubuntu.  In case of disasters, it should be possible to reinstall MacosX from an external firewire dvd drive, but not ubuntu. But you seem to have a problem there.

You can also use MacosX to put the 5 files (including an alternate CD iso) on a macos formatted usb stick 1GB will do, then you have a backup external usb ubuntu install/rescue using open firmware boot. So you can reinstall any time. No wireless required. You could probsbly drop a set of bcnm43xx firmware files on the usb stick and add a network install option.

Some of these options depend on what apple mac version you have.
For the ubuntu installer you need to get some preliminary partition info from MacosX.

---

### Post by fl1pper on 2007-07-21
Thanks pxwpxw,

This is starting to sound doable again. :)

I have another old PowerBook on the way in the mail right now, and it has at least a combo drive, if not the Super, plus I have a bootable backup of my main internal drive, so I'm not sweating losing macOS as much as I would be normally.

If I can get a hold of a decent FTP client in Linux (and I know they're out there) I'll end up switching one of the laptops to Linux-only, and use it for all the web-based stuff, and keep the Mac OS to run Adobe.

I'm determined to get this right, just going a lot slower due to some hardware messups. Thanks to you (and everybody) for keeping me in the situation here.

~flipper

---

### Post by guidop on 2007-07-21
As an aside, since you will now have a firewire equipped Mac with a good optical drive, you should be able to do this:
- Connect a firewire cable between the two.
- Boot the iBook with the good optical drive into firewire target mode by holding down the "t" key.
- Insert a bootable install CD in the good optical drive.
- Boot the Mac with the bad optical drive while holding down the "option" key, and when it's done scanning for all bootable disks, select the install CD to boot.

I did the above with an old eMac in target mode to reinstall OSX on a 12" Powerbook.

I eventually bought an aftermarket superdrive for $140 from [www.macsales.com](www.macsales.com), and used the instructions at [www.ifixit.com](www.ifixit.com) to replace it.  I had to download PatchBurn from [http://www.patchburn.de/](http://www.patchburn.de/) to get it to burn CD's and DVD's.  It took a half a day, and I needed to buy a Newer Tech screwdriver set, but my DIY cost less than half what a professional repair would have.

---

### Post by fl1pper on 2007-08-15
Thanks for the ideas. A funny thing happened here, though. I was having no SuperDrive in the Aluminum PB, and then the same day that I received the 'good' Ti-Book, I decided to pop a DVD into the 'bad' one, and it worked. It had one of those 10.4.8 reinstalls, from Apple, (instead of the 10.4.0 that I have to install with, so all those updates are streamed in on the one installer). so now I have two working laptops, and still, neither one of them wants to finish the ubuntu 7.04 install.

I used a 'live' CD on the Aluminum, and it as fine, but the CD I was using, was older than my OS, and maybe messed up, so it hung, 5 times oin a row, at the 43% point of the 'writing system files' place. Bummer. Obviously the drive was clobbered, and I ended up with no Linux, and having to re-install the OS X just to be able to work.

On the Titanium PB (1 gHz, 1 g RAM), the same CD was not getting past the initial verbose file checks. It would go to the next screen and just explode in washed out colors, despite trying every suggested CLI boot 'word' .

So late last night I downloaded a 'Feisty' installer ("ubuntu-7.04-desktop-powerpc.iso") and just now, here in the grocery store where I get Internet access, the installer made it to the second screen, went into a routine of some kind with an "in use, or 'operatinal' graphic, then went briefly back to a lone cursor, then back to the 'progress bar', and then did a nice, quiet 'killall -9' by the look of it. Heheh. 

I won't know until I get home if the thing will make it through the whole install on the newer Aluminum PB. And it kills me that it's so tricky on the Titanium, because I had done installs on an old 667, 2 or 3 years ago, and it was a breeze. It was, watch the verbose file check, select the partition, choose a filesystem, and hit OK a few times and boom, no sweat.

At this point, I don't get it. Why two years later, it's seems so dense. Even with Dapper, my older CD, on the Aluminum, before it finally froze at the halfway written point, I finallly had decided to clobber the entire drive, rather try to manually partition the second partition on the drive, for the simple reason that the installer offered all the types of 'partitions' (etc, home, \, swap, etc.), but there was no way to pick a size for any of them, so I just thought, screw it, I'lll do my Adobe bulllshit on the Ti-Book, and just run Linux on the Aluminum. 

Whatever, we'll see what happens later. Maybe I'm just getting retarded, but with two 'books' running great at this point, it seems the install should be a semi-no-brainer.

---

### Post by fl1pper on 2007-08-27
Okay, after being very delayed, I have an update. One, on an unrelated note, the Worldwide Skype outage two weeks ago caused me to reinstall OS X on both of my laptops (I thought I had screwed up the situation with Skype, because Skype didn't acknowledge the problem on their end until a week after the system started unraveling...

Side effect: My SuperDrive now works on the Aluminum PB.

I do not have any ethernet connect at home, relying on wireless, only, so the Aluminum, which has only Airport Extreme, is problematic for the install, and the Titanium will not present a coherent desktop when booted from the Ubuntu installer CD...

All this is obviated, to a huge degree, by the really generous advice I've gotten here. The 'delay' in my project is really a lot of situations (like staving off starvation, etc) that are not connected to the project at hand.

I have one minor problem or issue, at this point, and that is this: Several years ago, when booting from OpenFirmware into yaboot, I could see both partitions on one internal drive, select the one I wanted (the non-OS X boot partition) and then select ext3 from a drop-down menu and the 'spare' partition would get configured, automatically, and the install would commence. 

It was so easy, even I could do it. It was literally, choose the partition, select the file scheme, hit 'OK' 6 or 7 times, and Done. Nowadays it seems problematic. I do not want to over-write/partition the current OS X partition. I have a 15 GB partition all ready for Ubuntu, BUT, as soon as I select the partition, itself, the installer no longer offers any 'auto' file system config, and instead expects me to set up the /, /home, and 'boot' partitions, myself. 

I tried this on one of the laptops, repeatedly. never got it right. And wound up with no Linux, and my mac booting from sector 10 instead of 1 or 2. So that the boot partition to start the OS X bootstrap script was initiated from d0s1 or s2, but the OS was now residing on d0s10. Crazy. It might have been booting from a 'higher' sector, because there was a momentary 'suitcase w/question-mark' flashing right before it went into the initialization script.

I'd really like to avoid creating a dozen 'useless' sectors. The Mac likes things a 'certain way', it seems, and my pathetic work life depends, 100%, on my having a working system, 100% of the time. (Hence the second laptop, and redundancy all over the place, both local and remote).

But I'm giving it another shot. I do not give up easily, especially when I've 'done it before' for the most part. I had a working Debian install on my first attempt, once, so I'm not that inept, or maybe I was just lucky, either way... onward, and thanks again to everybody who has offered advice and great references, etc. 

I do wish there was an Installer that had the config for the Airport 'g' card driver streamed-in up front, but, hey...

~flipper

---

