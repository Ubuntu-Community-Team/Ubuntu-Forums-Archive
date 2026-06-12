---
title: "[SOLVED] another dumb video question - PNy nVidia 6600 GT"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-03-17
Well, I've tried some things that I found here on the ubuntu forums, but I'm not having any luck.  So, I'm hoping someone can help me.

A friend gave me a better video card than what I had, so I am going from an old Diamond V700(?) to a PNY Verto GeForce 6600 GT with 256mb on board.  I figured I would need the restricted driver, so (in KDE at the time, now using Gnome for now) I tried installing the "new" glx driver for nvidia and marking it for use in the restricted drivers manager.  I then switched the cards, expecting a "goofy" screen (which I did get) so went into a terminal and ran dpkg-reconfigure xserver-xorg and chose nvidia for the card type.  I also tried setting the modes down to just 600x480 and 800x640 to start, but even that didn't work.  I have used Envy in the past to install an nvidia driver, but I always had an xwindows session running and was connected to the net when I did so.  Now, if I use the "new" card, I can only get to a terminal, and I have no idea how to start the net from there or how to retrieve/run envy from the command line.

So, can anyone help me on this?  Please ignore my bean count if you're using that to judge if I should be able to figure this out - I've only answered some posts on wireless networking but have asked many questions!

Thanks in advance!

:)

---

### Post by anewguy on 2008-03-18
HELP!!!!   Please?  :)

---

### Post by meanburrito920 on 2008-03-18
what do you mean when you sasy you "switched the cards"? did you have a different card in when you installed the driver? If you are looking for a fix just the get the GUI back, edit the xorg.conf file in /etc/X11 so it reads

```
Driver   "nvidia"
```

instead of 

```
Driver   "nv"
```

that should at least get your GUI back.

if it already is that way, switch it back and it should start working.

---

### Post by Neo0351 on 2008-03-18
Try this
```
sudo apt-get -y install nvidia-glx
sudo nvidia-glx-config enable
```

---

### Post by anewguy on 2008-03-18
Well, I'll tell you what I've done to date, and then go back and give that last thing a try.

While up on my old card, I downloaded and installed Envy, knowing it would install the legacy driver (nv) for that card.  I then switched cards and ran Envy in terminal mode (sudo envy -t), told it to remove all drivers, then install the driver.  It deleted the old legacy drivers, then installed the "new" nVidia drivers.  I checked xorg.conf to be sure nvidia was specified, then tried rebooting - still no good.  Went into terminal mode and ran nvidia-glx-config enable - same result.  I then ran sudo nvidia-xconfig - same result.  It appears like the sync is off, so I ran dpkg-reconfigure of xserver-xorg again, and specified the rates it defaulted to so at least they were specified in xorg.conf - same result.

"Regular" text mode (i.e., at boot) is fine - it's when the graphics start up it is crazy, so I assume there is still something wrong with xorg.conf.  I don't know if there are extra options I need to specify for the device or what.  I know I get a failure to allocate message at boot for PIC device 1:0.0, which is the video card.

Please note the card does not work with the vesa driver either.

I'm really kind of at my wits end - I think I've been messing with this longer than I did to get my wireless working on 4 different PCs with 4 different adapters!  :)

Any help would be greatly appreciated!

Neo0351:  I tried the apt-get for nvidia-glx, and it wants to delete my new drivers - the nvidia "new" drivers.  Luckily I didn't specify force so for now everything is the same.

---

### Post by Neo0351 on 2008-03-18
Well there are three nvidia glx drivers, the "new", glx, and legacy.  The new ones aren't working for ya, so I would give the glx ones a try.  Yes it will uninstall the "new" glx driver, but it isnt working anyways.  I told you do use that glx because someone else in another thread had success with it.  Here's the thread
[http://ubuntuforums.org/showthread.php?t=221313&highlight=6600gt](http://ubuntuforums.org/showthread.php?t=221313&highlight=6600gt)

---

### Post by anewguy on 2008-03-19
I'll give that another try, but be aware that when I first started that is what I did - I used synaptic to install nvidia-glx and had "nvidia" as the driver but it didn't work.  That's when I went ahead with Envy (tselliot, the op of the post you linked to, wrote Envy to install the proper driver - that's why I assumed when I had the new card in and it went to the "new" drivers that they were needed).

