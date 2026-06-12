---
title: "any way to get ubuntu on my powermac g5?"
date: 2008-02-08
forum: Apple PPC Users
---

### Post by skier354 on 2008-02-08
I've tried and tried to get ubuntu running on my powermac g5 and have had no luck. I was able to successfully install ubuntu using the alternate cd on my secondary internal hard drive (I've tried 7.10, 7,06, 6.06). I have read many forums and know that there is a problem with yaboot but I cannot get it to work. I know you have to manually configure it in some cases but I have not been able to get to that point because I have not been able to get ANY live cd to boot on my system. Is there any way to get a stubborn live cd to boot? or is there another way to edit the yaboot config file? I have tried the methods in this post: [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues). When I boot the computer with both hard drives attached (160 gb with mac osx and 320 gb with ubuntu ect...) it flashes the little finder/question mark symbol then proceeds to load mac osx, without even showing yaboot. when I unplug the osx hard drive it loads yaboot but when I press l to load ubuntu it comes up with a distorted finder/question mark box. When I try to load a live cd, it either comes up with nothing at all, or it comes up with the loading splash but it is distorted and eventually the screen just turns to black and seems to freeze like that. I have tried the video=ofonly and everything on the powerpcknownissues page. anyone know what to do? I have tried everything I can find in forums and have come up with nothing. 
system specs:
Powermac G5 dual 2 GHz (model identifier: PowerMac7,2)
ati radeon x800 xt video card 256mb w/dvi
1.5 gb ram
160 gb sata hard drive(osx)
320 gb sata hard drive(ubuntu partitions and hfs+ partition for use in mac osx)

---

### Post by stream303 on 2008-02-08
Does holding down the option key on boot allow you to select your desired boot drive?

In my case, when I boot from a firewire drive, I have to hold down option, wait for the tiny hourglass icon to turn into an arrow, and then select the drive I want to boot from.  More apple docs here:

