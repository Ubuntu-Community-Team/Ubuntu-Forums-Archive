---
title: "Is it worth installing Ubuntu on a Macbook 5,2?"
date: 2011-05-16
forum: Apple Hardware Users
---

### Post by jamesjenner on 2011-05-16
G'day all,

I've got a Macbook that just sits on the desk gathering dust. As I'm looking at returning to Uni soon I suspect I will get some use out of it, but I find OSx uncomfortable to use. I currently use XP at work (they're migrating to 7 soon) and 11.10 at home, while a couple of other devices at home have win 7 on them. 

I'm not really inclined to 'learn' OSX as I have no need for it right now. I also don't ever intend to purchase another Mac based device.

As such I've been doing a bit of googling and I've discovered various people complaining about heating issues, fan speed issues (which I think is related to the heating issues) and battery life (which again I presume is related to the fan speed issues). This makes me apprehensive about the switch. While I do wish to use Ubuntu, I don't wish to reduce the battery life or increase the speed of the fans to a dull roar.

So, I'm curious what are people's general perception from actual use of Ubuntu on a Macbook? Is it worth the hassle of installing ubuntu? If I do, is there any reason to keep OSX?

Any recommendations appreciated. 

Cheers,

James.

PS. would have created a poll but found out you cannot do that in the support forums. If this post is deemed inappropriate for support then please move, but I wanted it in an area where Mac owners would be.

---

### Post by jamesjenner on 2011-05-16
Well no replies, so I thought what the hell, lets do it anyway. From what I can tell from the guides I'm only allowed to install Lucid. I would really like to use Natty so I reckon why not give it a bash and see what happens, I can always reinstall with Lucid if Natty is that big of a deal.

Wish me luck. However I would still like to know the answer to my questions.

Cheers,

James.

---

### Post by jnorthr on 2011-05-16
Dont know any reason why you cannot use natty unless your macbook is very old and uses the PPC chipset rather than an intel processor. If you have a PPC processor you may have a limit on your choice of which ubuntu to try.

First create a backup of anything on your macbook that you value - it is almost certain that you will loose anything on the macbook when you install.

Would also suggest that you first create a live CD of natty and try running ubuntu from the live CD before you start the install process. Yes it will run much more s l o w l y   while you are testing but you may decide that learning linux is too much trouble. also suggest getting in a crate of fosters and have a second machine connected to the internet so you can still reach us here on the forums.

eventually you will decide to do a full install or use the "dual-boot" choice. then we can go from there. 

welcome to ubuntu :D

---

### Post by JohnAtilano on 2011-05-16
I'm running Natty 64-bit on my MacBook Pro 5,1.  When I run Ubuntu, it is slightly warmer than OS X but not "hot."  Fan speeds have also not been an issue for me as well.

You should definitely keep a copy of OS X on the MBP.  If only to get firmware updates for the hardware.  Additionally, I find OS X incredibly more stable than Ubuntu.  I use OS X as my primary system.  Ubuntu is for play (No offense, gentlemen.  This is just how I use both systems).

I've always installed from a LiveCD after testing (as jnorthr recommends). 

The only time I've lost my OS X partition is when I installed the bootloader to /dev/sda.  Install to /dev/sda3 or whichever partition your Ubuntu system will be installed.

When booted from the LiveCD I always use gparted to create my partitions before the install.  I only assign 30GB total to ubuntu.  My current partition looks like this:

sda1 = EFI
sda2 = Mac OS X
sda3 = Ubuntu (9.3 GB)
sda4 = /home (for Ubuntu) (19.7 GB)
sda5 = LinuxSwap (1.0 GB)

Ensure you install grub to sda3 or you will wipe out OS X.  I've never tried but I have heard you MUST have OS X installed in order to run Ubuntu.  I've never tested this theory though.

I posted a ["how to"]("http://johnatilano.com/dual-boot-mac-os-x-and-linux-mint-9-on-a-macb") article on my blog.  The instructions are for Linux Mint 9 but I used the same process for Ubuntu 10.04, 10.10, and 11.04.  The screen shots are slightly dated but it sounds like you know what you are doing.

Hope this was helpful.

---

### Post by 3rdalbum on 2011-05-16
If it's a Macbook, it has an Intel CPU. Apple's older laptops with the PowerPC processors were called Powerbooks.

To the OP: Not all computers are the same. If someone says "Don't use Natty on a Macbook", you'd have to take that with a grain of salt because different Macbooks have totally different components in them; although they have the same name, they're completely different; you'd have to go by model number or model revision.

---

### Post by jamesjenner on 2011-05-16
Thanks peoples for your responses.

Well it's been an interesting experience. I followed the guide that can be found from the sticky but forgot the gparted step (instead I changes the partitions via the install tool). It appeared to install okay, i rebooted, got the sync issue (though it said update the MBR, which wasn't the same message but figured out after meant the same thing) and got the two options.

