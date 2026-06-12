---
title: "Solaris installing with USB drives"
date: 2011-06-24
forum: Any Other OS
---

### Post by javajames97 on 2011-06-24
I would quite like to try solaris and also to have it with me on a pendrive. So i decided it best to install to a usb pendrive which i can boot from. I wouldn't have thought installing solaris to a pendrive is impossible (correct me if; it doesn't support usb booting) however i dont know how to install it? i only really have a netbook - no cd drive. How would i go about installing from a pendrive to a pendrive?

EDIT: i may be able to burn solaris install to a CD and install it using a main computer, but the 'install' disk that opensolaris downloads page (at: [http://hub.opensolaris.org/bin/view/Main/downloads]("http://hub.opensolaris.org/bin/view/Main/downloads")) rather annoyingly turns out not to be bootable. Could someone point me in the direction of an actual bootable installer!

---

### Post by MAFoElffen on 2011-06-24
> **javajames97 said:**
> I would quite like to try solaris and also to have it with me on a pendrive. So i decided it best to install to a usb pendrive which i can boot from. I wouldn't have thought installing solaris to a pendrive is impossible (correct me if; it doesn't support usb booting) however i dont know how to install it? i only really have a netbook - no cd drive. How would i go about installing from a pendrive to a pendrive?

EDIT: i may be able to burn solaris install to a CD and install it using a main computer, but the 'install' disk that opensolaris downloads page (at: [http://hub.opensolaris.org/bin/view/Main/downloads](http://hub.opensolaris.org/bin/view/Main/downloads)) rather annoyingly turns out not to be bootable. Could someone point me in the direction of an actual bootable installer!Hmm.  A Unix question on a Linux distro install/support board.  I have a link for you, for the free version: 
[http://www.oracle.com/technetwork/server-storage/solaris11/downloads/index.html](http://www.oracle.com/technetwork/server-storage/solaris11/downloads/index.html)

Wondering why you you aren't trying this with OpenIndiana? Both of these also run real well from VirtualBox running under Ubuntu 11.04.  When you create a VHD, use Solaria as the disk type.

(Remember- if this problem is solved, please use the forum thread tools menu to mark this thread as solved.)

---

### Post by javajames97 on 2011-06-25
> **MAFoElffen said:**
> 
Wondering why you you aren't trying this with OpenIndiana? Both of these also run real well from VirtualBox running under Ubuntu 11.04. 
Hmm, well sure, im just going to use virtual box on a machine with 1gb of ram and 1.33ghz of proccessing power, that would work????

> Hmm.  A Unix question on a Linux distro install/support board.  I have a link for you, for the free version: 
[http://www.oracle.com/technetwork/server-storage/solaris11/downloads/index.html](http://www.oracle.com/technetwork/server-storage/solaris11/downloads/index.html)

ok great, but isn't this the closed source distro?? nevermind, i will try it

also, UNIX and linux being so similar, and there being an OTHER OS tag i thought that people from the 'nix community might be able to help.

well, thanks

PS: i know how to mark the thread as solved ;)

---

### Post by MAFoElffen on 2011-06-25
> **javajames97 said:**
> Hmm, well sure, im just going to use virtual box on a machine with 1gb of ram and 1.33ghz of proccessing power, that would work????


ok great, but isn't this the closed source distro?? nevermind, i will try it

also, UNIX and linux being so similar, and there being an OTHER OS tag i thought that people from the 'nix community might be able to help.

well, thanks

PS: i know how to mark the thread as solved ;)
Did I not sound enthused enough?  I really was!  Your post was a breath of fresh air to me. (See my sig line)

Yes, Solaris 11 Express is the free cut-down version of Solaris..  You "asked" for Solaris.  

I used to be active with support on the OpenSolaris Dev forums until a bit after Oracle bought out Sun Microsystems.   The first thing Oracle did, was to cut off giving Solaris 10 away...  Then much time later, after the outcry, created that cut-down version of  Solaris 11 Express, with no updates or support, then had announced that would no longer support OpenSolaris.  I have all the Official and dev builds to that point.  You should still be able to find them in the PPA's at OpenSolaris up through what was proposed for 2010.10.  If you were active with Opensolaris before, you might remember that the last distro project project at OpenSolaris was named "Indiana." (keep that in mind.)

IMHO- Solaris 11 (just like Solaris 10) is not as user-firendly on the install, modifications, support, tweaking, (the background, under the hood system stuff) etc. as OpenSolaris was for a new user.   OpenSolaris had a good free Application base. Etc.  And once you get things worked out and setup... it's rock solid.   But there is and will not be anymore "new" under the OpenSolaris "Name." (But read on... it's more a technicality.)

After the deadend at Oracle for OpenSolaris, there were still a few dev builds and such, but things shifted to OpenIndiana.  It is sweet.  Funny thing is that all the people that "were" on the projects and forums at OpenSolaris.org-- Are now there at OpenIndiana.  (Even the old Sun people.)   The offshoot distro's are now going off that.  If you want, I could post or PM you the links to all those... and other Unix variants, but from what I can see and have tried, for a low to mid-skilled person trying out Unix I'd recommend OpenIndiana in a heartbeat.

If you want to try things out in VirtualBox would still work at 1GB, if you don't throw a lot at it and it's not going to be a speed demon... But you can try things out until you settle on something.  Some of the Distro's do run off a LiveCD.

OpenSolaris and distro builds based on OpenSolaris:
[http://www.genunix.org/](http://www.genunix.org/)

OpenIndiana:
[http://openindiana.org/](http://openindiana.org/)

---

### Post by javajames97 on 2011-06-27
thanks

sorry it is just that solaris asked me for job titles and stuff; being 14 i am still in schooling

if i get oracle solaris i will probably torent it - any distros specifically??

Being an ubuntu and win user i am used to booting from a pendrive (though i know mac and various other OS' in there early stages like jnode, wont boot) but would it be possible to install solaris to a memory stick?

is it possible to install a live CD of opensolaris to a USB pendrive?
is it possible to install a bootable distro of solaris to USB "?

***i am obsessed with USB pendrive booting for 3 main reasons:
    1)i have a bigger-than-netbook-smaller-than-laptop device which doesnt have a CD-DVD drive
    2)i would like to support demand for modern techniques of living
    3)i can boot the OS on our schools computers! *YAY*


also: virtual box is slow on my families 2gb machine - but that is running OS X and windows 7 - how much memory would solaris and ubuntu take up?
 would it be faster or slower to run on windows or ubuntu?

---

### Post by javajames97 on 2011-06-27
Thank you also for suggesting open indiana, i may try this too, solaris mainly had its appeal in looking similar to windows in the eyes of our inexperienced and useless IT teachers!
Although, thinking about it, i could probably customize ubuntu to look like windows!

---

### Post by MAFoElffen on 2011-06-27
> **javajames97 said:**
> Thank you also for suggesting open indiana, i may try this too, solaris mainly had its appeal in looking similar to windows in the eyes of our inexperienced and useless IT teachers!
Although, thinking about it, i could probably customize ubuntu to look like windows!
I think you will be pleasantly surprised by OpenSolaris and OpenIndiana.  And yes, you can do a dist-upgrade from OpenSolaris to OpenIndiana.  Yes you can do USB using the same instructions for Ubuntu.  

"i could probably customize ubuntu to look like windows!" < But why?  That look is still veolving and Windows itself is still changing it's look to try to look like someone else.  Once you get used to where everything is in what your using... "That's" the important thing right?

---

### Post by uRock on 2011-06-27
Moved to Other OS/Distro Talk, since it has nothing to do with ubuntu.

Have you asked on their forums?

---

### Post by javajames97 on 2011-06-28
> **MAFoElffen said:**
> 

"i could probably customize ubuntu to look like windows!" < But why?  That look is still veolving and Windows itself is still changing it's look to try to look like someone else.  Once you get used to where everything is in what your using... "That's" the important thing right?

my apologies but, did you read what i said?

[SIZE="3"]i am not trying to make a windows look alike because i think it to be aesthetically pleasing[/SIZE] 

i am used to booting a live CD on my schools computers because i can access a compiler from it, but it is blatantly obvious if im running ubuntu, so i make it look like windows XP, which is what our school computers are suposed to have

never mind... OTL

yeah, i will go somewhere else, thanks

---