I'll try this a little later tonight - got some supper going right now.  :)

Thanks for the help!!  :):)

---

### Post by anewguy on 2008-03-19
Hummmmm, another dumb question - I have an old PIII-500 with an AGP 1.0 slot (I think it's just 1x and 2x), and I saw mention in that post that they had an 8x card.  It's been a while, but I didn't think most of the 4x-8x cards worked in AGP 1.0 slot due to voltage differences.  I assume since mine at least runs that it is okay for the slot??

:)

---

### Post by Neo0351 on 2008-03-19
You know what, I got to thinking, and maybe downloading the driver the driver nvidia and installing might be easier.  Here's to do it.  Download the driver for x86
[ftp://download.nvidia.com/XFree86/Linux-x86/169.12](ftp://download.nvidia.com/XFree86/Linux-x86/169.12)
and x86-64
[ftp://download.nvidia.com/XFree86/Linux-x86_64/169.12/](ftp://download.nvidia.com/XFree86/Linux-x86_64/169.12/)

Then grab what the driver needs to compile.
Code:

uname -r
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install linux-restricted-modules-'uname -r'
sudo apt-get install linux-source-2.6.22 build-essential

Of course make sure to replace 2.6.22 with whatever kernel you're using

Then ctrl+alt+F1 and log in as root

Code:

killall gdm
chmod a+x /location/to/driver
sh /location/to/driver

follow the directions, then

Code:

nano /etc/default/linux-restricted-modules-common

The last line should look like

Code:

DISABLED_MODULES="nv"

After that cross fingers and reboot
Hope that works for ya

---

### Post by anewguy on 2008-03-19
Well, the downloading, compiling of the driver was a small disaster.  It came up with a message saying the kernel module wasn't linked against my version of the kernel (I'm using Gutsy 2.14.22 as well).  Also, I have no "default" directory under my /etc directory, so I couldn't edit the file suggested.  Instead, I added nv to the blacklist, since that seems to be where kernel modules are held out.

Also, I noticed at boot there is a message about Nvidia probe not finding device at 1:00.0 which is the PCI "address" of the video card.  This I think goes along with the message at the very start of boot saying could not allocate resources for......0000:01:0.0 - the same device.  I'm starting to wonder if there is something I need to add to the boot line in grub for this all to work.

I'm going to try booting the kubuntu livecd I have sometime and see if it recognizes the card.  Right now I'm pretty tired of trying, failing, trying, failing, trying, failing...


If ANYONE has ANY ideas PLEASE let me know!  :)

---

### Post by Neo0351 on 2008-03-19
> **anewguy said:**
> Well, the downloading, compiling of the driver was a small disaster.  It came up with a message saying the kernel module wasn't linked against my version of the kernel (I'm using Gutsy 2.14.22 as well).  Also, I have no "default" directory under my /etc directory, so I couldn't edit the file suggested.  Instead, I added nv to the blacklist, since that seems to be where kernel modules are held out.

Also, I noticed at boot there is a message about Nvidia probe not finding device at 1:00.0 which is the PCI "address" of the video card.  This I think goes along with the message at the very start of boot saying could not allocate resources for......0000:01:0.0 - the same device.  I'm starting to wonder if there is something I need to add to the boot line in grub for this all to work.

I'm going to try booting the kubuntu livecd I have sometime and see if it recognizes the card.  Right now I'm pretty tired of trying, failing, trying, failing, trying, failing...


If ANYONE has ANY ideas PLEASE let me know!  :)

huh, well I think you might be onto something here.  You're absolutely right that a 8x card wouldn't work in AGP1.0 slot, even though it might fit because of the voltage differences.  You would need at least a 2.0 to run it.  Since it's not finding your card, that might be the problem.  If it doesn't work with the live cd that would be my guess.  Also you could try to see if its finding your card
```
lspci | grep VGA
```

---

### Post by anewguy on 2008-03-20
Latest developments:

