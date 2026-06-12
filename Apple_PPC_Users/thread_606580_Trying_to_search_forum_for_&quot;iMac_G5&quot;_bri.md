---
title: "Trying to search forum for &quot;iMac G5&quot; brings 0 results...?"
date: 2007-11-08
forum: Apple PPC Users
---

### Post by indiworks on 2007-11-08
Hello,

I'm just downloading what I hope is the right Ubuntu version (ubuntu-7.10-desktop-powerpc.iso) for my iMac G5 (the  first one) and was trying to search these forums for more info, but somehow I always get 0 search results, also when using the advanced search...?

So I have to ask if anyone has links to:

• how-to install Ubuntu on an iMac G5 with Leopard/Bootcamp
• possible issues (fans, 16:9 display, sound...?)

I once tried a Live CD about 1 1/2 years ago and at the time Ubuntu got stuck during booting and the iMac fans were working at full speed...

Thanks!

---

### Post by indiworks on 2007-11-08
I just saw that someone here [http://ubuntuforums.org/showthread.php?t=427714&page=4](http://ubuntuforums.org/showthread.php?t=427714&page=4) says that 

"After many hours of burning, booting and googling, I finally figured it out:
Ubuntu Gutsy 7.10 simply doens't work on Mac/Powerpc!!
Feisty 7.04 does!"

So I cancelled the other download and will try Ubuntu Feisty 7.04...

A suggestion: on the main Ubuntu download site [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) there is no information for Ubuntu on PPC and I first downloaded the wrong .iso (since when answering those questions I would think that I have a "Standard personal computer" - if looking at the other two choices...). This is really misleading and will cost many Mac users extra time and on the other side it costs Canonical extra downloads that only end up in the trash...

Best would be a simple, clean chart where you can look up your pc/mac with links to the distro that works (best) and possible help pages.

---

### Post by MRiGnS on 2007-11-08
PPC support was dropped officially...

---

### Post by indiworks on 2007-11-08
Aha... Thanks for this info! So I wonder if it makes sense to try installing Ubuntu on the iMac G5 at all...? I need a fully working machine with sound/video etc., mainly for use with Blender (open-source 3D app). I thought I'd go for Ubuntu because that is what most Linux Blender users seem to use...

If anyone knows of another iMac G5 compatible Linux distro or a special Ubuntu hack for the iMac G5 please let me know.

Thanks!

---

### Post by drumsticks on 2007-11-08
I'm writing this on Gutsy on a Powermac G5, rev B (dual CPU, not dual core). Everything that matters to me works, but with a little tweaking. Video acceleration works (Radeon 9600), Bluetooth Apple keyboard and mouse works (though I use a wired 3 button mouse). I haven't tried the modem nor Airport Extreme, but there has been no errors detected. Superdrive works, widescreen display works (Apple Cinema Display 20in), fans are fine, sound is fine.

Some minor annoyances, but I spend 95+% of my time on Linux. Only use Mac when I [rarely] need some proprietary software.

I see no reason why it shouldn't work on your iMac G5...

---

### Post by indiworks on 2007-11-08
Ok, thanks for your answer! The thing is that from what I once experienced with the Live CD and read about there used to be real problems with the internal fan running at full speed all the time (it is already too loud under OS X when working with full processor power).

I'll see if I can get 7.04 to run on my iMac, since I've never installed Linux before I think this is the easiest way to get started with Ubuntu...

---

### Post by pxwpxw on 2007-11-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu-website/+bug/107828](https://bugs.launchpad.net/ubuntu-website/+bug/107828) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **indiworks said:**
> Ok, thanks for your answer! The thing is that from what I once experienced with the Live CD and read about there used to be real problems with the internal fan running at full speed all the time (it is already too loud under OS X when working with full processor power).

I'll see if I can get 7.04 to run on my iMac, since I've never installed Linux before I think this is the easiest way to get started with Ubuntu...

Try your Desktop Live CD and see how that goes. I have Gutsy ubuntu on an iBookG4 and xubuntu on a powermac G5, both done by upgrades from feisty, some bugs but about the same as feisty, but like it better than feisty. Dont know of particular problems with iMacG5.

See the [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
for some comments on graphics driver limitations with ppc in general.

Re the difficulty finding the downloads there is a launchpad bug entry complaining about lack of clear links, ubuntu reluctant to help.

[https://bugs.launchpad.net/ubuntu-website/+bug/107828](https://bugs.launchpad.net/ubuntu-website/+bug/107828)

Edit:
Just tried the ubuntu710 Desktop ppc on the iBookG4, and it needs the "live-nosplash" boot option (<TAB> gets the options),
otherwise just a black hole on the screen. Now running nicely.

---

### Post by indiworks on 2007-11-08
> **pxwpxw said:**
>  Try your Desktop Live CD and see how that goes. I have Gutsy ubuntu on an iBookG4 and xubuntu on a powermac G5, both done by upgrades from feisty, some bugs but about the same as feisty, but like it better than feisty. Dont know of particular problems with iMacG5.

See the [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
for some comments on graphics driver limitations with ppc in general.

Ok, in that case I maybe should try Gutsy first... Downloading it (again)... Thanks!

---

### Post by indiworks on 2007-11-08
Ok, I just successfully booted from the 7.10 Desktop/Live PPC on my iMac G5 and it looked like the basics all worked (video had sound) and fan noise was ok. There seem to be minor pixel errors in the top menu (black dots), but not quite sure yet what this is about.

So that's really good, but I now only also just found out that Bootcamp is an Intel Mac only feature - so upgrading to Leopard was not what I needed to do to get a dual boot system with OS X/Ubuntu. Hmm...

Are there any other ways of doing this with an iMac G5...? I don't want to give up OS X, but need Ubuntu as well. Could I maybe install it in on an external hardrive and boot via USB or FireWire...?

Any ideas or success stories...?

---

### Post by Auria on 2007-11-08
> **indiworks said:**
> 
I now only also just found out that Bootcamp is an Intel Mac only feature - so upgrading to Leopard was not what I needed to do to get a dual boot system with OS X/Ubuntu. Hmm...

Are there any other ways of doing this with an iMac G5...? I don't want to give up OS X, but need Ubuntu as well. Could I maybe install it in on an external hardrive and boot via USB or FireWire...?



Boot camp is to dual-boot Windows and OSX, not linux :)  all you need to dual-boot OS X and Ubuntu is the Ubuntu disk you currently have :)

Use the partitionner on the CD to shrink your OS X partition (backup important data first!!!) don't add anything in the empty space left, then, in the installer, tell it to install in the largest available free space (be careful not to tell it to wipe the entire disk)

if all install wells you will have your dual-boot system

---

### Post by stmiller on 2007-11-08
> **MRiGnS said:**
> PPC support was dropped officially...

This is not quite accurate. Ubuntu is still making PowerPC releases, the same as all other versions, complete with all packages and updates as normal. They only dropped paid tech support from Canonical. So if you need help you'll have to come here (the forum).

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

PS: Try searching the forums with google like [this]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+imac+G5&btnG=Google+Search").

---

### Post by indiworks on 2007-11-09
> **Auria said:**
> Boot camp is to dual-boot Windows and OSX, not linux :)  all you need to dual-boot OS X and Ubuntu is the Ubuntu disk you currently have :)

