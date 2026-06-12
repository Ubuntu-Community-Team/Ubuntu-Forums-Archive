---
title: "Only OpenSuse Install DVD Boots on my G4 PPC"
date: 2008-07-26
forum: Apple Hardware Users
---

### Post by motsteve on 2008-07-26
I know a lot of people are going to be saying "What?!" to my problem.  They may even suggest doing this or that to generate a DVD, but believe me, I have tried everything involving burning DVD's from using different media to burn software
to drive to different operating systems, etc.  Linux distro's, except for OpenSuse, will not boot on my >>G4<< ppc and this includes Linux distro's on a commercially made DVD. DVD's, commercial or made on my DVD drive, which boot into the MacOS, always boot on my G4.  I've never read about any problems with
G5's, but there very well could be an explanation for this. Read this page:

[http://penguinppc.org/bootloaders/yaboot/doc/yaboot-faq.shtml](http://penguinppc.org/bootloaders/yaboot/doc/yaboot-faq.shtml)

This would explain somewhat why OpenSuse boots and the other distro's don't, and I repeat, on my >>G4<< ppc.  It could be that the G5's have Open Firmware that easily recognizes a bootable Linux distro DVD and so there's no problem with Linux.  What I am wondering is whether anyone out there knows of a trick to change the G4's Open Firmware or an alteration that can be made to the Linux distro's image before burning, that will enable all Linux distro's to be bootable.  The firmware on my G4 is the last firmware that was Apple blessed and distributed.(Power Mac G4 Firmware Update 4.2.8)  My G4 system: Digital Audio Tower.

BTW, all of the distro's I've made for my Intel iMac boot, but iMac uses Intel standard EFI for booting.

---

### Post by tiresia on 2008-07-26
Sorry for my stupid question, are you sure that you use the right DVD medium to burn? I mean do you know if your drive can use both DVD-R and DVD+R? And why do you use a DVD? You need just a CD (at least for Ubuntu)

---

### Post by mkvnmtr on 2008-07-26
I am on a 5 year Ibook. I can't get 8.04 or 7.10 to boot either. Gets to a point goes black, tells me it is loading, then usually goes grey and nothing. Sometimes I couldn' get 7.04 to boot, sometimes it would. 6.06 always boots. Have you tried to boot an older version? Then upgrade.

---

### Post by motsteve on 2008-07-26
> **tiresia said:**
> Sorry for my stupid question, are you sure that you use the right DVD medium to burn? I mean do you know if your drive can use both DVD-R and DVD+R? And why do you use a DVD? You need just a CD (at least for Ubuntu)

I don't consider that stupid.  Yes I've tried DVD+RW DVD-R DVD+R, etc.  My drive according to the info is compatible with everything except I'm not sure if double layer is included.  OpenSuse works no matter what media and I've tried to make it not work also, but it's a Timex.  Takes a lickin' and keeps on tickin'.

The DVD drive is a DVR115D with the latest firmware.  

To answer another question in the thread, I tried Intrepid Ubuntu, but it was a no go also.

Anybody need Linux distro DVD's?  I have a load of them. :-)

---

### Post by tiresia on 2008-07-26
As I sad before, why do you use DVD? you need just a CD.
Anyway, you can try to boot the installer with Open Firmware command.
OF in NewWorld is just fine.
Try typing:
0 > boot cd:,\install\yaboot

Here you can find more informations:
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html)

---

### Post by motsteve on 2008-07-26
I did try a CD.  No go.

Type OF command into what?  I'm not on some system trying to run Linux from a CD.  I'm trying to install Linux onto a hard drive.  I can not get the installer disk to boot so that it can run its installation software.  I would imagine that Yaboot is already on the installation disk.  At least yaboot.config would have to be there to tell the cpu what kernel, etc to install.  I'm only familiar with installing Linux or MacOS booting from the CD or DVD and not from some other method.  Installation of OpenSuse required only inserting the DVD and away it went.

---

### Post by tiresia on 2008-07-26
Can you please specify:
1. which Ubuntu version are you trying to install
2. how have you burned the .iso image
3. your graphic card
4. your processor
5. RAM

What does it happen, when you press C in order to boot the installer?
Do you get anything?
And what does it happen, if you press the Option key during start up?

If you want to try with Open Firmware, you should press O+F+Option+Command (Please, read the link I mentioned before).

---

### Post by motsteve on 2008-07-26
> **tiresia said:**
> Can you please specify:
1. which Ubuntu version are you trying to install
2. how have you burned the .iso image
3. your graphic card
4. your processor
5. RAM

What does it happen, when you press C in order to boot the installer?
Do you get anything?
And what does it happen, if you press the Option key during start up?

If you want to try with Open Firmware, you should press O+F+Option+Command (Please, read the link I mentioned before).

