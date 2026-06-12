---
title: "Grub Lost!!!!! Urgent"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-08-29
Hi all
I was having Ubuntu only. Now my sis got a new phone and to see its Cd she installed windows now my grub is lost ... :( How can I re install the grub so that I can boot into Ubuntu and Xp both :(  So plz lemme know soon :) If there are easy method then plz lemme know :D

---

### Post by ripit on 2007-08-29
I think this page will help you.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Dark Star on 2007-08-29
That's confusing :( Can some 1 post what to do :) by dictating steps :p Well I have windows now which I hate .. Plz help me torestore Ubuntu option in boot list :(

---

### Post by xtapolapaktl on 2007-08-29
Basically the quick start guide on the page is all you need to do, and it's already in steps so it's easy to follow.

Just take the steps one at a time.

---

### Post by Surkow on 2007-08-29
The goal is to replace the MBR of Windows with Grub, the boot loader of Ubuntu.
You will have to do the following:

[LIST]
[*]Boot from the live CD (just the standard install CD);
[*]Start the Grub prompt where you can alter stuff in the terminal with "sudo grub";
[*]Tell Grub what partition the root partition is where it's files are located with "root (hd$,$)". The first $ in hd$,$ is the physical hard drive number. The second $ is the partition number where Ubuntu is installed. You can use "(tab" (using the tab button on your keyboard) to autocomplete these numbers.
[*]Tell Grub what the setup hard drive is with "setup (hd$)". The $ in hd$ is the physical hard drive number.
[*]Type "quit" and press enter to exit the Grub prompt.
[*]Reboot to see if Grub installed itself succesfully.
[/LIST]

---

