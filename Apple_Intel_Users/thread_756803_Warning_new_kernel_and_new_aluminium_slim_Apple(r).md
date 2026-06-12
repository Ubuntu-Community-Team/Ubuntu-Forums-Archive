---
title: "Warning: new kernel and new aluminium slim Apple(r) keyboard"
date: 2008-04-16
forum: Apple Intel Users
---

### Post by blurg on 2008-04-16
Hi,

I am new to Ubuntu. I installed Hardy 8.04 beta off the LiveCD on my iMac7,1 20" (new aluminium model) and all was fine.  However the kernel on the CD contains a 'fix' for the newest MacBook* keyboards which has caused a regression issue for the new aluminium wired keyboard: it took me a lot of hunting to find this issue it is flagged up as a bug in Launchpad but I'm guessing most people will look here first, hence my post.

The bug: the kernel thinks the aluminium wired keyboard is a laptop keyboard so (1) if you touch the key above 7 (looks like box with an X through it) on the numeric keypad it turns all keys off except enter on the numpad and turns the keys around UIOP area into a numpad HOWEVER pressing that key again DOES NOT revert the keyboard to normal function! and (2) the numpad won't work at all

Solution: (1) the kernel people need to fix this patch (2) if this happens to you press F6 twice and your keyboard will return to normal use (except the numpad of course).

Also watch out for the F-keys: another kernel patch has made them function as they do in Mac OS X which was not I believe how they functioned previously under linux. Use Fn+F-key to get the F-key rather than the printed Mac OS X type function (e.g. volume, brightness etc). Search launchpad I think there is a fix for this there but I don't have time to find it again and link it.

All the best,

blurg

Edit: The link to the launchpad bug report is: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887")

---

### Post by cyberdork33 on 2008-04-16
The Fn key functionality is how it has worked for the Macbook / Macbook Pro keyboards.

It would be best to post your confirmation of the bug and your findings if you have not done so already!

EDIT: After checking the bug report, it is marked as triaged, which means the fix should make it into the kernel... evenutally

---

### Post by alcyon on 2008-04-24
I'm seeing this same issue using an apple pro keyboard on a non apple pc now I've upgraded to Hardy Heron, was working fine on Gutsy.

Any idea when this might be fixed anyone or if there is anything else I can do other than having to press F6 twice?


Also if I try to change my keyboard layout from within the prefs I get an "Error activating XKB configuration"

Any help much appreciated!!

---

### Post by justmehere on 2008-04-26
I can confirm that the slim apple wired keyboard on non apple hardware broke when I upgraded from 7.10 to 8.04. I'm using a different keyboard till there is a fix or a workaround.

The fn+function key change seems like a backwards step. It makes normal things like renaming files with f2 very difficult.

---

### Post by djungelmums on 2008-05-04
My keyboard also stopped functioning :( waiting for fix :)

---

### Post by cyberdork33 on 2008-05-04
There is a new apple users' forum. Please post there:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

