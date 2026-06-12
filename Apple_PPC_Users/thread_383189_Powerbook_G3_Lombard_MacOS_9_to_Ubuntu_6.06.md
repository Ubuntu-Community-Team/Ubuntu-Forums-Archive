---
title: "Powerbook G3 Lombard: MacOS 9 to Ubuntu 6.06?"
date: 2007-03-13
forum: Apple PPC Users
---

### Post by clarklinux on 2007-03-13
Hi -

I'm not too good with all the linux tech stuff (took me about a year to get dvd playing working with my desktop running suse,) but I'd like to make this work.

I have a pretty minimalistic powerbook lombard g3: 333 mhz, about 4 gigs HD, and 256 mb ram.

I bought it on ebay andt he guy had OSX on it but it was too slow to use. I put OS 9 on it, and I don't mind it expect for the lack of a halfway decent browser.

I'd like to wipe the OS 9 and put linux on it (is ubuntu a good choice?)

I tried booting the powerbook from a burned 6.06 alternate iso disc image by holding command, alt, shift, delete or whatever it is, and I get a little icon of a folder with a question mark flash alternating to the finder icon. The CD drive revs a little and then it goes into OS 9 startup. What's going on? Is Ubuntu even the right choice?

I just want something small that I can later expand upon, that has gnome, and that i can install relatively easily (I know that's a lot to ask in the world of linux.)

Thanks in advance for any help.

---

### Post by sword_king on 2007-03-13
Being a complete newbie myself, I've been spending altogether too much time reading up on stuff like what you're going through. :confused:   I'm putting Xubuntu on an "old world" beige G3, and I see that some notebook G3s are "old world" as well.  You need to check that out, cuz the way they boot is different than later models.

And there is really no reason not to go with Edgy (6.10), if you can get it going, cuz it has a lot better support for hardware than Dapper (6.06.x) or Breezy (5.10).  One thing I've found is 700mb CDRs won't run on my G3.  I found some old 650mb CDRW blanks and burned Breezy on that and got it going.  Dapper is too big -- about 700 mb, so my Apple CD drive won't read it.  Xubuntu Edgy is smaller, and I got it through the first stage of install, but it kept hanging up and messing up the (required on Old World) MacOS partition.

I'm now working with 800x600 video, but that's a lot better than fighting getting it installed.  and it seems a little quicker than OS9.2 or OS 8.1 on this old mac.

If you do have an old world mac, I may be able to give you some more pointers.

SK

---

### Post by 3rdalbum on 2007-03-13
Booting up from CD requires you to hold down the "c" key as the computer boots. I gather that if OS X was on the machine before, that it was probably a Newworld Mac and therefore will work no-fuss with Ubuntu.

---

### Post by clarklinux on 2007-03-13
Thanks a lot for the info:

Here's what I did:

I burned the Edgey PPC Alt. Install (I only have 128 MB RAM) ISO on a 700 mb CD-R. I booted from the CD on the G3 Powerbook and it revved for a long time, making, to be very technical, an array of R2-D2 sounds.  While it revved, the same folder icon with the alternating finder logo and question mark was in the center of the screen. After a while, it eventually booted to OS 9. I let it startup, and a dialog box came up before going to the desktop that said it could not read the disc and prompted me to format it.

I thought that this must be what you were talking about before: that the old G3 drive couldn't read 700 meg CD-Rs. To test this, I popped in another 700 meg CDR with music on it. As soon as I pushed in the CD tray, the music started playing.


I have no idea what's going on...haha. Any ideas?

Thanks again.

---

### Post by 3rdalbum on 2007-03-14
I know the iMacs around that period have trouble reading CDRs, so maybe it's the same with the Powerbooks? From your description of the noises the drive is making, that's what it sounds like.

You're going to think I'm mad, but try burning the disc image onto a CD-RW. My iMac has trouble with CD-Rs, but not with RWs.

---

### Post by grazie on 2007-03-14
Hi clarklinux,

What 3rdalbum suggests is certainly worth a try. As discussed already I think your problem is most likely your cdrom, but there are a few other things that may help which weren't discussed on the irc channel. You could try some of the things suggested [here]("https://help.ubuntu.com/community/Installation/PowerPC"). Also, a lot can be done in Open Firmware, but it's not the most user friendly environment. I think the notes [here]("http://www.bombich.com/mactips/openfirmware.html") are worth looking at.

To get into Open Firmware use Command+Option+O+F on boot. For reference some useful Open Firmware commands are
```
0 > printenv
0 > eject cd
0 > shut-down
0 > mac-boot

```
I think the meaning of each command is self explanatory.

Assuming the problem isn't with the cdrom, although I still think it is, it may well be worth trying to boot with a minimal install cd as it's only a 12M [download]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current//images/powerpc/netboot/mini.iso"). The Gentoo minimal install cd is also a great tool to have on standby (55M download).

As the machine is quite low spec, I think xubuntu would be the best option (but I'm biased).

---

### Post by clarklinux on 2007-03-14
thanks for the suggestions. I just tried the CD-R (with xubuntu 6.10 alt install) through open firmware. I used the boot cd:,\\:tbxi command and I got this:

> 0 > boot cd:,\\:tbxi DISK-LABEL: read of block0 failed
can't OPEN: cd:,\\:tbxi
ok

As I am writing this I'm burning the same iso with a CD-RW at 1x speed. I'll post back once I've tried that.

ps- grazie: I've tested my cdrom drive with both audio and data cds (burned from x64 desktop) and it's worked fine. Do you think there could still be a problem with it? What kind of problem would it be?

---

### Post by clarklinux on 2007-03-14
Yes!

Thank you 3rdalbum! The CD-RW works and I'm installing right now. I'll get back to you later with the success (?).


Thanks a ton.

---

### Post by grazie on 2007-03-14
Weird! Really good news though. I'll make a mental note of this CD-R/CD-RW issue as I've not come across it before. CD-RWs usually make things more difficult.

---