1. Intrepid Ubuntu. Also tried were Gentoo, Fedora, Debian.
2. I burned the .iso several different ways on several different media on three different drives on three different OS's using Brasero, Disk Utility, Simple Burn, InfraRecorder and Dragon burn.
3. The G4 mac contains an AGP Rage128 w 16M ram which came stock.
4. The G4 mac has a G4 processor running at 466 MHz
5. 640M ram.

It rejects any Linux disk using c key down after a short read.  It will show a boot icon for all bootable disks using option key down method, but will stop loading the disk shortly after starting up after the proceed arrow is pushed.

All CD's or DVD's which are meant to boot into MacOS will boot with the c key down or by the option key down method.

---

### Post by tiresia on 2008-07-26
Ubuntu Intrepid is the Unstable version. You should try Hardy.
Here is the link
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

Which version of Debian have you downloaded? Debian Etch is VERY stable.
You can install it and the upgrade to Lenny if you prefer.

Anyway first try to understand why you can't boot.
Did you buy the OpenSUSE-DVD?

---

### Post by stream303 on 2008-07-26
A couple of questions that may seem dumb, so don't hit the messenger. :)

Are you burning PPC specific images, and not Intel?

Did you burn OpenSuse yourself, or was it commercially produced or burned by someone else?

Have you tried burning the other distros at a lower speed to make sure that your drive can read it?

You can also try holding down the "Alt/Option" key instead of the C key.  Are you holding down the C key long enough to ensure booting?  With the disk in the drive, have you tried powering up first, and VERY quickly holding down the C key?

I wouldn't put too much stock in an Alpha of Ubuntu Intrepid.  How does the recent release go?

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by motsteve on 2008-07-26
> **stream303 said:**
> A couple of questions that may seem dumb, so don't hit the messenger. :)

Are you burning PPC specific images, and not Intel?

Did you burn OpenSuse yourself, or was it commercially produced or burned by someone else?

Have you tried burning the other distros at a lower speed to make sure that your drive can read it?

You can also try holding down the "Alt/Option" key instead of the C key.  Are you holding down the C key long enough to ensure booting?  With the disk in the drive, have you tried powering up first, and VERY quickly holding down the C key?

I wouldn't put too much stock in an Alpha of Ubuntu Intrepid.  How does the recent release go?




[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)


PPC all the way.

I burned the iso myself on two different drives.  OpenSuse always boots.  I also have the commercial version, but I'm sure it'll work also.  I also have commercial versions of Fedora and Debian and they won't boot.

I tried burning at 1X and it still didn't work on anything except openSuse, both 10.3 and 11.0

The c key down trick gets a short read on the drive and then the drive ejects the disk.  Option down gives me an icon for the Linux ROM disk, but after selecting it and pushing the proceed arrow and a short read, the select window comes back again with everything kind of cracked looking.  The refresh button does nothing at this point and the only thing to do is to hit the power or reboot buttons.

I've tried the c key down at several times after startup beep.

Apple OS disks both burned and commercial boot fine as well as the only linux distro that my Mac likes, OpenSuse, does also.  Do you think my Mac is partial to German software? :-) Anyway, Novell seems to have the magic touch with the G4 PPC Mac.

I have nothing against OpenSuse, it has its good points, but I'd like to try out some of the others also on my PPC.  All of them work great in vm's on my iMac and I flip from one to another all the time depending on the mood I'm in.  When I have no other option and have to use it, I drop into XP Pro, but it's all I can do to keep my lunch down while I'm using that thing. I feel like I should be wearing one of those beanies with the propeller on top when I'm using it. :-)

---

### Post by stream303 on 2008-07-26
Wow -that is truly bizarre!

I'm assuming the md5sums match.  Have you also tried CD-R, not CR-RW?  Any way to burn on a different machine?

I gotta' admit that desktop full of coasters must be frustrating. :)

---

### Post by cyberdork33 on 2008-07-26
I think we should clear up some terminology as well just to make sure.

Is your CD not booting, or is it just not getting to the point where you see a desktop. There is a big difference. If it "boots" then what is the last thing that you see before there is "nothing" do you see any text on the screen?

To boot into OF:
OPT+CMD+O+F on bootup.
This will bring you to a commandline interface. Then you can use the OF commands suggested.

---

### Post by motsteve on 2008-07-26
> **cyberdork33 said:**
> I think we should clear up some terminology as well just to make sure.

Is your CD not booting, or is it just not getting to the point where you see a desktop. There is a big difference. If it "boots" then what is the last thing that you see before there is "nothing" do you see any text on the screen?

To boot into OF:
OPT+CMD+O+F on bootup.
This will bring you to a commandline interface. Then you can use the OF commands suggested.

