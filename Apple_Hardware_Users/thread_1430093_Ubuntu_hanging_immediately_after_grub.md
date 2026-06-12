---
title: "Ubuntu hanging immediately after grub"
date: 2010-03-14
forum: Apple Hardware Users
---

### Post by rhysaj92 on 2010-03-14
I have just installed Ubuntu 9.10 on my macbook, i am using refit, and everything is fine until I get to booting ubuntu, i get to grub, and press enter to boot ubuntu but the screen just goes blank and does nothing.
Any help please?

---

### Post by wireonfire on 2010-03-15
Looks  like grub is not installed properly.  You can boot with the CD (do a live boot) and resintall grub.  There are plenty posts on the internet on how to do that.

---

### Post by mcoleman44 on 2010-03-15
Well if you dont have anything important saved I would just do a fresh install. Because if the grub menu actually shows up and lets you enter a choice then it might not be a grub problem. So take another 30 minutes, reinstall and if that doesn't work we'll see whats going on then.

---

### Post by rhysaj92 on 2010-03-15
If it makes a difference, I had to disable all the options on my live disk to even get it to start.

---

### Post by mcoleman44 on 2010-03-15
What options?

---

### Post by rhysaj92 on 2010-03-15
The live cd was coming up with a flashing horizontal cursor bar then would go blank, so I went to other options and selected

acpi=off
noapic
nolapic
edd=on
nodmraid

selecting these let me boot into the live cd

---

### Post by mcoleman44 on 2010-03-15
Thats kinda strange. Im not sure if I know what to tell you about the options. But like I said, the easiest solution, I feel, would be to reinstall. But thats just me.

---

### Post by linuxopjemac on 2010-03-15
It's always good to read the special settings for your type of macbook and type of Ubuntu distro [here]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages").

---

### Post by rhysaj92 on 2010-03-15
I re-installed ubuntu following those instructions, which were pretty similar to what I did in the first place, but I still have the same problem. If this problem can't be fixed, would anyone be able to suggest a better distro for a macbook?

---

### Post by linuxopjemac on 2010-03-15
I guess you have to put the options you gave in for the liveCD, also for the installed version in /etc/default/grub

```
"GRUB_CMDLINE_LINUX="acpi=off""
```

then you need to update grub

```
sudo update-grub
```

You also need to sync the partition table within rEFIt's 0.14 partition tool, if you haven't done that already.

---

### Post by jamesey on 2010-03-15
Make sure you're using refit 0.14

Refit 0.13 and Ubuntu 9.10 Don't play well together. You have to do a lot of grunt work to make them play nice together.

---

### Post by rhysaj92 on 2010-03-16
After attempting to get ubuntu to work, it killed my drive, thank God for backing up. So, at least until I get a new computer or a new ubuntu, I might try other stuff.
Thanks for your help everyone.

---

