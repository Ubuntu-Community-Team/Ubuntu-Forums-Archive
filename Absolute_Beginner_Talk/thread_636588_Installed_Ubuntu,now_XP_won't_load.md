---
title: "Installed Ubuntu,now XP won't load"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by 4iko on 2007-12-10
OK.I just installed Ubuntu,but now my XP Pro won't load.Ubuntu loads fine but when I try to load XP I get a blue screen saying:
 "A problem has been detected and windows has been shut down to prevent damage to your computer.

  UNMOUNTABLE_BOOT_VOLUME

 If problems continue ,disable or remove any newly listed hardware or software...
...
 Disable BIOS memory options such as caching or shadowing.."

i have not installed any new software or hardware and haven't done any changes in the BIOS...

Any ideas?
Thanx

---

### Post by Threbus5 on 2007-12-10
Hi,

Someone more experienced will certainly be able to provide additional guidance.

I am assuming that during the install you selected a dual boot option and can select to start either Windows or Ubuntu.

Under similar circumstances I recall observing more than one choice displayed for the Windows start option(s). In my experience the top or first Windows start option failed. If more than one Windows start option is available, try selecting one of the other Windows start choices. 

Also, search the forum for MBR (master boot record) correction procedures.

Try rebuilding the MBR as described here: [http://ubuntuforums.org/showthread.php?t=616540#2](http://ubuntuforums.org/showthread.php?t=616540#2)

Good luck.

---

### Post by rockinlinux on 2007-12-10
ok here are a few questions i am going to ask to get more info so i can help you:

1) do you get the grub screen?
2)os ther more than one windows entry if you get the grub screen?
3)do you have a Super Grub Disk?

if you ont have a Super Grub Disk please download it from [here](http://supergrub.forjamari.linex.org/) and burn it at the slowest speed to ensure a good burn. This disk will allow you to try to boot windows and then you will be able to see if windows itself has an error or if it has to do with grub.

---