The direct nvidia driver install failed.  I decided to boot into my Windows 98SE partition and see if I could load a driver there.  Windows obviously defaulted to a low res driver, but it did at least run.  I downloaded what was supposed to be the Windows 98SE driver for the GeForce 6600 GT, but when I ran it it said no nvidia chip found.  Now I'm really confused.  Tried booting with the Kubuntu 6.06 livecd - it had the same messed up screen as I get in Gutsy.

I'm at a real loss here - the card itself is obviously working (at least with a low res driver in Windows).  I can get text mode fine in Gutsy.  I can't get any graphics mode going in Gutsy - this includes using Envy and just installing the NVidia driver direct from NVidia.  A lspci does show my video card.  I have tried specifying the vertical and horizontal rates for my monitor, both the "nv" and "nvidia" drivers in xorg.conf, etc.  I even tried just letting it default to 16 bit color and only having 800x600 and 600x480 resolutions.  All I get is a garbled screen.

For now I've gone back to my old cheapy Diamond Viper v770 - at least it will run okay.

I'd really appreciate some input here - am I doing something wrong?  When Gutsy is booting there is a message about not being able to allocate resource at 0000:01:0.0 - which is the PCI id of the video card.  It also kicks out a message saying nvidia probe failed.  I'm really at a loss!

:(

---

### Post by anewguy on 2008-03-21
Tech support from PNY says PNY doesn't support Linux.

Does anyone out there have this card working?

---

### Post by forrestcupp on 2008-03-21
I'd use Envy from the command line, like you were wanting to do.  First, I'd uninstall everything.
```
envy --uninstall-all
```
Then to use it to reinstall from the command line
```
envy -t
```
for text mode in the command line.  It works just like the GUI in that you can choose to have it download and install the drivers for you automatically.  Then you should be able to reboot and be ok.

---

### Post by anewguy on 2008-03-21
> **forrestcupp said:**
> I'd use Envy from the command line, like you were wanting to do.  First, I'd uninstall everything.
```
envy --uninstall-all
```
Then to use it to reinstall from the command line
```
envy -t
```
for text mode in the command line.  It works just like the GUI in that you can choose to have it download and install the drivers for you automatically.  Then you should be able to reboot and be ok.


I want to try again as you suggest - a quick question first.  Should I go through synaptic and remove all the nvidia stuff there that is currently installed so I am starting from scratch?  Also - using the driver directly from nvidia goes into a compile, but then fails on the load of the .ko - says the kernel was compiled with a different version of the compiler than was used for compiling the driver.  Since I think Envy gets that same driver, will I run into that same problem?

Thanks SO much for the reply!!  :)

---

### Post by forrestcupp on 2008-03-22
Envy should uninstall it ok.  Try that first, then if it doesn't work, go through synaptic.

Sorry the response is so late.  I'm sure you've done something by now.

---

### Post by anewguy on 2008-03-22
Well, I seem to have run into a few snags again, so here are the things I need help on before I can try Envy again with the "new" card.  BTW - I tried Envy last night with my existing card (old Diamond Viper v770) and it installed everything for it - even got the nVidia splash screen during boot.   Anyway, here's my snags:

(1) Somehow or another in all of this (I assume from following another post) I ended up with another set of entries on my grub menu, these for the "rt" (I assume real-time) kernel.  I know I don't need it but I have no idea how to delete the rt kernel (I do know how to edit the menu for grub - I need to get rid of the entire kernel).

(2) I can only assume that it is perhaps related to (1), even though I boot the "normal" kernel:  Envy, without internet access fails, so I downloaded the pkg file it references directly from nVidia.  It fails saying it can't install a .ko (kernel object ??) file because the driver was built using a different version of the compiler than the kernel.  Any ideas?

(3) To truly run Envy from the command line, I need internet access.  The only way I ever connect to the net is via network manager in the GUI.  I tried dhclient eth1 - didn't work, so I tried the same for eth0 - didn't work.  I know one of those gets mapped to wan0, but wan0 didn't show in the ifconfig list.  My network is wireless, using ndiswrapper (shows as a running process) and a WEP open password.  What/how do I set up so I can access the net from the command line?

I'm hoping that removing this rt kernel will help out (2), but I have no ideas on how to do any of these things.

Any help is GREATLY appreciated!  :)

---

