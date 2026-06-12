---
title: "Success on Macbook 5,2 Karmic"
date: 2009-11-15
forum: Apple Hardware Users
---

### Post by hoborider on 2009-11-15
I have Karmic (9.10) successfully installed on my macbook 5,2 (5.2). I've got sound and graphics acceleration and function keys (except brightness) and wireless. I've also got the grub-efi working so don't have to boot with acpi=off. This gives you both cores of your processor and gives your correct battery reading (and it seems it reduced brightness on my screen to a tolerable level ++ ++ ).

I followed the writeups for installing Karmic and Jaunty on a 5,1 macbook. 
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) (follow the links on the right side - read Karmic and Jaunty writeups for 5,1 and Karmic for 5,2)

This got me sound. And this writeup was also used for the config file for the touchpad. You can use the enable laptop mode and fan setting in the writeup as well.  

1) Install rEFIT in OSX. It's necessary. It's easy. Google rEFIT and install. Easy.

2) Run bootcamp in OSX and carve out a partition (I did 20g - 16g for ubuntu and 4g for swap).  You'll make the swap partition in gparted in the ubuntu install.  Bootcamp only makes 1 partition. 

3) Download the ubuntu amd64 iso and burn to DVD or CD. 

4) Reboot the CPU with the CD/DVD in the drive. Hold down C to boot from disk 
 ***make sure you've got an ethernet cable and its already plugged in to your modem or router - wireless don't work outta the box***

5) When the install menu comes up and AFTER you select english as the language press F6. Check off acpi=off and hit ESC. Now chose install (don't bother with trying the livecd)

6) Run the advanced partition setup and double click on the partition that bootcamp made. This will popup a window that allows you to resize and format the partition as ext3. Don't use ext4. Make sure you mount it at / 

7) Leave enough space for a swap partition. (twice your RAM - no less). 

8) Continue with the install after all this is done. After the install - or just before I can't remember, you'll be presented with a screen with an ADVANCED button in the lower right corner. Click advanced and put GRUB in the UBUNTU partition - not on hd0,0 - it'll most likely be hd0,3 for you.

9) finish install and reboot. The CD/DVD will eject. Remove it. Continue reboot INTO OSX.  Again. Reboot into OSX. This blesses the UBUNTU partition automagically. After that, reboot again - this time into UBUNTU from rEFIT.

10) If it doesn't boot the GRUB menu - do a hard restart (hold down power button). Both times I installed, I had to do a hard restart at this point. This is the only time you should have too. 

11) At the GRUB menu that starts after rEFIT, press E. This brings up a command list. Add acpi=off at the end of line that has your kernel version.

Looks something like this:
 /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 

12) Press ctrl+X to boot with this new parameter. 

13) Ubuntu now boots. 

14) At this point add medibuntu and mactel repositories. Do a search on the forum or in google for how to add the mactel repositories. ubuntuguide.org has the process for adding medibuntu.

15) After adding those repositories - do:
sudo apt-get update

16) By this time, the hardware driver icon should have popped up in your notification tray. Double-click this icon or chose System > Administration > Hardware Drivers. You'll see 4 available. Activate Broadcom STA and NVIDIA 185. 

17) run: 
sudo apt-get install pommed
sudo apt-get install nvidia-bl-dkms
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install build-essential
sudo apt-get install grub-efi (see below as this will pop an error but will give you the correct package name to install)

18) There is a thread for configuring grub-efi the hard way (compiling from scratch). In Karmic you can install grub-efi for your platform. (I am using amd64). Just do:

sudo install grub-efi. This will pop an error most likely and give the package for your platform (i386 or amd64).  sudo install that package. CD into /usr/lib/grub

You'll see a directory with your package (i386/amd64). CD into that directory. Then run grub-mkimage as root and pass the necessary options. 

 sudo grub-mkimage -d . -o grub.efi part_gpt hfsplus fat ext2 normal sh chain boot configfile

The above works great and will generate a grub.efi file in the directory /usr/lib/grub/whateveryourplatformis
Open up gedit as root: 
sudo gedit grub.cfg