[http://docs.info.apple.com/article.html?artnum=106178](http://docs.info.apple.com/article.html?artnum=106178)

I'm not familiar with using more than one internal hard drive at a time, but maybe this will help...

---

### Post by skier354 on 2008-02-08
yeah I have tried that too, whenever I do that, I get the disk with the X for mac os x then a disk with the penguin but when I choose the penguin, the colors go all crazy on the icons and it just goes in a loop within that same menu

---

### Post by stream303 on 2008-02-08
Ah, I think this is related to what I had to do to get my external firewire to boot.  Moving yaboot.conf around, blessing it, etc.  I have an easier method idea:

Have you tried leaving only the hard drive you intend to install Ubuntu on in the machine, and reinstall with just that hard drive active, so that yaboot will get written to disk properly?  Once that is done, and is successful as a single-hard drive system, add your other hard drives back into the mix.

---

### Post by skier354 on 2008-02-08
Ok, I unplugged my hard drive with os x and re-did the installation. I erased the existing ubuntu partitions and had it automatically partition the free space. When it finished and rebooted, yaboot loaded but when I presses l for ubuntu, it got stuck when it says "Loading second stage bootstrap..." with the finder/? blinking. I plugged in my os x hard drive and it booted straight into os x without even showing yaboot. still no ubuntu :(

---

### Post by oswaldkelso on 2008-02-08
Have you tried zapping the p-ram I have similar trouble on my g4 tower with it always booting into osx. After I zapped it I got the linux menu x,l,c

---

### Post by skier354 on 2008-02-08
I followed what this site says about zapping pram [http://forums.macrumors.com/archive/index.php/t-1859.html](http://forums.macrumors.com/archive/index.php/t-1859.html) and had no luck. same results as in post #5. I reset it with both hard drives attached and with only the ubuntu drive attached. My machine still boots straight into mac os x. Is it possible to have ubuntu and yaboot on a seperate hard drive from os x?

---

### Post by skier354 on 2008-02-09
I can get yaboot to boot up when i unplug my os x hard drive but when I push l to boot ubuntu it shows the finder/? blinking with screwed up colors. Is there any way of getting yaboot to load ubuntu? I have read that you have to change the yaboot.conf file but I cannot get any live cd's to work so I don't know how I would go about doing that.

---

### Post by stream303 on 2008-02-09
Hrmmm...

Any chance of physically swapping your Ubuntu drive in place of your OSX drive as the only drive on the system and reinstalling to see if it will come up as a single-drive machine only first?

---

### Post by skier354 on 2008-02-09
ok so this is where I am at now: I physically swapped hard drives, reinstalled ubuntu and now when I turn on my machine yaboot boots up, not os x so that should be correct. Listed on the screen is only linux and cdrom, and ubuntu won't load when I select linux. It just brings up a white screen. I believe yaboot.conf is screwed up and I am needing to manually edit it to fix the ubuntu boot and add the osx boot. there is a post in another thread ([http://ubuntuforums.org/showthread.php?t=439629&page=3](http://ubuntuforums.org/showthread.php?t=439629&page=3)) that says yabootconfig does not work with powermac g5's. I booted into rescue mode from the installer cd and executed a shell in the root directory. This is where I am stuck. I am very inexperienced with the command line and am having troubles editing yaboot.conf. I ran ```
man yaboot.conf
``` and it came up with a big thing on editing yaboot.conf. I pressed 'h' and it gave me a "summary of less commands". I tried opening yaboot.conf to edit and cannot seem to get the file to open for editing. any suggestions? thanks!

---

### Post by oswaldkelso on 2008-02-09
list your partitions 

sudo fdisk -l (small L)

theres my yaboot.conf

boot=/dev/hda16
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=17
root=/dev/hda17
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda9

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old

# This entry automatically added by the Debian installer for an existing
# Linux installation on /dev/hda12.
image=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:12,/boot/vmlinux
    label=hda12-Linux
    root=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:12
    append="root=/dev/hda12 ro"
    initrd=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:12,/boot/initrd.img

# This entry automatically added by the Debian installer for an existing
# Linux installation on /dev/hda12.
image=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:12,/boot/vmlinux.old
    label=hda12-old
    root=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:12
    append="root=/dev/hda12 ro"
    initrd=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:12,/boot/initrd.img.old

---

### Post by skier354 on 2008-02-10
ok, when I type "sudo fdisk -l" it shows the partitions for sda and sdb then pauses for a second and the screen fills up with this:
"16547: @ 0 for 0, type=0x0"
except the beginning number is different for each one. This is what my sda and sdb look like: (got these using "sudo fdisk -l /dev/sda" and "sudo fdisk -l /dev/sdb") Sorry it looks so sloppy.

```
            #                                type name         length          base          (size)            system
/dev/sda1     Apple_partition_map Apple        63               1                ( 31.5k          partition map
/dev/sda2        Apple_Bootstrap untitled        1954            558488560  (077.0k)     NewWorld bootblock
/dev/sda3        Apple_HFS untitled         558226352  262208      (266.2g)      HFS
/dev/sda4         Apple_UNIX_SVR2 untitled     63816407     558490514z (30.4g)    Linux native
/dev/sda5        Apple_UNIX_SVR2 swap         2835527       622306921  (1.4g)        Linux swap
/dev/sda6       Apple_Free Extra                     262144       64                 (128.0M)    Free space

Block size=512, Number of Blocks=625142448
DeviceType=0x0, DeviceId=0x0
```

```

            #                                type name         length          base          (size)            system
/dev/sdb1     Apple_partition_map Apple        63                    1            (31.5k)         Partition map
/dev/sdb2       Apple_Free                    262144            64          (128.0M)      Free space
/dev/sdb3    Apple_HFS Untitled             319910848   262208     (152.5G)       HFS
  
Block size=512, Number of Blocks=320173056
DeviceType=0x0, DeviceId=0x0
```

I am still unsure how to write the data into the existing yaboot.conf file. Should I use vi, or what would be the easiest way for me to understand? Thanks for everyone's help, I really appreciate it.

---

### Post by oswaldkelso on 2008-02-10
to edit yaboot.conf

first open a terminal

code:

sudo cd /etc/

this will put you in the directory with the yaboot.conf file.

you can check by listing the things in that directory with

code:

ls

now back up the file just in case

code:

cp yaboot.conf yaboot.confbu

you can check it worked with ls again

now look at/edit the yaboot.conf file

code:

nano yaboot.conf

I think it should look like this but the second line will be relevant to your hardware. but you may want to post it first but I suspect you just need to add the last line? macosx=/dev/sdb3


boot=/dev/sda2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=4
root=/dev/sda4
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sdb3

---

### Post by stream303 on 2008-02-10
When that is done he might also have to issue the

sudo ybin -v

command to make it work once it is edited.  Reboot and tada!

While researching this I just found something that I was never aware of before:  an interactive yaboot configuration routine known as:  **yabootconfig**

So I guess one could try running sudo yabootconfig and answer the prompts.  Interesting.  I never knew we had that utility - at least it is here on my Gutsy box.

Looks like there was something else on that hard drive, and it got partitoned for free space, rather than using the whole disk.  That's another option: wipe out the whole disk and reinstall with only that one disk installed, and when guided partitioning comes up, make sure to change the option to use the whole disk.  Although by now, I'll bet skier354 is about to throw the disk down a mountain. :)

---

### Post by oswaldkelso on 2008-02-10
Thanks for that I totally forgot about the "holy penguin pee" bit!!  That was a good tip about yabootconfig its on my debian system and just gone into my notes. Cheers

---

### Post by skier354 on 2008-02-10
ok, you said to post my info for line 2 of yaboot.conf. I got this using > sudo find /proc/device-tree/ -name '*disk*' and it listed this (I only posted what seemed to fit the same format as what you have on your yaboot.conf):

/proc/device-tree/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@1/disk@0
/proc/device-tree/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0
/proc/device-tree/ht@0,f2000000/pci@5/ata-6@d/disk

I would assume I would want to put the first one in there without the /proc/device-tree. Is this what I would want to do? Thank you all again! 

also, I have tried the yabootconfig thing from the rescue disk but I don't believe it works on certain machines, at least not on mine.

---

### Post by oswaldkelso on 2008-02-10
Sorry I will calify, what I meant.

"I think it should look like this but the second line will be relevant to your hardware."

I mean do not expect the second line to look the same as** mine** as it is relevent to your hardware. the rest I hope :0 would look the same.

This command will go to the correct directory, make a backup and display your yaboot.conf ready for editing.

sudo cd /etc/;  cp yaboot.conf yaboot.confbackup; nano yaboot.conf

I suspect adding this 

macosx=/dev/sdb3

under the line "enablecdboot" is what you need to do. Then as stream303 says you would run 

sudo ybin -v

this would rewrite the yaboot file and make it active.

---

### Post by stream303 on 2008-02-11
So what we need to do is edit your /etc/yaboot.conf file after booting with the rescue mode.

Doublecheck your boot and root lines and edit them to the following, since that is what your partition table shows as boot and root.

Here is where it might get sticky - I just tried recovery mode, and although I am very comfortable with the VIM editor, you may not be.  Hopefully nano will work for you.  On my G5 iMac, nano did not work in recovery mode.  

(RANT!  Why can't we take a tip from our BSD brethren and put the EE (easy editor) on our install/rescue disks?!?! - learning vim is just another hurdle in the way of support for newcomers if nano doesn't work.  Arrrggghhh)

What OswaldKelso is saying is that your device line will look different from his example.  Let's just concentrate on getting the boot and root lines.  It appears that your system will want boot=/dev/sda2 and root=/dev/sda4, just like it is here:

> **boot=/dev/sda2**
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=4
**root=/dev/sda4**
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sdb3

When you've finished making the boot and root line edits and saved the file, issue a ybin -v, or perhaps sudo ybin -v, and reboot

Let's see how it goes from there.  This dual-disk driver issue is starting to get me confused now. :)

---

### Post by skier354 on 2008-02-11
Ok, haha this is such a hassle to get this thing working! Thanks for your help though! So I tried the nano and it didn't work, but I did learn how to use vim and edited my yaboot.conf. After I edited it I did the sudo ybin -v and it wrote the updated version to yaboot. Now when yaboot boots up I can see that yaboot has in fact been changed with the addition of a macosx boot option. This is my problem now: when I press l for ubuntu, the screen just turns white and when I press x, the screen just turns white as well. I let it just sit for about an hour or so to see if it would eventually load up but it never did. It will fortunately boot from the cd when I press c. I'm wondering if I put the correct thing for line 2 of yaboot.conf. I realize that what I have in mine should be different than yours but I am not entirely sure if what I'm using is correct. This is how I managed to find something from my machine that looks similar to yours:

sudo find /proc/device-tree/ -name '*disk*' 

and then it output:

/proc/device-tree/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@1/disk@0
/proc/device-tree/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0
/proc/device-tree/ht@0,f2000000/pci@5/ata-6@d/disk
some other things with firewire ect in the name

Is this the right way to find out the correct info for my machine? And also why wouldn't os x boot? /dev/sdb3 is what I have it set to and that is the large partition holding all of my os x info.

---

### Post by stream303 on 2008-02-11
Cool!  When you boot without a startup disk now, and see the boot: prompt, if you hit TAB you'll see a list of optional startup parameters.  I wonder if the white screen (which I get briefly on my boxes too) is related to the framebuffer.

Take a look at your boot options when you press tab and perhaps try this:

```
live-nosplash-powerpc64 video=ofonly
```

BTW, your device line is yaboot.conf should be automatically detected and hopefully no editing is needed.

---

### Post by skier354 on 2008-02-11
when you say boot without a startup disk what exactly do you mean? when I boot and yaboot loads up, nothing happens when I hit tab and it won't let me type anything except l x or c.

---

### Post by stream303 on 2008-02-11
Hit "l" for linux and then the boot: prompt appears.  That's when you only have a few seconds to hit tab.  From then on the prompt will wait patiently for you for you to make a decision.  (or just hit enter if you got there by mistake.

---

### Post by skier354 on 2008-02-11
ok, something must still be wrong. When I press 'l' no boot: promp appears and it goes straight to a white screen. Here is what I have for my yaboot.conf

boot=/dev/sda2
##line 2 was originally "device=/disk@0:"
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@1/disk@0:
partition=4
root=/dev/sda4
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sdb3
defaultos=macosx
image=/boot/vmlinux
              label=linux
              read-only
              initrd=/boot/initrd.img
              append="quiet splash video=ofonly"

image=/boot/vmlinux.old
              label=old
              label=linux
              read-only
              initrd=/boot/initrd.img.old
              append="quiet splash video=ofonly"

---

### Post by stream303 on 2008-02-11
Ok, another way to doublecheck that device path is:

> ofpath /dev/sda

But it looks like you may have it right.

Ok, you've done sudo ybin -v after editing this file.

Have you run 
> 
sudo mkofboot -v

drum roll......

---

### Post by skier354 on 2008-02-11
hmmm interesting. I did the "ofpath /dev/sda" and it came up with /disk@0: maybe it was right to begin with? I'll change it back to /disk@0: and try the "sudo mkofboot -v"

---

### Post by skier354 on 2008-02-11
didn't work. I changed line 2 to device=/disk@0: and then saved the file. ran sudo ybin -v then ran sudo mkofboot -v. rebooted and same results, white screen after pressing l (no boot: prompt), white screen from x and c boots the cd correctly

---

### Post by stream303 on 2008-02-11
Between the dual disk drivers and cd booting, I'm getting my hd's confused. :)

Try /dev/sdb just in case.  I'm wondering if that machine can only boot from one specific hd physical position...

You'll definitely need a device path rather than a blank disk@0 I believe..

---

### Post by skier354 on 2008-02-11
sorry, I'm trying to see exactly what you mean. Do you mean to put that into the second line in my yaboot.conf?

---

### Post by stream303 on 2008-02-11
I sure wish I had one of those to work on here.  Frustrating huh?

Why the system can't find your ofpath on /dev/sda worries me.

I hate to say this, but unless someone sees the obvious, I'd be tempted to regroup and try it two ways:

With your drive that you intend to install Ubuntu on as your sole internal drive for the time being, reinstall and make sure that when you use guided partitioning to use the whole drive and not just the free space.  This will of course blow out that other apple partition you had in there.  If you absolutely need that, then I guess we stop.  Your other drive has osx, right?

That hasn't proven immediately successful, but we can now go in and take a look at the partition table, and use the ofpath command on that disk to edit yaboot.conf for the proper root and boot lines, and also the proper device line, issue a mkofboot -v and see what happens.

Failing that, I'd try yet again, but this time I would put the drive on the other physical slot, and try a full reinstall again using the whole disk.  If you had to, try editing yaboot.conf, ofpath, etc again, but this time using /dev/sdX, where X might now be "b" instead of "a".

Or you might toss it out the window! (not) :)

