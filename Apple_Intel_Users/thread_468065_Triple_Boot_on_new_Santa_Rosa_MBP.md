---
title: "Triple Boot on new Santa Rosa MBP"
date: 2007-06-08
forum: Apple Intel Users
---

### Post by Lacrosse200760 on 2007-06-08
I've read pretty much all the triple boot guides and it seems that the main and/or best way to triple boot is using rEFIt, but it currently does not work on the new MBP's. I did read that it is possible just using bootcamp to split the "windows" partition and then once you choose "windows" it boots into grub and i can then choose windows or ubuntu. Is this my only option to triple boot until rEFIt gets patched or am I missing something. O and it would be (Mac OS X, Vista 32-bit, Ubuntu 64-bit)  Thanks!

---

### Post by ronocdh on 2007-06-08
> **Lacrosse200760 said:**
> I've read pretty much all the triple boot guides and it seems that the main and/or best way to triple boot is using rEFIt, but it currently does not work on the new MBP's. I did read that it is possible just using bootcamp to split the "windows" partition and then once you choose "windows" it boots into grub and i can then choose windows or ubuntu. Is this my only option to triple boot until rEFIt gets patched or am I missing something. O and it would be (Mac OS X, Vista 32-bit, Ubuntu 64-bit)  Thanks!
Can you elaborate on rEFIt not working on the new MBPs? I see no documentation of it on the [official rEFIt page]("http://refit.sf.net"), and Googling for the problem has been largely fruitless, too. Please go into greater detail on what's changed.

As for the GRUB screen problem, choosing either Windows or Ubuntu will send you to the same GRUB screen, yes. This is because of the GPT/MBR conflict inherent to the Mactels and these older operating systems, which are used to different hardware (Intel has been pushing EFI as the standard instead of BIOS). To solve the problem, I believe you could install and configure ELILO, which is designed for EFI systems.

---

