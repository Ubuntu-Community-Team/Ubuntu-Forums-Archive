---
title: "forced check freezes"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by nosh on 2007-08-17
Hey, I've got a laptop here that's doing the normal automatic drive check every 30 or so boots, and the check freezes at a seemingly random percentage each time it runs.  I do not get an error message or a failure, it just freezes.  The computer works fine and was run extensively without any problems indicating a drive error.  Furthermore, the BIOS setup utility's hard disk self-check returns a clean drive.  What is going on?  Is it safe for me to bypass the drive check?  If so, how would I do it when I can't get past it into even a command line?  Is there some way to interrupt it?

---

### Post by louieb on 2007-08-18
My laptop does the same thing when it is having trouble making the wireless connection. i get a soft lockup error message when this happens. 
To see the messages at boot 
[LIST]
[*]highlight the Ubuntu entry
[*]press **e** to edit
[*]highlight the kernel line
[*]press **e** to edit
[*]remove **quite splash** from the line then press enter
[*]press **b** to boot[/LIST]now you should see all the messages at boot. post the last one and lets see if someone knows how to get around it. In my case if I move into the same room as the router my laptop will boot just fine.

---

### Post by nosh on 2007-08-18
Nope.  Still no error messages of any kind, even when quiet splash is deactivated.  All the drivers load correctly and the swap gets activated and then when it gets to this
```
fsck 1.40-WIP (14-November-2006)
/dev/sda3 has been mounted 39 times without being checked, check forced.
/dev/sda3: |===========================================           -81.3%
```
it just freezes. (note that the percentage varies with each boot attempt)

To follow up on the wireless theory, this laptop is in the same room as the router, in fact it's practically on top of it.  Now when the computer boots normally and after the user is logged on it has some trouble connecting to a network unless you turn the card off and then back on.  I've tried booting with the card on and with it off and I still can't get past the fsck.

Now I just remembered something that may or may not help.  Whenever the computer boots, normally or not, the very first thing that pops up even before the splash screen is
```
PCI: BIOS BUG 81[49435000] found
```
This has never been a problem before so I just ignored it, but it might be related, maybe.

Are there any other ideas out there?

---

### Post by nosh on 2007-08-18
Okay, so I was experimenting with it and thought I had a work around.  The computer is dual-booting so I installed [ext2IFS]("http://www.fs-driver.org/") on windows and got access to my linux files.  Then I edited my etc/fstab so that sda3 (and all other sda) had zero for their pass number.  This should tell fsck to not check the devices at startup, right?  Well dangit it didn't and I still have the same problem.  I do however have access to all the config files and etc. so can any one tell me how to disable fsck on boot?

---

### Post by nosh on 2007-08-18
eventually fsck got through the check with out freezing, on about the 20th attempt.  So now I'm in the computer and I used tune2fs to disable fsck on boot.  But this is really only a short term fix.  Does anyone know why it froze?  How to fix it?  Or any alternatives I can run to keep the disk clean besides fsck?

---

### Post by markph on 2007-08-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/124773](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/124773) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Had the same problem.

Run fsck manually before your nth forced check.

I was able to get around the problem by booting with LIVE CD, and manually running fsck myself.

Apparently the problem is related to only auto forced checks during boot up.

---

