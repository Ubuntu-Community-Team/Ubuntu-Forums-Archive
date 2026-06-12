---
title: "Repartitioning a Dual-Boot back to Linux"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by StarscreamD on 2007-03-08
My disks are a mess and I need a game plan. Here is what I have.

> Disk /dev/hda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1215     9759456    7  HPFS/NTFS
/dev/hda2            1216        1801     4707045   83  Linux
/dev/hda3            2350        2431      658665    f  W95 Ext'd (LBA)
/dev/hda4            1802        2349     4401810   83  Linux
/dev/hda5            2378        2431      433723+  82  Linux swap / Solaris
/dev/hda6            2350        2377      224847   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        7296    58605088+   c  W95 FAT32 (LBA)

I want to keep this partition, whichever one that is, and get rid of all other partitions on the first 18 gig drive and go straight ext3, and I need to import the settings I currently have into that partition so I don't lose any of my hard work getting this OS to work with my hardware. What should I do?

---

### Post by Neobuntu on 2007-03-08
It depends on your hardware, including memory doesn't it?

What do you have? Which Windows do you want to run and what Open software distribution release do you want to run? I recommend Kubuntu dapper.

---

### Post by K.Mandla on 2007-03-08
Oh boy. Hmm. :-k First thing I would do is back up everything, because any time you play with partitions you're asking for a disaster.

After that I would find the partitions you use for Ubuntu (root and swap), and then use the GPartEd live CD to delete and merge partitions as you like. I don't think I would trust anything but GPartEd to get it right, and not screw things up.

I believe after you've freed up the empty space, you can merge the partitions back together and not lose anything from your root setup.

I'd be very very careful about this. If you went through a lot of hoops to get things working, you might want to put this off for a while longer. A sloppy partition table is a minor fault if the alternative ends up being a complete reinstall. :shock: [-o<

---

### Post by rusty4r on 2007-03-08
looks like you have two linux partitions and two swap file partitions?

---

