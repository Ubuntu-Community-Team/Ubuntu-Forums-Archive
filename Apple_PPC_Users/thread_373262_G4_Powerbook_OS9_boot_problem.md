---
title: "G4 Powerbook OS9 boot problem"
date: 2007-03-01
forum: Apple PPC Users
---

### Post by soundman13 on 2007-03-01
I installed Ubuntu a few weeks back & had it running as a dual boot machine on my G4 Powerbook. If turned on holding the alt key, it would display the choice of Linux, OSX & OS9.

OSX & Ubuntu worked fine - I assumed that OS9 did, but I don't think that I actually checked it as I don't use it very often.

I have since removed Ubuntu & I'm left with a curious problem.

The mac will boot into OSX without any problems. Startup disk with OSX shows & recognizes my OS9 partition as being bootable. But when OS9 is chosen as a startup disk, I  am greeted with a blank grey screen & then the blinking folder? icon....not good.

To expand on this further - I have tried booting from OS9 based CD's (system rescue type disks)....these won't boot either. Except one which will boot fully into OS9 - this disk was created to test SCSI & Firewire drives & won't see/mount the internal laptop drive/partitions at all. At least I know that OS9 is still functional to some degree!

typically I can't find any OS9 install cd's so I haven't been able to try booting from one of those yet - or try a new install.

Finally I should also mention that classic runs perfectly from within OSX...i still need it to boot into OS9 as the software I wish to use won't run in classic.

Sorry for the long post - any help or pointers would be gratefully received.

thanks

Tom

---

### Post by machead5 on 2007-03-05
Hi
First off, when you removed Ubuntu, did you erase the partition it was on?

The blinking folder means that the OS9 system folder can't be located. First try resetting PRAM, restart and immediately hold down option-control-p-r and continue holding until you hear 3 startup chimes. This is a stretch on your fingers so get comfy.

If that doesn't work reset nvram by re-starting and holdong down option-control-o-f which will take you to Open Firmware. type in...

  reset-nvram (press enter)
  set-defaults (press enter)
 reset-all (press enter)

This should immediately restart and hopefully find your OS9 system folder

---

