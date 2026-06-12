---
title: "[SOLVED] Saving Ubuntu LiveCD settings on USB stick"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Goop on 2007-08-16
For a while now, I've been using the Ubuntu 6.06 "Dapper Drake" LiveCD, but it's quite annoying to have to change the settings every time to my preferred/needed ones. My question is this; is there a way to make Ubuntu load/save settings from a USB stick when the LiveCD boots? I think it's probably done through the boot cheatcodes, but I don't really know any of those. This would really be a great help to me if anyone could help. I have had no success in saving Mozilla Firefox's settings on my USB stick, I only tried saving Firefox to the USB stick, though. I'm a complete newbie to Ubuntu, (though I did get a lot more experience when I had to use it when Windows XP decided to delete some settings folder and not let it boot at all.) And for the record, the USB stick is only 64MB. Would that be enough?

Oh, and please don't just tell me to install Ubuntu. I want to, but the PC's I use are not mine. As soon as I get a laptop, though...

Thanks for reading.

---

### Post by petit.padavoine on 2007-08-16
Hmm.

I have no idea.

But technically, it should be as simple as mounting your stick on /home.

As you must know, in Linux, where a drive is physically is independent to where it is in the filesystem, so you could have your memory stick be the place where everything inside /home in the filesystem is stored.

I think that's what you want, as most config data is stored inside /home/youruser.

As to how to mount your stick, um...

[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)

---

### Post by Zylar on 2007-08-16
I would suggest [DSL]("http://damnsmalllinux.org") for this type of use.  It's designed to do exactly what you're talking about.  Boot from the CD and use the usb stick for /home.  It's also .deb based, like ubuntu, so it'll be similar.

If the PCs have cd-rw drives, you can even have it boot from the cd, and write your settings back to the cd-rw when shut down.  It's been a while since I kept up with DSL, and I never tried this feature, but it always sounded pretty dang cool.

Good luck,

Edit: [Here's]("http://www.damnsmalllinux.org/wiki/index.php/Persistence") the link for setting up persistence (backup/restore).

---

### Post by Goop on 2007-08-16
Thanks for the replies.

After reading the page on LiveCD persistent mode, I suspect that it might fill up  all of my USB stick just from GNOME settings, as someone wrote on the other page. Should I bother getting a bigger USB stick, or would a second CD be easier to use? (The PC downstairs has 2 DVD drives, one is DVD-RW.) I think that would be the easiest option, since the PC's I intend to use it on all have 2 CD/DVD drives, (except maybe the one in my room, but that won't boot Ubuntu properly; it gets halfway through the LiveCD loading screen (if I'm lucky) then changes to a sort of text-mode and freezes once it loads the desktop, with 640x480 resolution.)

Oh noes, I went a bit off-topic. Anyway, would a CD be viable?

Oh, and Zylar: I used DSL a couple of times; it never really appealed to me, I like Ubuntu's interface too much.:KS

---

### Post by Zylar on 2007-08-16
Understandable, DSL is *light* compared to Ubuntu.  Maybe look into DSLn, it came about after I had already moved on from DSL.

Good luck,

---

### Post by bodhi.zazen on 2007-08-16
Puppy linux is nice

You can also do this kind of thing with Wolvix : [http://wolvix.org/](http://wolvix.org/)

ie boot the live CD, save your changes to hard drive of USB :)

There are other live distros that do this as well. Puppy, slax, Dyne .....

---

### Post by Goop on 2007-08-17
bodhi.zazen: Thanks for the links. Wolvix looks really nice, am I right in saying that it also uses a GNOME interface? I might give that a try if I find out I can't with Ubuntu. No offence to any other distros, but Ubuntu is definitely my favourite and I'm detemined to get it working. :)

Oops, I forgot. I'll be testing the persistent mode later today, when I'll have access to my LiveCD (otherwise I would have been killed for apparently screwing up the PC. Apparently Firefox on XP was uninstalled because it conflicts?!).

---

### Post by Goop on 2007-08-17
Well. I tried  to format the USB stick as ext2, to save space, but I ran into a series of problems. I eventually managed to format it, but now I'm having problems with my network on the LiveCD AND Windows. The LiveCD says the ethernet connection is active, but there is no light on my router that usually lights up when my PC is connected to the router. Even trying to access the router's config page in Firefox fails. But on Windows, the ethernet connection keeps turning off for a second, then back on, and the wireless connection has "limited or no connectivity", regardless of what WEP key I use.

So, I either need to fix the Ubuntu network problem, keep switching between Windows and Ubuntu, or print off the instructions, which would be, really, a waste of paper. Any help here?

---

### Post by bodhi.zazen on 2007-08-17
Hmm .... hard to tell from the information you provided.

Sometimes wireless can be problematic, and sometimes it seems to work in one version of Ubuntu but not another.

Also not all versions of Ubuntu will work with saving persistent changes :(

See if these links help : 

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

	[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

	[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