Using the c key approach, the cd is ejected after a short read of drive.  Using the option key down approach, the cd starts up, but then the system is returned to the selection window after a two or three second read on the drive.

I'll try the the start up in OF next.  Give some time, though, I'm doing some other things now unrelated to computers.  I'm assuming the sequence is to start up with the disk in the drive and to push all those buttons at beep up.  Then execute the commands.  I'll try this in about a half hour from now.

---

### Post by motsteve on 2008-07-26
Okay.  I started up the Mac from power down and with the cd in the drive I pushed down cmd+opt+O+F as quickly as I could get my fingers on them.  The screen finally came up white with the > prompt showing.  The opening header before the prompt came up was:
"Apple PowerMac3, 4 4.2.8f1 BootROM built on 10/11/01 at 14:12:47"

At the > prompt I entered "> boot cd:,\install\yaboot"

The drive did nothing and the response to the command afterwards was:  "can't OPEN: cd:,\install\yaboot"

I then went on a google search for open firmware commands thinking that I could at least get you a version number of OF.  It is open firmware 3, which from the web page is saying is the correct Open Firmware for macs G3 and on up.

I hope this info is helpful.  My Mac is now sitting with the CD in the drive and the OF prompt on the monitor if you have some commands that you would like me to try.

---

### Post by cyberdork33 on 2008-07-27
I don't have a lot of experience with PPC Macs, but from what little I do have, that sounds like your drive cannot read the disc for some reason... i.e. not the software on the disc's fault.

---

### Post by stream303 on 2008-07-27
Man, this is weird.  Well, that cd/dvd unit is 3rd-party right?  When you installed it, did you match the cabling/jumpers like the oem unit?  I'm assuming it is an internal replacment, and not an external firewire.

What complicates matters is that OpenSuse seems to be recognized.  Makes me wonder if there is something that they do that all the other distros don't do.

Normally with any hardware replacment, I do a pram and smu/pmu reset just to make sure I've got a clean slate, but it doesn't explain why OpenSuse works for you..

..head-scratcher for sure. :)

---

### Post by tiresia on 2008-07-27
> **motsteve said:**
> 

The drive did nothing and the response to the command afterwards was:  "can't OPEN: cd:,\install\yaboot"

I then went on a google search for open firmware commands thinking that I could at least get you a version number of OF.  It is open firmware 3, which from the web page is saying is the correct Open Firmware for macs G3 and on up.



If you can boot the OpenSUSE-CD, it means that your OpenFirmware is correctly configured, as well as your Drive is correctly working.

It seems that your G4 can't boot the bootloader. 
I can see just two reasons, why it can happen
1. The Installer-CD has not the correct FileSystem (i.e. ISO 9660)
2. The Ubuntu-Installer of Ubuntu Intrepid is not yet ready

Before starting trying OpenFirmare commands, I would have a try with Ubuntu Hardy!

You said, you used Apple Disk Utility to burn your CD. Is your computer running Mac OS X?

---

### Post by oswaldkelso on 2008-07-27
What I find interesting about this thread is the only distro I really had a hard time booting on ppc is suse? Every other existing ppc distro boots easily, it makes me wonder about what machines they test the disks or what setting are on your drives, master slave cs etc. Its just really strange we have the same problem reversed.

---

### Post by motsteve on 2008-07-27
> **cyberdork33 said:**
> I don't have a lot of experience with PPC Macs, but from what little I do have, that sounds like your drive cannot read the disc for some reason... i.e. not the software on the disc's fault.

I would agree if that were true all the time, but it reads CD/DVD's that will boot into MacOS and it will boot DVD's that use Yaboot to boot into openSuse Linux.  Thanks for responding though.

---

### Post by tiresia on 2008-07-27
> **oswaldkelso said:**
> What I find interesting about this thread is the only distro I really had a hard time booting on ppc is suse? Every other existing ppc distro boots easily, it makes me wonder about what machines they test the disks or what setting are on your drives, master slave cs etc. 

Just to confirm what you write. I installed on my PowerPC Computers (7500, G3, G4, G5 Dual) different distros (Fedora, OpenSuse, Gentoo, Debian and of course Ubuntu). Debian worked always!  
Anyway I don't think, we can compare stable distros with unstable ones, especially with PowerPC releases (he is trying to install Intrepid).

I downloaded Ubuntu Intrepid (daily release), just to see if I can boot on my PowerPC G5.
I can boot the Kernel, but it can't find the right module for the CD. This is an issue, that I often experienced with Debian Unstable (not now, I tried Lenny Installer and it works smoothly)

So, again, I suspect it has to do only with the unstable release

---

### Post by motsteve on 2008-07-27
Thanks for all the help.  I'll just go on and keep my openSuse installation.  I really don't have any legitimate reason not to use it.

Thanks again.


Steve

---

