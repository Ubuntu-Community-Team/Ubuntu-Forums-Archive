---
title: "Installing on a Mac Mini 2011"
date: 2011-07-23
forum: Apple Hardware Users
---

### Post by BDNiner on 2011-07-23
Has anyone attempt to install ubuntu on the brand new mac minis? I just setup a virtual machine in virtual box and the graphics hardware is not detected. I got an error message stating that the unity desktop will not load on my hardware and to check for graphics drivers. 

Since I have the AMD graphics card I was hoping that the Additional Drivers application would detect the card. But no luck so far.

---

### Post by maxpolk on 2011-07-23
If you are using rEFIt and dual-booting to Ubuntu (not a virtual machine setup), I found that:
1.  rEFIt required Parallels Desktop to be uninstalled.
2.  Booting to the Ubuntu 11.04 live CD AMD-64would get caught up with a video issues, forcing me to install Ubuntu using the alternate text mode AMD-64 installer.
3.  After installing Ubuntu, it still had video issues.  I could use the boot parameter nouveau.modeset=0, but that invalidated high screen resolutions.  Finally I found that by adding "blacklist=vga16fb" boot parameter, Ubuntu Unity loads and I got video working fine.  Make the boot parameter permanent by editing /etc/default/grub and editing the line to say:  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash blacklist=vga16fb", then run update-grub.
4.  The magicmouse acceleration was horrible, so edit /etc/modprobe.d/magicmouse.conf to say: "options hid_magicmouse scroll-speed=45 scroll-acceleration=1".

---

### Post by BDNiner on 2011-07-25
Thank you for the response. That is a lot of information to take in. I will attempt it this week and post my experience.

---

### Post by pindar on 2011-07-25
[This]("http://www.phoronix.com/scan.php?page=article&item=intel_snb_apple&num=3") may also be of interest...

---

### Post by BDNiner on 2011-07-25
Thank you for the information.

I don't have the Mac Mini with the Intel graphics card. I got the one with the AMD card, but I will wait a little before attempting to install linux and brick my device.

---

### Post by maxpolk on 2011-07-25
Oh, one more kernel parameter to avoid crashing at system stop/reboot is "reboot=p", also add to grub default as described above.

---

### Post by Drovakoy on 2011-08-15
Hi guys,
How's the performance on it?
I'm aware ubuntu and ATI graphics have a bit difficulty getting on.

I'm thinking of installing ubuntu on my own Mini. Got it for some experience in support OSX.

---

### Post by phuongdt3 on 2011-08-17
Thank you for the response.

---

### Post by Wizard Sleeve on 2011-10-11
Hi ive managed to get ubuntu 10.40 alternate amd64 installed through the menu system described above (on a 2011 mac mini with the i5 2.5 with the uprated graphics card) It still boots osx fine and I can get to Grub using rEFIt. I then press e on the top menu choice (Ubuntu, with Linux 2.6.38-8-generic) which then brings up this:

GNU GRUB version 1.99~rc1-13ubuntu3

Setprams...........
.........
.........
......... Loads of extra stuff I cant be bothered to type
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=0b63ce06-5bcc-4653-9487-72bc5bffe0de ro  \ quiet splash vt.handoff=7

Now ive tried all you suggested above adding a space after the final 7 blacklist=vga16fb reboot=p (and different combinations and orders) all tried and all failed. They do make the screen flicker slightly different.

I just get a totally white screen and that's it. Am I missing something else or doing something wrong.

Your help will be much appreciated because there doesn't seem from my search engine endeavors many people trying to do this.  

Lee

---

### Post by Wizard Sleeve on 2011-10-11
Ive just tried with nomodeset in the boot command and that just hangs in this big list of things sucsessfully and unsuccessfully installing.

Now ive just tried beta 2 of 11.10 with the alternative install

installs again but didn't detect my Ethernet during installation where as 10.04 did

Still same problems with the white screen and tried the things mentioned above, no joy.

---

### Post by Mjchopperboy on 2011-10-11
Is it legal to install ubuntu on a Mac?!? I thought they were all locked down real tight...

---

### Post by Wizard Sleeve on 2011-10-12
Probably not but im a gangsta.