Copy and paste the following into that file (modify for your kernel version)
menuentry "UBUNTU 2.6.31-14" {
  # Set the root device for Linux.
  fakebios
  root=(hd0,3)
  # Load the loader. - other options: video=vesafb noefi
  linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 video=efifb acpi=force
  initrd /boot/initrd.img-2.6.31-14-generic
}

menuentry "MacOSX" {
  # Search the root device for Mac OS X's loader.
  search --set /usr/standalone/i386/boot.efi
  # Load the loader.
  chainloader /usr/standalone/i386/boot.efi
}

menuentry "Boot from MBR" {
  appleloader HD
}
menuentry "Boot from CD" {
  appleloader CD
}
#keymapping: remeber these keys when you boot, they can be helpful!!!
#F1 = ctrl-x
#F2 = ctrl-a
#F3 = ctrl-e

save and close that.

19) Copy that ENTIRE folder onto a USB drive. I accomplished this by chmod -R 777 /usr/lib/grub/whateveryourdirectoris and then using the GUI 'finder' window to drag and drop the directory onto the USB drive. 

20) Restart the computer. Boot into OSX this time.

21) Open finder and copy the directory from the USB drive into the /efi folder. The /efi folder is visible after clicking on Go > Computer.

22) Reboot

23) In rEFIT you should (will) have the new grub-efi available as bootable (the icon looks like 3 blocks stacked). Chose that and boot. 

24) The new grub menu pops up. Chose linux and boot (first choice - just hit enter). 

25) Ubuntu will boot. You'll have wireless (check the icon in the top right notification tray)  You might need to chose your wireless network. Enter your password if needed.

Follow the rest of the steps for activating sound in the writeups for installing Ubuntu on macbook 5,1. (All I did was change the /etc/modeprob.d/options.conf to include mbp=3 -- a reboot was required). I haven't tried patching alsa yet. I might. It works - so I'll probably leave it be. You'll also find a great config file for the touchpad and instructions on where to put that. This gives you a very functional touchpad. You can tweak speed/acceleration/sensitivity to your liking.

If I left anything out, or you have questions - fire away.  I'll try and hash it out.  

**I've yet to try iSight built-in camera.  Will find a way to test it soon.**
** I can also shutdown no problems.  I've not tried to sleep / resume yet.  Not to concerned if that works.**

---

### Post by thinktyler on 2009-11-15
Thanks for the information I will do this tomorrow. 5,2 ftw!

---

### Post by thor27 on 2009-11-23
Thanks for this great howto.

I've got ubuntu running fine with OpenGL working, wifi and bluetooth.

