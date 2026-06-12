---
title: "RAMDISK: error"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Marko Tica on 2008-03-29
I tried to install some damn boot-splash screen, and after restart I got this message, I tried to find some fix but...no success.

I get this error:

[15.107732] RAMDISK: ran out of compressed data
[15.107732] invalid compressed format (err=1)
[15.108343] Kernel panic - not synching: VFS: Unable to mount root fs on unknown-block(0,0)

Is there any way to fix this somehow with live CD so I can boot that version again?

---

### Post by tangibleorange on 2008-03-29
So it was working fine before you installed this new splash screen? Can you still get a GRUB menu before startup that enables you which option to boot? If you can, try selecting the "recovery mode" option and see if you still get the same error. This will enable you to get to a command line where you can try and fix your system...

Post again with whether you are able to get into recovery mode...

---

### Post by Marko Tica on 2008-03-29
> **tangibleorange said:**
> So it was working fine before you installed this new splash screen? Can you still get a GRUB menu before startup that enables you which option to boot? If you can, try selecting the "recovery mode" option and see if you still get the same error. This will enable you to get to a command line where you can try and fix your system...

Post again with whether you are able to get into recovery mode...

I managed to get to GRUB, tried rcovery mode...and got the same error.

---

### Post by louieb on 2008-03-29
Time to learn a little about the GRUB command editor. 
What your going to do is remove the splash option from the kernel line.

Look at the bottom of the screen - you will see a list of options. One of them is  **e for edit.  **Highlight the **Ubuntu** entry and press **e**. 

Look at the bottom of the screen again - you will see a list of options. One of them is  **e for edit.  **Highlight the **kernel line** and press **e**. 

Use the arrow and delete keys to remove **splash **from the kernel line and press <**enter**> when done.

Now press **b to boot. **This should let you get Ubuntu started and fix whatever it was you broke before.

(Note this change is temporary to keep the change you will have to make the same edit in /boot/grub/menu.lst)   Good Luck.

---

### Post by Marko Tica on 2008-03-29
I knew some of that :D
But I wasn't sure what I have to delete from the line...
I managet to boot in.
I should be able to manage changes to /boot/grub/menu.lst
Tnx for help.

---

### Post by tangibleorange on 2008-03-29
Remember to mark threads as solved :)!

---

### Post by tommawat on 2008-04-06
hi there!  some panic here too, unfortunately!  i had a splash startup screen ok, but the shutdown didnt appear, just some errors, but it actually did shut down.  i followed forum advice to change the splash resolution to vga=791, correct for me, and then updated, then restarted, and now i get the same error of kernel panic.  

i tried editing the splash section of the kernel (i deleted splash vga=791) and it still had the same error.  any suggestion?  can i fix this with the live CD somehow?  

any help would be greatly appreciated as i use that computer for work and all my files are there too.

many thanks in advance to anyone with advice...

please help me!

---

