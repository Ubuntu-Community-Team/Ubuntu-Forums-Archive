---
title: "Blank Screen After Login"
date: 2006-07-02
forum: Apple PPC Users
---

### Post by JoshHendo on 2006-07-02
I just installed Ubuntu (Breezy, I plan on upgrading to Dapper after as Dapper won't boot off the live cd) and when I login, it comes up a blank screen with just the cursor (i think thats how you spell it).

Is there a way that I could fix this? Would it work if I installed XFCE or KDE?

Thanks.

---

### Post by loserboy on 2006-07-03
what kind of video card u got?

(also what do you mean dapper won't boot off live cd?)

---

### Post by JoshHendo on 2006-07-03
Im unsure of the graphics.

It is a Imac g3, so that may help.

About Dapper not booting... [http://ubuntuforums.org/showthread.php?t=206298](http://ubuntuforums.org/showthread.php?t=206298)

---

### Post by LettuceandPickles on 2006-07-03
[QUOTE=JoshHendo]Im unsure of the graphics.

It is a Imac g3, so that may help.

About Dapper not booting... [http://ubuntuforums.org/showthread.php?t=206298](http://ubuntuforums.org/showthread.php?t=206298)[/QUOTE]

What color and speed is this iMac G3?

---

### Post by JoshHendo on 2006-07-03
Its a green one, im not sure of the speed.

It had MacOS9 on it before I tried to install Ubuntu.

---

### Post by LettuceandPickles on 2006-07-03
It would help if you knew the speed.  It would also be useful if you could tell us what version of OS 9 (9.0.x, 9.1 or 9.2.X) was on the machine and if the 4.19 firmware update had been applied (was any version of OS X ever on this machine?  If so, which?)  Also, it would help if we knew if this machine had FireWire ports.

The first green iMac (other then the original Bondi iMac which can look sort of green but is blue-ish) was a 266 MHz G3 with no FireWire and a 6GB Hard Drive.

That had a 6 MB Rage Pro Turbo card soldered to the board (which is how the video is done on all iMacs.)

But there were other, later, green iMacs and knowing the speed would help a lot.

---

### Post by JoshHendo on 2006-07-03
Ok. I will try to find out the speed and everything. I can't remember which version of OS 9 was on there before, and it is too late to find out. It has never had OS X on it. From what I can remember it doesn't have FireWire ports. The HDD is 8.6 gig.

Hope this help. Thanks for this :)

---

### Post by geeber on 2006-07-04
I'm having a similar issue with Dapper on a Wallstreet Powerbook G3 (233MHz -- no firewire ports).  I'm not sure of the firmware version, but this was a OS 9 (9.2)/OS X (10.3, I think) box with a replacement 10GB HD.  It was wiped, OS 9.1 installed, and Dapper added via OldWorldMac setup (BootX, etc.).

Original Dapper installation was successful, though I had no ethernet or sound.  I solved the ethernet issue, started applying Ubuntu updates (applied all found) and at some point during updates install, the screen went blank with just a cursor visible.

Rebooting results in same issue Josh is having: login screen shows up fine, but you get nothing but a cursor post-login.

Any thoughts would be appreciated.

Thanks.

---

### Post by macmusician on 2006-07-04
I can tell you my experience with the 6.06--both Kubuntu and Ubuntu.

I am using an iMac G3/400 384mb/ 40gb mutiple boot with 9.2.2, 10.3.9 and 10.2 and a Fedora 5 partiton as well--with an ATI Rage 128 Pro AGP video card.

The 6.06 CD seems to boot normally into "live" untill the x server starts up--then a blank screen. If I hit control-alt-backspace, it goes to the command line for a couple seconds, then  restarts the xserver almost immediately. I did not think of trying to open another virtual shell to examine the configuration files--not that I know how to do video configuration from the command line!

If I did get into the CLI, which configuration file shouild I be looking at? Is it possible to change the configuration of a running live system? If I did manage to install the HD version, does it use the same video configuration tools--hence the same problem? Is it even possible to run the installer from the command line?

By the way, I have not had any problems of this kind with 5.04 and 5.10.

---

