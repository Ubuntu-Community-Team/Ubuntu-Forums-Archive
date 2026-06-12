---
title: "Photoshop in Ubuntu"
date: 2007-11-09
forum: Art &amp; Design
---

### Post by Persepolis on 2007-11-09
Hi,
   
  To begin with I am completely new to Linux. I have used Ubuntu for just over 24 hours and I think it is great. I would like to know if you can run Photoshop on Ubuntu. If so could someone give me step by step instruction on how I could do this. 

 Thanks:guitar:

---

### Post by ticopelp on 2007-11-09
You can run Photoshop in wine, which can be added through Add / Remove Programs, or (I think this will work) you can just [click here]("apt://wine"). 

Once you have wine installed, you should be able to install and run Photoshop much like you would in Windows.

---

### Post by Persepolis on 2007-11-10
Hi,

Well success and failure. I installed Photoshop CS2 on windows, then switched to Ubuntu. I went to the Photoshop.exe file in the windows partition and ran it with wine and hey presto I had photoshop up and running, However, after a while it crashed and I had to force quit it. Now, whenever I try to run it, it says that there is a hardware problem and it will not load.

   Any ideas??

:guitar:

---

### Post by Steve1961 on 2007-11-10
Just to give you another option.  You could install a virtual copy of XP in virtualbox and then run Photoshop in that.

---

### Post by mech7 on 2007-11-10
ONly v7 seems to run normal under WINE..

---

### Post by Persepolis on 2007-11-10
How do I install a virtual copy of XP in virtualbox???????

:guitar:

---

### Post by aethralis on 2007-11-11
Have a look at [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) but I would actually recommend dual boot instead.

---

### Post by Nymphadora on 2007-11-12
> **mech7 said:**
> ONly v7 seems to run normal under WINE..

What sort of problems would CS2 Have, running in WIne?  I've actually been looking into this as well.

---

### Post by vishzilla on 2007-11-12
How about trying Gimp. its quite good and its getting there to the level of Photoshop. I suggest learning a few tutorials from the website!!

---

### Post by anaconda on 2007-11-12
I got the portable photoshop cs2 running well in wine without problems..

But nowadays I just prefer krita.. expecially when we will get the new 2.0 version

---

### Post by mech7 on 2007-11-12
> **Nymphadora said:**
> What sort of problems would CS2 Have, running in WIne?  I've actually been looking into this as well.

Installing / Activating for one :lolflag: there is a cracked copy portable version that runs but it has bugs.. well atleast that was my experience. v7 runs quite good except that it lacks features from cs2/3 :(

---

### Post by por100pre1 on 2007-11-12
> **mech7 said:**
> Installing / Activating for one :lolflag: there is a cracked copy portable version that runs but it has bugs.. well atleast that was my experience. v7 runs quite good except that it lacks features from cs2/3 :(

Who needs cracked software? There's FOSS available: GIMP.

---

### Post by Nymphadora on 2007-11-12
> **por100pre1 said:**
> Who needs cracked software? There's FOSS available: GIMP.

I've been playing around in Gimp, but there are particular features in CS2 that I love, specifically - that even PS7 doesn't handle well.  That's why I hope to be able to run it in Ubuntu somehow.

---

### Post by tyler22 on 2007-11-12
Say no to cracked software. 

If someone wishes to charge money for software it is their right. You wouldn't use a car that didn't belong to you because it had  a "cracked" car alarm.

---

### Post by tyler22 on 2007-11-12
> **Nymphadora said:**
> I've been playing around in Gimp, but there are particular features in CS2 that I love, specifically - that even PS7 doesn't handle well.  That's why I hope to be able to run it in Ubuntu somehow.

Virtual box is good and very easy to use.

---

### Post by anaconda on 2007-11-13
> **Nymphadora said:**
> What sort of problems would CS2 Have, running in WIne?  I've actually been looking into this as well.

I had just 2 problems. 
1. It runs in all virtual desktops. There was a workaround for that. so that wine would open cs2 in a separate window.. or something like that.

2. fonts didn't work, but I didn't even try to install windows fonts. Installing them to wine would probably have solved that problem

---

### Post by por100pre1 on 2007-11-13
> **Nymphadora said:**
> I've been playing around in Gimp, but there are particular features in CS2 that I love, specifically - that even PS7 doesn't handle well.  That's why I hope to be able to run it in Ubuntu somehow.

If you have a legally licensed copy of CS2 go ahead, try to run it in Ubuntu. Cracked software is always bad news.

---

### Post by Goombie on 2007-11-14
> **Persepolis said:**
> Hi,

Well success and failure. I installed Photoshop CS2 on windows, then switched to Ubuntu. I went to the Photoshop.exe file in the windows partition and ran it with wine and hey presto I had photoshop up and running, However, after a while it crashed and I had to force quit it. Now, whenever I try to run it, it says that there is a hardware problem and it will not load.

   Any ideas??

:guitar:
All you did was install Photoshop for Windows. To install Photoshop in Linux, you have to install it to Wine's fake "Windows" folders. To do this:
1) Boot into Linux.
2) Insert your Photoshop CD.
3) Navigate to your CD drive.
4) Look for the program named setup.exe, or something like that. I don't have Photoshop, so I don't know what the exact name is.
5) Right-click that program, and look for an option named "Open With.. Wine Windows Emulator."
6) Click that option.
7) The Photoshop install program should now start, and you can proceed as usual.

