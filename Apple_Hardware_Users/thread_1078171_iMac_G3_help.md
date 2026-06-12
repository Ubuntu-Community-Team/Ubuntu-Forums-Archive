---
title: "iMac G3 help"
date: 2009-02-23
forum: Apple Hardware Users
---

### Post by harrybissett on 2009-02-23
I've read the thread titled "Easy way to install Ubuntu on iMac G3" and need some help.

I booted the cd and some text comes up with a 'boot' prompt. I couldn't get the terminal up here as the thread directed me to. I press enter and the Mac shuts down immediately. After, I entered 'live video=ofonly' as it recommended if pressing enter doesn't work. It reads the disk for ages and eventually takes me to the terminal with the errors 'bogl_init failed: EXPLODE' and 'screen init failed'

I'm stuck on the part where you edit the xorg.conf file. After entering sudo nano /etc/X11/xorg.conf it opens the file. But I can't find 'dri' or Horizsync or Vertrefresh. 

I'm trying to install Ubuntu Desktop 8.04.1 LTS PPC that I found from here [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

---

### Post by Hume's doona on 2009-02-23
i'm having a similar problem. i've got it booted now. but i can't even open a terminal.

the capital "L" in "Linux" seemed to do the trick to get it booted to the desktop, now i just need to be able to open stuff

sorry, just reread your post.

i was directed to type "Linux video=ofonly" not "live video=of only"

from this thread
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by harrybissett on 2009-02-23
Thanks, but that doesn't seem to work.

---

### Post by harrybissett on 2009-02-23
Just for some extra info, the thread I'm talking about is located here [http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)

Basically, I do not get the 'blankscreen' when I boot the disk, I have this text onscreen - 

[B]Welcome to Ubuntu 8.04.1 (Hardy Heron)!

This is an Ubuntu live CDROM

The default option is 'live'.

If the system fails to boot at all use 'live video-ofonly'

Press the tab key for a list of options, or type 'help' for help.

*************************
In in doubt, just press Enter, and if that doesn't work,
type 'live video=ofonly'.
*************************
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot:
[/B]

Have I downloaded the wrong ISO or something? When I hit enter it Mac shuts down, and typing in 'live video-ofonly' brings me to the ubuntu terminal, but I cannot find the dri, horizsync and vertrefresh items in the xorg.conf file.

---

### Post by tiresia on 2009-02-23
The CD you downloaded is the right one. How much ram do you have?
At the yaboot prompt, try following
video=ofonly nosplash
If you want to install Ubuntu, for your machine is better to use the alternate-installer-CD. Althought I find that Debian works for those old machine better that Ubuntu

---

### Post by harrybissett on 2009-02-23
I've got about 380mb of RAM installed, above the required 320mb for a Live installation.

I found out that the xorg.conf files have changed since previous versions, so I decided to download the version he would have been using to write the tutorial, 7.04.

I'm going to try booting with this version and hopefully it should work as he is saying it will. Then I should be able to upgrade to higher version from the OS right?

---

### Post by harrybissett on 2009-02-23
Oh, and running 'video=ofonly nosplash' didn't work. But I've tried many of the options including 'live=nosplash' which I think you are referring to, but that didn't work either.

---

