---
title: "Boot Loader Hell"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by broadhead on 2005-08-07
Ive been drifting from forum to forum for a thread about this, but nothing so far has help, so im hoping one of you might have a good idea to figure this out.  Ive done the ubuntu install about 6 times now, one of them on a desktop running windows 2000 (which worked perfectly) and the other 5 on this laptop, which is the problem.  I just got a new harddrive for it, installed xp, and then tried installing ubuntu.  The installation goes along smoothly until the point where it should install GRUB but does a fatal error instead.  So, i installed LILO to the mbr (or so it would seem) and that worked ok.  The problem is when i restart, i dont get a choice of OS to choose from like i did when using GRUB.  Though i usually think of seeing less of windows as a good thing, i still need to run CAD software on it, so i really need to be able to boot my windows from time to time.  Thanks alot in advance!

JF

---

### Post by jasmuz on 2005-08-07
I have no idea for your problem, but there is a lot of CAD software you can try out for Ubuntu.

xtrkcad - Sillub Technologies Model Train Track CAD Program
varkon - A CAD-system with parametric modelling
pythoncad - Computer Aided Drafting (CAD) program
qcad - A professional CAD System

---

### Post by coolblue on 2005-08-07
Hi broadhead....I'd recommend u switch to a very newbie-friendly distro like Suse 9.3 pro....check out its BEAUTIFUL screenshots at osdir...mmmmm:) And with Suse, no matter what goes wrong, u can easily fix all that with the Suse install CD in a GRAPHICAL manner....in the bootloader option of Yast....it will scan ur bootloader and other things for inconsistencies and automatically fix things up for u...WAYYYYYYYY COOOOOOOOOL!
By the way theres this FREE suse admin guide & suse user guide which can download for free...they contain a lot of useful info on linux...apart from suse itself.

Which does not mean that Kubuntu is a bad distro of course....its lovely...its just that its not tooo easy on newbies who frequently happen to run into problems....I too have faced such things as u so I can understand very well:) And I'm also..well..just a little ahead than a newbie:)

Best of luck! BTW Suse is AWESOME for laptops!!

---

### Post by wvslkr on 2005-08-07
Add something like this to your /etc/lilo.conf

other = /dev/hda3
label = WinXP
table = /dev/hda
Substitute the location of your Win for /dev/hda3

Run /sbin/lilo    if all goes well that should do it.

---

### Post by poofyhairguy on 2005-08-07
[QUOTE=broadhead] The installation goes along smoothly until the point where it should install GRUB but does a fatal error instead.    [/QUOTE]

You had a bunk install CD.

---

### Post by broadhead on 2005-08-07
aright, thanks guys.  will definatly take a look at autoCAD replacements, though i will probably stick with autodesk just to keep things simple.  coolblue, thanks for your suggestion on using suse, im actually downloading it right now, so we'll see how that goes.  thanks alot, and hope it works out.

---

