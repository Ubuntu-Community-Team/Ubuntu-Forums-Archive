---
title: "How Many PPC Edgy Eft Users Out There?"
date: 2006-07-16
forum: Apple PPC Users
---

### Post by zachws on 2006-07-16
How many of you PPCers have made the jump to Edgy Eft?

How is it working out?

---

### Post by gThree on 2006-07-16
When I first installed Hoary, I didn't mind pre-release versions because I still did most of my work in OSX and just wanted to check Linux out.  Now that I rely on Ubuntu/Kubuntu, I'm much less likely to risk an early upgrade.  So, in my case, the reward Canonical gets for putting out a quality Linux desktop release is one less PPC tester :) ....

---

### Post by rasec on 2006-07-16
I think I'll wait until it becomes official. By the way, has anyone published a list of the changes in edgy yet? I hope they resolve the issue with network manager not working with wpa passphrases, and I would like edgy to utilize the yaboot.conf more for kernel updates. By utilizing the yaboot.conf, I mean that I if I have 10 kernels installed on my system, I want to be able to select which kernel I want to use, not just the two most recently installed ones.

I just temporary switched over to fedora to see how their kernel upgrades were handled, and it turns out that it has a universal x86/ppc installer script that automatically adds the new kernels to either grub or yaboot. I know that ubuntu has a similar update-grub script listed in /etc/kernel-img.conf for the x86, so I think the ppc needs a update-yaboot script. 

Anyway, those are just my two complaints about dapper.

---

### Post by calum on 2006-07-16
> **zachws said:**
> How many of you PPCers have made the jump to Edgy Eft?

How is it working out?

I haven't installed from the ISO, but I upgraded all my existing dapper packages from the eft repository.  There are certainly a few issues at the moment; gnome-panel runs at 70%+ CPU all the time, and some apps (evolution, glade) won't start for me due to X "BadParam" errors.

---

### Post by zachws on 2006-07-16
I tried the updating repos from "dapper" to "edgy" too, several times. Each time the system failed to load hardware drivers at reboot. I have yet to try the cd but will post the results on my G4 iBook.

---