I just couldn't get the grub.efi to work, when I try to boot on it it says that efti couldn't load the grub.efi (I don't remeber exactly the error message)

This could be due the fact I've choosen a 32bit version of ubuntu?

And it's possible to get ACPI working without this rEFIT?

thanks!

---

### Post by lepukowsky on 2009-11-24
Thank you immensely hoborider! I am a mac and linux/ubuntu newb and you got me running perfectly in just a few hours!:D

---

### Post by dbm_db on 2009-11-25
I too successfully installed Karmic x32 on my Macbook Pro 5,2. Upgraded kernel to PAE version so i see the full 6GB of memory i have.   Everything worked out of the box except ANALOG sound.  Digital sound works so that is the route i'm doing.  I'm using the default video, not the NVIDIA proprietary drives.   Installed it on an internal 160GB Intel SSD.

---

### Post by lepukowsky on 2009-11-26
dbm_db what are your current sound settings on your system that you think make it work? I played with linux sound a while back when using ubuntu studio and realized I was in way over my head.

I tried opening sound preferences and trying each of the hardware options that said digital but I still have no sound. Is there anything else you changed?

Thanks!

---

### Post by vibe3 on 2009-11-26
Why can't you use ext4 out of curiosity?

---

### Post by Super Sonic on 2009-11-26
Thanks a bunch for helping me put Ubuntu on my new MacBook:D! I always thought that KDE was Apple's only eye-candy rival. By the way, Is it possible to use the IR reciever in the MacBook for LIRC? I could then use my old PCTV133 and watch some TV:popcorn: :D  [This is really the only reason I would want Linux instead of Mac OS X, that and Linux has more emulators/games and less bloat/HD usage.] By the way, do the crossover ethernet smart-ports still work the same way in Ubuntu? Or is that independent of the OS?

BTW, when I try to hibernate, I get this. Can anyone make sense of this?

```
[ 8660.250000] btusb_bulk_complete: hci0 urb ffff88007b84f480 failed to resubmit
(1)
[ 8660.250000] btusb_bulk_complete: hci0 urb ffff88007b84f480 failed to resubmit
(1)
[ 8660.250000] btusb_bulk_complete: hci0 urb ffff88007b84fa80 failed to resubmit
(1)
[ 8682.480000] Power down.
[ 8714.040000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 8714.040000] ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 8714.040000]               res   40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeo
ut)
[  8714.040000] ata1.00: status: { DRDY }
[  8719.570000] ata1.00: revalidation failed (errno=-5)
[  8730.100000] ata1.00: revalidation failed (errno=-5)
[  8760.630000] ata1.00: revalidation failed (errno=-5)
[ 8761.160000] System halted.
```

---

### Post by dbm_db on 2009-11-26
> **lepukowsky said:**
> dbm_db what are your current sound settings on your system that you think make it work? I played with linux sound a while back when using ubuntu studio and realized I was in way over my head.

I tried opening sound preferences and trying each of the hardware options that said digital but I still have no sound. Is there anything else you changed?

Thanks!

For my setup i'm using the Digital Stereo Duplex(IC958).  I'm using an Optical cable from my Macbook Pro which connects to a D/A converter which has an Optical In. From there I run the Analog outs to my speakers. BTW, you can tell when the Macbook Pro is using optical because of the red-light coming out of the headphone. No red-light, no sound. The digital just works, the analog doesn't.

Hope that helps.

---

### Post by dentament on 2009-11-29
Yep, it works! Thanks a lot.

I'll add just some little corrections and some tips.

Hoborider's tip to make sound work is wrong, in order for analog sound to work you have to change /etc/modprobe.d/alsa-base.conf adding "model=mbp3" to the line that states "options snd-hda-intel power_save=10 power_save_controller=N", IE:

```
options snd-hda-intel power_save=10 power_save_controller=N
```

...must become...

```
options snd-hda-intel power_save=10 power_save_controller=N model=mbp3
```


The "MacOSX" entry in grub.cfg didn't work for me, instead it works this way...

```
menuentry "MacOSX" {
 root=(hd0,2)
 chainloader /usr/standalone/i386/boot.efi
}
```

I post the complete, slightly modified grub.cfg I'm using since it may be useful for someone (autoloads ubuntu after 10 seconds wait, adds "splash", adds a "recovery mode" entry)

```
default=0
timeout=10
## questo qua sotto non funziona, forse bisogna mettere il modulo direttamente
## nell'immagine?
#insmod png

menuentry "Ubuntu Linux 2.6.31-15-generic" {
# Set the root device for Linux.
 fakebios
 root=(hd0,3)
# Load the loader. - other options: video=vesafb noefi
 linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sda3 video=efifb acpi=force splash
 initrd /boot/initrd.img-2.6.31-15-generic
}

menuentry "Ubuntu Linux 2.6.31-15-generic, recovery mode" {
# Set the root device for Linux.
 fakebios
 root=(hd0,3)
# Load the loader. - other options: video=vesafb noefi
 linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sda3 video=efifb acpi=force single
  initrd /boot/initrd.img-2.6.31-15-generic
}

menuentry "MacOSX" {
 root=(hd0,2)
 chainloader /usr/standalone/i386/boot.efi
# Search the root device for Mac OS X's loader.
#  search --set /usr/standalone/i386/boot.efi
# Load the loader.
#  chainloader /usr/standalone/i386/boot.efi
}

menuentry "Boot from CD" {
 appleloader CD
}
#keymapping: remember these keys when you boot, they can be helpful!!!
#F1 = ctrl-x
#F2 = ctrl-a
#F3 = ctrl-e
```

Note that I removed the "Boot from MBR" entry given in hoborider's post since it didn't work on my system (it started osx in "text mode", but it crashed after a while), while the osx "normal" entry above works for me.

Also note that once you have grub booting linux and osx correctly you can get rid of refit by simply disabling it. This way you have grub soon starting up at boot and you can have linux boot automatically (see the grub.cfg above, "default" and "timeout" options at its beginning). With refit you can't have linux boot automatically: it defaults on osx, and the "legacyfirst" option in /efi/refit/refit.conf doesn't work here since we're using an "efi boot".
To disable refit without uninstalling it: in osx, just move the "refit" subdir which is inside the "/efi" dir somewhere outside of "efi", then move the "rEFItBlesser" subdir which is inside "/Library/StartupItems" somewhere outside "/Library/StartupItems", then bless your "grub-efi" dir by issuing:

```
bless --folder "/efi/_*your grub-efi dir*_" --file "/efi/*_your grub-efi dir_*/grub.efi" --setBoot
```


Regarding the question "why not use ext4" posted by vibe3, I suppose it's because grub's support for ext4 is not very stable yet and often gives problems.


The following "xorg.conf" works for me in order to have only my external monitor working, with the macbook's one off, as I needed:

```
Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "glx"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400M"
    Option  "NvAgp" "1"
    Option  "NoLogo" "on"
    Option  "UseDisplayDevice" "DFP-1"
EndSection
```

(
The "magic" line is this:
```
Option  "UseDisplayDevice" "DFP-1"
```
)


One other tip: if you have nautilus working very slow and eating a lot of cpu and memory, as I had, it could be because it has a problem when Desktop dir contains lots of files (even in its subdirs) **and/or** if the "XDG_DOCUMENTS_DIR" (and maybe the other "non desktop" dirs) specified in your homedir ".config/user-dirs.dir" file are subdirs one of each other... Well I'm not sure what was the issue, anyway I have my "documents" dir inside my Desktop one and it contains lots of files, and I had the problem; I managed to workaround it by editing "~/.config/user-dirs.dir" so that it states...

```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME"
XDG_TEMPLATES_DIR="$HOME"
XDG_PUBLICSHARE_DIR="$HOME"
XDG_DOCUMENTS_DIR="$HOME"
XDG_MUSIC_DIR="$HOME"
XDG_PICTURES_DIR="$HOME"
XDG_VIDEOS_DIR="$HOME"
```

(Btw as far as I've experienced this doesn't affect gnome's usability at all).

Hope this helps.

---

### Post by thor27 on 2009-11-29
Hello!

Playing around with sound I could get this:

model=mb5
Sound works after unmuting HP, but no headphones detection and no subwoofers, mic works

model=mbp3
Headphones detection works, sound works but no subwoofers, mic works 

model=asus-a7m
Headphone detection doesnt works, but subwoofers works and sound seems much cleaner, mic doesn't works

I'm using asus-a7m since in 99% of my usage in this notebook is for playing only in the internal speaker.

And just a tip for unload the snd-hda-intel and change without rebooting:

rmmod snd-hda-intel -w & 
sudo killall pulseaudio
<just press enter here and you will see background process going away - that is the module unloading>
modprobe snd-hda-intel model=XXXX

Don't worry to bring pulseaudio up again... it goes up automatically

---

### Post by alimh on 2009-11-30
Thinking about purchasing a MacBook Pro to put Ubuntu on because I like the size / style of the MacBook Pro.

A couple of questions if anyone can answer, it would be awesome:

1) How is the battery life?
2) Is there a way to tell the model (5.1, 5.2, etc.) from just the outside of the box? (i.e. before I buy it)