---

### Post by skier354 on 2008-02-11
haha, yeah I think I'm about to toss it out the window! :) Well thanks so much for yours and everyones help! I'll have to try some of those other things. I might be able to erase my whole hard drive, if I can find a place to back up all my movies :)  but if that doesn't work I guess I'll just wait until I eventually upgrade to an intel mac. Thanks again!

---

### Post by SLmanDR on 2008-02-13
:KS
I read this thread with great interest. stream & ok have exhibited commendable patience and understanding and have provided clear information. I thank skier for the clear layout of problems. I may get a lot out of this series of posts as I am trying get ANY distro to work on my 970fx PPC G5. I also have a X800 XT (in analog) card running. Dual HDDs. You don't know how glad I am to see this series of posts. Nah, I'm sure you do :) May I continue to lurk?
SL

---

### Post by stream303 on 2008-02-13
> **SLmanDR said:**
> :I am trying get ANY distro to work on my 970fx PPC G5. I also have a X800 XT (in analog) card running. Dual HDDs. You don't know how glad I am to see this series of posts. Nah, I'm sure you do :) May I continue to lurk?
SL

Thanks!  Take into account the fact that I don't own a dual HDD mac, so much of this is guesswork.  It is driving me nuts, however. :)

Ok, so you've tried OpenSuse, Fedora, Debian?

