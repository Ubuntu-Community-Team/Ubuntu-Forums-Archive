---
title: "Linux headers/kernel updates and Grub"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Hurricane on 2007-08-14
Hi,

Apologies for my 'nooby' explanation of my problem, but I am no Linux whizz so I will try and explain things how I see them.


First, some details of my setup.

I have 2 hard disk drives (Sata).  XP is installed on the first hard drive, along with grub.  Ubuntu is stored on the second hard drive.

During the Ubuntu installation (I upgraded to Feisty, originally had Edgy), Grub installed fine and I got the menu to select whether to select XP or Ubuntu.  Perfect.

However, whenever there are any linux headers/kernel upgrades, the menu.lst file gets updated naturally, to reflect the new kernel files so Ubuntu can boot up.

However, my XP entries then vanish.  I can either:

a) Add the XP entries in manually by looking at my backup of my old menu.lst, or:
b) Edit my backup of my old menu.lst to reflect the new kernel version.

(If you need an example of what I'm trying to say, please let me know, I'm posting this from XP at the moment so I don't have my files to hand).

Surely, if the kernel gets updated, my grub entries for XP should be added back as well?  It doesn't seem like, for example, 'Mrs Miggins' who isn't computer literate would be able to make these edits every time?  Also I have made amendments to the menu.lst file to have the operating systems ordered as I wish, renamed them all to, for example "Windows XP" and "Ubuntu", time outs altered, and (I forget the exact wording here) an alteration so my system will boot up the previously loaded operating system.  On each kernel upgrade (granted they aren't too often) this all gets eradicated.  Surely it would be better for the upgrade just to amend the current menu.lst with the new changes?

Thanks for any help

---

### Post by 5-HT on 2007-08-14
You can add any custom entries that you do not want update-grub to touch (such as your XP entry) after the 
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```They'll remain after a kernel update.
cheers,

---

### Post by Hurricane on 2007-08-14
Brilliant, that should do nicely.  Thanks for the reply.  There's no way to keep the ordering though, and the custom timeouts, and my option to 'boot to the last loaded OS' if timeout is reached? (Ie highlight the last loaded entry by default)?

---

### Post by BaffledMollusc on 2007-08-14
Yes, when there's a kernel update and the new kernel is added to the GRUB boot menu, it should definitely keep the old entries too. I'm not sure why your installation isn't doing this. All my installations have done this perfectly, and the changes I've made to my menu.lst file (default boot entry and time out) are retained when a new kernel line is added.

Maybe if you manually make some changes to the menu.lst it ends up ordered differently to what the updater expects, and consequently it misses the XP entry?  Just guessing...

---

### Post by 5-HT on 2007-08-14
You'll loose the ordering, but can still have all the other features including the default choice to boot. You may need to uncomment some options though. menu.lst is nicely commented with descriptive options, so that shouldn't be a problem. One thing that comes to mind is:

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

---

### Post by Hurricane on 2007-08-14
Thanks for the reply guys, I guess by default Grub puts the XP options in the ### END DEBIAN AUTOMAGIC KERNELS LIST  section, but when I ordered them I just stuck them in the same place as Ubuntu, consequently getting removed.

Thanks for the very prompt replies, absolutely fantastic.

---

