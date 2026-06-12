---
title: "I need a linux ppc live CD distro UNDER 700mb"
date: 2010-12-05
forum: Apple Hardware Users
---

### Post by pcmac55 on 2010-12-05
I need a linux ppc live CD distro no more 700mb to get data(itunes,photos)

off a dying iBook G4  running on power pc chip 

I was directed to kubuntu,

however the 

iso i downloaded kubuntu 9.10 ,can't be burned to CD as its 706MB

please advise a link for ppc live CD distro** under 700mb**

---

### Post by migs73 on 2010-12-05
Try this

[http://puppylinux.org/main/Download%20Latest%20Release.htm](http://puppylinux.org/main/Download%20Latest%20Release.htm)

Only 100mb or so, lives entirely in RAM when loaded. Fast as anything.


EDIT OOOPS a PPC for apple!! DOH didn't read thread properly. Try this thread;

[http://ubuntuforums.org/showthread.php?t=1088975](http://ubuntuforums.org/showthread.php?t=1088975)

---

### Post by pcmac55 on 2010-12-05
dont see any links for [B] ppc live CD ?

has be UNDER 700mb[/B]

---

### Post by migs73 on 2010-12-05
Found a list here;

[http://www.livecdlist.com/architecture/ppc](http://www.livecdlist.com/architecture/ppc)

Don't know much about the other distros, but at least the sizes are listed.

I'll need to keep out the Apple section of the forum!! I'm out of my depth here ;)

Hope it helps.

Mike

---

### Post by conal on 2010-12-05
If you just need this to access documents use an old version - the overize bug is quite recent. I think up to 8.10 or 9.4 worked fine but you could go all the way back to 6.10 to be sure, that was the last 'officially supported' powerpc version. Or, if you want to use a recent verison there is instructions here: [http://ubuntuforums.org/showthread.php?t=1335735&highlight=customize]("http://ubuntuforums.org/showthread.php?t=1335735&highlight=customize")

---

### Post by MisterGaribaldi on 2010-12-05
If you've got another Mac or if you have another Linux box with HFS/HFS+ Utilities installed, plug the iBook via Firewire into the other computer, and turn it on while holding down the **T** key. That'll put it into target disk mode and the HDD should just show up as another HDD on your other computer. Then, copy all the data off that you like.

---

### Post by pcmac55 on 2010-12-05
I can try that,however the damaged ibook  doesn't boot ,cuts out part way  
 
 on another ibook,not damaged one,I did burn using toast,but it wont boot from ibook,when hold C

using Disk Utility,the ISO of (Kubuntu 6.10)cannot be burned..says "no mountable file systems"

---

### Post by barbaGNU on 2010-12-06
maybe Finnix is the right choice.
CRUX PPC will work too but depends on your linux skills.

---

### Post by shawnhcorey on 2010-12-06
> **pcmac55 said:**
> please advise a link for ppc live CD distro** under 700mb**

The [Ubuntu Alternate CD]("http://cdimage.ubuntu.com/ports/releases/maverick/release/") is under 700MB.  The only difference between it and the Desktop CD is that it uses a text-based installer and the Desktop uses the GUI installer.

You may also want to check the [known issues]("https://wiki.ubuntu.com/PowerPCKnownIssues").

---

### Post by pcmac55 on 2010-12-06
> **shawnhcorey said:**
> The [Ubuntu Alternate CD]("http://cdimage.ubuntu.com/ports/releases/maverick/release/") is under 700MB.  The only difference between it and the Desktop CD is that it uses a text-based installer and the Desktop uses the GUI installer.

You may also want to check the [known issues]("https://wiki.ubuntu.com/PowerPCKnownIssues").
why is it  the ISO of (Kubuntu 6.10)cannot boot ,on ibook?

thats alot of "known issues."

so far wasted lot bandwidth downloading 2 CD versions of  Kubuntu, and [Ubuntu Alternate CD]("http://cdimage.ubuntu.com/ports/releases/maverick/release/")  none of which will boot from CD..

i give up!!

---

### Post by shawnhcorey on 2010-12-06
> **pcmac55 said:**
> so far wasted lot bandwidth downloading 2 CD versions of  Kubuntu, which dont work...

Agreed.  That's why I developed a method to boot and install from a USB drive:

[LIST]
[*][HOWTO Create A Bootable USB Drive From An ISO Image For Apple PowerPCs In Linux]("http://sites.google.com/site/shawnhcorey/howto-create-a-bootable-usb-drive-from-an-iso-image-for-apple-powerpcs-in-linux")
[*][URL="http://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware"]HOWTO Boot Apple PowerPCs From A USB Drive In Open Firmware
[/URL]
[/LIST]

---

