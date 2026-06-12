---
title: "Installing Ubuntu Again Lol"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by ochana25 on 2008-01-27
hey everyone umm i just formatted put xp back now i wanna add ubuntu in again and be able to choose which os at startup can someone help me out so i install it properly i have the ubuntu live cd

---

### Post by CCNA_student on 2008-01-27
If you want Ubuntu installed now you should be able to just stick in your disc and on step 4 of installation, use the second choice which is something like "Resize IDE 0, install Ubuntu in remaining area". Then after you finished installing and restarting your computer the GRUB boot menu should come up asking what OS you want to use. And please be sure to defragment your hard drive and back up all data before installing Ubuntu, as many people do not do this. I also put more detailed instructions on my Linux User's Group website if you would like to look. Good luck.

Sin Cere,

CCNA

---

### Post by ochana25 on 2008-01-27
k got it workin perfect one more thing sorry umm i wanna run em both at the same time on the cube here r my pc requirements u think it will run ok its not that crazy  p4 2.67ghz,  gforce 6200, p4800 asus motherboard and 1 gig memory

---

### Post by nwadams on 2008-01-27
you want to do what:O???

---

### Post by JoshuaRL on 2008-01-27
Not sure it can do what you want it to exactly.  If you want to run XP within Ubuntu you'll need to run it in a virtual environment.  If you put that on one desktop, then you can do that through cube.  Try this thread:

[http://ubuntuforums.org/showthread.php?t=631671](http://ubuntuforums.org/showthread.php?t=631671)

---

### Post by Scunizi on 2008-01-27
I get the impression you want to run windows inside a virtual machine so you can have Ubuntu as the main operating system and run windows inside of a "window" in Ubuntu.. If that's correct you either have to stick with the dual boot you seem to have going now or reinstall windows in a virtual machine.  When you do that and you have the same disk loaded for the win side of the dual boot you'll have validation problems.  Load one then validate it, load the VM version and validate it. back to the first and validate again etc.. pick one and stick with it.  Just remember that windows in a virtual machine has a virtual machine "video driver". you can't use nVidia's or Ati's in the VM so some games won't run..

---

### Post by emarkd on 2008-01-27
I second the info provided by JoshuaRL above.  It'll work just fine if you're careful doing it.  And your computer is plenty powerful.  I've got a 1.6 Ghz laptop with 1.25 Gigs RAM that handles this with no problems.  That's assuming you don't want to play games in your virtual windows, of course.  That's still a no-go, as far as I know.

---

### Post by emarkd on 2008-01-27
One quick clarification on a point that Scunizi makes above:

If you leave Windows on its own physical partition and set it up to boot both in a virtual machine and directly on your hardware, there can be validation/activation issues with some windows software.  I have this setup myself and while windows never complains, sometimes office will.  You have two options:

1.  Deal with the occasional activation headache because you still want to boot into windows and play games sometimes.

2.  Reinstall windows fully inside the virtual machine and give up 3D games.

---

### Post by JoshuaRL on 2008-01-27
> **emarkd said:**
> One quick clarification on a point that Scunizi makes above:

If you leave Windows on its own physical partition and set it up to boot both in a virtual machine and directly on your hardware, there can be validation/activation issues with some windows software.  I have this setup myself and while windows never complains, sometimes office will.  You have two options:

1.  Deal with the occasional activation headache because you still want to boot into windows and play games sometimes.

2.  Reinstall windows fully inside the virtual machine and give up 3D games.

I agree, however there is one coveat.  If you decide to reinstall XP virtually, you will eat at least 5gb of space on your HD.  So something to keep in mind if you are short of space.

---

### Post by ochana25 on 2008-01-27
hmm im addicted to world of warcraft lol as long as i can still play it then i wanna do it if i cant then i wont. one more thing ubuntu is the best lol

---

### Post by emarkd on 2008-01-27
According to [http://appdb.winehq.org/](http://appdb.winehq.org/), you can install WoW in Ubuntu using Wine and don't even need Windows!

---

