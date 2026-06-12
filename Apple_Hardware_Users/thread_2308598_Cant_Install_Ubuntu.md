---
title: "Cant Install Ubuntu"
date: 2016-01-04
forum: Apple Hardware Users
---

### Post by Marcos_Albernaz_Bi on 2016-01-04
Hi,

Im trying for the 4th time right now to install ubuntu, but after the configuration it always stay in the decteting system files window.
im running the the live usb in a local hdd partition with nomodeset on, otherwise wouldnt work.
Using a MacBook Pro from 2008/2009

Really need help

Update: 45 mins, and still stuck in the same place,

---

### Post by Bucky Ball on 2016-01-04
*Thread moved to **Apple Hardware Users**.*

Welcome. You might have better luck here. As far as I know, and I went through this trying to help a Mac user install not long ago, you can create a Ubuntu USB installer to install on a PC with a Mac, you can 'Try Ubuntu' from the USB on a Mac, but you can't install Ubuntu using the USB on a Mac. You need to use a CD or DVD.

Hopefully a Mac user in the know can leap in and help you out. Otherwise, try a disk. Good luck. :)

---

### Post by Marcos_Albernaz_Bi on 2016-01-04
i cant use the dvd driver... not working 
i made a usb didnt work either... the only way i could use "the try linux" feature was copying the content of the usb stick into a hdd partition and making it boot from there, already made another partition to install it but still taking too much time detecting system files.

---

### Post by este.el.paz on 2016-01-04
@BuckyB:  Thanks again for actually posting something helpful . . . not just moving the thread to Apple User and calling it "done" . . . .

@OP:

I have an 09 MBPro . . . there are some details that need to be followed to get a good install . . . and I have created USB boot drives in my MBPro using LM, but I haven't tried an install with it . . . I do as BB suggests and use a DVD.

But, you aren't mentioning any details of your install, what version of "ubuntu" are you trying to boot??  What version of OSX do you have installed?  Apparently there is a "mac-friendly" spin out there, but I use "rEFInd" as the boot loader . . . search the web for "rodbooks" and try to get rEFInd set up.  I don't suggest using Bootcamp to set up your Partitions . . . just use DU to set up some part of the HD as either "FAT32" or possibly "free space" and try to run the install ***from disk*** using "automatic" "install alongside OSX" . . . then, after install . . . shut down the computer, don't just reboot . . . and **hopefully*** the rEFInd window will open . . . in my case linux shows up as the "penguin" icon . . . or also as "windows" . . . and then clicking on windows it goes to the GRUB window.  Takes a little time to get it booted up, but, once running it's OK.  Good luck.

e...

---

### Post by Marcos_Albernaz_Bi on 2016-01-04
As i said earlyer im using a hdd partition to run as a usb bootable drive that was the only way I managed to make it work
The Mac OS I'm using is el capitan and the Ubuntu version is 14.04.3 32mb
I tried again with these option:
Gpt toram nomodeset
And i managed to instal but when I as going to run the partition a message that wasn't possible to enter the OS appears
To make the bootable drive I'm using Mac Linux sub loader
Already installed refind but it stopped working for one moment to the other

Is it possible that the OS isn't working because I didn't install a boot partition?

---

### Post by este.el.paz on 2016-01-04
> **Marcos_Albernaz_Bi said:**
> As i said earlyer im using a hdd partition to run as a usb bootable drive that was the only way I managed to make it work
The Mac OS I'm using is el capitan and the Ubuntu version is 14.04.3 32mb
I tried again with these option:
Gpt toram nomodeset
And i managed to instal but when I as going to run the partition a message that wasn't possible to enter the OS appears
To make the bootable drive I'm using Mac Linux sub loader
Already installed refind but it stopped working for one moment to the other

OK, I did see that your DVD burner doesn't work on yr MBPro after I posted my post; mine doesn't work anymore either to burn, but, it can boot them.  A fellow on a forum found a external USB DVD burner for $20 online . . . whereas to buy the internal one is like $200 . . . .  Personally I haven't been able to get the debian installer to be able to do a proper install on a HDD . . . so, I don't know if that is where your problem is??