Here's were it got weird. I ended up with two main options when booting. One was for OSX and one was for "Legacy OS" with a pseudo windows grey logo. When selecting it would say no operating system found. 

So I'm now trying to reinstall and checking the partition and install options to make sure i did it right. I remember there was an option to choose where to write the boot something or other (I presume it was talking about grub but don't remember it saying grub) and chose correctly based on above comments. So I'm going to try again and take note of what options I choose.

For "Preparing to install Ubuntu" I've chosen:

[INDENT]YES - download updates while installing
YES - install this third party software (which was for MP3s).[/INDENT]

Hmm in the Allocate drive space I have:

```

Device         Type    Size       Used
/dev/sda
 free space            0 MB
 /dev/sda1     fat32   209 MB     209MB
 /dev/sda2     hfs+    34225 MB   23695 MB
 free space            215624 MB  
```

I don't understand why there is the first free space, or what the fat32 is. 

Last time I left it like the following (or very similar):

```

Device         Type    Size       Used
/dev/sda
 free space            0 MB
 /dev/sda1     fat32   209 MB     209MB
 /dev/sda2     hfs+    34225 MB   23695 MB
 /dev/sda3     swap    1000 MB    unknown
 /dev/sda4     ext4    214624 MB  
```

At the bottom is a "Device for boot loader installation:" option, which I set to /dev/sda4. 

Is that correct? Options are:

/dev/sda ATA TOSHIBA MK2553GS (250.1 GB)
/dev/sda1
/dev/sda2 Mac OS X
/dev/sda4

Only other option I can see is to go "Back" and try another option but I couldn't see an appropriate choice other than the manual selection of how to do the allocation.

:edit:

just realised, should I change the title or post a new thread considering I've changed the thread to discuss my installation problems?

---

### Post by JohnAtilano on 2011-05-16
fat32 is your EFI partition.  It's part of Mac OS X.  Don't mess with it.

Use gparted to create your partitions BEFORE you install Ubuntu.  For you, just make two partitions.  One for ubuntu and another as swap.  Grub (bootloader) will go onto your Ubuntu partition.

---

### Post by jamesjenner on 2011-05-16
> **JohnAtilano said:**
> fat32 is your EFI partition.  It's part of Mac OS X.  Don't mess with it.

Use gparted to create your partitions BEFORE you install Ubuntu.  For you, just make two partitions.  One for ubuntu and another as swap.  Grub (bootloader) will go onto your Ubuntu partition.

No worries will try that. Is there any reason why it cannot be done during the install process?

---

### Post by jnorthr on 2011-05-16
any news jimmy ?

---

### Post by eenu on 2011-05-16
Hey there!

I don't mean to hi-jack a thread but I have a question related as I am looking at making my Macbook Pro fully Ubuntu. I am just wondering with either option 1. Install just Ubuntu or 2. Dual boot it with OSX is it possible to get the machine back to the way it shipped from the apple factory? 

I see things about changing EFI etc and that sounds like there are a few things being tweaked where there maybe margin of error for me going back to a full mac with OS X again.

EDIT: Just seen this [http://ubuntuforums.org/showthread.php?t=1743664](http://ubuntuforums.org/showthread.php?t=1743664)

---

### Post by jnorthr on 2011-05-16
off hand, i would say that it is unlikely that you could get your system back to the way it came from the factory, and anyway - why would you ?

Do you really KNOW if you like ubuntu enough to trash your mac ? Try getting a live CD of 11.04, i expect you can look in wh smith for the next issue of linux user & developer where they will probably have a live Cd with the 11.04 ubuntu release. Boot from that cd and take it for a test drive before you commit. Then we can talk install !):P

---

### Post by eenu on 2011-05-16
> **jnorthr said:**
> off hand, i would say that it is unlikely that you could get your system back to the way it came from the factory, and anyway - why would you ?

Do you really KNOW if you like ubuntu enough to trash your mac ? Try getting a live CD of 11.04, i expect you can look in wh smith for the next issue of linux user & developer where they will probably have a live Cd with the 11.04 ubuntu release. Boot from that cd and take it for a test drive before you commit. Then we can talk install !):P

