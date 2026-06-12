---
title: "On making Windows restore disk or backup etc."
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ccfjeff on 2007-06-13
I'm wanting to set up a dual boot system for now.  I have a "new" (to me) Dell that had apparently been wiped clean and WinXP reinstalled.  Unfortunately, it did not come with any install or rescue disks etc.

I am suffering the consequences of not making a backup or rescue disk or whatever for the computer I had been using prior to this new one (and am using at the moment).  It was an HP factory refurb purchased from PCMall and came with all of the software pre-installed but none of the installation software on removable media of any sort.  My hard drive crashed and burned and a computer company, which has since gone out of business, installed a new hard drive and reinstalled the software for me.

Unfortunately, a year or so later Microsoft installed their "Genuine Advantage" virus on my computer to give me delays on startup and warnings that the software may be pirated and that I need to buy another copy, not to mention occasionally hijacking browser pages to their purchase site, downloads doing who knows what despite the fact that they say I am not able to get updates from them, and so on.

The bottom line is that I would like to preclude such problems again on this new system in case my hard crashes or I mess up WinXP with my Ubuntu install or partitioning or whatever.

[ The Ubuntu Documentation Page]("https://help.ubuntu.com/7.04/windows/C/preparing-backing-up-entire.html") lists some proprietary disk imaging software for making duplicates, but I'm wondering if that is the only solution.  I have a couple of external USB drives that had Norton's Ghost Image but I had never been able to use them on my old system as I apparently didn't have enough free space to allow it to back things up to my external drives (which were 80 gig HD vs 40 gig on the C: drive).

An HP technician once told me that he had never had any success in using the Norton Ghost program to reinstall an OS that had been lost.  I don't know if he just wasn't familiar with how to do so or if the software just isn't capable of doing so, or isn't always reliable.

Can Windows XP make some sort of rescue or restore disk/CD that would do the trick?  Or is there any free software out there that would allow me to reinstall Windows should catastrophy strike?

Any advice or help would be appreciated.

Thank you.

---

### Post by Jimmyfj on 2007-06-13
It might just be worth for you to try out the Ubuntu Live-Cd before installing. Being without a Windows Install set is not the worst you experience - I think that when you first have tried out Ubuntu for some days running from the live cd you'd never go back to Windows. Windows isn't worth the effort of pirating the software

---

### Post by ccfjeff on 2007-06-13
> **Jimmyfj said:**
> It might just be worth for you to try out the Ubuntu Live-Cd before installing. Being without a Windows Install set is not the worst you experience - I think that when you first have tried out Ubuntu for some days running from the live cd you'd never go back to Windows. Windows isn't worth the effort of pirating the software

I have used the Live-CD and it seems to work OK, though, it doesn't look like it will be able to run my Visioneer scanner nor my Canon printer/scanner/fax/combo unit.

I would love to ditch Microsoft, but I have a Windows program or two that I use in my business that I don't think will port over to Ubuntu.  One, for instance, is a program that computes auto insurance rates for multiple insurance companies.

I believe at least one company I work with also has some sort of Windows application that must be run as well.

It seems that I am stuck with Windows unfortunately, at least for the time being.

Is there no way for me to do some sort of backup, restore disk, rescue disk, or disk image etc. for my existing WinXP installation without having to resort to some sort of pirating?

---

### Post by Jimmyfj on 2007-06-13
To test your scanner and printer go to the System/Acceseries/Removable Devices and look for the tab "Printer & Scanner - Mark the Run program automaticly when device inserted, (or something similar - I use the Danish language packet for my Ubuntu) Then turn on your scanner and see if Ubuntu supports it.

For your Canon printer simply go to System/Administration/Printing and find the printer in there. This will install the driver needed for the printing job.

---

### Post by ccfjeff on 2007-06-13
> **Jimmyfj said:**
> To test your scanner and printer go to the System/Acceseries/Removable Devices and look for the tab "Printer & Scanner - Mark the Run program automaticly when device inserted, (or something similar - I use the Danish language packet for my Ubuntu) Then turn on your scanner and see if Ubuntu supports it.

