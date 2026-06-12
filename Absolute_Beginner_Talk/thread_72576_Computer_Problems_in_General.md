---
title: "Computer Problems in General"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by Animus on 2005-10-06
I recently updated my bios by flashing it through windows, and all seemed to go well.  However, when I tried to go into the LiveCD for Ubuntu, I discovered I could no longer configure how my computer boots.  Naturally, next I tried to access the bios, but when I press Del during startup to get in, al l I get is the cursor blinking the corner of the screen.

Windows is working fine, however I have no idea how to restore my bios.  I do have a system restore point for windows set up, but I doubt that this will fix my bios settings (Plus I'll lose most of my programs should I choose to do that)

Also, I have no working floppy drive, but I can't configure my comp to boot from there anyway, so it really doesn't matter

My motherboard is a MSI Nforce 3 Neo2 Platinum...if someone could help me out, that'd be great, as I'm looking forward to installing Ubuntu on the 13th, and this will be impossible if I'm stuck in Windows with no other way to boot up...

Stupid bios (though its most likely my fault its shot anyways)

---

### Post by brentoboy on 2005-10-06
try f2 instead of del

if that doesnt do, try esc, and the other f-keys

maybe the updated bios changed the key that opens the bios settings.

---

### Post by Animus on 2005-10-06
It tells me to hit f10 when I boot up, but I'll give that a try.  I just tried flashing through windows again, with no change.  I'll let you see how it goes.

EDIT-yeah, tried the keys, nothing.

---

### Post by Animus on 2005-10-06
Alright, I found the last bios for this mobo 1.9, however I can't make a boot disk, and the directions given are pretty sketchy (It says not to make a boot disk, but to make a dos boot disk, and run their commands, but I have no idea what they're talking about for the most part.  Then there's the bios recovery method, but the link they give to go to it doesn't work....

Well, I'm going to try and see if I can figure out this other installation method...ugh.

---

### Post by brentoboy on 2005-10-06
The one time I flashed a bios, it wanted me to make a floppy and exit windows. and then boot to the floppy.

From what you are describing, you flashed your bios while you were in windows.
Is that correct?

I'm no expert, but that sounds dangerous -  One of the only things I really remember from flashing was the big "Warning: make sure you arent running windows in the background"

Either way, I dont think that ruined it, becuase if your bios was screwed, you wouldnt be able to boot at all!

My little bro fried a chip through a poorly applied flash, and had to pop out the bios chip and send it back to gigabyte, whe thankfully reflashed it and sent it back for free.

---

### Post by Animus on 2005-10-06
Well, I flashed it through MSI Live Update program, which has a windows specific flash.

I have instructions, but they say to make a Dos boot disk, and then to type some lines in that don't make sense.  All my drives are differently names then the ones they use, and the file isn't named  the same so I don't think it'll work.  It stinks that live update will only let me select and apply the 1.B Bios, but not any of the prior ones.  I downloaded 1.9, but the instructions are poor and rather convuluted.

---

### Post by SilentCacophony on 2005-10-06
Hrm... I'd always been advised that flashing from within Windows was a Bad Idea. Best to do it from a boot floppy, when the floppy ain't broke that is...

Anyway, I know it is generally possible to get a new, pre-flashed replacement bios chip for a nominal fee with at least some manufacturers, should you not find any other way.

---

### Post by SilentCacophony on 2005-10-06
I'm not sure if this is the one you tried (just did a quick google):

[http://www.msi.com.tw/program/support/download/dld/spt_dld_detail.php?UID=607&kind=1]("http://www.msi.com.tw/program/support/download/dld/spt_dld_detail.php?UID=607&kind=1")

This part of the doc looked incorrect to me:

```
7. When you get the A:\ prompt, type the following sequence:
C: <enter>
cd\test <enter>
C:\test> awdfl783m BIOS file
(to save or not to save old BIOS is the user&#8217;s decision)
```

I'd think it should read:
```
7. When you get the A:\ prompt, type the following sequence:

C: <enter>
cd test <enter>
AWFL859G W7025NMS.1B0 <enter>

(to save or not to save old BIOS is the user&#8217;s decision)
```

That would set the working dir to C:\test and run the correct file.

---

### Post by Animus on 2005-10-06
Aha!  Got it.  Downloaded and got Winflash going, and flashed the bios back to 1.3.  Came close to totalling my system though, had to guess which file was the bios and which was the Dos flasher, and then choose the file to load onto my bios.  I'm going to boot into Ubuntu Live CD now I think, as a celebratory measure.

Thanks for your input all, I really appreciate it.


EDIT:  Spoke too soon.  While I can access my bios, when I turn my computer off, it will not turn on.  The only way it will turn on I discovered, is if I pull the powercord out while the computer is off, and then plug it back on.  Otherwise, startup doesn't begin, and my monitor won't turn on and go into sleep mode....

Ugh, this is really annoying me.  I'm going to try and re-flash the computer with another bios, and see if that helps any...

---

### Post by Animus on 2005-10-06
Ugh, reflashed, same problem.  Have to start the computer, unplug it during boot, and then plug it in again in order to get the damn thing to turn on.  It's days like this when I wonder why I didn't just buy a mac...

Oh well, I'm going to hunt around the internet for any similar problems and or solutions.  If anyone has any idea whats going on feel free to let me know, lol

---

### Post by Animus on 2005-10-06
Update!

Got my computer to boot properly, had to wipe the Cmos.  However, I have a problem that perhaps someone here can help me with.  I have an Ubuntu Live CD which I've used twice with no problems.  However, now I put it in, it goes to the install screen and freezes, and I have to reboot.  Any known reason for this happening?

---

