---
title: "[SOLVED] linux install with floppy?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by natehall on 2007-11-27
[ATTACH]51602[/ATTACH]I have an old wiped disk HP pavillion that I tried to load Mandrake Linux onto and never could get it to work. (I have factroy install 1420 Dell now! ) I got as far as a Windows boot floppy (Probably lost now) that got the cd rom to read the boot cd and got it at least starting to load. Is there a Linux boot floppy that will drive the CD reader? I'd like to try and save this old PC again but this time with Ubuntu

---

### Post by bobbob1016 on 2007-11-27
You have a few options, you can install debian via netboot then install ubuntu via "sudo apt-get install ubuntu-desktop" or kubuntu-desktop or whichever you choose.
[http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)

You can also PXE boot it and install ubuntu if you have it on a network, with another computer.
[http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install) - This one assumes you have a linux machine                 already.
[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot) - Requires a Windows machine on the network.  I'm not sure if there is a gutsy version.  It is usually recommended to do install->upgrade->upgrade rinse and repeat.  If you wanted to go to gutsy, you couldn't do that with a dapper install, which is what the newest version on that link is for.

If you have another machine that can boot off of the CD-Rom, remove the HD from there, plug in the drive from this computer, and install on that.  Then put it back in this current machine.  Not the best way, but it might work.

---

### Post by hyper_ch on 2007-11-27
This section "Installation without a CD" here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by natehall on 2007-11-28
Well I went and retrieved the old clunker from the storage locker and it only has 128 MB of RAM. Ubuntu needs 256 MB does it not?

---

### Post by bluknight on 2007-11-28
Does the old clunker have a usb port? If usb2 then install there - I know sidux livecd installs boot iso onto usb.

Not sure its still available there used to be a skeleton-type linux on a floppy which you can boot from. Not sure if it has the utility to link to an internet install.

---

### Post by XVII on 2007-11-28
> **hyper_ch said:**
> This section "Installation without a CD" here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

That's your best bet.  I don't think that Ubuntu would ever be small enough to cram on to a floppy.

---

### Post by hyper_ch on 2007-11-29
Xubuntu runs on 64mb ram (but very, very slow).

---

### Post by natehall on 2007-11-30
Thanks for all your help, I do appreciate it. I tried the USB stick , the smart manager floppy, and  various other things with no luck. However I did find a used Red Hat Linux book and it's CD worked! Now to see if I can't get some Xubuntu on it.

---

### Post by Sef on 2007-11-30
With 128 mb ram, Xubuntu will do fine.

---

### Post by natehall on 2007-11-30
On the live CD Xubuntu was pretty slow. On the permanant install it got to about 83% or so and then went stagnant. It's not responding to the mouse but I here some of these installs take quite long so I'm going to leave it alone for awhile before I shut it off and try again.

---

### Post by natehall on 2007-12-01
I just happen to be near the local computer store and asked the owner "how much for a memory upgrade?"
 "100$, 200$ dollars depending."
 "Oh I just want the memory card , I'll put it in myself. "
He digs around on his workdesk, "I got a 128MB "
"How much?"
"Let you have it for 10$"
Needless to say I went for it. WIth the old clunker now up to 256MB I put my homemade Gutsy Gibbon CD in the drive. Works great! The only problem I had was it would not let me partition the whole drive so out of 12 gigs it uses a 6.5 partition. I figured I could reset that sometime later. Is there an easy way to do that?

---

### Post by natehall on 2007-12-01
[attach]micpanik.gif[/attach]Sorry for this bogus post I just want to see if my image worked.

---

### Post by rodica.balasa on 2008-01-18
here is how i installed on an old computer, using a floppy and netboot:

[http://www.len.ro/work/tools/life-to...d-i8000-1/view]("http://www.len.ro/work/tools/life-to...d-i8000-1/view")

---

