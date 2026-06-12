---
title: "okay. this is the last straw!!!!!!!!"
date: 2007-07-10
forum: Apple PPC Users
---

### Post by platinum on 2007-07-10
alright everyone. this imac is about to be thrown into a pool of gasoline and set on fire if i don't get it working

i burned all of the discs with my PC (which many people here seem to have done as well), using NERO or other good program (others have also done), burned them SLOWLY (2x), md5 all the images, and they are without flaw.

:x :x :x

here's the deal. i have this:
imac G3 400mhz, 512mb ram
slot loading cd rom drive
running mac os 9.2
open firmware is up to date
reset pram and nvram

i want to install linux on this damn thing because mac os 9.2 blows!!!! i have no access to buying os x on cds, and i'm tired of downloading and burning discs, i've used so many.

i have burned so many damn cds with ubuntu, xubuntu, kubuntu, from several different mirrors, and i get the same damn problem: i CANNOT boot off of a cd! 

i have tried all of this with the internal CD drive and an external one that is KNOWN TO WORK PERFECTLY FINE:

- press and hold C with the disc in either drive
- press and hold CMD+OPTION+SHIFT+DELETE to boot from external drive

i will try to explain this as best as possible: in all of these cases the screen goes white for a second or so, shows a folder with a blinking question mark, but all of the colors are inverted. like black is white, white is black.

so, i then try this:
- press and hold OPTION key to get to the graphical open firmware thing to choose which device to boot from. with either drive, the linux cd shows up as an option, so i select it

then it does this!
---[[IMG]http://img224.imageshack.us/img224/9378/pickersy9.th.jpg[/IMG]](http://img224.imageshack.us/my.php?image=pickersy9.jpg)

this thing is driving me crazy. all i got it for was a spare machine my dad can use to check his email and for me to play basic games and just an extra machine to have when i need one.

this thing is gonna stare down the barrel of my shotgun if i can't get it to work, and i'll post it on youtube!!!!!!!!!!!!

help, for the sake of this imac's life, help!

---

### Post by lisati on 2007-07-10
Please forgive me if I state the obvious, but a common source of headaches seems to be burning the image as a data disk by mistake. On your CD burning software there should be an option named something like "Burn image".

---

### Post by platinum on 2007-07-10
don't worry. i know how to burn an iso image.

i burned the image (several of them, several times) like you are supposed to, so it burns the contents of the iso file, not just the iso file as is.

no worries lisati, i can burn an iso image :)

but i can't get this imac to work!!!!!!!!!!

help!!!!

is there like a light linux i can try? something like puppy linux, or damn small linux, or something, that way i don't have to wait 45 minutes to an hour or so for a 700mb iso to download just find that it doesn't work?

---

### Post by johng4 on 2007-07-10
My g3 iMac had an issue, however it was from the final series of iMacs (it was a "Snow" iMac berry) before the eMacs.

I did the standard "Hold C" however I didn't use the liveCD disk.  I had a serious issue getting that to work, and it did things that puzzled me.  I got the alternative-install CD image, which uses a text based installer to install the system.

Makes life easier.  I believe my cpu is a 600Mhz with 256MB RAM.  I've recently did a distribution upgrade to Feisty from Edgy.  No problems, runs even better now in fact.

Try using the alternative CD, and make sure you are using the correct image.  Don't give up yet.. I've seen iMacs with worse stats that that work just fine.

---

### Post by platinum on 2007-07-10
well, the current ubuntu discs are live AND install discs.

is the alternate disc different?

---

### Post by rccharles on 2007-07-11
I do not recognize your situation.  You might try looking at these posts.
 You need to modify xorg.conf. See:
