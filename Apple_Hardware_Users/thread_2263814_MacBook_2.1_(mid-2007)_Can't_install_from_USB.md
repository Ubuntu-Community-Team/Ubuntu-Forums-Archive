---
title: "MacBook 2.1 (mid-2007) Can't install from USB"
date: 2015-02-03
forum: Apple Hardware Users
---

### Post by cat2 on 2015-02-03
i have a macbook (2.1, mid-2007) only mine has no dvd-drive (not incredibly interested in paying £30~ for a new one). or os x install. -- long story short, my os x hard drive died.

so yeah, i cannot get ANY bootable usb's to do anything on this macbook.


[LIST]
[*]os x lion shows up on the boot menu when i hold option, but then the screen is just white forever. light on usb flashes, but after leaving it for an hour i figure it wasn't actually doing anything.
[*]os x snow leopard doesn't show up in the boot menu.
[*]windows 8.1 doesn't show up in the boot menu.
[*]windows 7 doesn't show up.
[*]ubuntu 14.04 amd64 doesn't show up.
[*]ubuntu 14.04 amd64+mac .. no dice
[/LIST]

i put the hard drive in my pc and installed ubuntu 14.04 amd64, it booted fine and everything. put the hard drive back in my macbook, nothing. no boot option. i'm not super well versed in boot loaders, i know *of* them and the types, but not really anything further.

refit actually does show up in the boot menu and runs, however everything you can select errors. when trying to load the linux os (it doesn't say ubuntu, but it does detect 'linux os') it goes to a black screen and then says something about no bootable drive being inserted. -- this at least confirms booting from usb isn't totally impossible or my usb ports are broken, but it seems odd that even os x usb's wont work? (usb's burned with transmac on windows)

so right now i am kind of at a loss. i have access to a pc running windows 8.1, or i can put the hard drive in my pc and do some magic in the ubuntu install if that may be able to help.

thanks in advance if anyone can help!

---

### Post by maclenin on 2015-02-03
**cat2!**

Give [this]("http://ubuntuforums.org/showthread.php?t=2259849") a whirl.

Good luck!

---

### Post by Bucky Ball on 2015-02-03
*Post moved to own thread.*

You do yourself no favours resurrecting a thread that has been dead for five months. I have moved your post to its own thread to improve your chances of getting support.

Feel free to change the thread title by editing the first post and clicking 'Go Advanced'. Good luck. ;)

---

### Post by este.el.paz on 2015-02-03
@admin types:  I was subscribed to the old thread . . . just complicates any attempts by those of us who are actually trying to help to move stuff around or edit posts . . . especially in Apple hardware sub-forum where help itself can be slow in arriving, as I've mentioned before in the forum discussion area.

@OP:

You can see some other posts on this forum from Lars nooden where he is posting about problems with the installer using USB, which should be in "Vivid" but might also be influencing other flavors of Ubuntu . . . it seems to relate to the debian installer having some problems.

Also, from reading your post, you mention "refit" . . . but rEFIt only is supported up to 10.7???  So, you might try to install rEFInd and see if that will show your systems in the boot manager . . . also, you could try SuperGrub2  repair disk to see if it will recognize your OSs and boot them.

e.e.p.

---

### Post by cat2 on 2015-02-03
maclenin, i shall give this a try.

Bucky, sorry, i had used the 'find already posted' button when creating a new thread and found the one i originally replied in and figured it wasn't ~that~ old and it was almost identical to my situation so it seemed like a good place to post, should the thread have subscribers.

este.el.paz, i put refit on my usb just to see if my macbook would boot anything at all from the usb and while it did get to the refit menu, none of the options did anything useful


to try and be a bit clearer about my situation, the hard drive in my laptop was put into my PC and i installed ubuntu 14.04 amd64 onto the drive via my usb.
i took the hard drive and put it in my macbook in hopes it might boot, sadly it only shows the white screen with the ? folder. holding option during boot brings me to a completely empty boot menu - i can move the mouse around but there is absolutely nothing to select, even with my usb inserted - but it is not a problem with the usb drive / port.

i have read that macbook 2.1 has terrible efi support, but mine is not even recognising os x bootable usbs. so i am completely lost. -- and i am going to repeat, the os x drive is dead and gone. there is no recovery partition or anything like that.

i ordered a sata > usb cable and i am going to try plugging in a dvd-drive i have laying around and try to boot from the ubuntu dvd - everyone with this macbook has great success with dvds, but i am not sure if it'll have any joy reading a dvd via usb cable. my fingers are crossed and hopefully the cable arrives tomorrow. kinda need my laptop by saturday :(

in the mean time, i am going to attempt maclenin's route. -- well, can't really do that as i can't get the bootable usb to show up on my macbook still.

---

### Post by maclenin on 2015-02-04
**cat2!**

I fooled around with a handful of different methods for setting up "bootable" usb sticks (for the Mac) until giving the method I explicitly describe a try (see section **A. PREPARE A BOOTABLE LIVEUSB ON LINUX BOX** of the [guide]("http://ubuntuforums.org/showthread.php?t=2259849")) - and be certain you use **Startup Disk Creator** to create your bootable (64 bit) usb....

---

### Post by cat2 on 2015-02-04
not having os x anywhere makes it hard to do that, but fortune has swung in my favour and i am getting a new laptop tomorrow off a friend instead. this old macbook is probably due retirement anyway, will stick the parts on ebay as the body is held together with selotape and has more scratches than a very scratched up thing!

thanks for the ideas anyway!

---

### Post by peter_london on 2015-02-05
Hi cat2, although I have no solutions on hand for your specific situation I'd still like to share my experiences.

I have a Mac Mini 2,1 - mid 2007 - which is now running Ubuntu Server just fine. However, I spent one whole day trying to get it to boot from USB, couldn't get it to work, tried EVERYTHING I could find on Google. refit or refind are nice because they give you options during boot but in my experience, neither one of them makes it possible to boot from USB on a 2007 Intel Mac.

My last attempt to get it to boot from USB was this nice little util - [https://sevenbits.github.io/Mac-Linux-USB-Loader/](https://sevenbits.github.io/Mac-Linux-USB-Loader/) , however - USB sticks created with that tool still didn't work on my 2007 Mac Mini. I even tried on a Firewire drive - still couldn't get it to boot.

Just for funsies I tried a USB stick created with the Mac Linux Boot Loader on my newer MacBook Air and it worked in an instant. So, even though tons of pages tell you that all Intel Mac's are bootable from USB, I'm not so sure anymore that this is the case. With or without refit / refind (I sure don't have either of those installed on my Macbook Air...).

So - do yourself a favour and get an external USB drive and burn the ISO on DVD because you should be able to boot Ubuntu from these just fine. If £30 hurts too much (which I completely understand) try to borrow one from a friend or something - anything to avoid spending hours on trying to boot from USB :).

Let me know if you make any progress!

Cheers

Peter

---