Disclaimer: I cannot make any guarantees about the above steps, as I don't have Photoshop, so I had no way of testing them. :) Good luck!

---

### Post by mdpalow on 2007-11-14
Photoshop won't work well in Wine unless you use version 7, which you don't want to do.

Use VMware or Virtualbox and you'll be a happy, happy camper. Promise. :)

If you were my personal friend, I would recommend VMware. :) I have a friend who did Virtualbox and it ran well, but he had a few minor issues that I never had, plus I thought VMware was easier to use. 

good luck....

---

### Post by NRTech on 2007-11-15
I have just installed Virtual Box on Ubuntu 7.10 but when I attempt to Start the Windows Installation, I get an error as attached...
I have added the Virtual Box site to my repositories, but it fails to bring in any updates. Has anyone run into this problem?
Thanks

---

### Post by zakk on 2007-11-15
> **vishzilla said:**
> How about trying Gimp. its quite good and its getting there to the level of Photoshop. I suggest learning a few tutorials from the website!!

GIMP is not Photoshop.
- no shapes
- no effect/adjustment layers
- no way to copy effects from a layer to another
- no layer groups
- no CMYK, no 16bit image handling (for photo and printing professionals)
- no layer linking (yes, there is, but you cant link layer1+2, and layer3+4, because you will have all 1+2+3+4 layers linked)
- no guideline snapping to selection (its just annoying)
- very bad interface (window management, too much dialogs, etc)
- edit: and one important thing: text handling. No in place text editing, and you cant use different fonts/sizes/colors in one text box.
- etc.

---

### Post by nandaiyo on 2007-11-15
Well said.  :KS

---

### Post by smartalecks on 2007-11-15
Do **not** use Virtual Box or any other VM app if all you want to do is run Photoshop. Install wine (sudo apt-get install wine), and once it is done installing run 
```
$     winecfg
```
Set it to emulate Windows XP... 

Next, put in the CD and either:
1. Navigate to CDROM drive, right click 'setup.exe' or 'install.exe' or whatever it is.
2. Copy all the files to a folder on your desktop. Open a terminal and

```

$     cd "/home/USERNAME/Desktop/FilesFolder"
$     wine setup.exe

```
And follow the prompts to install it...

Either way is fine, but if you copy the files to your desktop first and run setup.exe in the terminal it should go a bit faster and it'll report what errors occur.

Once it is done installing, you can make a desktop launcher that points to:

```

wine "/home/USERNAME/.wine/drive_c/Program Files/Adobe/Photoshop.exe"

```
Or whatever/wherever the .exe is... should be something like that.
It should install fine! It received a platinum rating on Wine's AppDB (highest) [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631)

---

### Post by Photonic Nature on 2007-11-15
**If you&#8217;re straddling the fence between OSes, who says you have to choose? **

Just as with languages, different operating systems have strengths and weaknesses. You may prefer Linux for day-to-day use but need Windows XP for certain applications. Maybe you&#8217;ve upgraded to Vista but have some applications that currently only run under WinXP.

Gone are the days when you were limited to a single operating system per computer. And setting up a system to run more than one OS isn&#8217;t the geek-intensive operation it used to be. In fact, there are so many options available these days that the permutations are almost endless

