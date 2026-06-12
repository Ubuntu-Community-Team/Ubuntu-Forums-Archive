---
title: "Non ECC memory issue?"
date: 2011-07-19
forum: Any Other OS
---

### Post by Naiki Muliaina on 2011-07-19
Ok, an odd one!

I have always had issues installing every distro onto my PC (except SUSE oddly). I used to think it was my Eco Green hard drives (the old sector issue). I usually crash at at some point during formatting or near the end of the install when using live disks. It happens on nearly everything, Sabayon, Fedora, Scientific, Mandriva, Mageia, Salix, Zenwalk, older Ubuntu's, and various other top distros on distrowatch.

I have now tried just leaving 4 different hard drives in the PC individually, from the eco green 1 tb drives to a lowly 80 gig drive thats 8 years old. Still no joy.

When attempting to install a few distros recently I have been using text mode. It comes to a bit of a halt at 'Your memory is 'non ECC'. A quick google and sure enough my memory doesnt support ECC. Could this be the reason why I cant install anything via live cd? 

Is there any other suggestions for what could be causing every live cd to crash during install except SUSE and recent Ubuntus?

---

### Post by jeffathehutt on 2011-07-19
The non ECC is a non issue. :)  Usually ECC ram is used on servers, and is rarely found on any standard desktop or laptop computer.  However, your problem might be bad ram.  Have you tried running a memory check program?  If I remember correctly the older Ubuntu disks included an option at boot that let you run memtest, and maybe the new ones do too.  If you can find a cd that has the memtest option, try that and let it run overnight.  If there are problems with the ram, that test should find them. :)

---

### Post by Naiki Muliaina on 2011-07-20
Hmm odd one then. I vaguely remember the timing being funny when I first installed it. Maybe its less of an error on the memory, more a user error?

Ill have a fiddle with it tonight and run a memtest if I don't solve it.

Thankya! :popcorn:

---

