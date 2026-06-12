---
title: "[SOLVED] GRUB Help"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by privaterolf on 2008-04-03
New issue:
If I mess up my grub list file, will I be able to use a Ubuntu Live CD or ANYTHING to fix it, if I can't boot any OS?

--------------------------------------------------------------------------------

Alright, here's my issue.

I need to list Windows as the first boot option [this I know how to do]
I'd like it so I can group Windows in One Category, and Ubuntu boot ups in another.

What I mean

At boot up:

Select your OS:

Windows
Ubuntu

You key down to Ubuntu and hit enter

Select your OS/boot up option:

Ubuntu
Safe mode
The other one I can't remember the name of

Is there a way to do this?

---

### Post by rsambuca on 2008-04-03
You should be able to do that, but **why **would be my first question :)

Anyways, you would have to set up a separate /boot partition with the first grub containing just your desired Windows and Ubuntu options.  Then, for the Ubuntu selection you will have it point to another grub on your Ubuntu partition via chainloading.  Should work in theory, at least!

---

### Post by privaterolf on 2008-04-03
> **rsambuca said:**
> You should be able to do that, but **why **would be my first question :)

Anyways, you would have to set up a separate /boot partition with the first grub containing just your desired Windows and Ubuntu options.  Then, for the Ubuntu selection you will have it point to another grub on your Ubuntu partition via chainloading.  Should work in theory, at least!

My sister is...well....a- :P

I'll try that when she gets home from school with the laptop (hers is in the shop).

She's incoherently lazy and refuses to scroll down to Windows.

I'd just also like to hide the Ubuntu partitions partially from my dad, who is very skeptical about proven free software :confused:

---

### Post by rsambuca on 2008-04-03
I would put the Windows portion above the automagic line (so it isn't affected by kernel updates to Ubuntu).  Then set the default to 0 (zero) for Windows.  

Then just leave the Ubuntu stuff in there as normal, but make the grub menu hidden by removing the # sign in front of #hiddenmenu.  Change the timeout to 2 seconds, and no one other than you will even know that Ubuntu is on the computer.  When you want to boot to Ubuntu, just hit an arrow key within the 2 seconds to bring up the grub menu.  The timer then stops, and you can select your Ubuntu.

If your Dad is turning on the computer, he won't even see the grub menu and it will boot straight into Windows for him after a short 2 second delay.

---

### Post by privaterolf on 2008-04-03
> **rsambuca said:**
> I would put the Windows portion above the automagic line (so it isn't affected by kernel updates to Ubuntu).  Then set the default to 0 (zero) for Windows.  

Then just leave the Ubuntu stuff in there as normal, but make the grub menu hidden by removing the # sign in front of #hiddenmenu.  Change the timeout to 2 seconds, and no one other than you will even know that Ubuntu is on the computer.  When you want to boot to Ubuntu, just hit an arrow key within the 2 seconds to bring up the grub menu.  The timer then stops, and you can select your Ubuntu.

If your Dad is turning on the computer, he won't even see the grub menu and it will boot straight into Windows for him after a short 2 second delay.

Cool.  Thank you so much. :D

And, in the off chance this doesn't work, will I be able to edit the grub list again with a live CD or something else?

---

### Post by privaterolf on 2008-04-03
Bump, new issue

---

### Post by Tatty on 2008-04-03
Yes.  If you mess up the grub menu to the point that you cant boot into anything all you need to do is boot off a live cd and edit your menu.lst file  ... make a backup of it before you do anything so all you have it to go back to.

---

### Post by privaterolf on 2008-04-03
> **Tatty said:**
> Yes.  If you mess up the grub menu to the point that you cant boot into anything all you need to do is boot off a live cd and edit your menu.lst file  ... make a backup of it before you do anything so all you have it to go back to.

Thanks. :D

---

### Post by rsambuca on 2008-04-03
> **privaterolf said:**
> Cool.  Thank you so much. :D

And, in the off chance this doesn't work, will I be able to edit the grub list again with a live CD or something else?

Yes.  Just mount the partition from the liveCD, and then edit the menu.lst.

---

