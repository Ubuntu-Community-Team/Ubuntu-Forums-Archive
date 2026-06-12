---
title: "Has Ubuntu changed my partitions making grub unusable?"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by john61930 on 2007-01-22
I’ve been wrestling with a problem for over two weeks. Grub fails to 
be usable from the Mbr. I have 3 other boxes which multi-boot up to 
five o/ss without problem and were easy to install.

I built a new box (for testing and to try to learn programming) with:-
	An Asrock 775Dual-VSTA M/board + Intel 3.2Gig CPU.
	1Gig DDR Memory.
	Maxtor 120 Gig IDE PATA Hard Drive.
	Combo CD/DVD Writer, and a Floppy Drive.
	Asus ATI Radeon A9250 128 Mb Graphics Card.

Two days ago I started anew, and did the following:-

1. Wiped the Hard Disk.
2. Using Linux fdisk, created three 20 Gig partitions, Fat, Ext2 and Ext2.
     Verified the creations were contiguous using cfdisk.
3. Installed Win 2000 Pro on Hda1 - it booted OK.
4. Installed Debian Sarge (my normal Distro) in Hda2, and got it to install
     Grub on the Mbr. Something went onto the Mbr as neither o/s would
     boot. However, putting Grub on a floppy  and getting a Grub prompt
     allows me to boot into either by using the details obtained by using Knoppix.
5. Installed Ubuntu Edgy Eft in Hda3 and let it install Grub on the Mbr. It
     correctly found W2000 and Debian, and knowing it would overwrite the
     Mbr, it should have provided multi boot of the three o/ss. It didn’t!.
     Now, I could not boot Ubuntu from a Grub prompt, but I could still
     boot the other two that way.

Here, I decided to see what fdisk had to say. It disclosed ‘missing’ sectors
between Hda2 and Hda3 and also between Hda3 and Hda 5.
Cfdisk shows a similar situation but with slightly different figures. It does
identify 3.33 Mb between Hda2 and Hda3 as ‘unusable.

Starting to assume the Drive is faulty, I downloaded Maxtor’s testing
software and spent hours today running all tests - the lengthy scanning
programme, three passes of the burn-in test, the installation confirmation.
Everything gave a clean bill of health.

The only thing that could have changed the partitioning must be the Ubuntu
installation. It’s use of parted must have messed with my fdisk settings. To me that 
would be clear if Sarge had got Grub onto the Mbr as it normally does.

I don’t have the computer expertise to go further - can some expert please 
help me to sort things out?

Regards,

John.

---

### Post by Hendrixski on 2007-01-22
Did you go through the 'advanced' install, or the automatic one?  Whenever doing something as complex as tripple booting, be wary of 'automations'.
Also, have you checked that it isn't something as simple as a setting inside GRUB itself?  It's usually the simple things that hammer us.


Good luck in programming by the way.  it's much more fun than dealing with the kind of crap you're going through now.

---

### Post by john61930 on 2007-01-23
Thanks, Hendrixski.

I tried all install options - with the 'automatic' type version, parted seemed to have a
mind of its own. The 'expert' option appeared to allow me to have my own way, but as
I said the partitioning I created using fdisk was 'cocked up'.

Whilst certainly no grub expert, I do know just enough to ensure there's no setting
or syntax error there. In fact, I used Knoppix to verify the menu.lists compiled by each
Linux distros were correct (I have other boxes multi-booting, and I refreshed my memory
on the config of grub in these - details of 'root', 'kernel' and 'initrd' are of course different.

If Debian would boot grub from the Mbr, I would blame the Ubunbtu installer, but as I
said it doesn't. Then there is the situation where I can boot Debian fron a Grub prompt
but not Ubuntu.

This impasse is compounded by the fact that I'm almost 77 and have no one in a working
environment to discuss matters with. Additionally, I never studied any scientific subject,
I was a classics scholar (and that doesn't help with computer science!). I can only use
a little relevant knowledge plus commonsense to try to resolve the issue.

Is it due to a Mobo issue? A Bios one (I see nothing untoward - but then I could easily
miss something)? Can Grub not 'see' beyond certain cylinders - if I've googled well,
it should 'see' up to 2TB? I've done so much googling that I've become 'google-eyed!

Slightly changing the view, do you know if there's any way to read exactly what is on
the Mbr? I believe there are two areas within it. I've fdisked /Mbr and re-installed Grub from Debian without effect.

---