It seems like yaboot just gets confused by the dual drives when it comes time to make the drive bootable, even though you can install it initially.

Just to cut down on all the variables, I'd be tempted to do this:

1) Devote an HD solely to Ubuntu, and let guided partitioning use the whole disk, not just free space (default).

2) Only install one hard drive physically.

3) If possible, remove the other unused hd driver card.

4) If install is then successful, we can put back the other hard drive back into the system.

5) I'm not sure if the dual-hdd prefers to boot from one physical HD location over the other, so I'd repeat this process using the other physical position if this doesn't work,

6) When removing the driver cards temporarily, I'd be tempted to zap the pram to make sure the system doesn't retain a ghost drive setup.

Don't try this on a system that you aren't prepared to lose data on :)

---

### Post by SLmanDR on 2008-02-13
It wasn't my intention to hijack skiers post but here's what I have.
I've tried Live CD's and install CD's and DVD's from Ubuntu and the BSD's, Fedora and debian, and Slackware and Open SUSE. They all never got to install , instead experiencing kernel panic. See my post for an example: [http://slmandr.wordpress.com/2008/01/31/my-bsd-journal]("http://slmandr.wordpress.com/2008/01/31/my-bsd-journal"). I think I will take some tie this weekend and go back to Gutsy and debian Etch with your suggestion to use a single HDD in the machine and do a whole disc install and see what that looks like. I haven't done that as I always was attempting to keep a dual boot machine. Something else that strikes me is that every attempt at install messes with the system clock. I'll post with progress report. Also I see many recommendations to not use PPC64, instead using PPC (32 bit) iso. Thanks again.