### Post by Lacrosse200760 on 2007-06-08
Here is the link to the Bug report for the rEFIt problem, sorry for not originally including it.  [http://sourceforge.net/tracker/index.php?func=detail&aid=1732241&group_id=161917&atid=821764]("http://sourceforge.net/tracker/index.php?func=detail&aid=1732241&group_id=161917&atid=821764")

---

### Post by ronocdh on 2007-06-08
> **Lacrosse200760 said:**
> Here is the link to the Bug report for the rEFIt problem, sorry for not originally including it.  [http://sourceforge.net/tracker/index.php?func=detail&aid=1732241&group_id=161917&atid=821764]("http://sourceforge.net/tracker/index.php?func=detail&aid=1732241&group_id=161917&atid=821764")
Thank you, I've bookmarked the link. I don't know anyone who's bought the new MBP yet, but I'll look around, and I'll definitely be following the bug thread closely. Thanks again!

[I]Edit: 
And about GRUB, yes it should be possible for you to use Boot Camp to triple boot. However, I'm not sure how Boot Camp responds to the presence of multiple partitions. I know that it doesn't allow the creation of more than one additional one, but hopefully the bootloader won't crap out if you have more. You could create the needed third partition in the terminal in OS X using **sudo diskutil resizeVolume**[/I] or you could maybe use the Ubuntu CD to repartition your Windows one. This might require a reinstall of Windows once the partition is made, I'm not sure. Good luck, though, and please keep us apprised of your progress! It'll be interesting to watch the process on one of the new MBPs.

---

### Post by Lacrosse200760 on 2007-06-08
Looks like for now I will be just installing Vista using bootcamp and waiting for the rEFIt fix, but I don't leave for college for 2 months so I still got my ubuntu box at home :D until I can get a nice clean triple boot on the MBP

---

### Post by buzz11 on 2007-06-11
Anyone have this working yet?  I am trying to do a similar thing. Issue I have is I have a partimage that  I need to load. Every version of Ubuntu or Xubuntu I try and load either hangs or boots with no network support. Xubuntu alternate 7.10 boots with network support but does not have partimage. I need that to suck my image down.

---

### Post by chem on 2007-06-12
I am going to be purchasing a Santa Rosa MBP within the next few weeks, and am also interested in concise, correct instructions detailing how to triple boot Ubuntu, Win XP, and Mac OS X (and have wireless internet and CPU fan rpm control in all three...)

Thanks in advance to anyone who figures this out and posts the details to a wiki or thread!

---

### Post by ronocdh on 2007-06-12
> **chem said:**
> I am going to be purchasing a Santa Rosa MBP within the next few weeks, and am also interested in concise, correct instructions detailing how to triple boot Ubuntu, Win XP, and Mac OS X (and have wireless internet and CPU fan rpm control in all three...)

Thanks in advance to anyone who figures this out and posts the details to a wiki or thread!
You can subscribe to the thread on sourceforge and would thereby be kept in the know about potential fixes.

---

### Post by Lacrosse200760 on 2007-06-12
Looks like the second patch posted for refit fixed it! The menu works and I can boot into OS X and Vista, now its about time to take the leap and repartition the vista partition and install ubuntu. Although when i tried a couple days ago to install ubuntu under bootcamp (before I put vista on), it would boot into the screen to ask you want you wanted to do (install or mem test, etc) and then I would get an error after that.

Edit: Any recommendation for which partitioner I should use to repartition vista, the one included in refit or one within vista.

---

### Post by yanaventer on 2007-06-12
I've just picked up a one of the new MBP and managed to install Ubuntu & MacOSX together with the latest version of refit which has seemed to have fixed the previously mentioned bug.

The installation went fine but I'm having trouble getting the network card + graphics card to work under Ubuntu. I tried modprobing sk98lin and sky2, nothing shows up in dmesg when I do that despite now appearing in lsmod.

lspci shows there is a marvell technology ethernet controlled but as an unknown device, the same for my nVidia graphics card. I haven't really tried playing around with different graphics drivers since getting my network card working is my priority :D.

---

### Post by brtnrdr on 2007-06-14
I'm considering getting one of the new MBP's with the Nvidia 8600, however I am wondering about the OpenGL support under Linux and Windows running on the MBP as I do a lot of development for Linux and Windows with OpenGL.  I assume that just installing the Nvidia driver for Linux/Windows would result in supporting OpenGL 2.1 (which is what the card would support in a pc), however, I just want to make sure there isn't any strangeness with the hardware in the MBP that would limit what the card can do.  I guess OSX Leopard is supposed to support OpenGL 2.1, but it would be nice to have version 2.1 under Linux and Windows in the mean time.

If anyone who has installed Windows or Linux on the new MBP could verify what version of OpenGL is supported on Windows and/or Linux using a new Nvidia driver I would really appreciate it.

Just in case you don't know how to do this:
On Linux:  After installing the Nvidia driver (100.14.09 from the Nvidia site) open a Terminal and type "glxgears" at the prompt (don't include the quotes).  The supported OpenGL version should be printed in the terminal.

On Windows:  Don't know a real easy way to do this, what I have done:
First, the new Nvidia driver must be downloaded (nvidia.com)
1.  Download GLEW (google it, it's the first thing to come up)
2.  Open the unzipped folder and in the bin directory run glewinfo
3.  In the generated text file one of the first few lines is the OpenGL version

I'd appreciate any insight that anyone has.

Thanks.

---

### Post by pfistech on 2007-06-15
FYI: I've released rEFIt 0.10, which has the fixes for the Santa Rosa MBPs. No more need to grab the snapshot and apply manually. :D Download options are at [http://refit.sourceforge.net/](http://refit.sourceforge.net/).

---

### Post by tweeknockr on 2007-06-15
I've been trying to triple boot my new MBP. Windows runs great (with the new rEFIt), but unfortunately Linux is not very well supported at this point.

I first tried installing ubuntu, and the latest graphics drivers beta (100.14.09) yields very messed up colors (search nvnews.net). I then tried Fedora 6. The graphics work in fedora, but I couldn't get any ethernet support whatsoever. I then tried Fedora 7, but the installer could not detect the CD drive.

So I've yet to come across a successful installation of Linux on the new Santa Rosa MBP... I think I'll wait until someone else gets it going before trying again :)

---

### Post by Gen2ly on 2007-06-15
I'd like to see a few images of these sed beasties, see their bad charm.

---

### Post by tweeknockr on 2007-06-15
Here is the thread that talks about the nvidia driver issue:

[http://www.nvnews.net/vbulletin/showthread.php?t=92980](http://www.nvnews.net/vbulletin/showthread.php?t=92980)

Someone posted an image that is the same as what I see here: [http://flickr.com/photos/robbyt/537741087/](http://flickr.com/photos/robbyt/537741087/)

I don't have any screenshots of the ethernet not working in fedora :)

---

### Post by Gen2ly on 2007-06-16
Ah, that looks nice.

[IMG]http://farm2.static.flickr.com/1116/537741087_eef6145f6b.jpg?v=0[/IMG]

My MacBook feels old. :(

---

### Post by bcrawfor on 2007-06-16
I have a Macbook Pro that I purchases in Dec 2006. (Intel Core 2 Duo 2.16 ghz)

I have a triple boot system using rEFIt that works outstanding so far.
(Mac OS X...Open SUSE 10.2 64bit...Windows VISTA Ultimate)
The hadest part was setting LILO up for the linux partition.

I only have two problems.

Everytime I boot Windows Vista, I get an FDISK related error. I think it is because I am not marking my Windows Vista drive as bootable with FDISK...because Linux HAS to be marked as bootable to run at all. Vista will boot, it just gives me a bunch of errors before doing so. Any idea how to solve this problem?

Also, the only other minor issue i have is my graphics driver in Linux. Does ATI have as linux driver that works for the ATI x1600 mobile card? The driver i got from their website doesnt seem to work. I want graphics support so i can run BERYL. =(

---

### Post by ilmarw on 2007-06-19
I have triple boot working fine with the new MBP, rEFIt does what it is supposed to.. Take care, however, to install GRUB on /dev/sda3, not hd0, or else both booting Vista and Linux will send you to GRUB.

However, I cannot get the Marvell ethernet card to work, it says unknown device. Without htat, I cannot get any further. And oh yeah, this is Edgy, I cannot get past the tty problem with Feisty.

---

### Post by ronocdh on 2007-06-19
> **yanaventer said:**
> I've just picked up a one of the new MBP and managed to install Ubuntu & MacOSX together with the latest version of refit which has seemed to have fixed the previously mentioned bug.

The installation went fine but I'm having trouble getting the network card + graphics card to work under Ubuntu. I tried modprobing sk98lin and sky2, nothing shows up in dmesg when I do that despite now appearing in lsmod.

lspci shows there is a marvell technology ethernet controlled but as an unknown device, the same for my nVidia graphics card. I haven't really tried playing around with different graphics drivers since getting my network card working is my priority :D.
This thread is for triple booters on the new machines, and so your post might not get the attention it deserves. Try searching this forum for madwifi threads... [this one]("http://ubuntuforums.org/showthread.php?t=474144") pertains specifically to the new MBPs. Good luck!

---

### Post by mdegner on 2007-06-20
> **ilmarw said:**
> I have triple boot working fine with the new MBP, rEFIt does what it is supposed to.. Take care, however, to install GRUB on /dev/sda3, not hd0, or else both booting Vista and Linux will send you to GRUB.

However, I cannot get the Marvell ethernet card to work, it says unknown device. Without htat, I cannot get any further. And oh yeah, this is Edgy, I cannot get past the tty problem with Feisty.


I ran into the same issue, I could only install Edgy, and the Ethernet card didn't work.  My fix was to use a USB Ethernet adapter (Linksys USB200M) and do a distribution upgrade to Feisty.  You may also be able to do this directly with CD, though they suggest you have all of your packages updated to do this.  If you have network AND the CD, it will download upgraded packages from the Internet, but use most of the packages from the CD.  Slick.  And quicker.

[http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807](http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807)

Once upgraded to Feisty, the Ethernet port worked perfectly, and I downloaded the latest madwifi-ng SVN (as of 6/20/2007) to get wireless working.

Audio and video are still issues, however.

I went into this project hoping I could remove the EFI partition and use the 4 partitions for Mac, Linux, Windows and Data, but I haven't been able to successfully partition in that manner.  Everything wants to restore the EFI partition.  I have a possible solution, and I'm testing it right now.  My first potential solution was to install XP on a large FAT32 partition, but XP didn't want to boot off of it.  Now I'm running XP on a large  NTFS partition to store data and run the OS, and I'm accessing it from Linux and OS X using FUSE and ntfs-3g.  So far, so good, but I've just started testing.

---

### Post by ivesjd on 2007-06-20
Try running sudo update-pciids to get rid of the unknowns when running lspci

---

