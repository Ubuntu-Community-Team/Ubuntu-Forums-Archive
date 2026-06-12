---
title: "Complaint about Kernel Upgrades"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by BinaryDemon on 2007-12-25
I just want to start off by saying - I like Ubuntu, alot. Many of my computers are setup with a dual boot configuration with Ubuntu and XP. In the past I have heard alot of Linux users complain that Vista and XP don't play nice with other OS's- and their complaints are valid. I have seen Vista overwrite the boot sector removing grub completely. 

But today my complaint is that Ubuntu isn't playing nice with other OS's. It seems that whenever update manager installs a linux kernel or grub update- it overwrites any custom menu.lst configuration replacing my entries with the standard default ones. The non-linux OS entries disappear. Now this isnt a post requesting help, I always make backups of my grub configuration. Its a simple matter for me to boot into Ubuntu and add the appropriate entries to menu.lst. 

But imagine how this must seem to new linux/Ubuntu users. I understand that it would be difficult to update the kernel/grub and support all the possible configurations users have. But it should atleast prompt you to make a backup of your current boot configuration AND warn you.

/rant

Merry Christmas!

-BinaryDemon

---

### Post by LaRoza on 2007-12-25
That never happened to me.

Merry Christmas :)

---

### Post by forestpixie on 2007-12-25
I was under the impression that kernel upgrade didn't affect entries outside the automagic kernels list

---

### Post by BinaryDemon on 2007-12-25
Hmmm odd, maybe this less of a complaint and more of a bug then. Not sure what to say except it has happened to me on multiple machines and with both Fiesty and Gusty. Can I really be the only one experiencing this? I have no problems with most of the automatic updates. It only seems to occur with updates specifically for the kernel or grub.

---

### Post by LaRoza on 2007-12-25
> **BinaryDemon said:**
> Hmmm odd, maybe this less of a complaint and more of a bug then. Not sure what to say except it has happened to me on multiple machines and with both Fiesty and Gusty. Can I really be the only one experiencing this? I have no problems with most of the automatic updates. It only seems to occur with updates specifically for the kernel or grub.

No, I have seen other threads on it.

Perhaps you have done something odd to them? It is difficult to say because if it happened to you twice, and never too me, we'd have to take a very good look at our setups and other instances of this problem.

---

### Post by GGLucas on 2007-12-25
If a kernel is updated it runs update-grub to update all the grub entries to any new kernel versions, there's a whole "automagic" section for it, there should be "### END DEBIAN AUTOMAGIC KERNELS LIST" to indicate that anything after that won't be changed, try putting your windows entries after that, if it still removes them, then yes, it would be a bug.

---

### Post by nick_h on 2007-12-25
It would be a good idea to run update-grub to see if that reproduces the problem.  If the OP can consistently reproduce the problem then it would be worth reporting it.

---

### Post by mivo on 2007-12-25
The recent kernel update overwrote my menu.lst file of GRUB as well. I had to redo the entire thing by hand using the Live CD because the kernel doesn't work on my system without custom options.I was slightly put off by this as well because I had work to do and hadn't really planned on spending an hour on re-doing the menu.lst file. :/

---

### Post by nick_h on 2007-12-25
> I had to redo the entire thing by hand using the Live CD
You can always press "e" when you have a grub line highlighted to edit the entry.  This can be useful when testing an option without modiying the menu.lst file.

---

### Post by mivo on 2007-12-25
Using "e" never worked for me in Ubuntu (it does in Fedora and Arch). It prompts me for the options, but reboots the system from scratch when I press enter, ignoring the custom options.

---

### Post by GGLucas on 2007-12-25
Mivo, you can add the custom options you need to the "# defoptions=" line (leave it commented, it's not for grub, it's for grub-update), and when the kernel is updated, it should automatically add them to it.

---

### Post by mivo on 2007-12-25
> **GGLucas said:**
> Mivo, you can add the custom options you need to the "# defoptions=" line (leave it commented, it's not for grub, it's for grub-update), and when the kernel is updated, it should automatically add them to it.

Thank you! I shall do this. :)

---

### Post by louieb on 2007-12-25
[FONT=Arial]> **BinaryDemon said:**
> ...more of a bug then... multiple machines and with both Fiesty and Gusty. 
Haven't ever seen that bug. Are you placing your custom entries in a safe place?

When the kernel is updated  the  menu.lst  file is updated to boot the new kernel. 
it is safe to put your custom entry before this line - but
anything  after this line. 
```
### BEGIN AUTOMAGIC KERNELS LIST
```.. This area  of menu.lst changes between these two line when update grub is run. 
any custom entry placed here will probably be deleted or at least messed up.  

```
### END DEBIAN AUTOMAGIC KERNELS LIST
```your custom entires are safe from modification after the line above.

[quote=mivo]Using "e" never worked for me in Ubuntu[/quote] 
Weird :  Wish I could suggest something - I use it every now and then - always worked like it should.
:KSHolly Happyday. 
[/FONT]

---