### Post by StarscreamD on 2007-03-09
> **Neobuntu said:**
> It depends on your hardware, including memory doesn't it? What do you have?
I run a 1.3 Ghz Celeron w/ 512 MB of SDRAM and a NViDiA GeForce MX 420 video card.
> **Neobuntu said:**
> Which Windows do you want to run and what Open software distribution release do you want to run? I recommend Kubuntu dapper.
I have been playing with Ubuntu Edgy but I run many K apps such as Ktorrent and K3b. Perhaps I will run Kubuntu. I have already deleted windows, so let's forget that.
> **K.Mandla said:**
> ...and then use the GPartEd live CD to delete and merge partitions as you like. I don't think I would trust anything but GPartEd to get it right, and not screw things up.
My Dell Dimension has an onboard Intel chipset that automatically becomes primary display device during any automated install process. Gparted LiveCD could not get X running, and I suspect that this may be the reason. I attempted to change BIOS settings and use the onboard card to configure GParted as well. I could not get it to work. I just ended up deleting all the partitions and reinstalling Ubuntu. Currently, I am attempting restoring my partition through Simple Backup, and /var is taking an excruciatingly long amount of time.
> **K.Mandla said:**
> A sloppy partition table is a minor fault if the alternative ends up being a complete reinstall. :shock: [-o<
Hehehe... Too late!
> **rusty4r said:**
> looks like you have two linux partitions and two swap file partitions?
Not any more. I suspect this happened when the kernel was updated at some point. In the old GRUB menu I had when that table was setup, there were two versions of Ubuntu I could boot into, just different kernel versions. I think there was something I messed up on or something on install to cause this.

I understand /var is where all the downloaded packages of installed files are kept. How long should I expect to wait for /var to restore using Simple Backup with my hardware? If I can successfully restore my partition, I will be completely resolved. **Thank you all**.

---

### Post by Neobuntu on 2007-03-09
I was going to say, be sure to install Windows first; if you want a dual boot. Yet, your decision to go all Linux will save you, A LOT of time.

My recomendaion is to back up everything you can't live without to a USB flash drive and verifiy everything is there.

Then put in a verified **Kubuntu Dapper** Live i386 CD. (For your main; non-testing workstation)

(Yes, you can upgrade to Edgy later. Dapper will be more stable. Edgy is almost where is should be; being the current release.)

Let it do it's thing, quickly and automatically. Let it do all the partitioning and install on the whole, newer drive. Note what it did. Use your old drive for backup later (FAT32 for multi-OS compatibility?), maybe. Perhaps you could put it into an inexpensive, external USB enclosure.

Copy your important document type files, over (or keep them double backed up somewhere). 

Do not copy all your (hidden) setting files over at one time. 
Refer to them if you need to adjust something and if you want to do it, with it's configuration text file. 
Point and click from your new, clean, base, Kubuntu install.

I think this way will be the fastest way and produce the best, stable results.

P.S. You can (of course) add the ubuntu-desktop as well. Upgrades will take longer(with both). You must start with either Kubuntu or Ubuntu; if you want faster upgrades. 

Also, you can still run GTK based Gnome apps (or vise versa) without a problem. 

I downloaded the Gnome theme "Aquativo" ( [http://www.gnome-look.org/content/show.php?content=19911](http://www.gnome-look.org/content/show.php?content=19911) ) to use with Kubuntu when running Gnome programs. Just right click the download file to extract the directory, and then drag that "Aquativo" directory into a ".themes" hidden directory; in your home folder. It is not difficult.

Type the command "switch2" (install the "gtk-theme-switch" package) to set Gnome/GTK2 themes (engines) if you use KDE; for cool looking GTK'ness.  This includes the (GTK) scroll bars and other things in Firefox, using it's default theme. I use the "Baghira" kwin STYLE package for the KDE theme (set to match well). This matches everything. Yet, the default Kubuntu KDE theme is good to go, if you have little time to change it. it's the best I have seen on a fresh install (of anything).

P.S.S. For more theme specific coolness, I set Baghira (KDE Style) to Milk, Milk, and Milk. I reset the button color to "Aqua" blue and use rounded buttons. Then in KDE Windows Deco; set it to baghira. Set this Baghira Window borders to Milk too and that coincides with the right most tab "special"(I DO NOT KNOW WHY IT IS NOT CALLED MILK). I make all corners rounded and add a "4" for window boarder size. Then, I set the ACTIVE title bar to mid blue and light blue GRADIENT (matching with the easy color grabber dropper thing). Then the INACTIVE title to mid grey and dark gray GRADIENT(Normally, title bar colors are set in the KDE color settings but not when using Baghira for Window borders. It is more specific.)  

Note that the (GTK/Gnome) Aquativo theme matches very well (running gnome apps) with the above KDE tweaks and Firefox, set to it's default (GTK actually) theme.

Best of the best, of the best. :)

---

### Post by StarscreamD on 2007-03-09
OK, thanks for the advice. I think I will; I keep hearing that most prefer Kubuntu. This is where I'm at right now:

> Disk /dev/hda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2328    18699628+  83  Linux
/dev/hda2            2329        2431      827347+   5  Extended
/dev/hda5            2329        2431      827316   82  Linux swap / Solaris

Disk /dev/hdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        7296    58605088+   c  W95 FAT32 (LBA)


The only install disk I have currently is a Ubuntu Edgy 6.10, and I had it running with some modification because my legacy NViDiA card(GeForce MX 420) and my onboard card (Intel). If I get Kubuntu Dapper, will my NViDiA card be automatically detected and start X right away?

Also, I let the Ubuntu install disk install on the whole 20 gig hd up there, and I let it do it automatically. I assumed it would take 1024 mb for swap and take the rest of the drive, but that is what it did. Can somebody explain why this happened? Thank you!

Edit: I am currently downloading Kubuntu Edgy and Dapper so let me know which way I should go. Thank you!

---

### Post by StarscreamD on 2007-03-09
> **Neobuntu said:**
> You can (of course) add the ubuntu-desktop as well, but upgrades will take longer.

UPDATE- I have deleted all partitions and set swap to 1030 mb, and the rest for Ext3 Kubuntu Fiesty Fawn 7.04 on my 20 gig hd. I am currently completely updating using Adept updater. Two things strike me first-

I am familiar with most of these apps because I used them in Ubuntu already like Ktorrent, Konqueror and K3b. However, I like the Ubuntu setup much better desktop wise. You said I could install Ubuntu instead but the upgrades would take longer. Do I just install the package(ubuntu-desktop)? 

Also: why are the upgrades going to take longer if I install Ubuntu instead? Again, thank you for your time, patience, and advice everyone. You have been there through my PC's intensive OS/BIOS/Disk tampering.
=D>

---

### Post by Neobuntu on 2007-03-11
Umm, that's not what I said.

Reiterate:

Install Kubuntu Dapper First and on your largest and therefore probably fastest drive; as your main usable computer (workstation). 

Let it decide and do the swap, it's size and everything.

What I said was, installing both kubuntu-deskop and ubuntu-desktop is fine but will result in more programs (some you wind up not using) that need (automatic) upgrade. Therefore if you already know which one you want, it will save you time.

...and do not forget, one can run KDE AND Gnome apps on either KDE or Gnome. 

I strongly PREFER KDE and kubuntu therefore I recommend starting with the Kubuntu Dapper (x86) live CD. (Or Alternate Kubuntu Dapper CD  for special needs).

Feisty is ALPHA stage pre-testing; not even Beta yet (and not upgrading properly, it's a test people)  and IMHO Edgy is in between right now (though released and stabilizing for every use case) and easy to upgrade from Dapper LATER.

I make these general recommendations to everyone, but did I misunderstand your goal?

Then (due to politics and corruption) to click to load/unload "non-free" extras (Flash, Firefox plug-ins and a lot more) using easy to cut and paste-install [Automatix2]("http://getautomatix.com") (then click installation for latest matching, easy install) to complete your total install. Note: Automatix items can be done by hand, using the super ubuntu forums and may not be needed in future releases.

Tip: Tripple click to highlight a line of command text, then just cut and paste it into a "Terminal" window (such as Konsole) and hit your <ENTER> key. It's that simple. With Dapper (currently), you don't even have to do that, but just download the Automatix package and right click, install it.

Again, if you want to save time.

---

### Post by StarscreamD on 2007-03-11
Feisty is up and running fantastic. It far surpasses what Dapper or Edgy do in terms of getting X up the first time: it works around my onboard card, installs my nvidia drivers, and was seamless to install beryl. Fantastic. I chose not to install Gnome desktop as I was able to modify the kde desktop to suit my needs. Here's what I end up with, thanks again!
[IMG]http://i37.photobucket.com/albums/e71/starscreamd/desktop.png[/IMG]

---

### Post by Neobuntu on 2007-03-12
Excellent!

Yes, I have Feisty running on a notebook beside me. It sure is NOT my main work system though. 

It will be, after it's been released a while.

You guys out there, take it from me. Test away but be VERY reserved about your main systems and those you install for others.

Beta's, and especially alpha's like Feisty can be and should be installed elsewhere, as a secondary (or just not primary) stable working system. 

See, there's stable, and then there's really stable and then there's servers.  It runs and surfs the Internet; all the way to every popular, real world computer benefit, shines.

Enjoy:guitar:

---

### Post by AllanP on 2007-03-15
I have read most of the answers to your post and while I cannot add anything not already covered I can suggest a really neat backup solution. I mess around with my system a lot; trying out programs, messing with files that I shouldn't mess with. Acronis True Image always saves my but. It even backs up the MBR it isn't cheap but, in my humble opinion well worth the $70.00. The only problem is you have to install it into Windows to make the bootable emergency CD which is what I use. This CD may be included in the shrink wrap package. I have the downloaded product. Here is the link and good luck: [http://www.acronis.com/homecomputing/holidays/2006/](http://www.acronis.com/homecomputing/holidays/2006/)

---