---

### Post by stream303 on 2008-02-14
> **SLmanDR said:**
>  I haven't done that as I always was attempting to keep a dual boot machine.

Dual booting should be no problem after a good install of Ubuntu and we put the other hard drive back into the system.  Maybe triple boot OpenBSD or NetBSD?  That would be interesting.

---

### Post by skier354 on 2008-02-14
> It wasn't my intention to hijack skiers post
by all means, hijack my post haha, I hope you can get your system up and running! If you can do it, I might try again also. Best of luck.

---

### Post by SLmanDR on 2008-02-17
Well I stripped down to 1 HD in the upper slot. Formatted in Disk Utility for Free Space. I went through all of my Edgy Eft and ?7.1 Ubuntu disks, my 3 BSD's, SUSE, etc. They all get stuck in the CD boot. Can't get to install at all. :) The only CD I was able to get to install was Slackintosh. Every thing went well, learned about mac-fdisk and devices and all that. I get to reboot time and the system restarts to Yaboot ok. Select Linux and then the system stalls at the (white) Open Firmware screen. The clock reads 1904- many years before the build date. So I need to go learn about what is happening at this point. It doesn't look like an issue with having two drives in the bay at the same time. I have to give it a break for a while before I get back to it. Phew.

---

### Post by stream303 on 2008-02-18
> **SLmanDR said:**
> So I need to go learn about what is happening at this point. It doesn't look like an issue with having two drives in the bay at the same time. I have to give it a break for a while before I get back to it. Phew.