Use the partitionner on the CD to shrink your OS X partition (backup important data first!!!) don't add anything in the empty space left, then, in the installer, tell it to install in the largest available free space (be careful not to tell it to wipe the entire disk)

if all install wells you will have your dual-boot system

This sounds good, but could you just point me to a detailed step by step instruction (if there is any)...? I've never installed Linux before and have too many questions about this to just give it a try. (Like "use the partitionner on the CD": do you mean my Ubuntu 7.10 download...? Where do I find it, how does it work...? Do I have to reinstall OS X...? Etc...)

I found this blog entry from about a year ago:

[http://trainque.com/blog/2006/10/21/how-to-dual-boot-ubuntu-osx/]("http://trainque.com/blog/2006/10/21/how-to-dual-boot-ubuntu-osx/")

But I'm not sure if those steps would all be required/the same for Leopard/Ubuntu 7.10...?

Anyone knows of a more recent tutorial that also works without using additional software like in the above blog entry...? Thanks!

---

### Post by drumsticks on 2007-11-10
Yes, the partitioner is in the Ubuntu CD, both the live and alternate version. In the live version, it should appear under "System > Administration". In the alternate version, it should be directly visible to you.

Personally, I go straight to the alternate version, but that's because I know what I want already and it's quicker that way. I've never used the partitioner though - I have a phobia of dynamically resizable partitions, but that's just me.

No need to reinstall OS X. Like with Windows, it is best to install Linux *last*. That's because Linux is aware of the other operating systems, while the others assume that they are the only ones installed. It will still work the other way around, but it requires more work to force the proprietary operating systems to relinquish control.

Use Auria's tip of telling it to use the largest free space. This is because Macs need a special boot partition to boot Linux, which you can't get if you choose to manually partition. The automatic partitioning (on free space) does this for you.

Good luck!

---

### Post by indiworks on 2007-11-10
> **drumsticks said:**
> 

Use Auria's tip of telling it to use the largest free space. This is because Macs need a special boot partition to boot Linux, which you can't get if you choose to manually partition. The automatic partitioning (on free space) does this for you.

Thanks, ok, so far I get stuck when I use the automatic partioning: there is an error message that not enough free disk space was found, yet there are 16 GB of free space left...?

Any ideas what to do?

---

### Post by pxwpxw on 2007-11-10
> **indiworks said:**
> Thanks, ok, so far I get stuck when I use the automatic partioning: there is an error message that not enough free disk space was found, yet there are 16 GB of free space left...?

Any ideas what to do?

You need to actually shrink the Macos partition to leave a free space partition.
You can do this with the Live CD by using the Gnome Partition Editor a.k.a gparted, found in Menubar:System:Admin I think. 
It is not enough just to have free space on the macos partition.
Then the install partitioner will be happy to install in the free space partition.

---

### Post by indiworks on 2007-11-10
> **pxwpxw said:**
> You need to actually shrink the Macos partition to leave a free space partition.
You can do this with the Live CD by using the Gnome Partition Editor a.k.a gparted, found in Menubar:System:Admin I think. 
It is not enough just to have free space on the macos partition.
Then the install partitioner will be happy to install in the free space partition.

I can see a "resize" disk option in gparted, is this what I use to "shrink" my disk (without loosing my OS X data) before using the automatic partitioner...?

---

### Post by pxwpxw on 2007-11-10
Yes that sounds right,

---

### Post by indiworks on 2007-11-10
I'm trying to register with the gparted forums, so far no confirmation email...

So if anyone else here happens to know the details of how-to use gparted for resizing my OS X disk (before I can use the Ubuntu automatic partitioner), I'm still looking for a step by step how-to...

---

### Post by drumsticks on 2007-11-10
Is Gparted capable of resizing Journalled HFS+ partitions? I thought we still have limitations read/writing that. As I know it, we need to disable journaling if we want to write to it. I'd assume this would extend to partitioning, as well?

---

### Post by Auria on 2007-11-10
> **drumsticks said:**
> Is Gparted capable of resizing Journalled HFS+ partitions? I thought we still have limitations read/writing that. As I know it, we need to disable journaling if we want to write to it. I'd assume this would extend to partitioning, as well?

yes disable journaling first, anyway you can enable it again after you're done.

---

### Post by Sav on 2007-11-18
Hi, on my iMac g5 revC I was able to ear the splash sound, by booting using

live-nosplash-powerpc64 video=ofonly

But when the desktop is about to show itselsf, the screen becomes blurry and I'am unable to switch to the console.

There is a way to boot only in console, so I can adjust the xorg.conf file and start X manually?

Thanks

---

