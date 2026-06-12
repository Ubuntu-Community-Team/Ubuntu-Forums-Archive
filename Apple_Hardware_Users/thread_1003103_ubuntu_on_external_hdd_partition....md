---
title: "ubuntu on external hdd partition..."
date: 2008-12-05
forum: Apple Hardware Users
---

### Post by antiregulator on 2008-12-05
hi there!

as much as i've searched, i didn't find an already given satisfying scenario. so i give you my specific one.

i have an intel macbook core2duo 2.0 with osx 10.4.11 and an external 160 gb lacie firewire hdd.

i want to boot ubuntu on a partition scheme i have created on the lacie. the lacie partition table is as follows:

209mb: efi [i have rEFIt installed for multiboot]
140gb: hfs+ [use with osx]
100mb: /boot
  2gb: swap
 12gb: /
 ~8gb: /home

appart from any comment you could provide me when you see this setup, i would like to ask where on the filesystem should i instruct the installer to install the BOOTLOADER so that i can use rEFIt to boot linux from the external hdd.

thanks in advance ppl!

dave.

---

### Post by pxwpxw on 2008-12-05
> **antiregulator said:**
> hi there!

as much as i've searched, i didn't find an already given satisfying scenario. so i give you my specific one.

i have an intel macbook core2duo 2.0 with osx 10.4.11 and an external 160 gb lacie firewire hdd.

i want to boot ubuntu on a partition scheme i have created on the lacie. the lacie partition table is as follows:

209mb: efi [i have rEFIt installed for multiboot]
140gb: hfs+ [use with osx]
100mb: /boot
  2gb: swap
 12gb: /
 ~8gb: /home

appart from any comment you could provide me when you see this setup, i would like to ask where on the filesystem should i instruct the installer to install the BOOTLOADER so that i can use rEFIt to boot linux from the external hdd.

thanks in advance ppl!

dave.

Hi,

You will need an efi bootloader to boot the external. There is a grub-efi package on the grub address in my signature, which you can put (the EFI folder) on the root of your hfs+ partition, and it will be seen by refit. This can all be done before any Ubuntu install, and you dont need the grub1 bootloader and dont use it. grub1 is no use for booting external on intel mac. You need to have refit working first.
The grub.efi will bring up a text boot menu, the grub.cfg file may need editing. Once you get the boot menu up you can check what needs to be done.
I am using it now with an external and internal install on a MacBook2,1

---

### Post by antiregulator on 2008-12-06
thanx!!!

i'll try it asap! :D

---

### Post by luke white on 2008-12-06
I also have a problem with having tried to install ubuntu on an external partition - much more disastrous than the above posting. I really hope that someone can help me.

I have a macbook pro (15", 2Ghz core duo processor), and tried to install ubuntu 8.10 on my external Lacie firewwire drive, so that I could test it out without having to reformat the drive which has (or had) Mac OS X 10.4 (with latest update) on it. 

I downloaded the Live Cd and ran this without problem, so decided to put Ubuntu on my external. I started from the CD and chose the option to install. I went through the steps which the installer guides you through. I was careful to choose to install onto the external drive.

However, when I restarted the computer, I got a grey screen with an image of a disk with a flashing question mark in, indicating that the computer cannot see a valid OS on any drive. It does this whether or not the firewire is plugged in. Even more alarmingly, it will also now no longer boot from the original install CD that came with the mac. Holding down the C key and inserting a key causes the mac to whirr for a while and then spit out the CD. If I hold the D key down instead, I manage to get into the hardware test utility, and it confirms that there is no problem with the hardware as such. I have loaded the CD on another computer, and it reads OK.

The only thing I still seem to be able to do is to start up from the Live CD. When I do this, I can see my computer's hard drive, and it appears that all the original data is still on it, so at least I have not accidentally formatted my drive!!

I can only assume that something has happened in the install process which has changed something in the drivers or firmware (or whatever) which makes my hard drive not register as a startup disk. But whatever has happened I am rather up the proverbial creek without a paddle at the moment. 

Perhaps I have been rather reckless in hoping that I could port myself across so easily, but I hope that someone can help me. Am I the only person this has happened to? And does anyone know what I can do to get my back back up and running? Is there any information out there already in my problem?

Help me - please!!!!

Thanks very much,

Luke

:-<

---

### Post by antiregulator on 2008-12-06
hehe!!!

i've been there mate!

if you noticed during the istallation of ubuntu, right before it started copying files, there was an "advanced" button. there it asked you whether you wanted to install a boot loader. the default setting is yes (tick) and the default place to install it is in hd0 which means you overwrote the boot loader of osx with ubuntu's (grub, isn't it?)

i was lucky enough to have kept an image of my hdd before installing ubuntu, so i recuperated from the situation.

nevertheless, i would try this:
i.start up using osx live dvd
ii.open the disc utility and use the "repair" option on your main hdd partition
iii.use "startup drive" to select your macintosh hdd as the startup disc

i hope it works!

---

### Post by luke white on 2008-12-06
Thanks very much for your reply antiregulator - unfortunately part of the problem seems to be that my mac will no longer even start from the DVDs that came with it!! (I assume this is what you mean by 'osx live dvd') So I can't get to mac's Disk Utility software, etc. I will try tomorrow to take it to a friend's house and see if I can get it to load up as an external firewire drive, and see if I can run disk utility on it from there, and see if that helps.

But thanks in the meantime for your help.

What a blunderer I am !

---

### Post by cyberdork33 on 2008-12-06
note that there are other limitations when booting via efi rather than using the legacy grub bootloader