[http://ubuntuforums.org/showthread.php?t=219532](http://ubuntuforums.org/showthread.php?t=219532)

Mac G3 modem install Howto
[http://ubuntuforums.org/showthread.php?t=355205](http://ubuntuforums.org/showthread.php?t=355205)

------------

Can you still boot from Mac OS 9?  I'd try booting from one of your original cd's if you still have them.  At least, this will sort out whether you have a hardware problem or some problem with the Ubuntu cd.

Here is a source of Mac OS cd's:
[http://www.applerescue.com/](http://www.applerescue.com/)


Robert

---

### Post by kerry_s on 2007-07-11
Try debian, ubuntu likes to butcher alot of older system drivers.

[http://mirrors.kernel.org/debian-cd/current/powerpc/iso-cd/debian-40r0-powerpc-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/powerpc/iso-cd/debian-40r0-powerpc-xfce-CD-1.iso)

besides there dropping apple ppc line anyways, at least with debian you can always be up to date by using lenny/sid repos.

---

### Post by pxwpxw on 2007-07-11
> **platinum said:**
> well, the current ubuntu discs are live AND install discs.

is the alternate disc different?

Yes, text based menus avoid graphics problems during the install.

If you have the macos9 install cd, can you boot the iMacG3 from that?
Can you connect the iMacG3 to the internet from macos9 and at what speed?
Can you display the files on the burned ubuntu cd when mounted in macos?

Please confirm that you are using a 
 Mac (PowerPC) and IBM-PPC (POWER5) iso 
  from ubuntu at this url
 [http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)
 or if not, where from (url)

---

### Post by lisati on 2007-07-11
> **platinum said:**
> don't worry. i know how to burn an iso image.

i burned the image (several of them, several times) like you are supposed to, so it burns the contents of the iso file, not just the iso file as is.

no worries lisati, i can burn an iso image :)

but i can't get this imac to work!!!!!!!!!!

help!!!!

is there like a light linux i can try? something like puppy linux, or damn small linux, or something, that way i don't have to wait 45 minutes to an hour or so for a 700mb iso to download just find that it doesn't work?

That's cool. Hope your having some success......

---

### Post by platinum on 2007-07-11
well, i  tried the alternate cd, same problem as descibed above. i'll try debian. and boy, if this thing doesn't work....

i'm gonna......... :x

---

### Post by joninkrakow on 2007-07-11
I can think of two things--either you CD player is after-market, without the Apple ROM to boot it, or you really are not burning these things properly. Are you using OS X to burn them? If so, you ought not choose "Burn..." and select a file from the Finder. I did that, and it wouldn't boot. I had to drag the ISO image to Disk Utility's sidebar, select it, and then choose "Burn..." Don't know why, but it made the difference. But again, this is only OS X, not Windows, and this is only my experience.

-Jon

---

### Post by platinum on 2007-07-11
i am burning these on my pc with nero, and i know how to burn an iso image properly.

the cd drive inside the imac is apple brand.

the external drive shouldn't matter because it boots from the os 9 discs fine, but i want linux on this thing!!!!

---

### Post by shawnhcorey on 2007-07-11
I think the problem is that the newest versions do not have the correct drivers in them.

I had to re-install recently but I couldn't use the 7.04 disk; it would get to the first brown screen and hang.  I was able to install from the alternative but I don't have any sound. See:
[http://ubuntuforums.org/showthread.php?t=498660](http://ubuntuforums.org/showthread.php?t=498660)
[http://ubuntuforums.org/showthread.php?t=281100](http://ubuntuforums.org/showthread.php?t=281100)
(I also do not have any idea where to get the correct drivers.)

I don't blame you for wanting to give up.  I have started looking into other distributions to see if there is anything better.

---

### Post by hardyn on 2007-07-11
if you going to just set it on fire anyway... could you send it to me instead :p

---

### Post by platinum on 2007-07-11
IT WORKS!!!! I GOT IT TO WORK!!!!!!

it took some thinking, but it works!!!!!

i will post a quick how to on this forum on how i did it so others who have similar problems can fix them!!!! :D :D :D:D:D:D:D:D

---

### Post by thaibox on 2007-07-12
How did you get it to work?

I hold down the option key and it recognizes the disk and even shows a little tux guy in the corner.  when I select it and press enter, it goes to another boot option screen that shows the same stuff but is all jacked up (kind of pixelated).

I also know that the external firewire DVD drive I have will boot b/c I tested it with the os x install disk.

iMac G4 
1GHZ, 256 MB, broken SuperDrive (thus the external DVD)

I'm downloading Fedora 7 right now to see if that will work.  Please post your method for working this b/c I'd rather have Ubuntu to match my other computer.

Thanks

---

### Post by tgalati4 on 2007-07-13
I have heard that some older mac drives will only read 650MB CD's.  If you are burning a 700MB CD then your drive may have trouble reading it.  The solution is to check your local goodwill store for old CD-RW 650MB disks and erase them, or some unused 650 MB CD-R's that are harder to find.

---

### Post by pxwpxw on 2007-07-13
> **thaibox said:**
> How did you get it to work?

I hold down the option key and it recognizes the disk and even shows a little tux guy in the corner.  when I select it and press enter, it goes to another boot option screen that shows the same stuff but is all jacked up (kind of pixelated).

I also know that the external firewire DVD drive I have will boot b/c I tested it with the os x install disk.

iMac G4 
1GHZ, 256 MB, broken SuperDrive (thus the external DVD)

I'm downloading Fedora 7 right now to see if that will work.  Please post your method for working this b/c I'd rather have Ubuntu to match my other computer.

Thanks

There is a fatal problem with external firewire CD drive and the ubuntu install cd (desktop or alternate), it is this: Although the Applemac firmware recognizes a bootable disk and will try to boot, the CD boot code is configured to carry on from a CD drive, and not an external firewire drive. In short, a CD for booting from an external drive would need to be configured for that arrangement, not from an internal CD drive.
The Macosx install CD is apparently configured to run on either internal or external drives.

Will be interesting to see if Fedora (or anyone else) can do better, and what **platinum** did to get it to work.

If the CD won't work, you can do an hd-media or network install from an iso, after partitoning for dual booting.

---

### Post by thaibox on 2007-07-13
Unfortunately, the Fedora DVD didn't work either.  I guess I'll have to try from network.

I have already backed up the iMac and want to just wipe out the hard drive completely.  How do I set it up for network install?  My other computer is an HP laptop running Feisty desktop edition.  I appreciate your help and I hope this last one works...

---

### Post by thaibox on 2007-07-13
pxwpxw,

I've been reading your other posts on how to do this, but it just isn't clear to me.  I hate having to have my hand held through this process, but it looks like that is what I need.

Anyway, I'll keep chipping away at it until I get it.

---

### Post by pxwpxw on 2007-07-13
> **thaibox said:**
> Unfortunately, the Fedora DVD didn't work either.  I guess I'll have to try from network.

I have already backed up the iMac and want to just wipe out the hard drive completely.  How do I set it up for network install?  My other computer is an HP laptop running Feisty desktop edition.  I appreciate your help and I hope this last one works...

You should keep a minimal macos partition to allow a reinstall or rescue if needed. This is because you use the macos partition for the netinstall or hd-media boot files. If you have space for a 5GB macosx partition that should be plenty, a little more wold be useful, and the easiest way to do it is to reinstall macosx first, but on a  partition made using Disk Utility, leaving the remaining space as Apple_Free, then there is no problem with the ununtu partioner having to resize the macos partition. But I don't know the details of your system, or if you are able to reinstall macos.
The main thing is you must have a macos partition to keep an alternative boot for reinstall/rescue, or be able to reisntall  macos.
If you cant reinstall macos, you will need to resize the existing macos partition from the ubuntu installer, thats possible.

The Netinstall link in my signature below outlines the procedure, best check that out before doing anything drastic.
Edit:: just rereading the thread, if you can reinstall MacosX from the external drive that would be the way to go.

---

### Post by ajmctaggart on 2007-07-13
Okay, I totally understand, I nearly through a powerbook pismo out the window with this situation.  More than likely, it's something ridiculous, and more than likely it IS NERO...

If you have access to a mac, USE DISK UTILITY (IT KNOWS WHAT APPLES LIKE AS BOOT UP DISCS, CAUSE ITS MADE BY APPLE) convert the image from a iso to a dvd/cd master (.cdr)...let the conversion do it's thing, then burn the disc from disk utility by clicking the .cdr and then click burn disc...no drag and drop in the finder and all that.

USE THE NON-LIVE CD, USUALLY X11 AND OLD MACS...DOESN'T WORK BEST OUT OF THE BOX (just my experiences)

If you don't have another mac, with os x.? then I don't know what to tell you...the damn yaboot boot loader wont install via firewire so so much for target disc, unless you somehow get yaboot on a tiny partition first...I don't know how though, perhaps Yellow Dog Linux' distro would be an easier install most certainly, but the distro is not up to par w/ ubuntu...

Good Luck, If you do have another mac, this process shouldn't be as hard...

---

### Post by rccharles on 2007-07-15
> **ajmctaggart said:**
> 
If you have access to a mac, USE DISK UTILITY (IT KNOWS WHAT APPLES LIKE AS BOOT UP DISCS, CAUSE ITS MADE BY APPLE) convert the image from a iso to a dvd/cd master (.cdr)...let the conversion do it's thing, then burn the disc from disk utility by clicking the .cdr and then click burn disc...no drag and drop in the finder and all that.
.

another alternative...
Macintosh-HD -> Applications -> Utilities -> Terminal

hdiutil burn name-of-iso-image.iso

Robert

---

### Post by schmod on 2007-07-16
Remember -- this guy's using Mac OS 9.2

For you young whippersnappers, 9.2 didn't have any sort of terminal or command line shell.  

I don't actually remember if its Disk Utility app could burn CDs...

---