I've been using it for years in VM. I just don't know if i want to go full time on it yet. I would like to run it natively though to see if it wil change my mind but if I can't go back with out hassle I guess I won't bother. Thanks for your help.

---

### Post by Onoku on 2011-05-16
Not sure what version my macbook is, got it refurbished in 2009... but 10.10 works excellent on it.

---

### Post by jamesjenner on 2011-05-16
> **jnorthr said:**
> any news jimmy ?

Bonjour Jnorthr :)

Il est bon! 

I re-installed last night and had a god awful time sorting out the partitions. Grub defaults to the device, and I clicked next before I realised after fixing up the partitions, when I realised this I had to hard reboot and restart all over again :(

Funny thing is, doing the gparted was the trick. Got up this morning and the install was finished, rebooted and I saw the Ubuntu logo on the boot options, I was like cool. Selected it before I remembered about syncing the partitions, but the crazy thing is it booted fine! 

Gotta go to work now (6:20am is a bad time to go to work, but hey thats life). I'll post an update tonight, btw found some really buggy behavour with the install partition tool, so if not reported I'll have to report that.

Merci beaucoup Jnorthr pour votre grand secours :)

James

---

### Post by aysiu on 2011-05-16
I used to have a dual-boot on my Macbook Pro 3,1. There are definitely some advantages to Ubuntu over OS X. For one thing, my wireless took only ten seconds to reconnect after resume from suspend, but it would actually stay connected (in OS X it constantly connects and disconnects). The performance and responsiveness is amazing (with the same CPU and RAM, obviously). Apps just load instantly. No rainbow circle of death.

I did lose some things with Ubuntu, though, that ultimately sent me back to OS X. Resume was not smooth or instant. The screen brightness controls weren't fine-tuned enough. The options for screen resolutions on an external monitor were too limited. Battery life was abysmal (about 1 hour on OS X, about 15 minutes on Ubuntu).

---

### Post by JohnAtilano on 2011-05-17
> **jnorthr said:**
> off hand, i would say that it is unlikely that you could get your system back to the way it came from the factory, and anyway - why would you ?...

Maybe I've misunderstood this; please excuse me if I have.  

I've done this a few times.  Insert the Install DVD that came with your Mac.  Boot from it. Format the hard drive.  Install Mac OS X.  The laptop would be in the EXACT state in which you received it.

Another less drastic option.  Keep a SuperDuper! or CarbonCopyCloner backup of your OS X system.  Boot from it, format the internal hard drive, clone from the backup to the internal drive.

All traces of Ubuntu gone (with the exception of rEFIt which you can delete).

---

### Post by jamesjenner on 2011-05-17
I thought I'd document what works out of the box and any observations, in case someone else with a 5,1 system wishes to go to 11.10.

Firstly observations:
[LIST]
[*]Really really really important to follow the sticky and do the gParted for partitioning before installing
[*]I didn't try the default install option of "install next to OSX". The install recognised OSX but I wasn't willing to risk it.
[*]Make sure you choose the partition for linux to install the boot loader/grub into
[*]Didn't need to sync the partitions as mentioned in the sticky
[/LIST]

Now, as for what works out of the box with no extra stuff installed:
[LIST]
[*]Keyboard backlight is fine
[*]Sound works (initial state is muted, not sure why)
[*]Bluetooth appears to be working, however I have no devices to test it with
[*]Ethernet port works (worked in live cd as well)
[*]Wireless works (not sure if it did in the live cd though)
[*]Suspend on lid close suspends correctly
[*]Power Management in general appears ok
[/LIST]

Things that don't appear to work:
[LIST]
[*]brightness control screen overlay works but doesn't adjust brightness
[*]Restarting from suspend gives garbled black and white screen, will do more testing but doesn't appear to be working. Strangely I figured out I had a text field, typed in my password and I was back where I was. Initially side panel was garbelled but it recovered itself while i was typing this. On second attempt of suspend same thing happened at login screen (or maybe unlock screen) but this time unity side bar wasn't garbelled. I've now Used "Additional Drivers" to switch to the recommended drivers, fixed the suspend garbelled screen issue.
[*]Mouse is only single touch, not multi-touch.
[/LIST]

I've yet to determine how to monitor temp and fan speed, so not sure if that is all okay or not.

So only problem I have right now that I have noticed is inability to adjust brightness of screen. I've just searched and cannot find anything mentioned about this so may have to do some further investigation. 

Otherwise right now I'm ecstatic that it's all working. :)

---

