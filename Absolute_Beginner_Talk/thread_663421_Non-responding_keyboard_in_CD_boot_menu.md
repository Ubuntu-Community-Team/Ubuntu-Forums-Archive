---
title: "Non-responding keyboard in CD boot menu"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by RonnnL on 2008-01-10
I'm planning to install Ubuntu on a separate partition of my WinXP-system but my keyboard, an IBM M-type, ps/2 connector, doesn't work correctly. While the keyboard works when Windows or Ubuntu is fully started, it is non-responsive in the CD menu.

This problem also arises when I need to access a windows-XP CD by pressing F2 at the appropriate moment. My BIOS is always accessible, though. Looks like my system somehow blocks keyboard input during boot. 

Since I can wait for the 20-second timer in the Ubuntu CD-menu to boot into Linux, I CAN still install Ubuntu on my system. However, I am afraid that the boot menu that will be created won't respond to my keyboard. 

When I use another keyboard, such as a cheap DELL USB-keyboard, everything works correctly. But switching to another keyboard is not an appropriate solution, and attaching two keyboards only for boot purposes seems like a waste of space.

So I'm wondering:
-Is the boot menu that Ubuntu will create similar to the CD-menu, and are similar problems expected?
-Has anyone an appropriate solution? (Note that my IBM keyboard is a ps/2 one)

---

### Post by Joeb454 on 2008-01-10
Have you checked your BIOS settings for anything relating to PS/2 support during the boot sequence. Some BIOS' have options to enable and disable these things

---

### Post by RonnnL on 2008-01-10
PS/2 cannot be influenced in the BIOS. (Some system info: MSI 945P Neo2 M.B. with Intel Pentium D 2.8, using a standard coolermaster casing & power supply)

I'll try and turn off USB legacy support for keyboards in the BIOS and remove all of my USB devices. Maybe the system 'thinks' that one of them is a keyboard and therefore disables the PS/2 one? Far-fetched, but worth a try... 

Other suggestions are welcome!

---

### Post by mcduck on 2008-01-10
Of course you could get a PS/2-to-USB adapter and plug the keyboard to the USB port..

---

### Post by Joeb454 on 2008-01-10
That could work I guess, I can't think why the boot wouldn't recognise the keyboard...though I've not had a PS/2 keyboard or mouse for about 4 years, lol

---

### Post by RonnnL on 2008-01-11
Fiddling with the BIOS USB legacy settings has no effect at all. I connected an old USB-keyboard as a temporary workaround. A PS2-to-USB-plug adapter could also work, but I like to really fix the problem instead of finding a workaround.

Well, any other tips are welcome, in the meantime I'm going to fix my next problem: Automatic resizing/repartitioning of my NTFS-drive won't work in the Ubuntu-installer. Too bad my first encounter with Linux still lives up to the 'difficult & troublesome OS' stereotype... Won't give up though... ;)

---