However, the PowerPCFAQ does have a section on "How to boot from an iso" . . . it has a name, but, I don't know what it is or how to do it.  I believe you have to have the iso in the computer . . .  it's something like "live iso boot" . . . you might try that and see if you run the install from there???  Search Google for "PowerPCFAQ" . . . even though your computer isn't PPC it might give you some hints.

PS: The MBPro can run the 64 bit selections . . . which would be "faster" in nature.

---

### Post by Marcos_Albernaz_Bi on 2016-01-04
I will give a look to powerpcfaq...
I know it can run the 64bit version but that one was the only I could run until now

---

### Post by kyle69 on 2016-01-04
The OP would have to be using a mactel if the laptop is from 2008/2009, so the ppcfaq would not apply here. I would really recommend replacing the internal dvd drive if it's not working, flea-bay should have something functional and cheap. I've tried the usb route before and it was painful and a waste of time. Also, some of the live desktop images on the install dvd's in particular are wonky on macs, however an easy workaround is to use use the alternate installer on a cd, that should boot fine. HTH-

-kyle

---

### Post by este.el.paz on 2016-01-04
> **este.el.paz said:**
> 

However, the PowerPCFAQ does have a section on "How to boot from an iso" . . . it has a name, but, I don't know what it is or how to do it.  I believe you have to have the iso in the computer . . .  it's something like "live iso boot" . . . you might try that and see if you run the install from there???  Search Google for "PowerPCFAQ" . . . *****even though your computer isn't PPC it might give you some hints.******

PS: The MBPro can run the 64 bit selections . . . which would be "faster" in nature.

> **kyle69 said:**
> The OP would have to be using a mactel if the laptop is from 2008/2009, so the ppcfaq would not apply here. I would really recommend replacing the internal dvd drive if it's not working, flea-bay should have something functional and cheap. I've tried the usb route before and it was painful and a waste of time. Also, some of the live desktop images on the install dvd's in particular are wonky on macs, however an easy workaround is to use use the alternate installer on a cd, that should boot fine. HTH-

-kyle

@kyle:  Had that one covered if you read my post, just trying to point the OP to a place where he could get some ideas . . . .  Possibly good thought on the external burner, but, according to my tech buddy, it isn't an ***easy*** replacement in the laptop . . . hence the ext USB idea . . . .  Could be cheaper to just buy an old Powermac with a working DVD Superdrive . . . but, that does bring up the point that perhaps the OPs optical drive might not burn DVDs, but the CD burner might still work . . . and then there would be the alternate installer or the mini options to choose from . . . and, burn . . . .

---

### Post by kyle69 on 2016-01-04
sorry @este, I missed your disclaimer about it not being ppc. It shouldn't be too hard to replace the drive though, the "thicker" laptops usually can be taken apart easily. I found this with a quickie search: [https://www.ifixit.com/Guide/MacBook+Pro+15-Inch+Unibody+Late+2008+and+Early+2009+Optical+Drive+Replacement/826](https://www.ifixit.com/Guide/MacBook+Pro+15-Inch+Unibody+Late+2008+and+Early+2009+Optical+Drive+Replacement/826)

@Marcos, can you tell us anything more about the superdrive in your macbook? Might be able to get the stock one going, which would be even easier.

---

### Post by Marcos_Albernaz_Bi on 2016-01-04
@Kyle69 mine is the one before that one... not unibody, a little more complicated, the superdrive doesn't read or write, the only thing it does is make a lot a noise and then eject the cd/ dvd