---

### Post by Wizard Sleeve on 2011-10-12
Just to confirm this is a Mid 2011 mac mini with coer i5 running at 2.5ghz with AMD Radeon HD 6630M graphics processor[B]. 

[/B]I am outputting via HDMI (This might be the problem but I have no choice). 

I created a partition using bootcamp and installed rEFIt. Got the alternate install of both 11.04 and 11.10 Beta 2. Used the install to then delete the partition that boot camp created and used assisted partitioning, which created one large partition and one small. I chose Grub to boot from /sda and Im able to get in to grub. 

Tried the different methods listed above but they all end in a white screen except "nomodeset" which ends in a hang with this big list of items. I can post a screen shot if its of any help.

---

### Post by Wizard Sleeve on 2011-10-12
Hi this is where it hangs if the boot command "nomodeset" is used.

I Have now tried connecting via displayport/thunderbolt video terminal and that makes no difference at all to whats happening.

Im now trying to install the daily build of 11.10.

---

### Post by vesabios on 2011-10-15
ive been going through the same process. i have been working with the vanilla 11.04 x86 livecd. in order to get past the white screen i have had to use "noacpi nomodeset reboot=acpi"... i have been removing "vt.handoff=7" and leaving "splash quiet".... but i haven't exhaustively tested these to see what makes or breaks it.

the live cd comes up with the graphical installer just fine if i make those edits during boot from cd, but once installed, the machine wouldn't boot into x, startx complained about not having drivers for the chipset, so i ran "sudo apt-get install fglrx" from the shell and x came up straight away after a reboot!

immediately, the automatic 11.10 upgrade kicked in and somehow it borfed the windowmanager in a big way, i think because i was in the middle of another apt-get install and that really messed things up... i was able to fix it, sorta, but several things are broken now (additional drivers won't run now!?) i also have not yet been able to get fglrx or the open source drivers to work in dri mode with 3d acceleration, despite trying many things including downloading thr latest from ati and creating debs, trying a number of options in xorg.conf, etc. i was able to get very smooth performance in gnome and some opengl samples running, but nowhere near the speeds of the same apps runnng in osx, plus vertex and fragment shaders simply do not work at all...

i'm going to restart from scratch with 11.04 once more and if that doesn't work i'll try a clean install with 11.10.

---

### Post by vesabios on 2011-10-19
success, without too much headache:

1) I created a standard livecd of 11.10, booted off the disc, and chose "Install Ubuntu". i chose to install alongside OSX... i had resized the mac partition with disk utility in osx prior. once everything installed normally, i restarted the machine...

2)  for some reason the default video drivers don't play nice with the 6630M chip. so, when you reboot, you will get a white screen of death, unless you add "nomodeset" to the grub boot options.

3) afterwards, x will not be able to initialize a graphics context, so you will get a text-based console login. if you try to run startx you'll see errors about the kernel and ati chipset not being configured correctly, this is due to the nomodeset boot option i believe. the only thing i had to do at this point was run "sudo apt-get install fgrlx"... and then reboot.

4) you should now be able to boot into ubuntu --- with the vanilla, default grub config. 

5) i went into additional drivers and seleced ATI/AMD proprietary FGLRX graphics driver, and activated that. at the moment there is a bug which prevents you from installing the "post-release update" drivers, but there are reports that they have some problems with unity at the moment. 

i did run a few opengl apps i have been working with and they ran at very, very good framerates, comparable to the speeds i get in osx, but i haven't run any benchmarking tools to prove that.

---

### Post by gharris999 on 2011-10-23
I'm unable to get X to start on my Macmini5,2 with AMD Radeon HD 6630M graphics.  I was able to install 11.10 x64 using the ubuntu-11.10-alternate-amd64.iso.  

uname -a reports:

```
Linux mac-mini 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

I've attached my Xorg.0.log.

Any help would be appreciated.

Thanks.

---

### Post by wedof on 2011-11-15
> **gharris999 said:**
> I'm unable to get X to start on my Macmini5,2 with AMD Radeon HD 6630M graphics.  I was able to install 11.10 x64 using the ubuntu-11.10-alternate-amd64.iso.  

uname -a reports:

```
Linux mac-mini 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