I know how you feel - been there too many times. :)

I'm starting to wonder if we need to trick yaboot with master/slave jumpers or cables for dual-drive setups initially, and then be able to put them back afterwards.  Remember I'm not at all familiar with dual-drive macs, so this is purely speculation.

It seems that with an earlier test, yaboot was finally able to be written automatically by the system without that warning, but when you inspect yaboot.conf, it has no real info in the device lines etc.  Is a master / slave issue involved here for Linux, whereas OSX has no problem?

The date we can fix, and the white screen might be fixed with a kernel parameter at boot time such as Linux video=ofonly maybe.

Again, just guesswork on my part.

---

### Post by stream303 on 2008-02-19
Ok, here's the solution.  All you have to do is this:

[http://ubuntuforums.org/showthread.php?t=439629](http://ubuntuforums.org/showthread.php?t=439629)

Whew.  Looks like we weren't the only ones dealing with dual-drives. :)

---

### Post by SLmanDR on 2008-02-19
=D> > [http://ubuntuforums.org/showthread.php?t=439629](http://ubuntuforums.org/showthread.php?t=439629)
I will take some time to study and rewrite a condensed version I can use while off-line.
It's amazing what you can miss just by not quite getting the search terms just so. 
Many thanks.

---

### Post by skier354 on 2008-04-24
I was able to fix yaboot and get ubuntu running with a fixed ofboot file. It turns out that the system could not find my correct open firmware path. I still am having some graphical issues but at least I can boot into ubuntu now. [http://ubuntuforums.org/showthread.php?t=758301]("http://ubuntuforums.org/showthread.php?t=758301")

EDIT: The above thread will fix your yaboot problem if you are having troubling booting up. Take a look at post #8 by pxwpxw.

---

### Post by stream303 on 2008-05-06
Ah, with that radeon, have you tried disabling glx and dri in your xorg.conf?

---

### Post by SLmanDR on 2008-05-06
[QUOTE=stream303] Ah, with that radeon...[/QUOTE]
skier 354 and I have the X 800XT graphics card installed. Coincidence we have similar problem with graphics issue? Didn't think so.:) If skier would be so inclined perhaps he could follow your instructions and or reinstall his original card and have a go at installing Ubuntu again. I'd have done this previously but I accidentally disposed of my original card.:mad: Seems to me all these prob's relate to this card. Slackintosh may be the only distro to be able to allow the use of the X 800XT.
Regards, SLmanDr
[http://slmandr.wordpress.com/about-me/](http://slmandr.wordpress.com/about-me/)

---

### Post by skier354 on 2008-05-08
I'd be willing to take another go at ubuntu :) I only have the x800 xt card though. I actually thought it was the original card, I didn't in fact buy this machine as I was lucky enough to get it for free. Question though, which version of ubuntu should I try? It seems that hardy has been more difficult because of xorg.conf problems. I also noticed something interesting in the jumbled display, I could have sworn I saw half of an apple (the same as in the upper left hand of mac os x). Maybe it was nothing but I'm sure it looked just like it. I'll grab a picture if I see it again. I was also thinking that I should try to get it up and running in a non dual boot environment. I could remove my os x drive completely and use some free space on my storage only drive. Also did you see the screenshot of my jumbled screen on my [[COLOR="Navy"]other[/COLOR]]("http://ubuntuforums.org/showthread.php?t=771507") thread SLmanDR? Is yours similar to that?

---

### Post by SLmanDR on 2008-05-08
Huh, a PPC G5 for free, neat :) Somebody playing Halo on it no doubt with the X800 XT. It's a helluvan AGP card. Old but good. Never saw that screen you snapped before. I always got completely black or hung on OF white. I don't know well enough to recommend a Ubuntu version. I'd say the latest stable release would be the best bet. But I got the farthest with Slackintosh. I installed it thru the graphic installer. Something I was never even able to get to with any other distro. I ran out of time and patience when the restart didn't work. So many distros have in the documentation that the PPC G5 or SATA drives are not supported. I have settled down to Leopard for the time being. I hope Apple puts support in next release for my SE W580i cell phone. I have my iTunes all airported around the house, everything works. I'm lazy and happy enough for now. If I had another machine though... instead of mucking with my "production machine", I'd be thinking different. [IMG]http://www.drumchat.com/images/smilies/drumset-1.gif[/IMG]
Regards! S

---

### Post by skier354 on 2008-05-09
Yeah it was a good deal, actually an xbox360 dev machine from microsoft :) my dad's been in the gaming industry until recently. I will have to try to get ubuntu up and running again. And try out slackintosh if that can't get anywhere too.

---

### Post by skier354 on 2008-05-12
Hmmmm, ok so I installed ubuntu a little differently this time, I partitioned some space on my storage only hard drive and switched around the hard drives so that mac os x is now in the secondary slot and ubuntu and storage is in the first slot. It shouldn't make any difference, I just wanted to leave my mac os x partition alone. I can get ubuntu to boot up but I still have that terrible login screen. I did disable "glx" and "dri" in my xorg.conf but I saw no change. Has anyone managed to get ubuntu up and running with this configuration?

EDIT: I found [[COLOR="Navy"]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/93509") bug that I believe is relevant but it seems to me like it is outdated now, maybe not though. (I guess this isn't news to you SLmanDR, as you were involved with that thread)

---

### Post by stream303 on 2008-05-12
I'm not sure if this helps, but have you seen the latest firmware upgrade for single processors from late 2007?

[http://www.apple.com/support/downloads/powermacg5uniprocessor515f2firmwareupdate.html](http://www.apple.com/support/downloads/powermacg5uniprocessor515f2firmwareupdate.html)

As always, YMMV. :)

---

### Post by skier354 on 2008-05-15
I actually have the dual processor model so it says that the update is not applicable to my machine. So by looking around on the internet, it seems that the main issue with my machine is the x800 xt video card. Plus it doesn't help my efforts that my dvd drive just went out on me :(. I will post anything I figure out for fellow x800 xt owners as it seems that other graphics cards work just great (look at [[COLOR="Navy"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=726697") post).

---

### Post by stream303 on 2008-05-21
I gotta' throw this out there - even though I don't own the hardware...

Is the card in the right slot - I believe the 8xagp pro slot which is slot-1?

I saw a reference to the minimum system ram specs for OSX to be 512m when using that card.  Not sure it applies here..

Anyway, just a thought in case the card seems to work in another slot not really intended for it.

.. remember, this is coming from someone who doesn't even own the hardware, but I'd LOVE to have that card myself. :)

---

### Post by skier354 on 2008-05-22
Well on my machine there is only one slot that it will fit in as it has some sort of extra plastic part that won't fit in a regular slot. If this is different for anyone else please post. This card has been great to me except for two minor things, no ubuntu and the original fan went out so I put a huge Zalman fan on it :D.

---

### Post by stream303 on 2008-05-23
Another idea from the cloud..

Are you able to disable "DDC" from either your xorg.conf, or in the monitor itself?  I know some of the Apple monitors had the ability to turn DDC off in the menus.

---

### Post by skier354 on 2008-06-07
I'm sorry I have not posted for so long, I think I have officially given up on getting Ubuntu up and running on my Powermac G5 with ati radeon x800 xt. I believe it is possible without this card, but many ppc distros state that it is not supported. Thanks for all the help, I think I'm gonna sell it and buy an intel mac :)

---

### Post by cyberdork33 on 2008-06-08
> **skier354 said:**
> I'm sorry I have not posted for so long, I think I have officially given up on getting Ubuntu up and running on my Powermac G5 with ati radeon x800 xt. I believe it is possible without this card, but many ppc distros state that it is not supported. Thanks for all the help, I think I'm gonna sell it and buy an intel mac :)
You should post in the new Apple Forum from now on for both PPC and Intel Macs:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by SLmanDR on 2008-06-19
I had a fan problem with this card as well. [IMG]http://www.myfandoms.com/forums/images/smilies/blowup.gif[/IMG] Not that bad. I had tube of synthetic oil left from my tape deck days and put a miniscule drop of that on the bearing surfaces and resurrected the fan. Works fine now but I think ATI put a cheepo fan in the X800 XT.
SL
PS: if anyone tries this remedy DON'T use a dino oil. It will gum up quick and you will have compounded your problem.

