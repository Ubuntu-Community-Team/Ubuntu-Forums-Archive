---
title: "Trouble locating a download of 8.10 desktop for PPC"
date: 2009-01-09
forum: Apple Hardware Users
---

### Post by vamp4life666 on 2009-01-09
I recently upgraded my primary work computer to a Mac Pro 2.8 8-core, which made my MacBook Pro 2.0 dual core the Home machine, which rendered my Powerbook 1.25 very under used. 

But it still has so much life left in it, and who really needs three machines all running the same OS. I figured this would be the perfect opportunity to get back into Ubuntu, I will admit have been out of it for a while. 

So I went to the main page and downloaded 8.10 desktop edition... Wouldn't install... I figured I burnt it wrong and converted it to a .cdr still wouldn't boot. Some browsing around has lead me to believe that the iso I download is not Power PC compliant. 

If so could one confirm there is either or no 8.10 desktop edition for the PPC or give me a clue where I might find it.

---

### Post by stream303 on 2009-01-09
Here it is...

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by vamp4life666 on 2009-01-09
I am assuming this is the one I need?


ubuntu-8.10-alternate-powerpc.iso


?????

---

### Post by stream303 on 2009-01-09
That's fine.  Boot it by holding down the "C" key long enough to hear it boot.  I'm assuming you are burning it as an iso with disk-utility (drag the icon to left-hand pane of disk utility, highlight it, and then click burn)

And, there is a bug right off the bat in 8.10, but you can get around it.  When it fails to find the cd later, hit CTRL-ALT-F2, login, and enter

```
modprobe ide-scsi
```

then back to the normal installation with CTRL-ALT-F1.

The earlier LTS version, 8.04 is also a very nice choice which didn't have this problem.

---

### Post by tiresia on 2009-01-09
> **vamp4life666 said:**
> I am assuming this is the one I need?
ubuntu-8.10-alternate-powerpc.iso
?????

Yes, but be aware that the alternate Installer has a small bug, that you can easily solve reading this thread:
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

...
If you are looking for a Live-CD, than you should use the desktop-CD Ubuntu hardy (8.04.1)
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

(There is also a Desktop-CD of Ubuntu Intrepid, but it does not work - it is still a daily-build of 17-November 2008, and I'm not sure that it will ever release)

---

### Post by vamp4life666 on 2009-01-09
I got it 8.04 installed, looked good ran updates, took awhile but not a problem. Minus my header bar across the top in now on the side and is irritating the hell out of me. Call me blind and stupid but how do i get it back across the top?


Never mind I figured it out, I need to plug in a two button mouse....
I'm so used to my mighty mouse that I fogot this older PPC doesn't handle right click as well...

---