** Boot Me Up**

The most common way to run multiple operating systems is to set up a dual-boot or multiboot machine.

In practice, the order in which you load the operating systems can make a big difference to how easy your life is going to be.
Although Linux boot loaders are pretty smart about identifying and configuring both the Linux and Windows installations, the same cannot be said for Windows.

Because the basic rule of thumb is that the last OS installed is going to &#8220;own&#8221; the boot record (although you _can_ tell Linux not to overwrite it, unlike Windows), things work out better if you install Windows first. 

:!: As with any operation that mucks around with your hard drive, backing up any critical data before doing this is a wise move.

You also need to be careful if you update your Windows installation, since it may rewrite the MBR record. As a last resort, you can use a bootable Linux CD to mount the Linux filesystem and rerun GRUB against the GRUB configuration file currently on the root filesystem of the hard drive. This is obviously not a simple process. You can also make a bootable floppy disk with GRUB and the configuration file, which lets you boot into Linux even if the MBR is rewritten.

** The Virtual Approach**

Another common method of putting multiple OSes together under one roof is virtualization. The most common way to do this is using VMware [COLOR="Blue"]([[COLOR="Blue"]www.vmware.com[/COLOR]]("http://www.vmware.com"))[/COLOR]; the basic server and player are now available for free. Using this approach, one operating system runs inside the other. Virtualization has the advantage of letting you use both OSes at once,* but it has disadvantages of its own*.

For one thing, both OSes are likely to take a pretty significant performance hit. Although VMware has become more efficient, you still can&#8217;t get more cycles out of your processor than it had to begin with. Don&#8217;t expect a virtual OS to perform as well as a native OS.

Also, the &#8220;guest&#8221; operating system won&#8217;t have all of its features and abilities at its disposal. Again, VMware has made improvements in this regard, but some low-level hardware drivers or graphics capabilities may not be available. Running high-performance games in a VMware image may be difficult, if not impossible.

VMware also offers a product that eliminates the host OS altogether. Its ESX Server runs on &#8220;bare metal,&#8221; effectively acting as the host operating system itself, and is tuned to run VMs with minimal overhead. But unlike the basic server and player, ESX carries a significant price tag that will keep it out of the price range of anyone but an enterprise customer.
---
*Excerpts above from a copy of CPU Mag. ([[COLOR="Blue"]Computer Power User[/COLOR]]("http://www.computerpoweruser.com"))
[I] August 2007 &#8226; Vol.7 Issue 8
Page(s) 66-70 in print issue[/I]
_Article_: Bet You Can&#8217;t Boot Just One


**In Summary**

[LIST]
[*]Versions of Photoshop higher than v7 will not run in wine.
[*]Running Photoshop in a VM will severely tax both OS's
[*]All the resources Photoshop is looking for and used to using will not be available.*
[/LIST]
*Especially if you use a dual monitor setup like I do for PS with the tool sets on the other screen.

**Moral of the story **

_Dual Boot_ ! - and make sure winblows is installed first.
Submit to the MS gods and run whatever apps that are not team players yet on XP (NOT Vista!!)[URL="http://badvista.fsf.org/"]
[COLOR="Blue"]Bad Vista[/COLOR][/URL]
[[COLOR="Blue"]Whats wrong with Vista?[/COLOR]]("http://badvista.fsf.org/what-s-wrong-with-microsoft-windows-vista")

Until the Linux community gets up to speed and really puts forth a earnest effort to evangelize Linux to become more mainstream and begins to press the software and hardware companies to support it, we will always be plagued with the legacy of Bill.

The 3 key players I have seen making efforts for conversion of the masses from winblows are; [[COLOR="Blue"]PCLinux[/COLOR]]("http://www.pclinuxos.com/"), Ubuntu, and [[COLOR="Blue"]Linspire[/COLOR]]("http://www.linspire.com/") which is based on ubuntu.

**Edit:** PCLinux is free OSS and Linspire is sold commercially due to the proprietary software, drivers, and codecs built into it making it the "World's Easiest Desktop Linux!" freespire is the free version.
(Remember now, it's based on ubuntu. So, for the technically challenged you know, who don't possess the inclination to search here and tinker under the hood via the command line... I recommend Linspire)

~R

---

### Post by fjgaude on 2007-11-15
> **mech7 said:**
> ONly v7 seems to run normal under WINE..