[https://www.ifixit.com/Guide/MacBook+Pro+15-Inch+Core+Duo+Model+A1150+Optical+Drive+Replacement/489](https://www.ifixit.com/Guide/MacBook+Pro+15-Inch+Core+Duo+Model+A1150+Optical+Drive+Replacement/489)

---

### Post by kyle69 on 2016-01-04
@marcos- if the link you provided represents your laptop, I would definitely get a replacement. You should be able to get one off of ebay for a very reasonable price. Then burn an alternate install cd, and off you go-

---

### Post by Bucky Ball on 2016-01-04
> **kyle69 said:**
> @marcos- if the link you provided represents your laptop, I would definitely get a replacement. You should be able to get one off of ebay for a very reasonable price. Then burn an alternate install cd, and off you go-

+1. I bought an external USB optical drive a few months ago for next to nothing.

---

### Post by Marcos_Albernaz_Bi on 2016-01-07
Hi again i get a externel drive and hot ir running but know im having the "The system is running in low graphics mode" messege and cant bypass this problem....
Already tryed to boot into single mode (emergency) and type 
Sudo apt-get install nvidia current to get the drivers but in emergency mode seems like not having any online connection and when I boot it naturally always show that message, if I chose to run console when the message shows it freezes

Edit: writing from iPhone sorry for mistakes

---

### Post by este.el.paz on 2016-01-07
> **Marcos_Albernaz_Bi said:**
> 
Is it possible that the OS isn't working because I didn't install a boot partition?
> Hi again i get a externel drive and hot ir running but know im having  the "The system is running in low graphics mode" messege and cant bypass  this problem....
Already tryed to boot into single mode (emergency) and type 
Sudo apt-get install nvidia current to get the drivers but in emergency  mode seems like not having any online connection and when I boot it  naturally always show that message, if I chose to run console when the  message shows it freezes


@Marcos:  So, I'm posting your question about the "boot partition" in an earlier post, as a way of asking about how you did "install" your system.  You mentioned before that you were "booting from an extHD and you were going to install to another partition in the HD"???  Is that what you did?  That may or may not matter, if you are able to boot the system and you are in the GUI when it says "low graphics mode" . . . you could try going to "additional Drivers" tab in "Software Services" or "Software Updater" . . . and, I may be wrong, but possibly a list of various "nvidia" drivers should be there, and one of them is often flagged as "recommended" . . . click on that one . . . and it should switch to show the driver being downloaded . . . probably need to reboot, and your graphics should be "nvidia" approved . . . .  In my MBPro I see a "Nvidia" splash window as the linux side boots up . . . a sign (to me) that the correct driver is installed.  Try it the "easy" way before you start trying to run cli commands . . . .

e...

---

### Post by Marcos_Albernaz_Bi on 2016-01-07
I installed from an external dvd drive, botting from a partition in the local(internal) hdd... When it shows the message I press ok 

[http://i.stack.imgur.com/AiwJH.png](http://i.stack.imgur.com/AiwJH.png)

Then I get this one

[http://i.imgur.com/QaP9d.png](http://i.imgur.com/QaP9d.png)

---

### Post by este.el.paz on 2016-01-07
OK, but did you try any of the options?  Trouble-shoot?  Reconfigure?  Or, run in low graphics and then try the "additional drivers" gambit??  Also looks like you are running this in VirtualBox??

---

### Post by Marcos_Albernaz_Bi on 2016-01-07
I found a way to go to console mode and installed the drivers but now doesn't show any message just a dark screen and a underscore blinking 
Not the easiest Ubuntu install.
Nop not running in virtual box running dual boot with refind

Update: if I press alt+ctrl+f2 I can go to console mode so the screen doesn't freeze just stays there and doesn't launch the gui... Maybe something blocking?

---

### Post by este.el.paz on 2016-01-07
The "dark screen with blinking underscore" is "good" . . . better than no blinking underscore--it probably means that the video drivers are not working or are wrong--or you need some boot parameters.  The ctrl+alt+f2 is the "TTY" . . . you can use that run commands, but I'm not exactly sure what the problem is.  I don't think I needed an Xorg.conf file for my MBPro, but, maybe that needs to be set for the right video driver???  Maybe someone else has some insights on that??

Possibly I would suggest trying Xubuntu 14.04 LTS . . . I had that set up on my MBPro and it went pretty easy, whereas the straight Ubuntu didn't . . . possibly too demanding on resources????  Try Xu or Lu and see how that goes . . . don't know if the USB DVD drive isn't "fast" enough to get all the data installed??  Or, try a "mini" or "alt" installer . . . not "live" . . . it's just a basic installer . . . and then you add your DE at the end-ish phase of the install.  Mini/alt can be burned to CD . . . need internet connection.

---

### Post by Marcos_Albernaz_Bi on 2016-01-07
Yes I think the problem should be the driver or wrong driver does this already happen to someone?

Personally I'm more interested in Ubuntu and I don't really think its too demanding for the mbpro (2008) since the minimum system requirements are lower... 

Ubuntu Desktop Edition
700 MHz processor (about Intel Celeron or better)
512 MiB RAM (system memory)
5 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)
VGA capable of 1024x768 screen resolution
Either a CD/DVD drive or a USB port for the installer media
Internet access is helpful

---

### Post by este.el.paz on 2016-01-08
> **Marcos_Albernaz_Bi said:**
> Yes I think the problem should be the driver or wrong driver does this already happen to someone?

Personally I'm more interested in Ubuntu and I don't really think its too demanding for the mbpro (2008) since the minimum system requirements are lower... 



Yes, this has happened many times in terms of getting video driver set up and/or recognized.  Well, whether you "like" Ubuntu better than another flavor of, um, Ubuntu . . . what "we" are trying to see is what installs and runs well on your computer . . . then, see whether you like having a system that works, rather than the theory of which one is "better" . . . .  Since a fresh install only takes 15 - 20 minutes from live DVD, it's often a time saver to try a fresh install . . . also making sure that the md5sum numbers match correctly . . . in other words the download is "validated" . . . .  So, trying a different "flavor" of ubuntu, or trying another package installer . . . mini . . . or alt . . . ****might*** make a difference.  The more installs you run the more you learn, etc.

Otherwise you might search google for how to set up xorg.conf file . . . or how to "nano" it and check to see that the video driver is correct, etc . . . .

e...

---

### Post by Marcos_Albernaz_Bi on 2016-01-08
Already tryed install ubuntu Lts 14 lts (live cd) appears same message installed the drivers via this page
[http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)
Same problem (blank screen after tty)

Installed xubuntu (mini cd) same problem...

---

### Post by este.el.paz on 2016-01-08
> **Marcos_Albernaz_Bi said:**
> Already tryed install ubuntu Lts 14 lts (live cd) appears same message installed the drivers via this page
[http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)
Same problem (blank screen after tty)

Installed xubuntu (mini cd) same problem...

@Marcos:

OK, it really shouldn't be too hard to install and run linux . . . in the int HD of the MBPro.  Couple questions?  Can you boot and run the Live DVD as the GUI, and you can set the time, and you can open applications ***from the Live DVD*** or USB Live for that matter???  In other words using your "nomodeset" boot params gets you into a clean and working GUI . . . but, when you go to install it . . . something gets messed up???  And you install is in the laptop or in an ext HD??

In your installed version, when you boot it up do you see the GRUB window??  Or no GRUB???  And, just for jazz, if you have installed the PPA do you see the NVidia splash window like they show in your linked page???  Also, for your rEFInd install in OSX, did you follow rodbooks instructions and install [from memory] "gdisk" as well???  

Lastly, when you finish your install process do you **shut down** the computer; or follow their instructions in the installer and "reboot" . . . ????  Shut down is better for rEFInd to do its thing.

Possibly there are a few "errors" in the install process, but, really there is no need to add a PPA to get NVidia drivers installed . . . read my post #15, I believe I described the GUI way to install the drivers . . . but, let's say on boot you see the Nvidia splash then it should be that the drivers are installed, but possibly the xorg.conf file might be showing something else . . . I think i mentioned that part before . . . .  Can't remember if I asked or you answered whether you checked the md5sum numbers?? sometimes if the file is "corrupt" you might be able to boot it, but the install will go sideways.

e...

---

### Post by Marcos_Albernaz_Bi on 2016-01-09
Hi e

Yes I can run a live cd from all the versions i tried (Ubuntu 15 /14 xubuntu 14) and I can use apps and everything normally the problem is after install and yes installed in the internal disk.
I have some news... I tried xubuntu via mini cd it worked but the screen was flashing changed the drivers but continued the same 
So I tried again xubuntu but via live cd it gave me problem in the first boot then I rebooted and goes directly to tty1 already tried to install nvidia drivers, everything stay the same 
Tried this: 
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
After installing the drivers, stay the same.
Tried to run startx gives me a error unable to connect x server: connection refused 

Getting desperate here 

About the other questions...
I never saw the nvidia logo most of the times stay a black screen with the underscore and if I start pressing keys it goes to tty1 and sometimes tty6
About refind I don't remember but I will install again without problem
Use shutdown
About the xorg.conf I don't know how to change it

---

### Post by este.el.paz on 2016-01-09
@Marcos:

Desperation isn't going to help you . . . it's not that this a really serious problem . . . right???  But, OK, good news, you can run the live DVD and everything is fine when you do that?  The graphics are fine and the system works more or less normally???  That would point to something in the install procedure where a problem is occurring . . . the question is . . . what or where??

I've asked a few times if the md5sum numbers on these iso files checks out . . . have you checked it, for each of your install iso's??

Then, how are you running your install??  Are you using "automatic" ???  Or you are using "manual"????  If you are using "manual" how are you setting up your partitions??  How are they formatted?  And flagged??  It's easiest to try to run it "automatic" into "largest free space" or "along side OSX"--I mentioned that before, is that how you are doing it???

Also, hopefully by now you understand that the TTY is another non-GUI way of accessing the Terminal/CLI . . . so you have to be clear on what you are doing in the TTY . . . best at the beginning to ***not*** be trying to add drivers until you know whether they are there already.  You could try to run "lsmod" from the TTY and see if "nvidia" shows up.  But, really, you should be able to run a simple automatic install and it should at least give you a somewhat working GUI . . . then use "additional drivers" to select your choice of driver . . . then . . . reboot and you should see the Nvidia splash in the boot sequence.

So, usually it is something that we are doing that complicates the install . . . or possibly the machine has "issues" and those mechanical issues are messing with the install . . . OR the md5sum numbers are not matching and somehow the iso is "corrupt."  A few years ago that wasn't so critical, lately if those numbers don't match the install gets messed up.

Also, for right now I don't want to waste your time by talking more about the Xorg.conf file . . . I'll have to check my MBPro install . . . later today or tomorrow . . . but, I don't recall having to set up an Xorg.conf file, or, having to use "nomodeset" to get the DVD to boot . . . I think I just used "live." ???

Enjoy the process . . . the "journey" is the reward . . . .

e....

---

### Post by Marcos_Albernaz_Bi on 2016-01-09
I HAVE NEWS!!!

Good News:
Running Xubuntu 14 right know installed via mini cd

Bad News:
Erased Mac OS boot Partition
No Recovery partition for Mac OS
Erased Refind
Machintosh hdd desapeared from the boot

Basically i can enter Xubuntu pressing command key or shift key, which goes to a black screen (GNU GRUB 2) similiar to this one : [http://www.howtogeek.com/wp-content/uploads/2014/09/640x480xgnu-grub2-boot-loader-menu.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.gh1Zn0zLtS.png](http://www.howtogeek.com/wp-content/uploads/2014/09/640x480xgnu-grub2-boot-loader-menu.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.gh1Zn0zLtS.png)

But with different options, but mainly to enter Xubuntu i have to chose recovery mode, and while in recovery mode choose to enter normal mode that will work otherwise not.

Right now installed gparted to see what i can do...
Trying to make a Mac OS bootable Dvd to recover Mac OS partition...

---

### Post by este.el.paz on 2016-01-09
@Marcos:

OK. that's great that you have a working install . . . so possibly you are able to do that again.  Probably in the install you picked "use whole disk"??? because if OSX isn't showing up in GRUB it has been ***deleted**** . . . ***probably*** nothing to recover . . . unless the GParted shows an apple HFS+ partition; in which case possibly "recovery" will work . . . .  So, if recovery is possible try it.

But, if it has been deleted, then . . . begin again . . . .  First!!!!!!! use the install disk from OSX to partition the HD into roughly two . . . one up front for OSX . . . and the other one formatted as "free space" or "FAT32" which you will use for your Xubuntu install.  Install OSX again. Install rEFInd/gdisk??  

Then try for the xubuntu install . . . using "automatic" . . . "install alongside OSX" . . . you have to indicate that you ***want OSX to remain*** . . . .  Try it again until you have OSX with rEFInd . . . which using option or rEFInd window will boot either system that you want to use.

e....

---

### Post by Marcos_Albernaz_Bi on 2016-01-09
lool its kind of funny but i think now i can understand what went wrong, and i think that the problem was because of the speed of the ext dvd, since doing the install via online went well.

Next step will be:
1-Install OS X Again in whole disk;
2-Install refind;
3-Make the partitions (+- 25 Gb for Xubuntu or Ubuntu + 2 Gb for swap) since i managed to use Xubuntu via GNU Grub2 bootloader is it a good idea to install a boot partition?
4-Via Live DVD format ubuntu partition via Gparted;
5-install ubuntu or Xubuntu via mini cd
I think thats my best choice.

I deleted the mac boot partition on purpose, because it wasnt booting very well (most of the times booted directly to some grub bypassing refind) and since i didn't know what was the problem, i just erased them and hope for the best... not the best ideia lol

This is what gparted looks like
[http://en.zimagez.com/zimage/screenshot-09-01-2016-203528.php](http://en.zimagez.com/zimage/screenshot-09-01-2016-203528.php)

my big doubt right know is knowing if i'm booting from /boot/efi or /boot?
this can make the difference in the next install

Enjoing the Journey ;)

---

### Post by este.el.paz on 2016-01-09
Yeah, you don't want to get rid of the apple boot partition . . . also, you can install OSX to whole disk, but, you can use disk utility in the OSX installer to format and partition your HD . . . rather than installing to whole drive . . . .  It's "better" to use DU to set up the "rough" partitions . . . one for OSX and the other for linux.

But, main reason for posting . . . I don't exactly like how you have two partitions formatted as "ext4" . . . for my installs I do have three partitions, but the small, possibly 10MB "boot" partition for GRUB is labeled as "bios_grub" . . . it doesn't have to be too big.  Then the "ext4" is flagged as "/" . . . and then the swap is 1-2x RAM . . . .  Some people set up a separate "home" folder . . . and that is so if you want to have a number of different linux "root" systems that all would use the same "home" . . . .  But, I prefer simple, so I just do the three.  If you don't label or provide the small "bios_grub" partition I found that the install would say "successful" but it wouldn't boot.

If that isn't clear, let me know and I'll drag out my MBPro and try to show you my GParted table . . . you are almost there.

---

### Post by este.el.paz on 2016-01-09
Took a screenshot of my GParted table . . . from my Linux Mint 17.2 install . . . looks like something has been tweaked because the line that is highlighted and says "unallocated" 9.74 MiB . . . was formatted or labeled as "bios_grub" . . . .  The bottom three lines are the linux lines.

---

### Post by Marcos_Albernaz_Bi on 2016-01-17
Hello,

Some news here.
Already reinstall everything, and made the process described earlier
> Next step will be:
1-Install OS X Again in whole disk;
2-Install refind;
3-Make the partitions (+- 25 Gb for Xubuntu or Ubuntu + 2 Gb for swap)  since i managed to use Xubuntu via GNU Grub2 bootloader is it a good  idea to install a boot partition?
4-Via Live DVD format ubuntu partition via Gparted;
5-install ubuntu or Xubuntu via mini cd
I think thats my best choice.

Also made the Bios_Grub partition.
I manage to install Ubuntu Xubuntu and Kubuntu, they worked but always with a flashing screen, tryied to change the driver to Nvidea 340 and 304 and no longer i have access to GUI, when i boot the OS goes to TTY and if i don't press anything goes to a black screen with the "_" Blinking

---

### Post by este.el.paz on 2016-01-17
Seems like we are back where we were . . .  before you see the blinking _ do you see the GRUB boot loader window??  Do you see the rEFInd window?  Or, it just goes to the blinking _????  After your install, did you shut down???  Or reboot???  If the installer says the "install was successful" try to shut down . . . wait for a couple of breaths . . . then cold boot . . . should go to GRUB or rEFInd window.  Or, try to boot using option key and see what shows up in the OSX boot loader . . . .

Also, try not to just add nvidia drivers via the TTY, until you are sure that they aren't loaded, from the TTY run "lsmod" and see if you see anything mentioning "nvidia" . . . .  Possibly you might have to play with boot params to get passed the black screen, but if you start adding drivers via TTY I think it's just making the waters muddy . . . .  If you add video drivers, try to do it from "additional drivers" . . . right??

e....

---

### Post by Marcos_Albernaz_Bi on 2016-01-17
i did shutdown after install, and then i went to refind select ubuntu partition and managed to boot normally, just with the flashing screen problem, then i selected the nvidia drivers in GUI from "additional drivers". After adding the drivers i no longer could boot to GUI, just TTY and then the Blinking _

In the OSX Bootloader just appears the recovery partition and Mac OS X Partition.

---

### Post by este.el.paz on 2016-01-17
> **Marcos_Albernaz_Bi said:**
> i did shutdown after install, and then i went to refind select ubuntu partition and managed to boot normally, just with the flashing screen problem, then i selected the nvidia drivers in GUI from "additional drivers". After adding the drivers i no longer could boot to GUI, just TTY and then the Blinking _ 

Is one of the drivers listed as "recommended"??  and did you pick that one???  And, you mentioned before you "installed ubuntu xubuntu and kubuntu"???  Is it just one??  which one?  I have had very few problems with Xubuntu on my various computers, but did have problems with Ubuntu & Kubuntu . . . harder time getting them to run glitch free . . . . The only thing I can think of is that something in the install process is not going through properly . . . I think I've asked about whether the md5sum number is correct . . . did you answer that question??  I've been posting on a number of similar threads lately . . . .

> In the OSX Bootloader just appears the recovery partition and Mac OS X Partition.

This is a bit "odd" . . . usually there will be a "penguin" or linux shows up listed as "windows" on my 09 MBPro . . . but, it shows as a system choice.  Also, did you follow the "rodbooks" instructions for rEFInd . . . I believe he mentions needing to install "gdisk""????  Did you see that and do that?  Or, it's not needed???  I believe (from distant memory) that I also installed "gdisk" to the OSX install as a part of the rEFInd install . . . might make a difference in linux showing up in OSX boot loader . . . .

e..

---

### Post by Marcos_Albernaz_Bi on 2016-01-18
> is one of the drivers listed as "recommended"??  and did you pick that one???

Yes, i use the recommended and after that reboot, then same problem blinking _

> And, you mentioned before you "installed ubuntu xubuntu and kubuntu"???   Is it just one??  which one?  I have had very few problems with  Xubuntu on my various computers, but did have problems with Ubuntu &  Kubuntu . . . harder time getting them to run glitch free

I tryed all three and same problem with all of them

> The only thing I can think of is that something in the install process  is not going through properly . . . I think I've asked about whether the  md5sum number is correct . . . did you answer that question??  I've  been posting on a number of similar threads lately . . . .


I don't know how to run the md5sum so no i didn't, but i'm using mini install cd so the install its via internet....

> This is a bit "odd" . . . usually there will be a "penguin" or linux  shows up listed as "windows" on my 09 MBPro . . . but, it shows as a  system choice.  Also, did you follow the "rodbooks" instructions for  rEFInd . . . I believe he mentions needing to install "gdisk""????  Did  you see that and do that?  Or, it's not needed???  I believe (from  distant memory) that I also installed "gdisk" to the OSX install as a  part of the rEFInd install . . . might make a difference in linux  showing up in OSX boot loader . . . .

It doesnt appear the linux partition, for  refind install i used this [http://www.rodsbooks.com/refind/sip.html](http://www.rodsbooks.com/refind/sip.html), gdisk not needed 

Steps:


[LIST=1]
[*][Download the rEFInd binary .zip file]("http://www.rodsbooks.com/refind/getting.html")  and unpack it. You can unpack it on your regular hard disk or on a USB  flash drive. Pay attention to where it's located, though; you'll need to  find it later. Pay attention to both the name of the volume and the *complete* path to the directory in which it's stored. (Your home directory is normally /Users/yourname, where yourname is your username. Your Desktop is normally /Users/yourname/Desktop.
[*]Reboot the computer.
[*]At the startup chime, hold down the Command+R key combination. The  computer should launch into the Recovery system. This is a very bare  system, with only a window providing a way to launch a handful of  utilities and a menu bar. You must use the latter.
[*]Select Utilities -> Terminal from the menu bar. A Terminal window should open.
[*]If you unpacked rEFInd on a USB flash drive, insert it and wait for its access light (if it has one) to stop blinking.
[*]Increase the size of the Terminal a bit. (This just makes its output more legible, since the next step produces long lines.)
[*]Type df -h in the Terminal. This produces  a list of partitions that are mounted. Locate the one on which you  unpacked the rEFInd files. It will normally be /Volumes/Somename, where Somename is the volume's name.
[*]In the Terminal, use cd to change to the directory where the rEFInd files you unpacked earlier are stored. For instance, on my MacBook, I would type cd /Volumes/Macintosh\ HD/Users/rodsmith/Destkop/refind-0.10.0. Note that if any element of this path includes a space, you must either enclose the *entire path* in quotes or precede the space with a backslash (\), as in this example's Macintosh\ HD volume name.
[*]Type ls to verify that refind-install is present in this directory.
[*]Type ./refind-install to run the installation script. It should run normally, as described on the [Installing rEFInd]("http://www.rodsbooks.com/refind/installing.html")  page. You can add options, if you like, as described on that page.  Alternatively, you can perform a manual installation, also as described  on that page.
[*]Reboot.
[/LIST]

---

### Post by este.el.paz on 2016-01-18
> **Marcos_Albernaz_Bi said:**
> Yes, i use the recommended and after that reboot, then same problem blinking _

I tryed all three and same problem with all of them

I don't know how to run the md5sum so no i didn't, but i'm using mini install cd so the install its via internet....

It doesnt appear the linux partition, for  refind install i used this [http://www.rodsbooks.com/refind/sip.html](http://www.rodsbooks.com/refind/sip.html), gdisk not needed 



@Marcos:

OK, back to the work week, so less time for a few days . . . so, before you install the nvidia drivers the screen is "low resolution" . . . but it works??  After you install, the screen goes black?  Is that on reboot?  Or, right after installing it goes black?  Possibly try to reboot after the nvidia install and see whether that fixes that problem???  Or, after doing the install, in the low res screen or in TTY try to run "sudo apt-get update" . . . and then when the prompt returns, run "sudo apt-get upgrade" . . . and see what shows up . . . and, try to upgrade the install . . . could be something in there will fix your problems . . . ????  Try it a few times over a few days . . . a lot of times the system "figures it out" and fixes itself . . . .

On the md5sum number, these days they must match . . . at the top of the download page is the list of the various checksum numbers, search google for "how to check md5sum in ubuntu" . . . .  Even on the mini it **could** make a difference if the md5sum numbers don't match . . . sometimes I've downloaded a 1GB+ file three times to get a match . . . .  If you use "zsync" it checks the number automatically.

And, then on 10.11 and rEFInd . . . that looks more complicated than it is for 10.9 . . . I don't have time to read through all of that SIP info . . . but, did you "disable SIP" as he points out???  Also, I was saying "gdisk" . . . but he was referring to "fdisk" . . . which might be what I was thinking of????  

Catch you later, good luck, try some stuff for a few days . . . or try some other distros to see if you can get to a clean running install . . . .

e...

---

### Post by Marcos_Albernaz_Bi on 2016-01-18
Good News

It's running great...
i made the update and then selected the most ancient driver (Nvidia-173), its running fine for now
Right Now running Xubuntu, and tryied that option which ended being a good solution, maybe when i get bored of Xubuntu i try to make the same using Ubuntu, to see if it works, or maybe someone can try and then see what it gets
Finnaly Solved :)
Thank you everyone

---

### Post by este.el.paz on 2016-01-18
Great news . . . good job . . . .  Right, go with what works on your machine . . . perhaps with a kernel upgrade it ***might*** be possible to try a newer nvidia driver . . . but, really, just stay with what works . . . .  Thanks for marking the thread as solved . . . .

e...

---

