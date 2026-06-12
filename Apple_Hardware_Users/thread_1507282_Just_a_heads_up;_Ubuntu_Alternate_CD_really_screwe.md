---
title: "Just a heads up; Ubuntu Alternate CD really screwed my system up."
date: 2010-06-11
forum: Apple Hardware Users
---

### Post by frikker on 2010-06-11
Hey everyone.  Just a heads up.

[LIST]
[*]I had a working 9.04 install on my macbook 2,1
[*]Dual booting OS X with rEFIt
[/LIST]
I just wanted to create a bootable USB drive.  My normal attempts had failed, so I just said "no big deal I'll just use the Ubuntu Alternate DVD and install directly onto my usb drive, /dev/sdb".  That worked, and it installed, but I haven't even been able to test it yet (more pressing issues at hand).

What the install DID do was fudge with the grub configuration on /dev/sda, which is where my original Ubuntu install lives.  Not sure how, considering it asked me zero times about GRUB configuration (I assumed it just went ahead and put it on /dev/sdb).  Now I get this elusive error: "GRUB Hard Disk Error" when I try and boot my Ubuntu install from rEFIt.  From searching around it appears this error is unsolvable in most situations and no one knows what it means.  Great.

I had been wanting to upgrade to 9.10 anyways, so now I can.  

I tried "grub-install" and it gave the impression that it worked successfully (from the LiveCD).  All that it ended up doing was creating an additional rEFIt icon that gives the same error.  I now have "Boot Linux from HD" and "Boot Linux from Partition 3" (/dev/sda3)

Any suggestions would be great, but honestly I'm in a time crunch and need an operational system, so I'll probably just be reformatting and re-installing.  Any idea why on earth my grub install would be hosed?

---

### Post by frikker on 2010-06-11
Awesome; now my fresh Ubuntu 9.10 install has the same error: GRUB Hard Disk Error.

So.  What now? Is there something I have to do to my partition tables or something? OS X boots fine.

---

### Post by frikker on 2010-06-11
Current Situation:
  * If I hold down "alt" and boot from Hard Drive, same Grub error.
  * I booted from a Super Grub CD, did "Detect all OSs", and booted that way.  It worked! Would have been nice to do without reformatting, but oh well.

So now... what the crap do I do? I can boot from SuperGrub -> Detect OSes, but both my EFI booter and standard hard drive boot with the alt key do not work.  I have re-installed GRUB as many ways and times as I can imagine, still to no avail.

Suggestions? I currently can't boot without SuperGrub.

---

### Post by cyberdork33 on 2010-06-11
The installer asks you about grub on the very last screen of the install setup. There is an "Advanced" button (or at least that is what it used to say) where you can choose where to install Grub (or to not install it at all).

Anyway, onto your issue... the problem is that the grub installer tried to make your external drive the primary for booting, and that screws things up... you can manually install grub back into your internal drive. You can also make a rEFIt cd or USB drive and boot from that. Something else to try is boot from your OSX install dvd and use the startup disk tool to set the partition where rEFIt was installed as the active (bootable) partition.

Been a long time since I have worked any of this stuff, so sorry if the above doesn't help anymore. there are several threads about reinstalling grub, they should help you out.

---

### Post by frikker on 2010-06-11
That would make a lot of sense.  I'll try to get into OS X and re-set the EFI partition as the bootable partition.  Thanks for the info.

Every grub installation I've tried so far has failed unfortunately.

---