For your Canon printer simply go to System/Administration/Printing and find the printer in there. This will install the driver needed for the printing job.

Thank you.  I'll check that out.  I had been going on the assumption they wouldn't work as I didn't see the scanner on a Ubuntu or Linux hardware compatibility list.  I had also seen the printer All-in-one unit listed as a "paperweight" on another list.

I would be ecstatic though if they would work.

---

### Post by RedRover1 on 2007-06-13
You could also try the free part of VMware converter.  Some issues include that you need to save the output from converter to another PC through a network and even after its done you may get tripped up by "Genuine Advantage" as is sees the VM running on a new BIOS/virtual hardware.  If it works you can then just run VMware Server or Player.

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

[https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

### Post by ccfjeff on 2007-06-13
> **RedRover1 said:**
> You could also try the free part of VMware converter.  Some issues include that you need to save the output from converter to another PC through a network and even after its done you may get tripped up by "Genuine Advantage" as is sees the VM running on a new BIOS/virtual hardware.  If it works you can then just run VMware Server or Player.

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

[https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

Thanks for the feedback.  That looks like a unique way to do it.

I'm curious about a couple of things, however.

Excerpted from your first link:[LIST]
[*][COLOR=DarkRed]Restore VMware Consolidated Backup (VCB) images of virtual machines to running virtual machines.[/COLOR]
[*][COLOR=DarkRed]Clone and backup physical machines to virtual machines as part of your disaster recovery plan.[/COLOR][/LIST]1.  Would the saved files be a true backup ie. something that I could restore the system to as is?  Or would it be saved only as a Virtual Machine that could only be run inside other software?

2.  Would I have to have a CD of the original OS to make that backup or copy?

separate issue:

3.  Could I run Ubuntu as a virtual machine within XP Pro without having to reinstall the Windows software?

---

### Post by RedRover1 on 2007-06-13
> **ccfjeff said:**
> Thanks for the feedback.  That looks like a unique way to do it.

I'm curious about a couple of things, however.

Excerpted from your first link:[LIST]
[*][COLOR=DarkRed]Restore VMware Consolidated Backup (VCB) images of virtual machines to running virtual machines.[/COLOR]
[*][COLOR=DarkRed]Clone and backup physical machines to virtual machines as part of your disaster recovery plan.[/COLOR][/LIST]1.  Would the saved files be a true backup ie. something that I could restore the system to as is?  Or would it be saved only as a Virtual Machine that could only be run inside other software?

2.  Would I have to have a CD of the original OS to make that backup or copy?

separate issue:

3.  Could I run Ubuntu as a virtual machine within XP Pro without having to reinstall the Windows software?

1.  Never tried it but its called V2P, you can search google for V2P and vmware

2.  No VMware converter is designed to take the machine as is into a virtual environment.

3. Yes, I do it now.  If you install the free VMware server you can create a blank Ubuntu VM (Virtual Machine)and then load Fiesty into that.  The only issue with server is its not optimized for the best display or sound.  VMware Player is free and is optimized but can't create VMs only read existing ones.  For Player you can download already created VMs from the VMware site or use a site like EasyVMX.  You can also install Server, create the VM then unistall Server and then install Player.

[http://www.vmware.com/vmtn/appliances/](http://www.vmware.com/vmtn/appliances/)

[http://www.easyvmx.com/](http://www.easyvmx.com/)

---

### Post by ccfjeff on 2007-06-13
> **RedRover1 said:**
> 1.  Never tried it but its called V2P, you can search google for V2P and vmware

2.  No VMware converter is designed to take the machine as is into a virtual environment.

3. Yes, I do it now.  If you install the free VMware server you can create a blank Ubuntu VM (Virtual Machine)and then load Fiesty into that.  The only issue with server is its not optimized for the best display or sound.  VMware Player is free and is optimized but can't create VMs only read existing ones.  For Player you can download already created VMs from the VMware site or use a site like EasyVMX.  You can also install Server, create the VM then unistall Server and then install Player.

[http://www.vmware.com/vmtn/appliances/](http://www.vmware.com/vmtn/appliances/)

[http://www.easyvmx.com/](http://www.easyvmx.com/)

Thanks again!

Could Windows & Ubuntu share files at all?  ie. could Ubuntu read and write Windows data stored outside the virtual machine or could Windows read and write to the files created by Ubuntu?  I know they can't do so natively, but can do so on a traditional partitioned dual boot system with software such as [NTFS-3G Read/Write Driver]("http://ubuntuforums.org/NTFS-3G%20Read/Write%20Driver")

---

### Post by danny_kay1710 on 2007-06-13
from my experience norton ghost is a very good bit of software to back up a windows installation to make it work again however you do need to buy it.

Norton Ghost 9.0 is the one i would recommend (also known as norton ghost 2003) and can burn directly to a bootable disk for you - it has the best success rate i have ever seen with disk imaging software and it will only backup the data on the drive e.g. it will not backup the full 80gb capacity just the data on it - as far as i am aware the compression aint to bad either.

That may be your best option i would think

---

### Post by ccfjeff on 2007-06-13
> **danny_kay1710 said:**
> from my experience norton ghost is a very good bit of software to back up a windows installation to make it work again however you do need to buy it.

Norton Ghost 9.0 is the one i would recommend (also known as norton ghost 2003) and can burn directly to a bootable disk for you - it has the best success rate i have ever seen with disk imaging software and it will only backup the data on the drive e.g. it will not backup the full 80gb capacity just the data on it - as far as i am aware the compression aint to bad either.

That may be your best option i would think

Thanks for the feedback.  The Norton Ghost disks came as a package with the external drives as I recall, though I couldn't use them successfully at the time as my C: drive didn't have enough empty space on it even after I did some housecleaning and I eventually gave up.

I'll have to see if I can locate those disks.  It sounds perfect as the new drive is almost all empty space.

Thanks again for the feedback!

---

### Post by RedRover1 on 2007-06-13
> **ccfjeff said:**
> Thanks again!

Could Windows & Ubuntu share files at all?  ie. could Ubuntu read and write Windows data stored outside the virtual machine or could Windows read and write to the files created by Ubuntu?  I know they can't do so natively, but can do so on a traditional partitioned dual boot system with software such as [NTFS-3G Read/Write Driver]("http://ubuntuforums.org/NTFS-3G%20Read/Write%20Driver")

Yes, the easiest (and safest) is using SAMBA and using network shares.  It ends up being just like if you shared folders between two different PCs.

---

### Post by ccfjeff on 2007-06-13
> **RedRover1 said:**
> [quote=ccfjeff;2838973]Thanks again!

Could Windows & Ubuntu share files at all? ie. could Ubuntu read and write Windows data stored outside the virtual machine or could Windows read and write to the files created by Ubuntu? I know they can't do so natively, but can do so on a traditional partitioned dual boot system with software such as [NTFS-3G Read/Write Driver]("http://ubuntuforums.org/NTFS-3G%20Read/Write%20Driver")Yes, the easiest (and safest) is using SAMBA and using network shares.  It ends up being just like if you shared folders between two different PCs.[/quote]

Awesome!  That sounds like almost the perfect setup for me then.  I would prefer, of course, to run Ubuntu as the host system and Windows as the virtual machine, but it still sounds a lot easier than dual booting if you want to switch back and forth quickly.

Thank you very very much.

Do the links you provided earlier explain how to do all of that, or is there a tutorial that you are aware of giving step by step instructions or at least a pretty detailed explanation?

BTW, would browsing and retrieving/reading email in the Ubuntu VM provide much protection from Windows viruses if one doesn't deliberately access infected files from Windows?

---

### Post by RedRover1 on 2007-06-13
> **ccfjeff said:**
> Awesome!  That sounds like almost the perfect setup for me then.  I would prefer, of course, to run Ubuntu as the host system and Windows as the virtual machine, but it still sounds a lot easier than dual booting if you want to switch back and forth quickly.

Thank you very very much.

Do the links you provided earlier explain how to do all of that, or is there a tutorial that you are aware of giving step by step instructions or at least a pretty detailed explanation?

BTW, would browsing and retrieving/reading email in the Ubuntu VM provide much protection from Windows viruses if one doesn't deliberately access infected files from Windows?

Take a look at the below PDF if you are going to try with server. I would look through Chapters 1,2,3 to get you going and maybe 7 to get the network setup right.

[http://www.vmware.com/pdf/server_vm_manual.pdf](http://www.vmware.com/pdf/server_vm_manual.pdf)

The forums can be a lot of help also [http://www.vmware.com/community/index.jspa](http://www.vmware.com/community/index.jspa)

Yes, checking you email on an Ubuntu VM will protect you from Windows viruses nearly 100% at this point in time.  Also your web browsing is safer and you can even set your VM not to save any changes when it shutsdown making it a kind of Read Only OS if you like.

---

### Post by ccfjeff on 2007-06-13
> **RedRover1 said:**
> Take a look at the below PDF if you are going to try with server. I would look through Chapters 1,2,3 to get you going and maybe 7 to get the network setup right.

[http://www.vmware.com/pdf/server_vm_manual.pdf](http://www.vmware.com/pdf/server_vm_manual.pdf)

The forums can be a lot of help also [http://www.vmware.com/community/index.jspa](http://www.vmware.com/community/index.jspa)

Yes, checking you email on an Ubuntu VM will protect you from Windows viruses nearly 100% at this point in time.  Also your web browsing is safer and you can even set your VM not to save any changes when it shutsdown making it a kind of Read Only OS if you like.


Thanks once again!  It looks like I have a little more reading to do.

If I can open Ubuntu within a Windows Window and run Linux programs without having to reboot I will be a very happy camper.

---

### Post by ccfjeff on 2007-06-14
> **danny_kay1710 said:**
> from my experience norton ghost is a very good bit of software to back up a windows installation to make it work again however you do need to buy it.

Norton Ghost 9.0 is the one i would recommend (also known as norton ghost 2003) and can burn directly to a bootable disk for you - it has the best success rate i have ever seen with disk imaging software and it will only backup the data on the drive e.g. it will not backup the full 80gb capacity just the data on it - as far as i am aware the compression aint to bad either.

That may be your best option i would think

I stumbled across another piece of cloning software licensed under "the [GNU FDL]("http://www.gnu.org/licenses/fdl.html") Free Documentation License." :

[http://clonezilla.sourceforge.net/clonezilla-live/](http://clonezilla.sourceforge.net/clonezilla-live/)

[COLOR=DarkRed]...the Free Software Lab at the NCHC has combined [Debian Live]("http://debian-live.alioth.debian.org/") with Clonezilla to produce "Clonezilla Live," a new software that can be used to easily clone individual machines. ... Clonezilla Live can be used to clone individual computers using a CD/DVD or USB flash drive. Though the image size is limited by the boot media's storage capacity, this problem can be eliminated by using a network filesystem such as sshfs or samba. ///Note/// PXEBoot Clonezilla should still be used to clone many computers simultaneously.

[COLOR=Black]It is bundled with G-Parted partitioning program on a live bootable CD here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

[/COLOR] [/COLOR]

---

### Post by Castigate on 2007-06-14
Thanks for the links to Clonezilla and Gparted live.  Been looking fo something like those :D

---

### Post by Castigate on 2007-06-15
I tried out Clonezilla and Gparted.  Gparted is very good and easy to use.  Clonezilla is a little complicated.  I was able to back up system but it seems it only wants to backup to the same drive:(  Try using [Acronis True Image 10 Home]("http://www.acronis.com/homecomputing/products/trueimage/")  Its straight foward, easy to use and very good:D

---

### Post by ccfjeff on 2007-06-15
> **Castigate said:**
> I tried out Clonezilla and Gparted.  Gparted is very good and easy to use.  Clonezilla is a little complicated.  I was able to back up system but it seems it only wants to backup to the same drive:(  Try using [Acronis True Image 10 Home]("http://www.acronis.com/homecomputing/products/trueimage/")  Its straight foward, easy to use and very good:D

Thank you for coming back and posting that.

I had tried Clonezilla last night and agree that it isn't all that intuitive.  It hung up a couple of times and had said there wasn't enough room.  I wasn't sure exactly what it was doing.  If it was trying to back up to the hard drive their should have been plenty of room.  I just bought that computer (used) and the only thing on it is supposed to be the OS.

I was wondering if it was trying to back up to the CD/DVD.  

In [the Clonezilla tutorial]("http://clonezilla.sourceforge.net/clonezilla-live/"),  about halfway down the page it lists  some of the very early options:

[IMG]http://drbl.sourceforge.net/screenshot/?op=show&filepath=album//01_Clonezilla/03_clonezilla-live-boot-menu-gra.png[/IMG]

I believe I hit enter a little too quickly and didn't try the second option which may have allowed me to pull out the boot disk and record to the CD/DVD drive:
[INDENT][COLOR=DarkRed]The 2nd choice, "Clonezilla live (To RAM. Boot media can be removed later), is the same function with the 1st one except when Clonezilla live booting finishes, all the necessary files are copied to memory. Therefore you can remove the boot media (CD or USB flash drive) then.[/COLOR]
[/INDENT]For some reason I could not get back to that screen, even when I rebooted the computer (several times).  Maybe I'll try it again today before giving up.

Thanks again for the link.  Even if I'm able to get this other one to work, I'll bet others would prefer that software.

By the way, as you say having GParted is probably worth the download even if Clonezilla isn't used.  I read in another post where someone recommended using a separate GParted disk to partition the drive(s) and then installing Ubuntu.  I've read others recommend to people whose systems had hung up during the install to do the steps separately as well rather than using the Ubuntu LiveCD to do the partitioning and installation in one step.

---

### Post by Castigate on 2007-06-17
Yeah it's probably a good idea to prepare you partitions first with gparted than install Ubuntu.   I never had any problems installing Ubuntu from the live cd.  I gave up on Clonzilla though:(  It backs up your hardrive image on your harddrive or usb drive.  Then you have to burn it to cd/dvd.  Then when you want to reinstall you have to put the image back on a hardrive.  When I was trying to clone another system it seemed to only want to install on the first drive.  There is no way to change that in GUI:(  Probably from the command line you can do everything but the GUI sux.  I already had Acronis, it came as maxblast for maxtor drives.  I got the full version because I had some western digital drives.  It works pretty good:D  Good luck and post any new findings.  Also try [super grub disk]("http://supergrub.forjamari.linex.org/")   It will help you restore Grub on your MBR automatically if you lose it during installation.  I used it already once and it saved me.  Try also   [Ghost for linux]("http://sourceforge.net/projects/g4l") I downloaded it but havent  tried it yet.  I post results later.

---

### Post by ccfjeff on 2007-06-17
> **Castigate said:**
> Yeah it's probably a good idea to prepare you partitions first with gparted than install Ubuntu.   I never had any problems installing Ubuntu from the live cd.  I gave up on Clonzilla though:(  It backs up your hardrive image on your harddrive or usb drive.  Then you have to burn it to cd/dvd.  Then when you want to reinstall you have to put the image back on a hardrive.  When I was trying to clone another system it seemed to only want to install on the first drive.  There is no way to change that in GUI:(  Probably from the command line you can do everything but the GUI sux.  I already had Acronis, it came as maxblast for maxtor drives.  I got the full version because I had some western digital drives.  It works pretty good:D  Good luck and post any new findings.  Also try [super grub disk]("http://supergrub.forjamari.linex.org/")   It will help you restore Grub on your MBR automatically if you lose it during installation.  I used it already once and it saved me.  Try also   [Ghost for linux]("http://sourceforge.net/projects/g4l") I downloaded it but havent  tried it yet.  I post results later.

Thanks for the feedback and info!

I'll have to check those out.

I don't know if it's worth it, but I might try an older vesion of Clonezilla or see if they have a newer version out.  That last one was only a couple of days old when I downloaded it.  They may have left a little out on that update.  The screenshots were different than what was on the gui.

Thanks again!

---