Version 6 of Photoshop also runs okay in wine. I could never get PS CS to run so changed to VMware Server.

---

### Post by Mithrilhall on 2007-11-15
I would recommend the VMware route as well. I've run v7 of Photoshop in Wine and it still had a few bugs but that was over a year ago.

---

### Post by aonegodman on 2008-02-18
I tried using GIMP to edit and print a couple digital photos on my Canon i455 printer and the results were ok but not as good as PaintShop Pro in Windows.

I would get vivid sharp printing from  PSpro, but GIMP's pictures print a bit faded. Any ideas?

Thanks.

---

### Post by arteest on 2008-02-19
I'm new, but I just downloaded wine with the intention of installing PS7.  Thanx for the link.

---

### Post by mech7 on 2008-02-19
> **arteest said:**
> I'm new, but I just downloaded wine with the intention of installing PS7.  Thanx for the link.

CS 2 runs fine now under WINE since recently..

---

### Post by kristjans on 2008-02-19
4 things to do for Photoshop lovers on Linux before trying to run it with Wine/VMware/dualboot :)
[LIST=1]
[*]Try out GIMP ([Meet the GIMP](http://meetthegimp.org/) for tutorials).
[*]Try out CinePaint.
[*]Try out Krita.
[*]Tell Adobe that you want (and pay for; Adobe is a for-profit company) a Linux version of Photoshop.
[/LIST]

---

### Post by Tux Aubrey on 2008-02-19
> **mech7 said:**
> CS 2 runs fine now under WINE since recently..

Apparently that is thanks to Google's Summer of Code sponsorship.  But there are still some known bugs -[ read all about it]("http://apcmag.com/8034/google_behind_photoshops_new_linux_compatibility").

(I'm a big GIMP fan myself)

---

### Post by jcornuz on 2008-02-19
Hi there,

You won't find all the features of Photoshop in The Gimp - or any other Linux program, for that matter. So you can either 
[LIST]
[*]to the Wine route (with an older version of Photoshop)
[*]go the Virtual machine route (with a performance penalty)
[*]go the Linux route (use a combination of several OSS apps to cover your needs - and yes this includes quirks, workarounds and learning to use new tools)[/LIST]

If that last route if of interest, have a look at [my blog]("http://jcornuz.wordpress.com/") - I try to bring together all the know how necessary to use Linux for serious photography.

Take care,

Joel

---

### Post by jorgerosa on 2008-02-20
Just an idea... (seems great, to me) ;)
author´s main idea: "make users of Photoshop feel comfortable using GIMP"

Gimp + Photoshop  = **GimpShop**  ([Home Page]("http://www.gimpshop.com/index.shtml"), [Tutorials]("http://www.upstateforums.com/phpBB2/viewtopic.php?t=4464"))

---

### Post by dmn_clown on 2008-02-20
> **jorgerosa said:**
> Just an idea... (seems great, to me) ;)
author´s main idea: "make users of Photoshop feel comfortable using GIMP"

Gimp + Photoshop  = **GimpShop**  ([Home Page]("http://www.gimpshop.com/index.shtml"), [Tutorials]("http://www.upstateforums.com/phpBB2/viewtopic.php?t=4464"))

But that is just the gimp with a hacked UI you still do not have the feature set nor the technical capabilities of PS.

Oh, and for the record the only reason Adobe isn't porting PS to Linux and companies like Google have to fund Wine to support newer versions of PS is because they don't see a large enough market for PS on the platform. 

Google is only the latest company to do this, Disney funded Wine to get PS 7 working.

So, as has already been stated, be sure to mention to Adobe that you would be willing to buy their next version, but only as long as they port it to Linux, but ask them to keep the stupid MDI on Windows, we don't need or want it.

---

### Post by mech7 on 2008-02-21
I wonder how the color profiles work though under linux? I am no expert in this.. so i can't say for sure..

---

### Post by dmn_clown on 2008-02-21
> **mech7 said:**
> I wonder how the color profiles work though under linux? I am no expert in this.. so i can't say for sure..

I can't say how they work in Photoshop, but most native programs use liblcms and the patent encumbered icc profiles available in the package icc-profiles.

---

### Post by littlemog on 2008-02-21
Maybe we should start a petition of some sorts. get the community aroused.

---

