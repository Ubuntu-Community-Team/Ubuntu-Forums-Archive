---
title: "Booting Troubles!"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Bigguy2468 on 2006-12-31
Well, I have started a new thread on this problem.
I am having a problem booting up just about any release of ubuntu on my laptop. Just bought this machine and this is the configuration:

AMD Turion 64 x2 Mobile
Technology TL-50
803Mhz, 1gig RAM

Currently running:
Windows XP Media Center SP2

The problem always seems to be the same.
Tried the i386 version of Dapper Drake, tried edgy and also tried ubuntu-6.06.1-dvd-amd64 and it always seems to hang around the same place on boot. Using the 64bit version every goes fine until this process:


STARTING ENTERPRISE VOLUME MANAGEMENT SYSTEM...

at this point the computer "freezes" and then never goes anywhere. It was recommeded to me to press "ctrl > C", but that didn't work. I know a bit, but I am not technical enough to know what to do at this point. Can anyone assist in this problem. 

P.S. Does anyone have this HP Pavilion Entertainment PC Notebook currently running ubuntu?

Cheers

---

### Post by lingnoi on 2007-01-01
Try turning your wifi on when booting.

If that does not work then try turning off the splash screen so we can get a better picture of where your problem is.

When you get to the boot grub menu edit your OS line by pressing "e".

Then press "e" again on the line with "quiert splash" (second line I think) and delete thouse two words.

Press "b" to boot and then you should be able to see where the actual problem is.

---

### Post by Bigguy2468 on 2007-01-01
Thanks for the reply.
I will try that and report back

---

### Post by Bigguy2468 on 2007-01-01
OK, here I am reporting back and I starting to think this may have something to do with this HP machine just not liking Linux. I remember reading an article on installing Linux on a Compaq being problematic and I am starting to wonder, seeing HP and Compaq are one and the same, if that has something to do with it.

I followed the suggestion that was listed above and here is what I got on boot. By the way, my iso was burnt on a DL DVD disc. I am not going to give you every single line or I would be here typing all day and the wife would kill me. However, these are what appeared to be the more significant ones:

[COLOR="Blue"]110.679956] hda: cdrom_decode_status: status=0x51 (DriveReady SeekComplete Error)

110.703663] hda: cdrom_decode_status: error=0x40 (LastFailedSense = 0x04)[/COLOR]

I then looked futher down the page as there seemed to be a lot of repetitive of the above. Then I found:

[COLOR="Blue"]180:149766] hda: media error (bad sector): status 0x51 (DriveReady SeekComplete Error)

180.174235] hda: media error (bad sector): error=0x30 (LastFailedSense = 0x03)

180.222392] end_request: I/O error, dev hda, sector 66776[/COLOR]

OK, so to me it started to look like the problem might be with the disc I burnt itself, maybe my DVD/RW doesn't like dual layer discs.

So I then get a regular DVD disc and I burn the iso again. I first try to boot up into the live addition, but what do you know, it hangs again right at the same place. I then boot again, follow the instructions listed in the earlier post and watch the boot in text mode. P.S. this disc does boot much faster than the dual layer one.

Anyhow, the computer hangs again, but now I see more text than booting in the GUI mode. Of the line about "Starting Enterprise whatever...." the last 2 lines read as follows:
[COLOR="Blue"]
Checking all FileSystems....
Configuring Network Interfaces....[/COLOR][COLOR="Red"]..
....and right here is freezes![/COLOR]

hmmm....could the problem have something to do with the internal wireless network card???

---

### Post by gn2 on 2007-01-01
Instead of using DVD media, write to a CD-R at a low speed (2-4x) and all should be well.

Don't bother with 64-bit for now, stick with 32.

---

