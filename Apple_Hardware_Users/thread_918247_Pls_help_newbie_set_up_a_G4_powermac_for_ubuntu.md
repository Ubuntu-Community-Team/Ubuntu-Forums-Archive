---
title: "Pls help newbie set up a G4 powermac for ubuntu"
date: 2008-09-12
forum: Apple Hardware Users
---

### Post by jazzop on 2008-09-12
Situation:  I was just given two Powermac G4 800DPs w/ 1.5GB RAM each for free.  They have no hard drives, keyboards, or mice.  The last time I touched a Mac was in 1985, seriously.  I threw a HD in one and it boots up to a screen with a flashing question mark inside a file folder icon, so I suppose that's a good sign, given that there's no OS installed yet.

Goal:  Install Ubuntu on each and add them to my growing BOINC farm.  They will not be used for anything other than running BOINC 24/7.

Questions:

1.  I suspect that the lack of an Apple keyboard/mouse is going to be some kind of obstacle.  Judging from the connectors on the back of the machine, Apple must use USB (or Firewire?) input devices.  I have a generic USB kb & mouse; but at the current no-OS configuration, they do not appear to be active.  Any advice on making that work?

2.  I am downloading the 6.06.1-alt-ppc .iso right now.  Will I be able to use aptitude or the gnome updater to upgrade after install to the newer communty distros?

3.  Should the Mac boot directly from the CD?  Do Macs even have a PC-like BIOS and if so, how can I get into it?

---

### Post by cyberdork33 on 2008-09-12
get the ppc iso and burn it (slowly... old macs are notorious for having picky cd-roms). hold c on the keyboard after turning it on and it should boot the cd. (you can also try holding alt). Also, I'd get a newer release than 6.06 with a G4...

You can boot into the Open Firmware. There are some boot key combos here:
[http://www.namenerds.com/irish/granny.html](http://www.namenerds.com/irish/granny.html)

Some of them require the Command / Apple key. The Win key might work in its place. (also option is the same as alt)

---

### Post by gaussian on 2008-09-12
Answering only parts I know how to answer:
> 
2.  I am downloading the 6.06.1-alt-ppc .iso right now.  Will I be able to use aptitude or the gnome updater to upgrade after install to the newer communty distros?


Yes, you should be. I did it from 7.04 to 7.10 to 8.04.

> 
3.  Should the Mac boot directly from the CD?


Yes, hold down C when booting.

> 
 Do Macs even have a PC-like BIOS and if so, how can I get into it?

Yes, it is called Openfirmware. You hold Command-Option-O-F down  when booting. Don't know how to do that with a non-Apple keyboard.

---

### Post by jazzop on 2008-09-13
Thanks.  The "c" option at boot got me into the ubuntu CD.  It took me 30 minutes to figure out how to manually open the CD tray to get the disc in there!

Now I get an error during installation at the partitioning step:

"No NewWorld boot partition was found.  The yaboot boot loader requires an Apple_Bootstrap partition at least 819200 bytes in size, using the HFS MacIntosh file system."

Surely I don't have to have MacOS on the hard drive in order to install Linux?!?

---

### Post by Astinsan on 2008-09-13
Here are the steps to do the open firmware boot. For some reason your system isn't looking at the cd drive to boot from. Who knows what drive it is looking at.

Restart the computer and hold these keys: Command-Option-O-F

This asks the computer to start in Open Firmware.

type: "boot cd:,\\:tbxi" no quotes

This should load the cd. 

In case anyone doesn't know you can eject disks by holding the mouse button when powering on or during warm resets. Right after the cord sound (bong)

These tips also work for systems with non apple firmware cd rom and rewritable disk drives. (IE basicly Blue and white and sawtooth)

Sorry I didn't see the post earlier... Not many PPC's run Ubuntu. Hence the lack of pre built isos. 


Also if your disk doesn't boot you can try these tips posted by another ppc mac person running into issues. 

[http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html](http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html)

---

### Post by pxwpxw on 2008-09-13
> **jazzop said:**
> Thanks.  The "c" option at boot got me into the ubuntu CD.  It took me 30 minutes to figure out how to manually open the CD tray to get the disc in there!

Now I get an error during installation at the partitioning step:

"No NewWorld boot partition was found.  The yaboot boot loader requires an Apple_Bootstrap partition at least 819200 bytes in size, using the HFS MacIntosh file system."

Surely I don't have to have MacOS on the hard drive in order to install Linux?!?


When you run the partitioner, if you select the option to use the whole disk, or use largest free partition, then let it proceed automatically, it should create the small boot partition as well as root and swap. It does not show you the boot partition at the time, but its there.
If you did that and it has failed to create the boot partition, then it is likely the drive is using an unsuitable partition map (apple partition map is best for a g5) or no partition map - I am not sure but think the partitioner should be able to initialize a map if there is none.
You don't have to have Macos, just the small boot partition for yaboot, 
"apple" just refers to the partition type/name.

---

### Post by Bikerbob on 2008-09-13
Well I think there are quite a few ppc running ubuntu .. but I unfortunatly think that not many of them come to the forums and participate. SO a much smaller user base and few of those posting..means..

Anyway as you can see in my signature I am running the exact machines you have and I have 804 on them running like a top.. works great.. and I am also running boinc as well.. really kewl with the smp kernel so that you can run two tasks at the same time.

As thats all that you are using it for.. it will be np. IF you really wanted you could just run boinc from the cli and that would allow you to run it even faster.

James

---

### Post by jazzop on 2008-09-13
> **Bikerbob said:**
> As thats all that you are using it for.. it will be np. IF you really wanted you could just run boinc from the cli and that would allow you to run it even faster.

Eventually this is what I will do, but I am more comfortable using Gnome (I used to prefer KDE, but I am converting) as the GUI is easier to manage upgrades and configure the systems.

> **pxwpxw said:**
> When you run the partitioner, if you select the option to use the whole disk, or use largest free partition, then let it proceed automatically, it should create the small boot partition as well as root and swap.

This is what I ended up doing.  I originally wanted to preserve an old Windows partition on the HDD because I didn't know what data might have been on it that I might want to save.  But since this HDD was just laying around for a year, I figured the data weren't that important anyway if I didn't miss it.  I reformatted and used the full disk for the installation and it worked fine.  I now have a booting, working installation!  My very first Mac!

> **Astinsan said:**
> Restart the computer and hold these keys: Command-Option-O-F

Easier said than done with a keyboard that has neither "command" nor "option" keys. (See the OP)

---

### Post by Bikerbob on 2008-09-13
On a std 102 windows keyboard  ctr is control windows key is Command and ALT is Option.

I use a KVM switch between my pc and mac and use a Logitech keyboard for them both. Works great.

James

---

### Post by Astinsan on 2008-09-14
More tips:
Windows key and alt are command and option for non - mac keyboards. Not that many use the mac keyboards. Those tiny keys on some of them are lame.

I use PPC ubuntu on a old b&w g3 with a upgraded processor (g4) so it kinda like a sawtooth. 66mhz bus hurts the speed of this machine but its all good. Seems to do its thing just fine. I recommend getting the video card running properly. This will speed up the display rendering 2d and 3d dramatically.

---