---

### Post by bleedingpowers on 2008-06-26
> **SLmanDR said:**
> It wasn't my intention to hijack skiers post but here's what I have.
I've tried Live CD's and install CD's and DVD's from Ubuntu and the BSD's, Fedora and debian, and Slackware and Open SUSE. They all never got to install , instead experiencing kernel panic. See my post for an example: [http://slmandr.wordpress.com/2008/01/31/my-bsd-journal]("http://slmandr.wordpress.com/2008/01/31/my-bsd-journal"). I think I will take some tie this weekend and go back to Gutsy and debian Etch with your suggestion to use a single HDD in the machine and do a whole disc install and see what that looks like. I haven't done that as I always was attempting to keep a dual boot machine. Something else that strikes me is that every attempt at install messes with the system clock. I'll post with progress report. Also I see many recommendations to not use PPC64, instead using PPC (32 bit) iso. Thanks again.
I have a similar problem with my PowerMac G4. I have a hard drive with yaboot already installed, so I'm able to get past the booting from CD-rom prompt. However, when the cd starts loading the kernel and all the stuff, it gets frozen and I just get a "Loading devices, please wait" message or just an underscore in a blank screen. 

I'm trying a few different flavors of Linux distros (Debian, Ubuntu, Fedora, YDL, SystemRescueCD), and I'm still unsuccessful. What am I doing wrong? I even tried options like the recommended:  'install video=ofonly' or 'live video=ofonly'.

