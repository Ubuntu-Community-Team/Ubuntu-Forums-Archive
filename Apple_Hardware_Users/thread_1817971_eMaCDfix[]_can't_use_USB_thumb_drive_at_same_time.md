---
title: "eMaCDfix[?] can't use USB thumb drive at same time"
date: 2011-08-04
forum: Apple Hardware Users
---

### Post by c4c on 2011-08-04
Original 700 MHz, G4 eMac, 256 MB RAM, running Ubuntu 10.04/Gnome wouldn't mount CDs (although it did just fine mounting and unmounting a USB thumb drive from the get-go).

First there was the problem of the CD Drive popping out for maybe a 1/2 second before zipping right back in. I was using the "Eject" button on the original keyboard. That problem was solved by adding this command "dev.cdrom.autoclose = 0" to /etc/sysctl.conf (thank you teachop).

To get the CD in the drive to mount, I ended up executing this command in Terminal: udisks --poll-for-media /dev/hdc (thanks plecebo.mc). The CD appeared on the Gnome desktop and was accessible. Apparently this same command in works for mounting and unmounting. I then went on to create a Taskbar Launcher with this command (thanks JDFIght).

[for the benefit of noobs like me] I hovered over an empty area on the top panel/taskbar, hit the F12 key and chose Add to Panel. I selected Custom Application Launcher and clicked the +Add button. I left Type as Application and typed in "Mount/Unmount CD" in the Name text box, and typed the command "udisks --poll-for-media /dev/hdc" in the Command text box. I then clicked the Launcher icon and chose "cdrom_unmount.svg" from usr/share/icons/Humanity/devices/16/ and clicked the "Open" button.

Now to test mount. I closed the Terminal, hit the Eject button on the Apple extended (104 key?) keyboard, inserted a CD, hit the Eject button on the keyboard again and then hit my new CD icon (Launcher) in the taskbar - Viola! It mounted the CD! Now to test the unmount. I used the (F12) context menu to "Eject" the CD and hit the CD icon again. Success! I then hit the Eject key to close the CD Drive. It stayed close. I realized I had done it. Then for the benefit of future users of this machine I hovered over the CD icon, pressed F12, selected Properties and added "(press after inserting/removing CD)" to the Comments text box.

After all that, seems I have a new problem. I can't mount a CD and a USB thumb drive at the same time - the system seems to go crazy... The mouse cursor freezes (and unfreezes, but just for a couple of seconds) and neither the CD or the USB thumb drive gets mounted. 

The CD Drive will not eject via the keyboard button of course and my new launcher doesn't seem to help mount (or unmount?) either the CD or the thumb drive. If I pull the thumb drive out (probably not a good idea) of the side keyboard connection and stuck it in a USB port on the side of the eMac (and vice-versa) the thumb drive will mount, but the mouse will still be mostly frozen, rendering the USB thumb drive pretty unuseable through the GUI.

Is there a change I can make in one of the commands I listed above (or something else I can do) to make a CD and a thumb drive mount at the same time? Am I just taxing this PPC G4 machine (with too little RAM) too hard? Should I cut my losses and just include instructions not to have a thumb drive and a CD in the eMac at the same time?

Thank you in advance to anyone who can give me something(s) to try. I figure maybe two weeks max to play before I give these away [this what what I normally do - have two of these right now - I wouldn't be giving them away out of frustration]. :)

---

### Post by rsavage on 2011-08-04
One day if I'm really really bored I may look into why the audio/video/(I haven't got any data CDs to try! Do these not work either?) CDs don't automount. It is never something I need though, besides you don't need to mount them to play them. Certainly Gnome-mplayer works fine without mounting them.
 
A possible fix could be:
 
At a terminal type: 
 
```
 
hal-disable-polling --device /dev/hdc --enable-polling

```
 
or something similar like "hal-disable-polling --device /dev/cdrom --enable-polling"
 
No access to a mac at the moment so can't try this myself.

---

### Post by c4c on 2011-08-15
Data CDs didn't mount before either, but are just fine now (that was how I discovered the problem in the first place trying to add some files to one eMac via CD when all my ports were busy with other machines). Tried your suggested command above, got back "Cannot find device /dev/scd0." I didn't do anything more than that, as I discovered a work-around...

To have a CD and a USB thumb drive mounted and accessible at the same time, I just need to make sure the CD is mounted first, then the USB thumb drive. Then they must be unmounted in reverse order; the thumb drive and then the CD. As long as that little "rule" is followed, both are fine mounted at the same time

Sort of silly, I know. I included a note about CDs and USB thumb drives usage on these two eMacs and recorded a couple of small .ogv showing the process to put up on our (planned) support section. Don't know if I'll ever install Lucid on more than two of these - I had actually never seen a real live eMac before - but it's been fun.

Was actually going to mark this solved [and maybe I still should?] when I got an email from a recipient of a completely different computer that runs Lucid with the same problem (CD tray flying in and out). This is a Compaq Presario 6000, manufactured around the same time as the eMacs, (possibly with the same CD Drive manufacturer?) but the machine is no longer with me and the user is really, really new... so I'm walking her (very slowly) through the steps I did on the eMac via email to see if the same fix(es)/work-arounds will work for her. Haven't gotten to mounting yet...

