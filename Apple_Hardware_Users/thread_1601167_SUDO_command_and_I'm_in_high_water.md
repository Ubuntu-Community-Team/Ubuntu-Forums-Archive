---
title: "SUDO command and I'm in high water"
date: 2010-10-19
forum: Apple Hardware Users
---

### Post by SynoeciousCourageous on 2010-10-19
OK.  Here's the story.  I have a Mac Book G4 that I got at auction a few years ago.  I never could afford an OS so I installed. Ubuntu 6.01 (or something very similar) and when messing with the command screen in yaboot under SUDO I accidentally typed "Reboot'" instead of just "Reboot".  See the difference?  Well my computer did as well and now after every command I get simply the > sign.  In other words, whatever I try to command my computer in yaboot ends up looking like this:
>

And after hitting enter several times I get this:
>
>
>
>

So nothing seems to work.  What I would like to know is if there is a way I can undo my foolish fingery in order to get Ubuntu running again.  I can't even turn it off.  Also, the DVD drive on the Mac Book G4 doesn't work so I would have to update, should I choose that route, with a USB drive.  Can anybody help me?

Thanks!

---

### Post by zeroti on 2010-10-20
i wasn't aware that you could use sudo in yaboot. did you change your yaboot.conf file and run "sudo ybin" instead? if you made an error in the conf file, and then ran that command, you may have made your computer unable to automatically reboot.

an easy way to fix this is to reinstall. or you could boot up from the live cd and copy the /etc/yaboot.conf file to your hard drive, unmount it and then run ybin. (you'd have to read about the command with "man ybin" for the correct options. my guess is that it would be "sudo ybin -b /dev/hda2", without the quotes. check to see if that is the the bootstrap partition while you still have the disk mounted. it should be about 1MB.)

good luck!

---

### Post by conundrumx on 2010-10-20
Try ^c.

---

