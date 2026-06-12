---
title: "cannot for the life of me boot this mac from cd"
date: 2008-09-14
forum: Apple Hardware Users
---

### Post by darkenemy on 2008-09-14
I have been trying everything i can find to boot my PowerBook G4 Titanium from a live Ubuntu cd.

i have tried

using a Ubuntu 7.10 cd
using a Ubuntu 8.04 cd
using a fedora 9 dvd
using a OpenSUSE dvd
(i made double sure all the checksums lined up for these, as well as that they were all PPC versions)

when i boot the mac and hold down "c" nothing happens, it boots to regular osx

when i hold down the option key to see the graphical boot loader, it only shows a picture of a drive with the osx logo on it- no icon of a cd

when i go to system preferences>startup disk there is no option for booting from cd, the options are booting from osx, os9, or from a network thingy

i have not found a way to attempt booting the cd from single user mode

i have tried the "boot cd:,//tbxi" command in open firmware mode, the response of which is "can't OPEN: cd:,//tbxi"

the mac does recognize the Ubuntu cds, although it would, after about 30-90 seconds, reject the fedora or OpenSUSE dvds when i put them in.

i hope its not me, cuz i just cant get this to go.

ANY help will be greatly appreciated, i really wanna get linux on this laptop.

if it is any help, my version of osx is 10.3.9
it is the 550 MHz PowerPc G4 Titanium Powerbook

---

### Post by pxwpxw on 2008-09-14
**darkenemy**
> 
 i have tried the "boot cd:,//tbxi" command in open firmware mode, the response of which is "can't OPEN: cd:,//tbxi"


that should be with backslashes and a colon.
```

0> boot cd:,\\:tbxi

```

If thats no good, have you checked in macosx that it can see all the files on the ubuntu 804 cd.

If you have the macosx dvd, does that boot ok?

---

### Post by darkenemy on 2008-09-14
when I type "boot cd:,\\:tbxi" into the "0 >" prompt in open firmware mode it responds "bad READ-1 can't OPEN: cd:,\\:tbxi"

of the 4 different discs i have burned, the only one the mac recognizes the files on once it has booted is the gutsy 7.10 ubuntu cd.  by this i mean that i can click on its icon on the desktop and see actual files.  the hardy 8.04 cd shows up on the desktop but is blank in the finder window: it shows no files.  as previously stated, neither the fedora or OpenSUSE dvd would even stay in the drive for long, let alone be recognized.  

for the test in open firmware mode above, i used the gutsy 7.10 cd.

i do not have a macosx cd of any kind.  i bought this computer on ebay, and i also have absolutely no warranties of any kind.

i just want to find some way to get the macosx off completely.  it is so slow i can no longer make use of the computer.

---

### Post by mkvnmtr on 2008-09-14
Maybe this will help. When you restart and first hear the tone press the option key. Don't let it up until you see first the Mac icon come up and then the Linux icon come up. Wait for the ball to quit spinning and click on the Linux icon.It takes a while if you let up on the key too soon it will boot Mac.

---

### Post by darkenemy on 2008-09-14
when i hold down the option key there is no linux picture or cd icon.  there is only the mac icon for a hard drive with a macosx emblem in the lower right hand corner of the hard drive icon.  there is a refresh icon i can click and a button to execute my choice, shaped like a arrow.

there is nothing else in the graphical boot loader that appears when i hold the option key on startup.

---

### Post by tiresia on 2008-09-14
How did you burn your Installer-CD?

---

