---
title: "nothing happens after install"
date: 2009-05-23
forum: Apple Hardware Users
---

### Post by newbeehuston on 2009-05-23
So I installed Ubuntu 8.10 using the alternate powerpc iso because it was the only one that would install.  I found out that because I was using a G4 (I think) iMac I could not install the 9.4 option as that seemed to be for PC's only.  Next, I tried the regular powerpc install but it would hang at 6% during select and install software.  The alternate did work from start to finish except for having to type "modporbe ide-scsi" to find my cdrom drive.
It ejected my CD and said to remove the disk before rebooting and I did so.  It then began to boot listing various things I expect are normal for boot-up but then the screen went blank and stayed that way.  I thought that maybe I needed to type "tasksel install ubuntu-desktop" but that doesn't seem to be working; but then I don't know what I'm doing.  What do I do?

---

### Post by Kareeser on 2009-05-23
Once the black screen appears, press "Ctrl-Alt-F4", and copy down the error messages.

Those may help us diagnose the problem.

---

### Post by newbeehuston on 2009-05-23
The last thing I see is a black screen with the words "loading, please wait..." in the top right but then the screen goes completely blank and it sounds like the hard drive disengages. Control, alt, F4 does nothing.

---

### Post by marshag63 on 2009-05-24
Make sure you press Ctrl + Alt + F4 all at the same time - takes you to a console.



I had the same problem - my screensaver would come on before the computer was finished booting - all I needed to do was push the spacebar.

MarshaG.

---

### Post by newbeehuston on 2009-05-24
No, this is definitely not the same thing.  Ctrl, Alt, F4 at the same time, no matter when during boot-up, does nothing except before boot: linux where it stops booting and nothing can make it start again.  Spacebar also does nothing, when the screen goes blank the computer is unresponsive; it pretty much shuts down.

---

### Post by Benboom on 2009-05-24
You can install 9.04 on a PowerPC; in fact, it is much easier than getting 8.x to work. I have it working fine on my G4 Sawtooth and I couldn't get 8.10 to install at all because I'm such a dork with shell commands and I couldn't figure out how to escape the black screen to get a command line. But 9.04 just installs itself with no trouble; make sure you get the PPC distro, that's all. It's on the Ubuntu site.

---

### Post by newbeehuston on 2009-05-24
Yep, I found the link for 9.04 PPC but neither install was working.  I did a checksum on them and the sums are different.  Do you know of a better link where the download isn't corrupt?

---

### Post by tiresia on 2009-05-24
[http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)
[http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/)
[http://cdimage.ubuntu.com/kubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/kubuntu/ports/releases/jaunty/release/)

[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

---

### Post by newbeehuston on 2009-05-24
Thanks for the links.  The Ubuntu page is the same one I was using, the other two I  haven't dealt with yet because I wasn't sure the computer could handle them.  Maybe I'm downloading the wrong one.  I've tried the desktop cd for mac and the alternative install too.  I don't know what the desktop image i.MX51 is but I don't think that is for me.

---

### Post by tiresia on 2009-05-24
Maybe you can use a torrent, it should be more reliable

---

### Post by newbeehuston on 2009-05-24
OK, I downloaded Ubuntu 9.04 desktop PowerPC.iso via bit torrent and ran winMD5sum on it and the sums are different too.  Should I try one of the other versions?  Can the computer handle it?
Here is the info on the computer:
iMac PowerPC 750 @400 MHz
512k @160 MHz L2 Cache
1024 MB Ram (plenty)
ATI Rage 128 Pro
8 MB VRam

---

### Post by tiresia on 2009-05-25
I don't know, if there is any difference with WinMD5sum. Anyway you could just try to burn a copy of it (as iso image not just data).

---

### Post by newbeehuston on 2009-05-25
Alright, I finally got a download to validate and I am burning it now.  I will run a disk validation after that.  So if this does not work that means the problem is with the mac doesn't it?  I have a feeling that the CD drive is bad.

---

### Post by tiresia on 2009-05-25
If you get again a black screen, it does not mean that the installation wasn't successfull! It can just mean, that you have to configure your xorg configuration file.

After installing and rebooting, if you get again a black screen, restart the computer and type at the yaboot prompt ```
Linux nosplash
```
or ```
video=ofonly
```
or ```
Linux nosplash video=ofonly
```

Let us know, if it works

---

### Post by discourse on 2009-05-29
I just upgraded to 9.04 and after reboot login i am left with a brown screen. I have tried Failsafe Gnome but nothing happens.

---

### Post by tiresia on 2009-05-29
> **discourse said:**
> I just upgraded to 9.04 and after reboot login i am left with a brown screen. I have tried Failsafe Gnome but nothing happens.
Your Hardware?

---

### Post by discourse on 2009-05-29
> **tiresia said:**
> Your Hardware?

Sorry :) G4 PPC Mac Mini

---

### Post by discourse on 2009-05-29
> **discourse said:**
> Sorry :) G4 PPC Mac Mini

after sudo dpkg-reconfigure -phigh xserver-xorg i get xserver-xorg is broken or not fully installed

---

### Post by tiresia on 2009-05-29
Have you tried to reinstall it?

---

### Post by discourse on 2009-05-29
after lspci i get 

VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)

---

### Post by discourse on 2009-05-29
> **tiresia said:**
> Have you tried to reinstall it?

This was an upgrade from inside my previous install. I think installing xserver should do the trick I hope.

---

### Post by tiresia on 2009-05-29
```
sudo apt-get update
sudo apt-get install --reinstall xserver-xorg
```

---

### Post by discourse on 2009-05-29
> **tiresia said:**
> ```
sudo apt-get update
sudo apt-get install --reinstall xserver-xorg
```

could not resolve 'ports.ubuntu.com'

I will try to download the ppc cd and do a reinstall. i had no such problems installing 8.10. I will revert back to that if I'm not successful.

---

