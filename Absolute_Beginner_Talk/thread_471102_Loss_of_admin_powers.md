---
title: "Loss of admin powers?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by PureNRG on 2007-06-11
Well, i've been running Ubuntu for a total of two days so far. And after
adding a new user, checking all the admin rights boxes, and then
deleting the previous user, everything was going great. Until when
I turned my computer on this morning, logged in, and realized that
half of my admin options in the System menu, as well as the add/
delete programs option in the Applications menu was missing as 
well. 
What could've caused me to loose my administrative options, after
I've been able to use them for the past few days?:-?


Thanks for your time,
~ZSG

---

### Post by guardsman85 on 2007-06-11
Not sure how you lost them, but I might be able to help you get them back (assuming that's the ultimate goal here).

Right-click the menu  >>  Edit Menus  >>  Scroll down to the System menu  >>  Make sure items/folders you want to display are checked

---

### Post by PureNRG on 2007-06-11
Well that's the thing. All of the missing items are checked. :mad:
I can still check/uncheck items that are currently visable, and they
dissapear/reapear, but the there are some that just refuse to 
show up!

::kicks computer::

Would it be easier just to reinstall Ubuntu to fix the problems? :(

---

### Post by guardsman85 on 2007-06-11
> **PureNRG said:**
> Would it be easier just to reinstall Ubuntu to fix the problems? :(

The troubleshooter in me says, "No, NO, THERE'S GOT TO BE A BETTER WAY!!"

The slacker/guy-at-the-end-of-a-long-day in me says, "Heck, yes!"

;)

---

### Post by gerscht on 2007-06-11
you can boot with your live CD,
mount your root partition (assuming it's /dev/hda1, otherwise change in code below) and change the root
```

sudo mkdir /mnt/root
sudo mount -t ext3 /dev/hda1 /mnt/root
sudo chroot /mnt/root

```
Now you should be able to add/ change users and groups via the function on the live CD

If you've done that, reboot. It should have written the changed user data on your 'original' root partition.

---

### Post by PureNRG on 2007-06-11
Haha, well I'll keep plugging-away at it, and try to find out a way to make myself
an administrator, when there are no administrators on this computer >_<
Is there a command I can input into the terminal to grant myself administrator
abilities? Because I set the sudo password already, it's just that my Users are
all without administrator rights.
Well at least I *think* that's the problem. :-?

---

### Post by steve.horsley on 2007-06-11
A simple fix (if it works) would be to boot into recovery mode and issue this command:
**adduser <username> admin**
but of course replace <username> with the user name that can't do the admin tasks. Then reboot and try again.

I suspect you just didn't add the new user to the admin group (whcih means he's not allowed to use sudo).

---

### Post by gerscht on 2007-06-11
> **steve.horsley said:**
> A simple fix (if it works) would be to boot into recovery mode and issue this command:
**adduser <username> admin**
but of course replace <username> with the user name that can't do the admin tasks. Then reboot and try again.
I don't think that will work, as you are authenticated via the same system (if I can say so). If you do it as described above (booting from Live CD and chroot on disk), it should use the credentials from the live CD, but actually write onto the root drive (I haven't tested it ;)

---

### Post by steve.horsley on 2007-06-12
But recovery mode drops you in as root. Handy.

---