---

### Post by linuxopjemac on 2009-11-30
ad 2) [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages) and then look at a site like
[http://apple-history.com](http://apple-history.com) to look at the pics

---

### Post by thor27 on 2009-11-30
I think I got perfect sound now!

Subwoofer and everything is working, you just need to install karmic backports and set the model to mb31


Hope that helps :)

---

### Post by vibe3 on 2009-12-01
In step (24), trying to get grub-efi to boot ubuntu, I copied that exact grub.cfg file and I get the new rEFIt button with the 3 stacked blocks. When I try to boot the "UBUNTU 2.6.31-14" option, I get this error:

ROM image present
error: unknown command `initrd'

Press any key to continue...

Trying to select the MacOSX option gives this error:

error: unknown command `search'

Any ideas???

---

### Post by Dooley on 2009-12-01
With the new refit entry does anyone else boot straight to a grub shell prompt? 

I tried this using ext4, could this be an issue?

---

### Post by Drian42 on 2009-12-01
vibe3: I struggled with step 24 as well. I copied the whole folder (which for me was called x86_64-efi into the efi folder in my mac partition. I then got the same error as you, but after booting into OSX a couple of times and once into the GRUB option in refit it started to work!

I currently have ubuntu installed but I have one issue - the trackpad doesn't work for me. I need to press very hard and use the whole of my finger in order to get any response from Ubuntu, but if i plug in a mouse it works fine. I tried the config file - it didn't work for me.

Why is the refit entry with the three stacked blocks better than the legacy grub refit entry? Ubuntu seems to run the same through both of them, and brightness is adjustable through the graphics driver - in display preferences. Is there any reason why I shouldn't remove the three stacked blocks entry and just use the original grub one? I want my refit to look clean and efficient :). Or is there any way of removing the legacy/grub ubuntu entry?

I understand this could be because it only uses one core, but I don't know how to check.

---

### Post by nexx892 on 2009-12-01
Lulz I have been doing this with karmic beta.




It all works no tweakin.

---

### Post by vibe3 on 2009-12-01
One issue I am seeing with that step 24, is on my system, the legacy grub installed on /dev/sda3 sees the hard drive as hd0, but the EFI grub in the mac folder with the 3 stacked blocks sees it as hd1.

I changed the grub.cfg to use hd1 everywhere, and now its able to find the linux kernel and initrd image, but it just hangs when trying to boot it.

Also, if I type "ls" in the command line grub interface it hangs. But "ls" on the legacy grub works fine.

Rebooting a bunch of times into OSX doesn't seem to fix my problem.

---

### Post by Jonie on 2009-12-03
> **Super Sonic said:**
> Thanks a bunch for helping me put Ubuntu on my new MacBook:D! I always thought that KDE was Apple's only eye-candy rival. By the way, Is it possible to use the IR reciever in the MacBook for LIRC? I could then use my old PCTV133 and watch some TV:popcorn: :D  [This is really the only reason I would want Linux instead of Mac OS X, that and Linux has more emulators/games and less bloat/HD usage.] By the way, do the crossover ethernet smart-ports still work the same way in Ubuntu? Or is that independent of the OS?

BTW, when I try to hibernate, I get this. Can anyone make sense of this?

```
[ 8660.250000] btusb_bulk_complete: hci0 urb ffff88007b84f480 failed to resubmit
(1)
[ 8660.250000] btusb_bulk_complete: hci0 urb ffff88007b84f480 failed to resubmit
(1)
[ 8660.250000] btusb_bulk_complete: hci0 urb ffff88007b84fa80 failed to resubmit
(1)
[ 8682.480000] Power down.
[ 8714.040000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 8714.040000] ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 8714.040000]               res   40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeo
ut)
[  8714.040000] ata1.00: status: { DRDY }
[  8719.570000] ata1.00: revalidation failed (errno=-5)
[  8730.100000] ata1.00: revalidation failed (errno=-5)
[  8760.630000] ata1.00: revalidation failed (errno=-5)
[ 8761.160000] System halted.
```

Not sure if this is an appropriate place here, but yes, I get this error too when trying to hibernate, not on Mac. The machine is an old Nforce 3 rig. In my case the error is not written to log, just flashes on the screen. I checked HDD for errors to be sure this is not an coincidence and there are no errors. Does it repeat? If your HDD is sane too, it looks like a bug, not filed yet...

What my PC has in common with Mac is that it starts from GPT disk, too.

---

### Post by CellPhoneDude on 2009-12-07
> **hoborider said:**
> I have Karmic (9.10) successfully installed on my macbook 5,2 (5.2). I've got sound and graphics acceleration and function keys (except brightness) and wireless. I've also got the grub-efi working so don't have to boot with acpi=off. This gives you both cores of your processor and gives your correct battery reading (and it seems it reduced brightness on my screen to a tolerable level ++ ++ ).

I followed the writeups for installing Karmic and Jaunty on a 5,1 macbook. 
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) (follow the links on the right side - read Karmic and Jaunty writeups for 5,1 and Karmic for 5,2)