---

### Post by c4c on 2011-08-29
Received another original eMac with the same specs [G4 PPC, 700 MHz, 40 GB HD, 256 MB RAM, etc.] and installed Ubuntu 10.04 Lucid on it - using it to write this now. Only difference is this one didn't come with the white matching keyboard and mouse, so using black ones that came with iMacs.

I can confirm the exact same CD problems [tray flying in and out, CDs not mounting] and the same fixes listed above to cure. When the fixes are applied, the user just has to remember to hit the CD icon in the system tray to mount/unmount CDs and when using a USB thumb drive and CD at the same time, CD need to be mounted first, then the USB thumb drive and then they must be unmounted in reverse order.

The Compaq user of the same era hasn't gotten back to me yet, so I don't know if her CD issues are similar beyond the tray flying in and out. But, I believe any original eMac user (and maybe others can take a look and see if some part may help their issue) can bank on the fixes above.

Thank you! :P

---

### Post by c4c on 2011-08-30
I have an older (1999) 333MHz *tray-loading* iMac [had Linux MintPPC 9.2 on it, no CD/USB thumb drive work-arounds needed]. Just to see... I installed Ubuntu 10.04 on the Tray-Loading iMac. Lo-and-behold CDs would not mount until I did the tricks listed in my first post!

There are a couple of differences though. The CD tray did not fly in and out - but, it's a different kind of tray with a button on the front and it seems to lock into place when closing. A USB thumb drive and CDs *can* be mounted and unmounted *in any order* without making the system go crazy. But, when mounted together, the icon of the last mounted will cover the first. To make it easier to see what I was doing, I had to drag one below the other.

I don't remember the CD weirdness  on *slot-loading* iMacs. Does anyone have a slot-loading "gumball" with Lucid on it that can confirm (or deny) any of the things listed above? We gave several away with Lucid loaded on them - I'd like to update our (yet to do) support or documentation web pages with this info.

---

### Post by rsavage on 2011-08-31
For your latest machine I think you'd be better installing Lubuntu [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792).  It's quicker than mintppc to load.  It also doesn't have many applications doing the same thing so is less confusing.  The ubuntu software centre also runs really well under it (because of the lack of the  apt-xapian-index package - you really should remove this from any version of ubuntu imho).

I bet debian/mintppc still uses hal to detect cds.  That is why I suggested you try enabling hal polling.  If /dev/sd0 doesn't work then try something else like /dev/cdrom or /dev/hdx etc.

---

### Post by rsavage on 2011-10-13
> **rsavage said:**
> 
A possible fix could be:
 
At a terminal type: 
 
*hal-disable-polling --device /dev/hdc --enable-polling*
 
or something similar like "hal-disable-polling --device /dev/cdrom --enable-polling"

 
Enabling polling does cause problems with some people [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/801853](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/801853) . If it causes problems with you then disable polling again with the command:
 
```

hal-disable-polling --device /dev/hdc

```

---

### Post by rsavage on 2012-08-08
Bumping an old thread here (forgive me mods, but this thread is linked on the PowerPC wiki pages).  

I have a solution to the lack of automatic CD polling in 10.04.  It is a bit extreme....upgrade the kernel!  Basically you want a kernel with the newer pata_macio module.  This requires all sorts of adjustments though so this solution is not for everyone.

These instructions will install the kernel from 11.10 Oneiric into Lucid.  I'm not going to describe things in minute detail as most of it is already in the FAQ and Known Issues pages.

First thing to do is open the yaboot.conf file and remove any hda references (see the known issues for 11.10).  So for example, I changed the boot and root lines to:

boot="/dev/disk/by-label/bootstrap"
root="UUID=big-long-number-000"

If you need to find the UUID for your partition use the command "sudo blkid". Don't forget to run ybin!

Oh, I should say some people may also have to add an ofboot line to yaboot.conf.  If you get a black screen on reboot when you next run ybin this is why.

Then run the command 

```

echo pata_macio | sudo tee -a /etc/initramfs-tools/modules

```to make sure that pata_macio is used.

Next open the file /etc/apt/sources.list and add the line:

```

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric-updates main

```I think the oneiric-updates will include security fixes too, but that is something I need to check.  If you want to be certain you can also add

```

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric-security main

```Since we don't want to update all packages we need to now define the default version of ubuntu. 

```

gksudo gedit /etc/apt/apt.conf 

```and add the line

```

APT::Default-Release "lucid";

```Now we need to pin the kernel meta packages.

```

gksudo gedit /etc/apt/preferences

```And add (for the 32 bit non-SMP)

```

Package: linux-powerpc
Pin: release n=oneiric
Pin-Priority: 991

Package: linux-image-powerpc
Pin: release n=oneiric
Pin-Priority: 991

```Now sudo apt-get update.  When you next run synaptic or the update manager it should want to upgrade the kernel.  Do so and reboot!

The cdrom drive is now /dev/sr0 and your hard drive is /dev/sda.  USB drive is now sdb.  When you insert a CD-ROM it should now mount automatically.

You follow these instructions at your own risk!!!

EDIT: Forgot to say radeon users will have to do more adjustments to enable suspend.  See FAQ.

---

