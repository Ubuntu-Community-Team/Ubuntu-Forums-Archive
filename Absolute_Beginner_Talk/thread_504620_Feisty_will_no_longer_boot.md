---
title: "Feisty will no longer boot"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by tonyzbj42 on 2007-07-19
After weeks of trouble-free operation, my father-in-law's Dell will no longer boot into Ubuntu. The display reaches the Dell splash screen, then Starting... then-nothing. A black screen. My newbie status means that I need my hand held through problems (which I have never had on my own Ubuntu set up).
Can anyone walk me through possible solutions please?

Tony(UK)

---

### Post by starcraft.man on 2007-07-19
> **tonyzbj42 said:**
> After weeks of trouble-free operation, my father-in-law's Dell will no longer boot into Ubuntu. The display reaches the Dell splash screen, then Starting... then-nothing. A black screen. My newbie status means that I need my hand held through problems (which I have never had on my own Ubuntu set up).
Can anyone walk me through possible solutions please?

Tony(UK)

Ok since your in the UK I assume it wasn't a preinstalled Ubuntu Dell. With that in mind a few things it is best to mention to get help. What was the dell model (link to the specs would be nice)? Did you add or customize any hardware after? Did you have any troubles with the original install leading to special modifications or changes specific to your system? Did you (or your dad) do anything special right before Ubuntu stopped being bootable? This might include but not be limited to updates, change in kernel, editing grub, altering xorg, installing prorpietary drivers... 

It would be best if you answer all of the above, there are lots of reasons a machine can become unbootable.

---

### Post by wolfen69 on 2007-07-19
did you try recovery mode? (hit esc when grub is loading)

---

### Post by candtalan on 2007-07-19
if it boots feisty live cd then you have a start and it might be comforting to know.... :-)

using the live cd or using maybe another distro such as knoppix live cd it might be a little easier to do any editing that might be necessary.
question: - do you have any important data already backed up at this stage?

hth

---

### Post by tonyzbj42 on 2007-07-19
Thanks for the replies so far, I will try esc tomorrow, as he is sending his machine here. Is there a 'repair' option, as the booting problem comes after an update. Would this problem be kernel related? If there is an option to choose another kernel, would Ubuntu remember this option for subsequent boots?

---

### Post by twiceasworn on 2007-07-19
Well to be totally honest it could be any number of things causing the machine not to boot.  Do you know if he changed anything recently?  Once you get the machine I would be interested to know if you can get to a command line.  Hopefully you can, that would make things a bit easier.

---

### Post by tonyzbj42 on 2007-07-20
Thank you again for the replies. I booted the machine an pressed esc and selected 'recovery mode'. Ubuntu went through and checked various components, and failed on 'fsck', telling me to run this manually. At the command prompt, I typed in fsck, and this bought up several occurrences of hard disc related cluster errors, with the option to repair each. On answering yes to each, Ubuntu told me to reboot, and when restating, it booted normally into the Ubuntu login screen, and subsequently on to the desk top. All functions were normal, and I have rebooted several times to test. All is now fine. So, questions remain in my mind about the machine. Why would it develop these cluster errors? Would it be a failing hard drive? Or, is it a throwback from when Windows was installed (I installed Ubuntu using the 'whole disc' option in the installation wizard).

Thanks everyone for all your help - I have never encountered such a helpful forum of participants and members. It is the whole package of support, community and operating system that makes Ubuntu number one!

Tony(UK)

---

### Post by whorton on 2007-07-20
I my PC experience the bad disk cluster error means most likely the HDD is failing. I would contact dell explain the problems you are having and get them to send you a replacement HDD.

---

### Post by tonyzbj42 on 2007-07-22
Thank you very much to all that replied - a hard drive replacement is on it's way.

Tony(UK)

---