I found this and thought great I can fix all the issues with my triple booting macbook 5,2 and am happy to report that everything works great onlything i did differently just to test it was in grub2 i wrote maxcpus=1 after all the drivers and such were installed and left acpi=force out machine seems to hang less because of it as well not sure what I should check to see what kind of differnce its making. I also nixed all the boot camp stuff from my install process letting each OS's installer format its space that I had set aside during the install and everything boots as well as they all work now if only I could get osx/win7/ubuntu to all see each others partitions that would be amazing but I'm pretty freaking happy my superbook works... thanks

---

### Post by mkr_mkr on 2009-12-08
I originally tried to install Ubuntu 9.10 using instructions from another thread, but that didn't fix the acpi=off problem.

Then I found this thread and followed the instructions word for word, but ran into a tricky problem.  After installation, I get the following message when trying to boot ubuntu

"grub grub grub grub" ... forever.

When I first tried to install Ubuntu 9.10 I may have forgotten to click "Advanced" on the last page.  So perhaps the first grub was installed on hd0,0 instead of /dev/sda3 (where Ubuntu is installed).  Now that I'm trying to run grub on /dev/sda3, the system is getting stuck on the old grub install.

Here's my question.  Should I just reinstall Ubuntu again and not change the "Advanced" boot option?  Would this have adverse effects on my ability to boot Mac Os X?