I've attached my Xorg.0.log.

Any help would be appreciated.

Thanks.

I have exactly the same problem :(

---

### Post by ralf.messerer on 2011-11-29
Hi,
Try this:
Look at following link:[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
Use source ati-driver-installer-11-11-x86.x86_64.run
And then it should work.

But I have still problems with the sound. Maybe someone can help.

regards,

Ralf

---

### Post by BDNiner on 2011-11-29
Wow, I haven't been on the forums in a while but this looks promising. So what works and what doesn't besides installing the correct video drivers?

---

### Post by gharris999 on 2011-11-30
I'm sorry to say I never did get ubuntu 11.10 to work with my 2011 mac mini.  Fedora 16 x86_64 installed via netinst ended up working right out of the box, though.  I seemed to have no end of trouble with rEFIt so eventually, I ditched that.  I'm now triple booting this box: Lion, Windows 7 & Fedora 16, which is installed to a 2nd hard disk.  I'm using Windows' boot loader chaining to Easy BCD's NeoGrub.  Kind of a kludge, but at least I have my triple boot system working reliably now.  And by using gnome shell frippery, I've even been able to make peace with Gnome 3.  So...I'm a moderately happy camper who is only somewhat grumpy about just how much work this took.

---

### Post by ralf.messerer on 2011-11-30
Hi gharris999
Did you got the sound (ear jack) working with fedora 16?

---

### Post by gharris999 on 2011-11-30
> **ralf.messerer said:**
> Hi gharris999
Did you got the sound (ear jack) working with fedora 16?
No, not yet...nor have I gotten audio over hdmi working.  So, perhaps my saying that Fedora 16 "works out of the box" overstates things a bit.

---

### Post by AlbertP on 2011-12-02
In Virtualbox you do not need a graphics driver. It will only screw up the system.

You need a graphics driver on the host OS (Mac) and the VBOX Guest Additions on the guest OS (Linux).

---

### Post by gallagth on 2011-12-06
Hi all,

I'm trying to install 11.10 on my mac mini 2011 with AMD graphic chipset; using a SuperDrive. I've burnt an 11.10 alternate install AMD-64 cd. When I boot on it, I select language, then F6 to set nomodeset, then 'Install Ubuntu' but the install process just hangs there. I've also tried without 'nomodeset' but same result. Any ideas?

---

### Post by gharris999 on 2011-12-09
> **gallagth said:**
> Hi all,

I'm trying to install 11.10 on my mac mini 2011 with AMD graphic chipset; using a SuperDrive. I've burnt an 11.10 alternate install AMD-64 cd. When I boot on it, I select language, then F6 to set nomodeset, then 'Install Ubuntu' but the install process just hangs there. I've also tried without 'nomodeset' but same result. Any ideas?If you haven't already, you might try the 'mac' variant: [http://cdimage.ubuntu.com/releases/oneiric/release/ubuntu-11.10-alternate-amd64+mac.iso](http://cdimage.ubuntu.com/releases/oneiric/release/ubuntu-11.10-alternate-amd64+mac.iso)

---

### Post by fredc888 on 2011-12-10
Hi all.

Has anyone been able to get either 10.04 or 11.10 desktop to work on a MacMini 5,3 (i7 quad core server)?

I saw here someone did manage to get 11.10 server installed (though I couldn't get it to work past the installer boot screen)...


Any luck on desktop?

---

### Post by gharris999 on 2011-12-14
> **fredc888 said:**
> Hi all.

Has anyone been able to get either 10.04 or 11.10 desktop to work on a MacMini 5,3 (i7 quad core server)?

I saw here someone did manage to get 11.10 server installed (though I couldn't get it to work past the installer boot screen)...


Any luck on desktop?
That's pretty much the machine that I have (i7 quad, 8gig ram).  Mine has the AMD graphics, though.  Again, I eventually gave up on Ubuntu and moved to Fedora on that hardware.  I was able to boot the Fedora 16 x86_64 live desktop on a USB stick with no real problems (other than audio...see posts above).  That's a pretty painless way for you to kick the tires with this hardware.

---

### Post by cholesterol on 2011-12-16
thanks for the tips, thats really cool... :guitar: :lolflag: :popcorn:

---

### Post by BDNiner on 2011-12-16
I am going to try and install Fedora on a USB thumb drive and see if that works. I don't use HDMI so the standard audio jacks should hopefully work.

---

### Post by fredc888 on 2011-12-25
> **gharris999 said:**
> That's pretty much the machine that I have (i7 quad, 8gig ram).  Mine has the AMD graphics, though.  Again, I eventually gave up on Ubuntu and moved to Fedora on that hardware.  I was able to boot the Fedora 16 x86_64 live desktop on a USB stick with no real problems (other than audio...see posts above).  That's a pretty painless way for you to kick the tires with this hardware.


I'm confused. I don't think  there is a Quad Core i7 MacMini with AMD graphics.
There's a duo core i7 with AMD, and there's a Quad Core i7 with intel graphics (the macmini server, which is the one I'm having problems with)... 

I've tried 10.04,11.10 desktop and server versions and can't get past the initial installation screen. Someone apparently got server to work (I wasn't even able to do that), but I really need desktop anyway....

Someone got server to install here, but it didn't work for me either.

[http://askubuntu.com/questions/64609/installing-ubuntu-server-on-macmini-server-5-3](http://askubuntu.com/questions/64609/installing-ubuntu-server-on-macmini-server-5-3)

---

### Post by gharris999 on 2011-12-25
> **fredc888 said:**
> I'm confused. I don't think  there is a Quad Core i7 MacMini with AMD graphics.
There's a duo core i7 with AMD, and there's a Quad Core i7 with intel graphics (the macmini server, which is the one I'm having problems with)... 

I've tried 10.04,11.10 desktop and server versions and can't get past the initial installation screen. Someone apparently got server to work (I wasn't even able to do that), but I really need desktop anyway....

Someone got server to install here, but it didn't work for me either.

[http://askubuntu.com/questions/64609/installing-ubuntu-server-on-macmini-server-5-3](http://askubuntu.com/questions/64609/installing-ubuntu-server-on-macmini-server-5-3)
Eh...you're right.  Mine is dual core.  I was faked out by the fact that:

# cat /proc/cpuinfo | grep processor | wc -l

..returns '4'.

But my order from the apple store:

> 
Configuration

2.7GHz Dual-Core Intel Core i7
8GB 1333MHz DDR3 SDRAM- 2x4GB
750GB Serial ATA Drive @ 7200
User's Guide
Country Kit


---

### Post by dpny on 2011-12-25
> **gharris999 said:**
> Eh...you're right.  Mine is dual core.  I was faked out by the fact that:

# cat /proc/cpuinfo | grep processor | wc -l

..returns '4'.

That's because the machine is reporting both the physical and logical cores. The OS doesn't know the difference between the two.

---

### Post by fredc888 on 2011-12-27
> **gharris999 said:**
> Eh...you're right.  Mine is dual core.  I was faked out by the fact that:

# cat /proc/cpuinfo | grep processor | wc -l

..returns '4'.

But my order from the apple store:


Ok.  Just checking... Hmmm. I wish I had a solution to this. I really need to be able to have ubuntu for android o/s development/etc since I hate developing on PC and don't want to even bother doing this on OS/X....The purpose I got this machine was so I could triple boot like I use to with my older MacMini... But I guess I should have done some more detailed research beforehand. Might have to return it now.

I'll muck around with it some more and let folks know if I make any progress.

---

### Post by john.wheeler on 2012-01-03
I have installed 11.04 on my quad core Mac Mini Server. The audio and wi-fi don't work out of the box, but everything else looks OK. I had to install some patches to get the wi-fi working (see [http://www.ubuntubuzz.com/2011/10/macbook-pro-wireless-broadcom-bcm4331.html](http://www.ubuntubuzz.com/2011/10/macbook-pro-wireless-broadcom-bcm4331.html)).

 I did have a lot of hassle trying to run a MacOS/Ubuntu dual boot of the boot drive, so in the end I dedicated an entire drive to Linux and used the Master Boot partition scheme rather than GPT. I have Mac OS on the second drive and can boot into it by holding down the option key on startup.

I haven't tried upgrading to 11.10 yet. I tried this upgrade from another machine, and it didn't go smoothly, so I'm not ready to experiment with the Mac Mini just yet. I may make a full backup and attempt it when I have lots of spare time to fix it, if it goes wrong!

---

### Post by fredc888 on 2012-01-06
Ok folks, after spending countless days/weeks on creating different flavors of ubuntu install CD's for both ubuntu 10 desktop, ubuntu 11 desktop, ubuntu 10 server, ubuntu 11 server, and then trying to create a bootable USB drive of each of those flavors, and having no luck booting any of the above.. I have finally figured out why....

Ready?

These new Mac Mini's are really finicky and probably won't boot from just about a lot of the external CD/DVD drive that isn't the one made by Apple (the overpriced external superdrive)... At least that was my experience....I tried using multiple external USB CD/DVD drives with the mac mini, and while it appeared to boot ubuntu CD's, the boot would hang 10 secs into loading. I tried booting a Windows Vista install CD and it hung 10 secs into the boot process too. Then I finally tried a Win 7 install disk too, and it too hung for 10 secs....So just for kicks, I went to the apple store, bought myself a superdrive (Really apple, $80 for a plain old DVD/CD drive???) Boot problem solved....

I was able to install Ubuntu 10.10 from the Mac/Alternative image (and for that matter also install Vista and triple boot between OSX Lion Server, Vista 64 bit, and Ubuntu 64 bit...)

Sorry folks. I really thought this was a software problem for me. But it turns out it was purely a dumb hardware issue....

Since I was able to get 10.10 to load, I don't think ubuntu 11 is going to be a problem. 

... My networking is not working (both NIC and wireless), bluetooth obviously isn't working, and my display is running at the worst resolution, and no sound...I haven't worked had time to work out the driver issues yet. But I'll work out through them and post an update.

I can't wait to start building android o/s on the quad core i7... Currently, it's taking me about 2 hrs on a slow PC....

To summarize my MacMini's hardware:

Mac Mini Server (Mid 2011) MC936LL/A
  Quad Core i7 2.0 GHZ
  4GB DDR3
  Dual 500GB HD
  Intel HD Graphics 3000
  Osx Lion Server with boot camp 4.0.1

+One overpriced Apple Macbook Air superdrive MC584ZM/A


For what it's worth. I am currently able to triple boot OSX, Vista and Ubuntu from the boot drive. Here's what I did.
NOTE: I am not an expert at this at all. So please excuse me if things aren't exactly clear. My purpose was to get up and running as fast as I could, not try to understand the intricate details of MBR, GPT, how EFI works,etc... So if there is any inaccuracies, please let me know and I'll correct them...


1. From OSX, i used the disk utility to create the following partitions 4 and 5 below (ones marked * were created by Mac and was related to the EFI/GPT configuration)

Partition 1*: Boot (I didn't create this: contains EFI/Boot etc)
Partition 2*: Mac OSX (I didn't create this, but I resized this down)
Partition 3*: Mac Recovery  (I didn't create this. It's used for recovery)
Partition 4: Windows (Created and formatted to Fat...Doesn't matter. You will reformat)
Partition 5: Ubuntu (Created and formatted to Fat...Doesn't matter. You will reformat)

2. I then installed RefIt.

3. After confirming RefIt worked, I installed Windows Vista first by booting into that Vista install disk from RefIt.

To simplify things, I put the windows partition on Partition 4 of the drive. The Vista installer apparently things the disk uses MBR and doesn't seem to recognize GPT partitions and/or can't install into GPT partitions. Since there is a maximum of 4 primary partitions using MBR, and since the installer already things there are 3 previous ones, that's why you need to create the Windows as #4... The alternative is I could have just used my second drive in my MacMini, but I'm going to use that for something else. 
The installer reformats the partition into NTFS.

Vista installer completes without really any issues. From RefIt, I can boot into Vista.

4. After confirming Vista installed correctly, I used RefIt to boot into the Ubuntu 10.10 alternative/mac desktop image
I deleted the Ubuntu partition and recreated it as ext4 I also created a small swap partition.
I also had Grub installed in the MBR of the drive, NOT in the Ubuntu partition. I wasn't able to get refit to boot Ubuntu if Grub was installed on the Ubuntu partition. I was only able to get things to work if Grub was installed in the disk's MBR... 

However, I have one minor issue.... When  I select to boot into either Windows or Ubuntu from RefIt,  it will bring up the Grub boot menu in both cases... and from Grub, I need to again select whether to boot into Windows or Ubuntu... It's mainly just annoying than anything else... If someone knows how to get Grub to work by not putting it into the MBR, that would be great... But otherwise, I'm just satisfied with something "working", albeit a bit clunky..

-Fred

---

### Post by BDNiner on 2012-01-17
Wow that is crazy that you have to use "apple" hardware to boot. I am going to order one anyways. Since I feel it will be a good piece of hardware to have just incase USB boot gives me problems.

---

### Post by QaysHP on 2012-02-26
I had a much easier time installing 11.10 on my "Mac mini Server mid 2011" but am unable to get wifi or sound to work. I was wondering if you had these issues, and how you might get around them.

---

### Post by CelticWebSolutions on 2012-02-27
Hi everyone,

Just received my mac mini server on Friday and want to get it dual booting Ubuntu (or possibly triple boot with Windows 7 too).  Could somebody let me know what version everyone is using to get it to install please?  Whatever I try seems to just not boot any futher than the first install menu :(

It would be much appreciated if somebody could link me to the downloads you are using.

Thanks in advance

Celtic.

---

### Post by QaysHP on 2012-02-27
I created a bootable USB drive with 11.10 Desktop 64-bit and used that. I followed the USB boot instructions from the Ubuntu download page ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) scroll to part 2, select USB and Mac).
I was able to boot and install with no tricks, however as I wasn't concerned with keeping Mac OS at the time, I dedicated both disks to the install. If you are, you may need to be a little more careful with the options you select.

You could also try 64-bit 11.10+mac from [http://cdimage.ubuntu.com/releases/11.10/release/](http://cdimage.ubuntu.com/releases/11.10/release/)

edit: full instructions here [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by CelticWebSolutions on 2012-02-28
> **QaysHP said:**
> I created a bootable USB drive with 11.10 Desktop 64-bit and used that. I followed the USB boot instructions from the Ubuntu download page ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) scroll to part 2, select USB and Mac).
I was able to boot and install with no tricks, however as I wasn't concerned with keeping Mac OS at the time, I dedicated both disks to the install. If you are, you may need to be a little more careful with the options you select.

You could also try 64-bit 11.10+mac from [http://cdimage.ubuntu.com/releases/11.10/release/](http://cdimage.ubuntu.com/releases/11.10/release/)

edit: full instructions here [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)


Thank you!  I had tried about 5 or 6 different versions and not got any of them to install on my 2011 Mac mini server.  I thought it was just never going to work, USB version installed and runs fine :)

Only thing I don't get is the boot menu, I have to hold alt and select the windows disk for that to work, I can't get it to default to loading Ubunutu (2nd partition boot now)

Other than that it all seems perfect so far.

Thanks again :)

---

### Post by QaysHP on 2012-02-28
> **CelticWebSolutions said:**
> Only thing I don't get is the boot menu, I have to hold alt and select the windows disk for that to work, I can't get it to default to loading Ubunutu (2nd partition boot now)
Boot to your Mac OS side and download rEFIt, install it from the dmg, then reboot (holding alt/option), chose rEFIt, and then fix partitions. Go from there :)

Does your sound/wifi work?

---

### Post by CelticWebSolutions on 2012-02-28
I tried installing refit before getting ubunutu to work.  Nothing happened.  

Sound and wifi do not work but that's fine for me as It's hard wired anyway and I'm not really interested in the sound side of things :)

---

### Post by QaysHP on 2012-02-28
> **CelticWebSolutions said:**
> I tried installing refit before getting ubunutu to work.  Nothing happened.
Did you boot into rEFIt and sync partitions? You may need to hold alt to get the boot screen where you may select rEFIt. There are lots of other posts and instructions if you look.

---

