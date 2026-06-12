---
title: "Help with Grub Boot Repair (Ubuntu 16.04.1 LTS via USB on MacBook with OSX)"
date: 2016-12-08
forum: Apple Hardware Users
---

### Post by eeckul on 2016-12-08
Hello.


I'm using a MacBook Pro with OSX. It has a 500GB SSD with no additional partitions.


I used "unetbootin" to create a Ubuntu USB and booted off the USB. I used the "Try Ubuntu without installing" option to boot into Ubuntu. From there, I installed Ubuntu onto *another* USB in order to have a persistent Ubuntu installation on a USB. It works fine when I turn on the MacBook with the USB inserted.


However, I get a GRUB terminal screen anytime I boot the MacBook without the USB inserted. The message at the top reads "Minimal BASH like line editing is supported. For the first word, TAB lists possible command completions. anywhere else TAB lists possible device or file completions.". If I type "exit", it boots into OSX just fine. I would like to remove that GRUB terminal screen and restore the MacBook to how it previously boots directly into OSX. How can I do that?


I tried following the instructions for Boot-Repair using the "Recommended Repair" option, but no luck. Here's the log output: [http://paste.ubuntu.com/23599206/](http://paste.ubuntu.com/23599206/)

Thanks in advance.

---

### Post by howefield on 2016-12-08
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by eeckul on 2016-12-09
Resolved.

This is how I ended up fixing it.

1. Boot into OSX.
2. Open Terminal and enter "diskutil list".
3. Find the disk with type=EFI.
4. Mount the EFI disk by entering "diskutil mount /dev/disk0s1". (Replace "disk0s1" with your EFI disk.)
5. Open Finder and browse to the newly mounted drive called EFI.
6. Inside the drive there is an EFI folder.
7. Inside the EFI folder there's an "APPLE" folder and a "ubuntu" folder.
8. Delete the "ubuntu" folder.
9. Restart.

Found the solution here: [http://askubuntu.com/a/703384](http://askubuntu.com/a/703384)

---

