---
title: "no refit options on boot?"
date: 2012-05-03
forum: Apple Hardware Users
---

### Post by sasasasasasa on 2012-05-03
I followed these instructions:

[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

then converted to kubuntu.

The problem I have is that when I reboot I do not get the rEFIt screen and therefore can't reboot into mac OSX - I get a white screen of ~1 second and then grub starts.

In some ways I don't really care (although I would like to recover the disk space I left for osx if I'm never going to use it again) but I have the really annoying mac power on chime set to a really loud volume and I need macosx to get rid of this (unless someone knows how to do this from linux).

Any ideas where rEFIt went and how I can get it back?

Other than that the install appeared to go very smoothly from a USB stick loaded up with this [http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso) using unetbootin.

---

### Post by sasasasasasa on 2012-05-04
Does anyone know how to get rEFIt to appear at boot rather than just grub? The loud apple chime I get everytime I open my laptop is really annoying!

---

### Post by rgogunskiy on 2012-05-04
Try to press the Alt(Option) key during startup.

---

### Post by sasasasasasa on 2012-05-05
Thank you! I know this solution sounded easy but I had no idea.  I've had several macs over the years and I only run linux on them so I have absolutely no idea how macosx does things - all my previous machines always booted to refit by default even if they had hibernated.  

A supplementary question now (I've fixed the hideous apple chime):

Since I booted to refit using alt(option) the machine now always boots to refit even when coming out of hibernation.  I'd prefer it to automatically boot to linux and skip refit (unless I intervene) any idea how I can now revert to the behaviour I had before?

Thanks!

---

### Post by sasasasasasa on 2012-05-05
I think this might be something to do with "blessing" a partition - I'm not sure what this means or how to do it but I think if I bless the grub partition it will boot this automatically - any ideas how I can do this? (preferabl;y from linux)?

---

### Post by Lars Noodén on 2012-05-05
The only way I knew of installing rEFIt was via OS X.  If you cannot boot to OS X directly do it via the install (rescue) DVD.  But before you do that, untar rEFIt to an HFS formatted USB stick.  Once you have that, you can boot via the install DVD, mount the USB stick and run and install rEFIt.

---

### Post by sasasasasasa on 2012-05-06
Ok - the alt key on boot got me refit now I can't get the computer to boot to linux automatically - this is a pain since I'm hibernating to HD when I close the lid and waking up gives me refit.

I'd like to know how to go back to booting to linux straight away.

Ideally I'd like to delete the OSX partitions completely and boot to OSX for maintenance from a USB stick (no DCD drive / MBA) problem is I didn't get and system  / rescue disks with the MBA (is this usual? nothing in the box...) so am a bit flumoxed as to how to build a maxosx usb disk to boot to!

Ta!

---

### Post by ts3 on 2012-05-06
> **sasasasasasa said:**
> A supplementary question now (I've fixed the hideous apple chime)

May I ask how you got rid of the chime? It's been driving me bonkers ever since I got the MBA.

---

### Post by sasasasasasa on 2012-05-06
The only way I know to get rid of the chime is to mute the sound (or lower volume to zero) in macosx before exiting macosx.

It appears the chime volume is set in the firmware by macosx - the computer boots with the same volume settings it was shut down in (last shut down in maxosx I mean).

There are macosx third part software packages that "remove" the chime without turning the sound off but these really just mute the sound at macosx shutdown and restore it on boot.

Once the sound is muted in macosx the chime remains muted until you shutdown macosx with the sound up.

None of this affects the sound once linux has booted. The chime is really really annoying.

This advice would be useful preinstall information for anyone stripping macosx from their system!

---

### Post by luckylud on 2012-05-06
[COLOR=#000000]For disabling apple chime, I used the following command in Mac OSX :
sudo /usr/sbin/nvram SystemAudioVolume=%01
  
And if I remember my last OS X session, the sound was not muted and I've no chime at start-up.
[/COLOR][COLOR=#000000]
  
For UEFI boot [/COLOR][COLOR=#000000]loader there is a good guide here[/COLOR][COLOR=#000000] :
[/COLOR]https://help.ubuntu.com/community/UEFIBooting

Quickly to select the first boot loader :

[COLOR=#000000]**rEFIt** : 
In Mac OS X launch :[FONT=Book Antiqua]
  [/FONT][/COLOR][FONT=Book Antiqua][SIZE=3][COLOR=Black][COLOR=#000000][FONT=courier new][SIZE=2]sudo /efi/refit/enable.sh[/SIZE][/FONT][/COLOR][/COLOR][/SIZE][/FONT][FONT=Book Antiqua]
[/FONT][COLOR=#000000]
It's a script that will call the bless command.
  
or 
  
  [B]Grub2
  [/B][/COLOR][COLOR=#000000]In Mac OS X, d[/COLOR]etect where your grub.efi is stored. For example, in  folder /Volumes/something, then uses bless it (type command in MacOS X  terminal):  
 sudo bless --folder=/Volumes/something --file=/Volumes/something/efi/grub/grub.efi --setBoot

[COLOR=#000000]
[/COLOR]

---

### Post by sasasasasasa on 2012-05-07
Great! I'll give these a go and see what it gets me, thanks!

---

### Post by ts3 on 2012-05-08
> **sasasasasasa said:**
> The only way I know to get rid of the chime is to mute the sound (or lower volume to zero) in macosx before exiting macosx.

[QUOTE=luckylud]For disabling apple chime, I used the following command in Mac OSX :
sudo /usr/sbin/nvram SystemAudioVolume=%01[/QUOTE]

Thanks for the advice :) I decided to go with lowering the volume in Max OSX to very low (one or two bars) and the chime sound is barely audible. I can live with that since the chime has some diagnostic value but from what I read the second option (disable sound through the command line) should also work.

So as not to hijack the thread completely I thought I'd mention that the arch wiki has some info on the "bless" command, in the Booting Directly from Grub section here: [https://wiki.archlinux.org/index.php/MacBook](https://wiki.archlinux.org/index.php/MacBook)

Thanks and cheers :)

---