### Post by forrestcupp on 2008-03-22
Here's what I would do.
```
sudo apt-get --purge remove linux-rt
```
to remove the metapackage for the real-time kernel.  Then
```
sudo apt-get --purge remove nvidia*
```
To remove anything that is for nvidia.  Then
```
sudo apt-get autoremove
```
To remove all of the unused dependencies leftover from what you just removed, especially from the kernel.  Then I would
```
sudo dpkg-reconfigure xserver-xorg
```
To reconfigure X.  Choose the vesa drivers so that you can boot to your desktop with no trouble.
If you are in recovery mode as root, you won't need sudo in those commands.

Then reboot.  The real-time kernel entries should be gone, and you should be able to boot to the desktop with your vesa drivers, which means you should be able to have internet access.  All of your nvidia drivers and settings are gone now, so there shouldn't be any conflicts there.

Now, go to System->Administration->Software Sources.  Make sure all of the boxes in the 'Ubuntu Software' tab are checked except the CD box.  Then in a terminal, type:
```
sudo apt-get update
sudo apt-get upgrade
```

When that's done, try installing nvidia drivers with Envy again.  But I'd make sure you have the correct version of Envy.  Go back to the Envy web site and make sure you have the correct version for whether you have 32-bit or 64-bit and the right Envy version for your version of Ubuntu, i.e. Gutsy.  If you have the wrong version of Envy, that could be the source for all of your kernel errors you get with it.

---

### Post by anewguy on 2008-03-23
I finally got the net up via the command line, so I ran Envy again with the new card in.  this time Envy ran to completion.  It changed the driver to "amd" - not "nvidia" or "nv", and it removed the legacy stuff.  Unfortunately it still doesn't work.  I tried starting X manually after it completed/rebooted/failed, and X bombs out saying no device found - I assume that means that whatever the driver is looking for my card isn't it.

I tried downloading the nVidia driver directly from nVidia again, and it still gets the compiler mismatch error.

I did check to make sure I have the right version of Envy, but thanks for that check.

Trying "nv" or "nvidia" as the driver after running Envy made X abort each time saying the respective driver wasn't found.

So now I'm stuck again.  I wish there was someway to download and compile a GOOD driver for this card in Linux, but for now I am closing this post and starting a new one based purely on getting/installing a working nvidia driver.

Thanks for the help!  :)

---

### Post by forrestcupp on 2008-03-23
AMD is ATI, like Radeon.  Are you sure you have an nvidia card?

---

### Post by phread59 on 2008-03-23
OK I'm no guru.  But I believe you are trying to put diesel into a gas engine here.  Your Diamond card would be running on an ATI chipset.  The GeeForce card requires an NVIDIA chipset.  You may be trying to pound a square peg into a round hole.  Doublecheck the compatabilitys of both cards.  I believe you will find a chipset incompatability here.

BTW both cards use a PCI slot so they will phisycly drop in the slot and some of the basic powers,groundsand signal wiring will be the same.  I think the chip programming will be different.  I just built this box and made sure of which chipset I had to get the proper video card (NVIDIA and GeeForce in my case).  Check it out,  This may solve your problem.

Mark Shuman

---

### Post by forrestcupp on 2008-03-23
> **phread59 said:**
> OK I'm no guru.  But I believe you are trying to put diesel into a gas engine here.  Your Diamond card would be running on an ATI chipset.  The GeeForce card requires an NVIDIA chipset.  You may be trying to pound a square peg into a round hole.  Doublecheck the compatabilitys of both cards.  I believe you will find a chipset incompatability here.

BTW both cards use a PCI slot so they will phisycly drop in the slot and some of the basic powers,groundsand signal wiring will be the same.  I think the chip programming will be different.  I just built this box and made sure of which chipset I had to get the proper video card (NVIDIA and GeeForce in my case).  Check it out,  This may solve your problem.

Mark Shuman

That is exactly your problem.  All along, I thought you had your nvidia card in.  The ATI drivers/settings will conflict with the nvidia drivers.  You need to set it up for one or the other and stop swapping.  Figure out which card you want to stick with, then do an
```
envy --uninstall-all
``` to start from a clean slate.  Then install the correct drivers for whichever card you are using.

---