---

### Post by antiregulator on 2008-12-06
you can "force" boot from the live dvd (yup, that's what i meant) if right after the "ping" opening apple sound you press and keep pressing the option key for a few seconds. you will then be asked to start using the osx dvd.

[IMG]http://knittsings.com/wp-content/uploads/2008/04/windows-on-an-apple-mac-computer.jpg[/IMG]

something like this, but with only one cd option instead.

---

### Post by antiregulator on 2008-12-06
> **cyberdork33 said:**
> note that there are other limitations when booting via efi rather than using the legacy grub bootloader

such as?

if i chose to install the linux boot loader in what i have defined as my / partition (always on the external hdd), would that work? i have, so far and unsuccessfully, attempted installing the ubuntu bootloader in /boot partition. of course all that while having rEFIt installed on the system through the osx.

//edit: ok, i am now reading cyberdork's links, dont runto answer my last post! thanks! :D

---

### Post by pxwpxw on 2008-12-06
> **antiregulator said:**
> such as?

if i chose to install the linux boot loader in what i have defined as my / partition (always on the external hdd), would that work? i have, so far and unsuccessfully, attempted installing the ubuntu bootloader in /boot partition. of course all that while having rEFIt installed on the system through the osx.

//edit: ok, i am now reading cyberdork's links, dont runto answer my last post! thanks! :D

I would like  to know if you can try my grub efi bootloader to see how it goes.

 You can just put it on the external hfsplus partition and if you have refit running, refit will let you start grub.efi and show you the grub-efi menu to see if it can do what you want. I need some feedback from people trying it.

---

### Post by cyberdork33 on 2008-12-06
> **pxwpxw said:**
> I would like  to know if you can try my grub efi bootloader to see how it goes.

 You can just put it on the external hfsplus partition and if you have refit running, refit will let you start grub.efi and show you the grub-efi menu to see if it can do what you want. I need some feedback from people trying it.

and since it is really the only way to do what you are trying to do, it won't hurt anything to try it out.

---

### Post by luke white on 2008-12-07
Thanks for your reply, again antiregulator. I did manage, with a little fiddling to get the 'option' key to work and to load up the MacOS X Install DVD, and as you suggested, ran disk repair, but to no avail. It still does not recognise the hard drive as bootable. I went on to an apple forum and asked about overwritten boot loaders, and got a couple of hints - but it seems that I'm going to have to back all up and spend a "happy" day reinstalling Mac OS on my machine. Oh if only I had a proper backup image as you had! (Of course, it was my usual backup disk that I was trying to load Ubuntu onto!!)

That will of course solve my immediate problem, but, you know, I'd still really like to make the move over to Linux some day. Obviously how I do it will need a little more consideration...

Thanks again for your help - much appreciated! (even if the final outcome is a little gloomy!)

Luke

---

### Post by Calzlum on 2008-12-07
Hello!, well i was thinking to install ubuntu on my macbook pro, but then i chanced upon this thread and thought it'd be awesome to just stick ubuntu on my portable hard drive, 
so, does anyone have any instructions for a noob? hahaha
all i want to do is to be able to boot linux from my mac through my external hard drive, but i don't understand any of this EFI stuff...
thanks in advance...
'
But if its easier to install it on my internal one i'd be happy with that as long as it doesn't delete my files.. thats the reason i want it on my external...

---

### Post by luke white on 2008-12-07
Well, my advice is that if you are a "noob" like me, I'd steer well clear of what seems rather like an advanced maneuver. External drives as startup seem to give Ubuntu something of a problem - to be tangled with by people who know what EFIs and grubs and things like that are... The world of Linux installations does not seem to be as straightforward as those produced by the commercial sector, and is riddled with shark-infested water. My other advice is that whatever you do, make a full, bootable backup of your system as it is, so that if things do go belly up, like they did on me, you can get back to normal again much more easily. Let me be an example to everyone...

Luke

---

### Post by pxwpxw on 2008-12-07
> **Calzlum said:**
> Hello!, well i was thinking to install ubuntu on my macbook pro, but then i chanced upon this thread and thought it'd be awesome to just stick ubuntu on my portable hard drive, 
so, does anyone have any instructions for a noob? hahaha
all i want to do is to be able to boot linux from my mac through my external hard drive, but i don't understand any of this EFI stuff...
thanks in advance...
'
But if its easier to install it on my internal one i'd be happy with that as long as it doesn't delete my files.. thats the reason i want it on my external...

Hi, what is your Mac model - from  Apple-about this mac-more-hardware.
The MacBook2,1 runs the gru.efi loader well, easy to try, 3,1 does not,
others unknown at this stage.
Not difficult to try from a USB stick if you have refit installed.

---

### Post by Calzlum on 2008-12-07
Okay, i just purchased this macbook pro, 
and the model is:
MacBookPro5,1
judging by how new it is i'm doubting that i can actually install anything on it at this moment..

And whats "refit"? i wouldn't know...
hahaha i'm such a noob...
thanks though!

---

### Post by pxwpxw on 2008-12-07
Enjoy

---

### Post by pxwpxw on 2008-12-07
> **Calzlum said:**
> Okay, i just purchased this macbook pro, 
and the model is:
MacBookPro5,1
judging by how new it is i'm doubting that i can actually install anything on it at this moment..

And whats "refit"? i wouldn't know...
hahaha i'm such a noob...
thanks though!

You will need refit (its an efi utility to manage booting).
You might also like to look at some of the installation guides.
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

---

