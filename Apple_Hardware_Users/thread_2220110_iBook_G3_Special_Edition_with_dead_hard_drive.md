---
title: "iBook G3 Special Edition with dead hard drive"
date: 2014-04-26
forum: Apple Hardware Users
---

### Post by mikeebean on 2014-04-26
I have an iBook G3 Special Edition, and I'm pretty sure the hard drive is dead (on startup, it flashes a question mark.) I thought I might try the 12.04 PowerPC Live CD to see if I can recover anything on the hard drive. At the very least, even if the hard drive is not accessible, I'd like to use the live session or boot from a USB key.

When I boot from the CD, I'm greeted by the boot menu and I hit return. Lots of text, then a white screen with text, then a black screen.

At this point, the hard drive clicks repeatedly for *several* minutes, followed by many errors similar to: udevd[102]: timeout: killing '/sbin/blkid -o udev -p /dev/sda' [181], etc.

The Ubuntu 12.04 splash screen appears (text only), which cycles through the red/white lights. Hard drive continues to click for several minutes. Pressing ESC shows many I/O errors:

stdin: I/O error
chroot: can't execute 'mktemp': Input/output error
followed by lots of: can't stat, can't execute, can't create, can't open, timeout, etc. And finally:

General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
bash: groups: command not found
root@ubuntu:~#

Can anyone suggest a fix for me? I always thought Live CDs worked even in the absence of a hard drive? Thanks!

Michael

---