### Post by darkenemy on 2008-09-14
i downloaded the .iso image from ubuntu.com (here specifically [http://cdimage.ubuntu.com/ports/releases/7.10/release/](http://cdimage.ubuntu.com/ports/releases/7.10/release/)) and used brasero to burn it by opening brarsero, choosing burn image, and choosing the path of the file (on my desktop).  i also went to properties and clicked the slowest burn speed to make extra sure there are no errors.

---

### Post by tiresia on 2008-09-14
Can you please check what kind of medium your optical drive can read/write? According to everymac your powerbook can read only DVD/CD-RW. Are you using DVD+R?

Anyway, if you can read in MacOSX the CD with Ubuntu 7.10, there must be another problem. You could try to install from a USB Memory, if you can't find a solution. I believe, that there must be something wrong with the file system on the CD. (Otherwise why can't OSX see Ubuntu Hardy?) 

Can you burn a CD with the PowerBook?

---

### Post by darkenemy on 2008-09-14
the ubuntu ppc 7.10 cd i am using is burned to a cd-rw, that i blanked before buring it with brasero as described above.

the powerbook both cannot burn cds, and cannot boot from a usb drive.  it was made in 2001 according to my open firmware mode readout, and that was long before booting such booting was practical.

i have actually tried burning the image to a usbdrive and booting from that, it doesnt work..

the dvds i used as well that had fedor 9 and OpenSUSE on them were dvd+R.
and yes, they didn't read.  although i am sure it does read dvds, as i have some that play fine on the mac.

as said before, the ubuntu cd's, burned on cd-rw's on a different computer running ubuntu computer and the brasero program, are readable on the mac, just not bootable.

---

### Post by tiresia on 2008-09-14
> **darkenemy said:**
> the dvds i used as well that had fedor 9 and OpenSUSE on them were dvd+R.and yes, they didn't read.  although i am sure it does read dvds, as i have some that play fine on the mac.

Ok, at least we know, why you can't start from those DVD (Fedora and SUSE). Your optical drive can read DVD-R but not DVD+R

> **darkenemy said:**
> as said before, the ubuntu cd's, burned on cd-rw's on a different computer running ubuntu computer and the brasero program, are readable on the mac, just not bootable.

Can you please have a try burning the image with wodim (from terminal), may be as root or with sudo

```
sudo wodim -v filename.iso
```

---

### Post by darkenemy on 2008-09-14
i burned a the cd-rw (after blanking it with brasero) using the "sudo wodim -v filename.iso" command as you instructed. (boy did that take a long time)

the only catch is, i accidentally deleted the ubuntu 7.10 ppc file permanently, and the file .iso i burned that i still had around was teh .iso file for ubuntu hardy ppc 8.04. 

naturally, this one does so up on the desktop of my mac, but is shown to be a blank folder when opened, although the desktop icon does bear the title "Ubuntu_PowerPC_hardy"

additionally, when i try holding the option key on the boot, well, same old beans.

now it looks as though i have to re download the ubuntu 7.10 file and try that using your suggestion of the wodim command.

unfortunately i cannot do this tonight, as my internet connection cannot download the .iso from ubuntu that quickly.

tomorrow then, i will burn the 7.10 file and see if that works.  until then, thank you very much for all your help (2nd plural usage here)

---

### Post by darkenemy on 2008-09-14
so, i actually just had the most disasterous 30 seconds of my life.  i was talking to someone in my room about this post, and just after i submitted the last post, i gestured with my hadn and spilled a nalgene FULL of water all over the keyboard, right on the mac.  so i quickly unplugged it and took out the battery, but this was not before the screen went to black and white stripes and the computer tuned off.  right after this happened, in my panic i held the computer by the two edges of what would be the hinge of the computer (the top of the monitor and the bottom of the keyboard parts of the computer) in order to drain out some of the water as quickly as possible.  then came the next cataclysm.  the monitor snapped right at the connection to the computer.  

i immediately put it on a fan and will not even think of plugging it back in until it is BONE DRY.

this sucks. i no longer have a mac it seems.

well, problem solved! thanks for the help

---

### Post by Bikerbob on 2008-09-18
seems like you know your way around linux, also that the hardware itself is working fine because you can read cd's once they are in, and the OS X is running etc.

I have run into issues with cdrw? Anychance that the notebook drive does not like the cdrw medium?

images are .iso's so they can be burned on any computer.. you are correct to slow it down to 4x so that almost any cdrom can read it. I would try it again on a cdr 804 ubuntu ( I say that because I have had issues with other builds)

my 2c

James

---

### Post by japadamaray on 2008-09-18
cd-rw disks have never booted for me. i always use cd-r disks.

---

### Post by FredSambo on 2008-09-18
I have the exact same issue with my tibook (onyx), the hardy cd just won't boot, and I know it isn't the burn because it boots fine on my iMac DV g3 (400Mhz).

---

### Post by Bikerbob on 2008-09-18
FredSambo that is not really true as all cdroms drives are not equal. I have burned .iso's that I have used on my pc no problems .. CDr is the only media that is always the same.. no ups or downs.. but I always suggest to burn at 4x just to be safe.

FredSambo - do you have other cds that will boot? or can you not get any cd to boot on that tibook?

James

---

### Post by FredSambo on 2008-09-19
> FredSambo - do you have other cds that will boot? or can you not get any cd to boot on that tibook?

Yes, the Kubuntu 8.04 Live CD boots fine, actually (with no X but that is another matter)!  HAHA!  I have burned the regular ubuntu ppc install disk three times on three different burners at 4x and still no go.  The version of the alternate install disk doesn't boot either, it gives the same read error in open firmware mode as mentioned above.

I've given up running Ubuntu on this machine, although the funny thing is my old copy of the Edgy Eft Live CD boots fine, goes straight into x with the proper screen resolution and everything, no tweaks!  I tried dist-upgrading all the way up to Hardy but that gave some pretty interesting results in the end, to say the least.

---