Edit: Fixed the problem by following these instructions...
[http://ubuntuforums.org/showthread.php?t=1297229](http://ubuntuforums.org/showthread.php?t=1297229)  Post #6 by proycon

---

### Post by Gambit- on 2009-12-09
I have been unable to get sound working, trying model mb31 and other variations, including upgrading to the latest snapshot of the alsa drivers.  Are there any other suggestions or directions?

---

### Post by lepukowsky on 2009-12-21
Hey y'all I've had 9.10 running on my 5,2 macbook for probably about a month now, but I've noticed something I'd like to change.

When I boot up and my external hard drive is plugged in, ubuntu cannot boot. It says "I need to boot from the kernal first"...and the only solution is to restart. It allows me to select the "3-block" stack in rEFIt to go to grub2, but when I get to grub2 it gives me this error every time. 

It is not a huge problem, but as I basically always have my external plugged in so it's just an extra step to unplug it first if i wanna boot linux.

Could this be because I have ubuntu OS iso's on my external and it thinks I am trying to boot from these images? 

Thanks for any possible help!

---

### Post by &lt; Tristan &gt; on 2009-12-21
> **Gambit- said:**
> I have been unable to get sound working, trying model mb31 and other variations, including upgrading to the latest snapshot of the alsa drivers.  Are there any other suggestions or directions?

I have been through two weeks of pain trying to get sound on my MacBook Pro 5,2 fully functional with 9.10.

It was easy in the end - make sure you use "model=mb5" on the end of the snd-hda-intel option in /etc/modprobe.d/alsa-base.conf.

It's a bit choppy when you adjust the volume level - but otherwise good.

Apparently 2.6.32 kernel is supposed to make the sound issue go away, but who can wait for that.

---

### Post by mool on 2009-12-31
Hi, first of all sorry for my bad english.

I have my Macbook 5,2 working great with grub-efi, now I can use both cores and everything runs faster, but I can't access to text based consoles, the screen goes black. Any ideas about how to fix this?

Thanks!

---

