---
title: "Ubuntu (with Boot Camp) on a Mac mini"
date: 2007-11-16
forum: Apple Intel Users
---

### Post by Rudy A Winchester on 2007-11-16
I am considering purchasing a Mac mini to run as a file server.  I wanted something small, ascetically pleasing, quite, and reasonably priced.  So, despite my dislike for Mac computers (won't get into that here), I have decided that the Mac mini may be what I'm looking for.

So, here's the thing.  While I'm not a fan of Mac OS X by any means, if I'm buying a computer that must come with it, I'd like to be able to use it.  But, at the same time, I want to run Ubuntu for the file server part.  So Boot Camp is my answer.  Though I've been seeing a lot of different things about how to dual-boot an Intel Mac; and most of the things I do see are for the MacBooks or MacBook Pros.  I need a complete guide to get a Mac mini running OS X 10.5 and Ubuntu 7.10.

The reason I am posting here is that most stuff I read is outdated and (like I said before) specifically for MacBooks or MacBook Pros.  So any help about Mac minis in particular would be awesome.

Thanks in advanced.

---

### Post by cyberdork33 on 2007-11-17
> **Rudy A Winchester said:**
> I am considering purchasing a Mac mini to run as a file server.  I wanted something small, ascetically pleasing, quite, and reasonably priced.  So, despite my dislike for Mac computers (won't get into that here), I have decided that the Mac mini may be what I'm looking for.

So, here's the thing.  While I'm not a fan of Mac OS X by any means, if I'm buying a computer that must come with it, I'd like to be able to use it.  But, at the same time, I want to run Ubuntu for the file server part.  So Boot Camp is my answer.  Though I've been seeing a lot of different things about how to dual-boot an Intel Mac; and most of the things I do see are for the MacBooks or MacBook Pros.  I need a complete guide to get a Mac mini running OS X 10.5 and Ubuntu 7.10.

The reason I am posting here is that most stuff I read is outdated and (like I said before) specifically for MacBooks or MacBook Pros.  So any help about Mac minis in particular would be awesome.

Thanks in advanced.

Well, there is really not much of a difference between a Mac Mini and a Macbook as far as the hardware. Just use bootcamp to make another partition on the disk. Then boot up the Ubuntu install CD, open the partition editor and delete the windows partition that Bootcamp made (leaving unused space). Start the Ubuntu Installer, and tell it to use the free space. That's it! You will probably want to install rEFIt (in OSX) as well.

You will run into issues using the Mac Mini headless as a server if that is what you plan to do since things don't start up properly without a display connected.

You can search mini in this forum and pretty much find all the mini specific questions... although there are not many posts.

Also, if you really just want the form factor of the Mac Mini, and don't care for the Mac itself, there are other options available:
[http://system76.com/product_info.php?cPath=27&products_id=53](http://system76.com/product_info.php?cPath=27&products_id=53)
There are others too.
If you plan to just use Linux, save yourself the Mac hardware headaches and just get something you know is compatible.

---

### Post by Rudy A Winchester on 2007-11-17
> **cyberdork33 said:**
> Well, there is really not much of a difference between a Mac Mini and a Macbook as far as the hardware. Just use bootcamp to make another partition on the disk. Then boot up the Ubuntu install CD, open the partition editor and delete the windows partition that Bootcamp made (leaving unused space). Start the Ubuntu Installer, and tell it to use the free space. That's it! You will probably want to install rEFIt (in OSX) as well.

You will run into issues using the Mac Mini headless as a server if that is what you plan to do since things don't start up properly without a display connected.

You can search mini in this forum and pretty much find all the mini specific questions... although there are not many posts.

Also, if you really just want the form factor of the Mac Mini, and don't care for the Mac itself, there are other options available:
[http://system76.com/product_info.php?cPath=27&products_id=53](http://system76.com/product_info.php?cPath=27&products_id=53)
There are others too.
If you plan to just use Linux, save yourself the Mac hardware headaches and just get something you know is compatible.

While I know there are other options to have a small server such as the Mac mini, the price is hard to beat right now (that sounds like a ridiculous oxymoron; not being able to be a Mac's price).  For instance, the Koala Mini that you posted is the same amount for $599.  But the specs are nowhere close.  To get that Koala Mini with the same specs, it comes to just above $1,000.  I don't think it's worth $400 to avoid the driver installs.  :P  Hence my choice with the Mac mini.  If you know of another computer setup similar to the Koala Mini that can compete with the Mac mini's price, the please post it here.  But from my searching, I didn't find much.  Right now, Mac's prices for their computers seem to be extremely reasonable: the first time that I remember.  For instance, a Dell equivalent to the $1,099 MacBook comes to about thirty dollars more.  So it seems like the only way to beat their price, at the moment, is to build your own computer.  Which is something I don't think is overly reasonable while trying to get it into that small form factor, yet under $599.

With the Mac mini, I will definitely boot up the server with a monitor connected (will probably have a switch for the same monitor as my desktop, so I can just toggle back-and-forth between them).  So that part I'm not worried with (though I'm very confused as to why it needs a monitor to boot up).  I just need to be able to boot it into Ubuntu without any major problems.  Wireless I don't need working, as I will have this working via wire (though I would like it to work, if possible).  But things like full stability, full keyboard/mouse support, full display support, and all of that good stuff are quite essential.  I need to be able to run a file server without having to smack the thing everything I want to do something.  So if there are any major problems that are still unsolved with the Intel Mac mini and Ubuntu, I may have to either wait for the server, or consider using a standard case instead.

On a side note: does Ubuntu plan to add better support for Intel Mac in the near future: possibly with the release of 8.04?  Or, on the other hand, does Apple plan to add support for Linux with Boot Camp anytime soon?  I just find it strange that they don't seem to care about allowing Linux users to easily and effectively install Linux distributions on their new hardware.  From what I understand, PPC Macs were used a lot by Linux users to run Linux.  So why not try and capture that base when moving to the Intel chips?  Just doesn't make sense to me.  Maybe we'll see better support for Linux, Solaris, et cetera somewhere down the road.

Again, the reason I am asking on this forum right not and not necessarily looking at past posts, blogs, howtos, et cetera, is because the information seems to get outdated rather quickly.  Looking at various MacBook howtos (since they seem to be everywhere), I can see a good difference about how things are done, and there is a strong correlation to the instructions and when they were posted.  And with the recent release of Boot Camp 2.0, I assume that several things have changed.  So I am just trying to get the latest information on Intel Mac minis and Ubuntu.  It doesn’t seem overly hard to get working, but it is not a simple install to get everything working correctly.

---

### Post by ThunderMoon1994 on 2007-11-17
As someone who used the Boot Camp beta and now uses Boot Camp on Leopard (MacBook Pro), I can assure you that nothing (unfortunately) has changed between them.  Many of us were hoping for the ability to pause one OS and then quickly boot into the other and then back again without having to wait for the system to completely reboot.  Another thing that was rumored was the ability to use Boot Camp assistant to change the size of the Boot Camp partition after it was created.

Using software, such as Boot Camp, is exactly the same on ANY computer running Mac OS X.

~Damien

---

### Post by cyberdork33 on 2007-11-17
> **Rudy A Winchester said:**
> While I know there are other options to have a small server such as the Mac mini, the price is hard to beat right now (that sounds like a ridiculous oxymoron; not being able to be a Mac's price).  For instance, the Koala Mini that you posted is the same amount for $599.  But the specs are nowhere close.  To get that Koala Mini with the same specs, it comes to just above $1,000.  I don't think it's worth $400 to avoid the driver installs.  :P  Hence my choice with the Mac mini.  If you know of another computer setup similar to the Koala Mini that can compete with the Mac mini's price, the please post it here.  But from my searching, I didn't find much.  Right now, Mac's prices for their computers seem to be extremely reasonable: the first time that I remember.  For instance, a Dell equivalent to the $1,099 MacBook comes to about thirty dollars more.  So it seems like the only way to beat their price, at the moment, is to build your own computer.  Which is something I don't think is overly reasonable while trying to get it into that small form factor, yet under $599.

touche

> With the Mac mini, I will definitely boot up the server with a monitor connected (will probably have a switch for the same monitor as my desktop, so I can just toggle back-and-forth between them).  So that part I'm not worried with (though I'm very confused as to why it needs a monitor to boot up).  I just need to be able to boot it into Ubuntu without any major problems.  Wireless I don't need working, as I will have this working via wire (though I would like it to work, if possible).  But things like full stability, full keyboard/mouse support, full display support, and all of that good stuff are quite essential.  I need to be able to run a file server without having to smack the thing everything I want to do something.  So if there are any major problems that are still unsolved with the Intel Mac mini and Ubuntu, I may have to either wait for the server, or consider using a standard case instead.I think that Ubuntu will run fine on a Mac Mini, it is just the Apple proprietary things that cause odd problems sometimes (like the non-attached monitor). I am not sure why the monitor has to be hooked up, but there are a few posts here about the problem and they even sell special loopback connectors to put on them so that you CAN run headless. Strange, I know, but none-the-less something you may have to face.

> On a side note: does Ubuntu plan to add better support for Intel Mac in the near future: possibly with the release of 8.04?  Or, on the other hand, does Apple plan to add support for Linux with Boot Camp anytime soon?  I just find it strange that they don't seem to care about allowing Linux users to easily and effectively install Linux distributions on their new hardware.  From what I understand, PPC Macs were used a lot by Linux users to run Linux.  So why not try and capture that base when moving to the Intel chips?  Just doesn't make sense to me.  Maybe we'll see better support for Linux, Solaris, et cetera somewhere down the road.I am pretty sure it fully supports it now, it is the Apple oddities that are an issue. I can't see Apple modifying Bootcamp to help linux users out. Not anytime soon anyway. It is really an unneeded tool anyway. You just need to partition the drive. I will give more details below.

> Again, the reason I am asking on this forum right not and not necessarily looking at past posts, blogs, howtos, et cetera, is because the information seems to get outdated rather quickly.  Looking at various MacBook howtos (since they seem to be everywhere), I can see a good difference about how things are done, and there is a strong correlation to the instructions and when they were posted.  And with the recent release of Boot Camp 2.0, I assume that several things have changed.  So I am just trying to get the latest information on Intel Mac minis and Ubuntu.  It doesn&#8217;t seem overly hard to get working, but it is not a simple install to get everything working correctly.Bootcamp is pretty much exactly the same on Leopard. The wiki pages for the Intel Mac hardware is pretty up to date as far as I can tell. (Actually, it doesn't cover the newest Macbooks well, but they just came out, and they have very different hardware).

Here is my suggested procedure, but some depends on some choices that you have to make. Firstly, Bootcamp is limited in the size of the Windows partition it can make, so I would just forget about using that since you will likely what a much larger Ubuntu partition.

The decision is, _Do you want to keep OSX on the main hard drive?_ If it something that you just want to play with, and maybe have around for firmware updates (it will be required for that), then you might just wipe the entire hard drive installing Ubuntu normally and install OSX to an external harddrive that you can boot up when you want.

** Ok, well assuming you want to dual-boot on the mini here we go:**

1. Leopard has a nice new feature in the Disk Utility that allows you to 'add' a partition without reformatting the entire partition table (a capability that Bootcamp already uses). So if you do not want to just do a complete reinstall of OSX, you can boot the OSX DVD, start Disk Utility and add a partition (or whatever type, it doesn't matter as you will be deleting it later). Don't worry about separate partitions for swap, home, and the like right now.

2. After the changes are made, boot into OSX, and install rEFIt: [http://refit.sourceforge.net/](http://refit.sourceforge.net/) This is a nice little tool that will get your Mac to boot into Linux by default, and you can select to start OSX in the menu if you like instead (note you have to edit the refit.conf file to boot legacy OS first).

3. Pop in the Ubuntu Live CD and boot it up. (hold c on startup, or select the optical disc icon in refit).

4. In the Ubuntu environment, start the partition editor (gparted). you should see an EFI partition (needed for updates), the OSX partition, and your linux 'partition'. select the partition you made for linux, and delete it, leaving free space, then close the application.

5. Now start the installer, and when the time comes tell it to install "to the free space", or if you are looking to make some custom partitioning scheme, then start the manual partitioner, and create your partitions in the free space. Note that the GPT partitioning scheme used does not have 'extended' or 'logical' partitions. Furthermore, the emulated bios in the Mac will have a hard time booting from a partition that is not one of the first four, so make sure you make your root (/) partition as partition 3 or 4 (or your /boot partition if you have one). Other partition locations do not matter. You will want to make sure that it does not attempt to mount the EFI partition in your new system either.

6. Install Ubuntu normally. You will likely have trouble with the Wi-Fi depending on the hardware type, and it mght work out-of-the-box, it is kind of a surprise. You really shouldn't have much of an issue with other hardware (Other than maybe a irritating keyboard bug that prevents you from selecting kernels in Grub.... but there is no real fix for this if you are completely updated in OSX.

---

### Post by Rudy A Winchester on 2007-11-17
Thanks a bunch for your help.  Clears some things up.  I may consider going the easy route and just install OS X on an external drive, and just format the whole internal drive for Ubuntu.  Maybe be the best way to go.  Will have to consider the different options when the time comes.

Again, thank you very much for your help.

---