### Post by TREESofRIGHTEOUSNESS on 2014-04-27
Hi,
Live CDs do work without a harddrive.  It may be easier to use a USB than a CD, though.
The first thing you need to do is check the md5sum of your iso file that you downloaded from the website.
replace ubuntu.iso with whatever your file is named... be sure to do this in the directory where the file is (or change the filename to include the path)
open a terminal and...
```

md5sum ubuntu.iso

```
you can compare that with the md5sum listed on the page you downloaded it from.
which might be here
[http://releases.ubuntu.com/12.04.4/](http://releases.ubuntu.com/12.04.4/)

I highly suggest using a lighter DE like Lubuntu, as Ubuntu requires more memory than my G3 has.

So, you can go to:
[http://cdimage.ubuntu.com/lubuntu/releases/](http://cdimage.ubuntu.com/lubuntu/releases/)
and try one out!

Now, for USB booting....
plug in your USB
and then open a terminal and:

```

dd if=~/Downloads/lubuntu-14.04-desktop-powerpc.iso bs=1M of=/dev/sdb

```

(substitute lubuntu-14.04-desktop-powerpc.iso for your iso file name)

then, when you boot go into open firmware by holding
Option+Apple+O+F
You'll get a white screen with black text (if you did it right)

and type in:

```

boot usb1/@1:2,\\yaboot

```

(note: it may be usb0 depending on which USB port you use)

and voila!
Now you may have corrupted graphics (unfortunately) when you boot into the OS...
Go here, and get the correct file:
[http://mac.linux.be/content/xorgconf-files](http://mac.linux.be/content/xorgconf-files)
I use:
[http://mac.linux.be/files/xorg/ibook6.txt](http://mac.linux.be/files/xorg/ibook6.txt)

Press Ctrl+Alt+F1
login, and go to the folder you downloaded the text file from and:

```

sudo mv ibook6.txt /etc/X11/xorg.conf
sudo restart lightdm

```

Voila!!

This is a nice resource to have, by the way:
[http://mac.linux.be/content/apple-powerpc-wiki](http://mac.linux.be/content/apple-powerpc-wiki)


I just did all this stuff with my iBook, it had a dead hard drive and I used a USB for a bit, and then switched out the HD with an iBook that had a broken hinge for the screen (That hard drive is VERY hard to get out!!  Not for the faint of heart)
If you want/need to switch it out:
[http://www.zathras.de/angelweb/blog-ibook-disassembly.htm](http://www.zathras.de/angelweb/blog-ibook-disassembly.htm)


Whew... One more thing...
If you use 14.04 you will most likely not have sound :(
See this bug
[https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373](https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373)

Cheers!

---

### Post by mikeebean on 2014-04-28
Wow, thank you so much for the detailed response! I'm excited to try this out, but wondering if I need to buy a new/old USB key? I really missed this machine, so nice to have it out of the box again! It's the one computer I've owned that was actually a joy to use.
 
I'll be surprised to recover anything from the HD, but I simply can't toss it without trying. I plan to replace it with a compact flash drive (lots to consider there, but at least it's inexpensive), and I'm not sure if I'll install OS9, OSX, Lubuntu, or something else, then maybe I'll let my daughter play with it if I haven't fallen in love with it again!

> **TREESofRIGHTEOUSNESS said:**
> 
I just did all this stuff with my iBook, it had a dead hard drive and I used a USB for a bit, and then switched out the HD with an iBook that had a broken hinge for the screen (That hard drive is VERY hard to get out!! Not for the faint of heart)
I've had this iBook apart a couple of times, you are absolutely right! The HD is nearly the last thing you can take out!

---

### Post by rsavage on 2014-04-28
I think (though I'm not certain) the live cd looks for a swap partition.  You used to see references to a boot parameter "noswap" to turn it off, but I'm not sure if that still works (if it ever did).

---

### Post by mikeebean on 2014-04-28
**EDIT: Never mind, I seemed to have fixed it!**
> **TREESofRIGHTEOUSNESS said:**
> Now, for USB booting....
plug in your USB
and then open a terminal and:

```

dd if=~/Downloads/lubuntu-14.04-desktop-powerpc.iso bs=1M of=/dev/sdb

```

(substitute lubuntu-14.04-desktop-powerpc.iso for your iso file name)

I'm stuck on this bit... clearly I'm doing something wrong. It took me a while to figure out how to become su. Here's what I've got so far:

```
su -- ubuntu ***(my unimaginatively-named admin account)***
Password: 
sudo dd if=/home/public/Downloads/lubuntu-14.04-desktop-powerpc.iso bs=1M of=/dev/sdb ***(public is the user account)***
[sudo] password for ubuntu: 
dd: opening `/dev/sdb': No medium found ***(so I tried a suggestion on an unrelated thread: )***
sudo dd if=/home/public/Downloads/lubuntu-14.04-desktop-powerpc.iso bs=1M of=/dev/sdb1
755+1 records in
755+1 records out
792600576 bytes (793 MB) copied, 20.5789 s, 38.5 MB/s
```

But now I have a 792.6 MB /dev/sdb1 file and nothing on my USB key. Help! :)
Michael

**EDIT: ***sudo lshw* shows the USB key as /dev/sdc, and that seems to have fixed the issue. Now to try it out on the iBook, fingers crossed!

---

### Post by TREESofRIGHTEOUSNESS on 2014-04-28
Oh... good, sorry I forgot to mention the part about figuring out which one was your device....  I knew there had to be something I missed (it was a long post)

---

### Post by mikeebean on 2014-04-28
After a bit of trial and error, I figured out that even though the terminal reports that the transfer to USB is complete, it really isn't and I needed to wait a few minutes longer. However, I'm still unable to boot the iBook into Lubuntu...

With Lubuntu 14.04 I get an error:
Kernel panic - not syncing: No working init found. Try passing init= option to kernel. See Linux Documentation/init.txt for for guidance

With Lubuntu 12.04, after several minutes it hangs at "Generating locales." 

With plain Ubuntu 12.04, it appears to very slowly boot, then freezes on a black screen. Left overnight, it never made it to the desktop. Perhaps insufficient RAM, I had extra RAM installed in the clamshell when I bought it, but I have no idea now what's in it.

I could try a few older releases, 10.04, 9.04, but I was hoping to get at least 12.04 up and running. Maybe a different distribution?
Michael

---

### Post by TREESofRIGHTEOUSNESS on 2014-04-28
Did you make sure to md5sum your iso?
That is a very important step to make sure everything was downloaded correctly.
If the md5sum isn't correct you can install zsync and zsync it to get the rest of the file.

The blank screen is an issue with the graphics card (or that has been my experience with that issue) you should try a yaboot parameter like radeon.modeset=0
Do you know what kind of graphics card it has.. I am guessing it has one similar to mine that is why I gave you that parameter.
You should NOT try one of the older ones, because they are no longer supported, and will be vulnerable to numerous bugs that have since been fixed (some very serious issues have been fixed even this past month, like the Heartbleed vulnerability)

I am downlaoding 12.04 and putting it on a USB to try out right now.

---

### Post by TREESofRIGHTEOUSNESS on 2014-04-28
You know I just thought of something really basic, but easy to overlook.
Did you download the PowerPC iso?
Because that is the ISO you will need with an iBook.
You may have done this, but sometimes the most obvious things get overlooked, and we can put a lot of effort trying to make the solution something complicated :)

---

### Post by mikeebean on 2014-04-28
Hi again,

I hope I'm not being too much trouble? I really appreciate all your advice.

I did check the md5sum against the following page and it matches in each instance:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Since my short-term goal is really to access the hard drive if at all possible, I had already tried Ubuntu 9.04 and 10.04 before your last post. Ubuntu 9.04 gets past login to a black desktop with movable pointer and white bars, but freezes. Ubuntu 10.04 gets to a desktop with movable icons, dialog boxes that don't work, and no panel.

I suspect that the original RAM upgrade I had on the clamshell is simply insufficient to handle much. Perhaps I will look around for my original Apple disks and see if I can't install OS9 on the USB key. Next month I plan to upgrade the RAM with a 512MB module, install an Airport card, and purchase a compact flash drive. Hopefully then I'll be in a better position to try Lubuntu!

Michael

---

### Post by mikeebean on 2014-04-28
Yes they are all PowerPC iso's:

lubuntu-14.04-desktop-powerpc.iso
lubuntu-12.04-desktop-powerpc.iso
ubuntu-12.04-desktop-powerpc.iso
ubuntu-10.04-desktop-powerpc.iso
ubuntu-9.04-desktop-powerpc.iso

Good idea though!

Oh and, I have no idea what graphics card is installed; I'm not sure how to check. Whatever came with the laptop originally, but I know that isn't necessarily consistent across a production run.

---

### Post by TREESofRIGHTEOUSNESS on 2014-04-28
The 12.04 PPC Lubuntu is installing right now on my machine.  It is working just fine.
Are you planning on using the Compact flash for the Hard drive??  That is something I have been wondering about trying.  I had a 60gig HD that crashed (I kept getting the ? on powerup)  Then I took a 20Gig from an iBook that had a broken hinge and installed it.  And now the once dead useless computer is alive!!!
I also moved over some memory from the other one, and now have 512.... When it had 128MB it took FOREVER to load Lubuntu, so I installed a Debian Mini ISO, and built everything from the ground up using JWM instead of LXDE, as JWM is possibly the lightest stacking window manager.  It is kinda ugly, but you can do a lot to make it look nicer.  You may have to simply install the OS on the machine (though partitioning might lose some data).
Does it have an OS on it?  If you are planning on upgrading the hard drive anyway, you can get a USB case for the harddrive and access data from another computer that way.  Though, be forewarned the iBook is not meant for people uncomfortable with opening the computer to service the harddrive.  It is like an hour process.. seriously.  Getting the case apart was the hardest part.

Can you give me the specific device you have?
this is mine:
[http://www.everymac.com/systems/apple/ibook/specs/ibook_800.html](http://www.everymac.com/systems/apple/ibook/specs/ibook_800.html)

---

### Post by mikeebean on 2014-04-28
This is mine, a bit older than yours:
[http://www.everymac.com/systems/apple/ibook/specs/ibook_se.html](http://www.everymac.com/systems/apple/ibook/specs/ibook_se.html)

The current HD had OS9 on it, but I get a ? on startup, so probably it's dead, and I'm reticent to buy a USB caddy for it if it is dead. I've taken this computer apart in the past, and it was a bit scary but rewarding. My only concern is that the case plastic seems brittle now. 

I do plan to use the compact flash drive as my main HD. I've read concerns that the CF could fail due to repeated write operations, but the prevailing attitude seems to be that the minimal cost is worth the risk, and I agree. I've also read warnings about compromised speed with CF, but it seems this isn't an issue with these older computers, and that there may actually be an improvement. I considered an SSD, but I don't really want to try that right now. I'm also not keen on simply installing a replacement mechanical hard drive. 

I also just discovered that my OS9 Zip disks aren't readable in Ubuntu, Windows 7, or Mountain Lion, at least without a lot of effort, plus I have a ton of old floppies, so it would be wise to get OS9 running just to clear off those disks.

---

### Post by TREESofRIGHTEOUSNESS on 2014-04-28
Whew... that has very little memory.  I am not entirely sure you can do a good live cd.
One option would be to run a live cd and install to a USB drive.  Then you can boot the computer using that USB drive from openfirmware.  It is REALLY slow, but... it works!  It might do just what you need.
Though... I'd try installing the Ubuntu Mini ISO, and install a very minimal WM, like JWM.  You'll need to install the package named 'menu' to get a useable menu... but it might be worth a try.

---

### Post by mikeebean on 2014-04-29
Tonight I checked the RAM, and it's the standard 64MB (although I truly remember being offered and accepting a RAM upgrade.) So I swapped in a 128MB module from my white dual-USB iBook and voila- Lubuntu 12.04 boots and works! Slow as molasses, but it works.

GParted considers the built-in 6GB HFS-formatted drive to be "unallocated(!)". hfsutils is already installed, and I tried to install hfsprogs in case that helps, but the computer freezes up during the install. I also tried to uninstall some unneeded applications to make room for hfsprogs, but that freezes up the computer as well.

If I can find a USB hub, I might try to install lubuntu from one USB key to another and boot from the installation, or use my install disks to put OS9 onto the USB key. I'm not sure any of this is even possible. Otherwise I'm stuck until next month!

Michael

---

### Post by TREESofRIGHTEOUSNESS on 2014-04-29
Glad it worked (mostly).  You could potentially put a swap partition on the usb drive, and have extra memory (make it aroung 512MB)... not terribly sure if the live environment will use it.
Are you using the terminal to install?  Every program you open eats up more memory, and you could Ctrl+Alt+F1  Then you could even stop lightdm and install hfsprogs.
```
sudo service stop lightdm
```
I have had to stop lightdm to add in an xorg.conf to make the graphics not so psychedelic, so I know that works.
make sure you don't have any programs open, and install it from the command line
```
sudo apt-get install hfsprogs
```
Then restart lightdm
```
 sudo start lightdm 
```
Anyway this is worth a try :)

---

### Post by mikeebean on 2014-05-03
Success! (Well, sort of...)


I managed to get Lubuntu 12.04 to install on a USB key using the alternate install ISO on a second USB key (I could have used a CD but I hate to burn one every time.) Both keys were connected through a hub to the one USB port. I was briefly worried that the installation had frozen at 83%, but I left it alone and it was fine. Unfortunately it couldn't install yaboot (a commonly-reported problem) and won't boot by itself; so I boot to the alternate iso's yaboot, then select the yaboot.config file from the other key. I might play with that later, but it's not a priority since I'll be replacing the USB key with a compact flash drive. At any rate, it works and runs very smoothly. Hot-swapping USB devices on the hub can freeze up the system, but that will also be remedied with the CF HD. Boot-time is acceptable, except for a lag at "HDIO_GET_IDENTITY failed for /dev/sdb: Invalid argument". (My HP laptop lags at the same message on Ubuntu.) I'm really enjoying Lubuntu, it's a very clean and fun environment. Maybe I'll try Mint next!


I also installed OS9 from the original CDs to a USB key (very easy) and it boots fine as well, from the USB port or a hub. Strangely, I had to keep the mouse moving during installation to prevent the CD drive from going to sleep. Rediscovering OS9 has been great, it's really nice to see an old friend again! I definitely want the option to dual-boot!


OS9 and Lubuntu both confirm that the HD is toast. In a few weeks I'll tear down the laptop, remove the HD and try to create a dual-boot on a CF HD. Incidentally, the OS9-formatted Iomega Zip disks *do* work in Ubuntu, OSX and Windows 7. The first one I tried just happened to be corrupted and unreadable.


Thanks for all your help! I'll come back and report on my CF HD experience in a new thread, since there seems to be lots of questions and few answers out there. Take care!


Michael

---

