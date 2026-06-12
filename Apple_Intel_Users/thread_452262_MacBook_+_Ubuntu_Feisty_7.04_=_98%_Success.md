---
title: "MacBook + Ubuntu Feisty 7.04 = 98% Success"
date: 2007-05-23
forum: Apple Intel Users
---

### Post by anujseth on 2007-05-23
So I got myself a Mac. Its simply brilliant, I mean its hard to look at the damn thing and not fall in love. The OS X operating system is another thing though. I mean its good but lacks a lot of serious functionality. Lets get this running then. Detailed below is a dual boot up configuration for the new Core 2 Duo MacBook White.

Hardware Specs -
2Ghz core 2 duo processor
4MB Cache
1 GB DDR2 RAM
80 GB HDD

The 2 operating systems in your machine after this install will be Mac OS X and Ubuntu Feisty 7.04. If you're look for a triple boot with another EVIL and USELESS OS in mind you'll need to read up somewhere else (or manage it based on whats here the basic setup is the same).

 -> [https://wiki.ubuntu.com/MacBookPro]("https://wiki.ubuntu.com/MacBookPro")

A few notes before we begin. I like to think of myself as a purist and would rather have only the Ubuntu Linux operating system on by itself. This however gave me a lot of trouble. For example, the Num Lock and Caps Lock keys would light when USB devices were plugged in etc.

-> [http://ubuntuforums.org/showthread.php?t=439541]("http://ubuntuforums.org/showthread.php?t=439541")

These problems do go away with the dual boot setting(don't ask why). Another thing is the fact that if you want the iSight camera running in Linux you need the Mac OS X partition since you will need to mount it(only once) and use the iSight Apple Firmware.

As the choice of version of Ubuntu, I normally prefer and use Kubuntu, but the MacBook's keyboard controls like volume and brightness work out of the box with Ubuntu and not Kubuntu. Actually in Kubuntu the volume buttons' work but not the brightness. Another thing is that Kubuntu does detect the the in built Bluetooth (which for some reason does not work). The Bluetooth is something you can easily install in Ubuntu later, so I went with it.

Lets go.

**Testing Screen Resolution**

You can try and run Ubuntu from the Live CD (to boot from the Live CD keep the 'option' button pressed when you power on, this gives you a menu, choose the Windows CD here, as another side note all linux things partitions etc. will be shown as Windows by the MacBook). This will however leave you with a bad taste because the display resolution is not set properly. There are 3 things you can do here.

1. Trust me when I say Ubuntu looks beautiful on the MacBook 13" wide screen once configured.

2. Decrease the resolution of Mac OS X to 1024x768 (in System Preferences), this will prove to you that even your beautiful Mac OS looks bad when not configured properly.

3. Set the correct display for the Live CD itself. Explained below, you must however be prepared to do this again when Ubuntu is installed.

You need an Ethernet connection (LAN cable) to do all this. The wireless is not detected out of the box, but the Gigabit Ethernet port is.

Setup a password for the default Live CD login account.

```
sudo passwd ubuntu
```

This opens a file in gedit, you need to remove the '#' from in front of 2 lines, to enable the needed repositories  (universe repositories, its looks like this -> deb http:// ,,,,,,  ... so basically remove the # from infront of all such lines).

```
sudo gedit /etc/apt/sources.list
```

Update your package lists.

```
sudo aptitude update
```

Install the correct resolution package.

```
sudo aptitude install 915resolution
```

At this point you need to restart 'gdm' to refresh your settings. Press Ctrl + Alt + Delete. You will be taken to a login screen.

Login with the user name ubuntu and the password that you setup before. Yeayyy! You should now see the Ubuntu Desktop with the correct settings. You can play around a bit, even enable the basic Desktop Effects (Compiz) in the System -> Preferences menu.

**Ready to Install**

Like what you see. Lets get down to the real thing then. You need to go back to the Mac OS X to get started. Before we begin I recommend you reinstall Mac OS X from the DVDs that came along. The reason I say this is because the default install takes almost 16GB, while if you customize it and remove all the crap(iDVD iPhoto printer drivers (keep them for your printer type) etc.) you can get it down to about 3 GB. Of course you can manually delete this if needed. I reinstalled it and named the Macintosh HD -> Anuj Seth. You can rename, repartition your HD from the Disk Utility in the menus above the installer window.

About*** Bootcamp and refit*** --> if you've been reading other places (which you should have been) you've probably seen things about getting Bootcamp, refit etc. If you just bought a ne MacBook (mines May 2007, with Mac OS X Tiger '10.4.8') you DONOT need this. Its already there, infact the option button you pressed earlier at boot up to get the Live CD running is Bootcamp (or something similar).

In Mac OS X open a Terminal window. You can find this in Applications -> Utilities.

Use 'diskutil' to partition the drive space. This step does NOT delete your existing data. However as with all partitioning operations you should back up since a lot can go wrong. In the terminal punch in the following.

```
diskutil list
```

This will show you the current HD configuration. Donot touch the EFI partition. It contains all the MacBook Hardware drivers etc. and you will be unable to install Mac OS X again if you delete it. Here is what mine showed.

[IMG]http://www.freewebs.com/anujseth/Snapshot%2D1.png[/IMG]

You can see 3 partitions. Actually its 2. The first one is a summary of your disk. The second (200 MB as compared to 80 MB in the earlier MacBooks) is the EFI partition. The partition we need to modify is the 3rd thing listed. Its identifier is important 'disk0s2' in this case.

```
sudo diskutil resizeVolume disk0s2 20G "Linux" anujlinux 54G
```

reference -> [http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Creating_a_Partition_Map]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Creating_a_Partition_Map")

This will re-partition your HD to create 20 GB space for Mac OS X and 54 GB for Ubuntu Linux. The actual space for Ubuntu is immaterial as we will delete this partition later to reclaim free space. The pictures below illustrate the process. The actual partitioning is done when you reboot your system. Your Mac OS X is now resident in a 20 GB partition.

[IMG]http://www.freewebs.com/anujseth/Snapshot%2D2.png[/IMG]

[IMG]http://www.freewebs.com/anujseth/Snapshot%2D3.png[/IMG]

After rebooting.

[IMG]http://www.freewebs.com/anujseth/Snapshot%2D4.png[/IMG]

**Installing Ubuntu**

[UPDATE - Before you do this please read the "More Things Work - Updates" section at the end of this post]

Restart and boot into the Live CD by pressing the Option key at startup. Ubuntu boots. Click the Install icon on the desktop. Follow simple instructions until you come to the Partitioning screen(Step 4). Select 'Manual' partitioning here. Check the box in front of the Linux partition you created (54GB) /dev/sda3 in my case. This is why I earlier said the size of the Linux partition is not important. When you delete this partition it gets merged with the free space which is what we will use to install Ubuntu. You need to create 2 partitions one to mount root '/' i.e. your linux file system and a swap space. Select the free space and create a 'New Partition'. Select this such that 1GB remains for the swap space (or less or more as you see fit, swap can be resized later). Select this partition (53 GB for me) to be 'ext3' formatted and give it a '/' mount point. Create another partition from the remaining free space and use it as swap. The pictures below demonstrate the process.

[IMG]http://www.freewebs.com/anujseth/Partitioning%2D2.png[/IMG]

[IMG]http://www.freewebs.com/anujseth/Partitioning%2D3.png[/IMG]

[IMG]http://www.freewebs.com/anujseth/Partitioning%2D4.png[/IMG]

[IMG]http://www.freewebs.com/anujseth/Partitioning%2D5.png[/IMG]

Now you're ready to install. This is basically the most difficult part for many, so the detailed write up and pictures. To get other things working after the install numerous excellent tutorials already exist. The links are below. You donot need to change the bootloader i.e. grub settings etc. the defaults work fine including where it is installed. Upon booting after installation completes, your machine will go to Mac OS X by default. To go to Ubuntu keep the 'option' button pressed when putting on power, you should see 2 Hard Disk icons, go to the one labelled Windows its actually your Linux install, grub takes over from here. The other option is ofcourse your Mac OS X install.

**Getting the resolution to 1280x800**

Follow the same steps as the Live CD procedure above, except this time there is no need for setting a password, once done you can re-login with your user account, which is what you are using.

**LCD Subpixel smoothing **

In the Menu Bar above System -> Preferences -> Font.
Select the radio button next to Subpixel Smoothing(LCDs).

**Microsoft True Type Fonts**

-> [http://ubuntuforums.org/showthread.php?t=208396]("http://ubuntuforums.org/showthread.php?t=208396")

A potential problem here is that you might not like this. To remove this simply type 
```

sudo aptitude remove msttcorefonts
```

```
cd /etc/fonts; sudo rm *.conf

```

**Installing WiFi**

-> [https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")
-> [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo")

There is a bug in these though. The damn thing shows only half signal intensity even when standing right next to an access point.

**Installing Bluetooth**

```
sudo aptitude install gnome-bluetooth
```

To turn of bluetooth -> System -> Administration -> Services. Uncheck the box in front of the Bluetooth Symbol.

-> [http://ubuntuforums.org/showthread.php?t=94713]("http://http://ubuntuforums.org/showthread.php?t=94713")
-> [http://live.gnome.org/GnomeBluetooth]("http://live.gnome.org/GnomeBluetooth")

You may also install the Kde Bluetooth applications if you prefer them from the Add/Remove Programs menu.

[B]Installing Restricted Formats
[/B]

To get your movies, mp3s etc working.

-> [https://help.ubuntu.com/community/RestrictedFormats]("http://https://help.ubuntu.com/community/RestrictedFormats")

**Installing Beryl**

Bling!!

-> [https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")

**Installing USB Ports **

The pure Ubuntu installed gave me major trouble with the USB ports. Caps and Num Lock keys would light up when devices were plugged in, turn of when removed. Moreover a USB mouse and a Seagate Porta Disk would not run together. There have been no such problems in the dual boot install.

**Installing the iSight camera **

The links to the source. The guy who wrote(or hacked together) the drivers. Use the links below these to do the actual install. These are for reading up more and troubleshooting.

-> [http://blogs.gnome.org/portal/rbultje]("http://blogs.gnome.org/portal/rbultje")
-> [http://ronald.bitfreak.net/isight.php]("http://ronald.bitfreak.net/isight.php")

Install using instructions on these pages. 

-> [https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")
-> [ http://ubuntuforums.org/showthread.php?t=225621]("http://ubuntuforums.org/showthread.php?t=225621")

The iSight camera works like a charm.

**Installing Sound**

Everything, including muting on headphones works by default. The volume is a little weak though, specially on the headphones and there is the occasional hissing noise in the far background. 

**Installing the Microphone**

->[ http://www.jasonparekh.com/?page_id=9]("http://www.jasonparekh.com/?page_id=9")
-> [http://ubuntuforums.org/showthread.php?t=198453]("http://ubuntuforums.org/showthread.php?t=198453")

I havent done this yet.

**Suspend**

Works out of the box with the white light pulsing and everything. However to get back after suspend you need to press the power button.

**Keyboard and Mouse**

Work, including USB, you may however need to set key preferences.

-> [http://www.dadeb.it/index.php/macbook-and-ubuntu-linux/]("http://www.dadeb.it/index.php/macbook-and-ubuntu-linux/")
-> [http://modular.math.washington.edu/macbook/]("http://modular.math.washington.edu/macbook/")

Right Click settings (Not tested) 

->[ http://felipe-alfaro.org/blog/2006/02/14/right-click-on-apples-powerbook-and-ubuntu-linux/]("http://felipe-alfaro.org/blog/2006/02/14/right-click-on-apples-powerbook-and-ubuntu-linux/")

Disabling the touch pad (Not tested, some people might want this option, especially if they find themselves for no apparent reasons in weird parts of documents while typing ... yeah its generally this thingy)

-> [http://ubuntu.wordpress.com/2006/09/20/disable-touchpad-temporarily-when-typing/]("http://ubuntu.wordpress.com/2006/09/20/disable-touchpad-temporarily-when-typing/")

**Fan and Battery**

Definitely work. I managed to boil the damn thing quite a few times already. The Fans dutifully kick in and at varied speeds too. Maybe there is an app like Mac OS X to control fan speed, I havent looked though.

This is also a problem. In my experience the Mac Book heats up a lot more in Ubuntu Linux as compared to Mac OS X especially when the WiFi is on. This is almost always as the MadWiFi drivers dont have a power on/off option. There is a C program which does this but I haven't tried it (and can't find the link now). Battery backup is definitely less when running Ubuntu.  

-> [http://ubuntuforums.org/showthread.php?t=434639]("http://ubuntuforums.org/showthread.php?t=434639")

There are also options available for cutting down battery usage. 

(Not Tested)
-> [http://www.dadeb.it/index.php/macbook-and-ubuntu-linux/]("http://www.dadeb.it/index.php/macbook-and-ubuntu-linux/")

**CD / DVD **

Keyboard Eject works. CDs / DVDs work. Not tried the burning though it should work by default though, these things are generally pretty standard.

**Not tested the Firewire and video out **
[UPDATE - Firewire works see 'seamyst's post below']

**Things that don't work **

Maybe I missed something and u'll help me out here. But like I said at the beginning of the post most problems like lighting up of num lock keys etc. on plugging in USB devices go away on dual boot, still some remain.


[UPDATE - This WORKS -- see the "More Things Work - Updates" section at the end of this post]
One thing I really miss is the green light on my Caps Lock and Num Lock keys. The keys work but the lights on them don't.

Another problem is the brightness defaults to full, which is extremely bright, on restarting. Though you can decrease it using the keyboard, doing this everytime is a pain. I did manage to find a setting in Preferences that keeps your preference across boots, I found this setting when I did a pure Ubuntu installation. Its gone now and I'm not even sure what is was. Some links tell you to change the setting in Mac OS X and it stays in Ubuntu, it doesnt for me. 

-> [http://modular.math.washington.edu/macbook/]("http://modular.math.washington.edu/macbook/")

Another untested hack,
-> [http://felipe-alfaro.org/blog/2006/09/11/basic-backlight-support-for-macbook-pro/]("http://felipe-alfaro.org/blog/2006/09/11/basic-backlight-support-for-macbook-pro/")

Things like Shift + Delete, Alt + F2 don't work and you will need to set keyboard shortcuts for them manually. You can find the necessary options in System -> Preferences. You can also do this on the command line. 

-> [ http://modular.math.washington.edu/macbook/]("http://modular.math.washington.edu/macbook/")

[B][U]More Things Work - Updates 
[/U][/B]
1. The little green lights on the Caps Lock and Num Lock key WORK. Please select English and then when prompted for keyboard type select "US - Macintosh" NOT the standard one during install. This is something I overlooked earlier and it works if you take care to select this simple option during install.

---

### Post by zAo on 2007-05-23
Great tutorial dude! Thanks!

Since I got a iMac with a Wifi card that doesn't work (Broadcom 4328 rev 01), I still use OSX.

---

### Post by LittleNate on 2007-05-23
Thorough job there it appears. I've tried so many times for a clean install on a MacBook Pro but failed with both BootCamp and Parallels (for the Evil Empire OS). It is driving me nuts. This is where I'm at:

BootCamp installed but inoperative. Fatal kernel disconnect and init asssassination attempt has stopped Ubuntu. It's still looking for a Cyrillic script! It also freaked because it couldn't find X11 at the install. 

I need to dump it and start again. From what you've written I need to dump BootCamp also. But can I do this  without a total re-install of OSX, and a dozen others licensed apps that go through the whole registration palava?

Can I just nix the partition(s) I have now for Ubuntu, or resize them and just attempt another install? Seems like BootCamp might be an issue. It won't operate because Ubuntu created the partitions, its documentation says.

I hope all this is worth it. I love using Linux and my son swears by Ubuntu but getting it on this machine is a real pain.:(

---

### Post by anujseth on 2007-05-23
@Little Nate

Ubuntu rocks no doubt about it ... another 5 years of work and it should be killer. Anyway, don't know much about the MacBook Pro ... these new ones have BootCamp pre - installed so no problem here. But yeah reading some of the tutorials it does seem like a lot of work getting it to run on the older ones.

---

### Post by Seamyst on 2007-05-23
Firewire does indeed work - I use it for my iPod.  Great tutorial, though!

---

### Post by ronocdh on 2007-05-23
> **LittleNate said:**
> Thorough job there it appears. I've tried so many times for a clean install on a MacBook Pro but failed with both BootCamp and Parallels (for the Evil Empire OS). It is driving me nuts. This is where I'm at:

BootCamp installed but inoperative. Fatal kernel disconnect and init asssassination attempt has stopped Ubuntu. It's still looking for a Cyrillic script! It also freaked because it couldn't find X11 at the install. 

I need to dump it and start again. From what you've written I need to dump BootCamp also. But can I do this  without a total re-install of OSX, and a dozen others licensed apps that go through the whole registration palava?

Can I just nix the partition(s) I have now for Ubuntu, or resize them and just attempt another install? Seems like BootCamp might be an issue. It won't operate because Ubuntu created the partitions, its documentation says.

I hope all this is worth it. I love using Linux and my son swears by Ubuntu but getting it on this machine is a real pain.:(
You don't absolutely have to use Boot Camp. Now, I think from your post that you are interested in dual booting and have given up on Parallels, yes? If this is the case, you can just reinstall Ubuntu on the existing partition for it. Yes, you will get an X failure on the MBPs, just see the link in my sig about that.

If you want to jerk around your partitions before installing Ubuntu again, try [iPartition]("http://www.versiontracker.com/dyn/moreinfo/macosx/23828"). It can nondestructively adjust HFS+ partitions. Good luck!

---

### Post by ronocdh on 2007-05-23
> **zAo said:**
> Great tutorial dude! Thanks!

Since I got a iMac with a Wifi card that doesn't work (Broadcom 4328 rev 01), I still use OSX.
Have you tried ndiswrapper with this card? I've seen many Broadcoms working with ndiswrapper, at least one or two of which I know were in iMacs.

*Edit:* I found [this link]("http://ubuntuforums.org/showthread.php?t=405990") regarding the 43xx Broadcoms. Sorry if you've seen it before. Hopefully we can get you in working order soon!

---

### Post by anujseth on 2007-05-23
@ronocdh

yeah those are good options i guess ... anyway can you tell me if your MacBook or whatever you have heats up a lot more on Ubuntu ... this is something thats of great concern and am looking at various fixes ... 15 mins into netbeans and java development with the WiFi on and its boiling ... 


ps: do you know a link that has pictures of a MacBook opened up ... would be nice to know what is causing the heat and work specifically on that end first.

---

### Post by ivesjd on 2007-05-23
For partitioning, you can download the live-cd and use gparted. The only thing is you can't move the partition. But resizeing the HFS+ does work. And its free!

---

### Post by anujseth on 2007-05-23
so is disk util ... anyway started a new thread for the heating thingy 


[http://ubuntuforums.org/showthread.php?t=452628]("http://ubuntuforums.org/showthread.php?t=452628")

---

### Post by ivesjd on 2007-05-23
Disk util has to unmount the disc to partition. And if your booted in OS X it cant, you could boot from your OS X install disc, and you could always just partition the drive during the install as well. I was just adding another option.

---

### Post by anujseth on 2007-05-23
:)

---

### Post by Darrena on 2007-05-24
Does the patch I posted here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/69709](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/69709)

Fix your problem with the signal strength issues?

---

### Post by anujseth on 2007-05-24
Yes thats the exact same thing ... but mine does go to 3/4 th in the signal bars occasionally. I can't test the patch I let out my frustration some time back --> /dev/sda3 formatted to HFS+ ... ****

---

### Post by anujseth on 2007-05-24
@Darrena 

re - installing ubuntu .... grrr ... can you tell me if there is a way to add an on/off thingy for the wireless card. I have a thread on this -> [http://ubuntuforums.org/showthread.php?t=452628]("http://ubuntuforums.org/showthread.php?t=452628")

I remember seeing a C program that can add such a capability to the madwifi thing ... but i cant find the link now.

ps: how ironic is it that i have robert love's kernel book open in front of me  ::D

---

### Post by Darrena on 2007-05-24
> **anujseth said:**
> @Darrena 

re - installing ubuntu .... grrr ... can you tell me if there is a way to add an on/off thingy for the wireless card. I have a thread on this -> [http://ubuntuforums.org/showthread.php?t=452628]("http://ubuntuforums.org/showthread.php?t=452628")

I remember seeing a C program that can add such a capability to the madwifi thing ... but i cant find the link now.

ps: how ironic is it that i have robert love's kernel book open in front of me  ::D

I think the mad-wifi tools package used to have a command line tool to determine radio status but that is all I remember.   What I think you want is rfkill which I think will be in the next kernel release.

---

### Post by Darrena on 2007-05-24
I put up some packages with the Madwifi fix included here:
[http://www.darrenalbers.com/networkmanager/](http://www.darrenalbers.com/networkmanager/)

This is a simple rebuild of the Ubuntu packages with the madwifi patch.  Please let me know if this helps since I am considering purchasing a macbook to replace my Inspiron 700m.  I tested this on my Mac Mini and it /seemed/ to help but it sits inside a hutch so it isn't a good test of wireless reception!  ;-)

---

### Post by anujseth on 2007-05-25
@Darrena

They work alright. The signal strength in my room which is about 40 feet away from the router goes to 73% as compared to 52%. The Mac OS thingy however shows full strength at the exact same spot. 

I installed each package individually ... both work ... but install with broken dependencies .... sudo aptitude install -f ... takes you back to the standard gnome manager.

Did you read the other heating post by the way, is it possible that the Wireless Card is causing all the heat. I've only just started reading up on the Kernel etc (I wasted my years on Java) so a patch from me is atleast 3 months away. Is there no way to add a Wifi card On/Off capability to the Linux wireless drivers. 

If you're buying the mac book go ahead, i mean its brilliant. But the heat is really an issue. This is however  a non issue if you plan to use OS X(which I doubt). But seriously mac book battery management (backup goes down to about 2.5 - 3 hrs as compared to almost 5)and heat is a major issue in Linux.

---

### Post by zAo on 2007-05-26
> **ronocdh said:**
> Have you tried ndiswrapper with this card? I've seen many Broadcoms working with ndiswrapper, at least one or two of which I know were in iMacs.

*Edit:* I found [this link]("http://ubuntuforums.org/showthread.php?t=405990") regarding the 43xx Broadcoms. Sorry if you've seen it before. Hopefully we can get you in working order soon!
Thanks, but the 4328 rev 01 cannot use ndiswrapper, nor can it use the bcm-43xx ](*,)](*,)](*,)](*,)](*,)

I hate this Microsoft world :evil:

---

### Post by Darrena on 2007-05-26
> **anujseth said:**
> @Darrena

They work alright. The signal strength in my room which is about 40 feet away from the router goes to 73% as compared to 52%. The Mac OS thingy however shows full strength at the exact same spot. 

I installed each package individually ... both work ... but install with broken dependencies .... sudo aptitude install -f ... takes you back to the standard gnome manager.

Did you read the other heating post by the way, is it possible that the Wireless Card is causing all the heat. I've only just started reading up on the Kernel etc (I wasted my years on Java) so a patch from me is atleast 3 months away. Is there no way to add a Wifi card On/Off capability to the Linux wireless drivers. 

If you're buying the mac book go ahead, i mean its brilliant. But the heat is really an issue. This is however  a non issue if you plan to use OS X(which I doubt). But seriously mac book battery management (backup goes down to about 2.5 - 3 hrs as compared to almost 5)and heat is a major issue in Linux.

Oops I should have put in the instructions to remove the old packages first.   I took a look at the macbook today and while I love the size I don't like that it has an Atheros card and the single mouse button  :(

---

### Post by AWerner32 on 2007-05-26
Is resizing the HFS+ partition with gparted non destructive?

---

### Post by ivesjd on 2007-05-27
Yes, just boot to the live-cd open gparted (or just use the gparted cd) and resize it.

---

### Post by excrabot on 2007-06-09
Hey, I've just started the how to you've described here. but i'm getting the following error message when i'm using the resize command in diskutil..

'Resizing encountered error No spce left on device ( 28 ) on disk0s2 Macintosh HD'

even though my command is as follows on a 148.7GB disk0s2 partition..

'sudo diskutil resizeVolume disk0s2 20G "Linux" Ubuntu 100G'

I'm looking forward to running ubuntu on this Macbook but this has me stumped.

---

### Post by ronocdh on 2007-06-09
> **excrabot said:**
> Hey, I've just started the how to you've described here. but i'm getting the following error message when i'm using the resize command in diskutil..

'Resizing encountered error No spce left on device ( 28 ) on disk0s2 Macintosh HD'

even though my command is as follows on a 148.7GB disk0s2 partition..

'sudo diskutil resizeVolume disk0s2 20G "Linux" Ubuntu 100G'

I'm looking forward to running ubuntu on this Macbook but this has me stumped.
This could be because although you've enough space on the drive to support the partitions you've used, not enough of it is free. In other words, you'd have to have less only about 10GB taken up in OS X, which is little more than a basic install. So you'd need over 100GB of "free space" on the drive.

If this isn't the case, then it sounds like you might have had other partitions, and OS X is reticent to move them. You might have to restore the drive to one big piece using Disk Utility (you might have to boot from the OS X installer disc to do this). Once that's done, and your drive is all together, try the terminal command again.

---

### Post by excrabot on 2007-06-10
Thanks ronocdh, used disk util from the OS X install cd and viewd the drive. This computer is fresh of the shelf and as i suspected the drive had no other partitions on it and had only 17G used.

so i rebooted off the hard drive again and i changed my resize command to ..

'sudo diskutil resizeVolume disk0s2 25G "Linux" Ubuntu 50G' 

given that i would be resizing the partition later during the install i figured making the ubuntu partition smaller and the original one a little larger might avoid running out of free space during the resizing.

I worked and i'm now half way through installing ubuntu fiesty. thanks for the help.

---