Should I try booting with a re-formatted hard drive? Perhaps, it's the old swap partition is causing conflicts?

Please, help. I really want to get rid of MacOS X. However, I had success with my imac G4. I'm not sure what I'm doing wrong with this other machine (PowerMac G4).

---

### Post by stream303 on 2008-06-27
I'd definitely heed the suggestion to post in the newer Apple forum, instead of this reply-only archived one to get wider exposure.

My first suggestion would be to use the "alternate" installer image, rather than the live-cd desktop:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

You may also want to try using the "nosplash" parameter when you reach the second-stage of the yaboot boot: prompt (hit -tab- to stop the auto countdown)

```
Linux nosplash
or
Linux video=ofonly nosplash
```

Also best to provide some more details about your G4 Powermac such as speed, and also onboard ram.

---

### Post by karryjonjon on 2008-06-27
With the approach of the Beijing Olympics, people will focus more and more on the Olympic events. Whether Dalai be left out after the Olympics is no longer a question. What the westeners think highly of are  not only China's economic power of , but also China's political and diplomatic power. On the one side is China, on the other side is Dalai. It is doughtless which one is much important in the heart of the Westeners.

Therefore, if Dalai continues to give political performances on the international stage while China shows goodwill to him, it means he himself gives up these opportunities.

We all clear about how much sincerity with what Dalai has said, including those Good words. If Dalai really cherish the opportunity, he will make up his mind, and reply the Central government's goodwill with concrete actions. What's more, this kind of actions should solve real problems. Only in this way can the Central government dispel the distrust and wariness on him. While in those days, the distrust and wariness were much heavier because of the political and international shows of Dalai. If Dalai misunderstands the support from the Westen countries, asks for a sky-high price, and even connive at exile tibetans's voilence and behaviers which enraged the central government, it will only futher worsen the relations with the central government, and even let the central government make the final desicion to abandon him. This is not imporsible.

---

