---
title: "replace drive with ubuntu on"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by jtclicker on 2008-03-05
I've been playing with ubuntu on a small drive as a dual boot with win xp on a bigger drive. I've no space to keep the small ubuntu drive so I need to pull it out of the bay and put a bigger drive in.  I'm on a win dual boot system. In my ignorance I just pulled the drive then tried to use the live cd to install ubuntu on the new drive. The live cd froze at 82% 'scanning mirror', then when I tried to boot into windows I got GRUB error 15 as, of course, GRUB was looking for the old drive. So back out with the new drive and back to the old small drive with ubuntui to try and sort things out.  How do I  get rid of the point to GRUB on the win size so I can just install ubuntu afresh on the new drive? I've done a backup of the files I need to keep.
Thanks for any advice!

---

### Post by opositive on 2008-03-05
I have used the Super Grub Boot Disk to save myself a few times:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

######
If you don't want to use that boot disk and just want to go back to the Windows way and reinstall Ubuntu/grub...

Here is how I have restored the normal Windows boot record in the past.

   1. Insert Windows XP Setup or Installation CD
   2. Restart your computer
   3. If you see this message, “Press any key to boot from CD…” press a key to start the computer from Windows CD.
   4. After a few minutes, you’ll see Windows Setup Menu.  Press “R” key to start repair Windows XP installation using Recovery Console.
   5. Microsoft Recovery Console will start.
   6. If you’re prompted to enter a number related to the Windows XP installation that you need to repair.  Most likely “1&#8243; if any.
   7. Enter your Administrator password, if you’re asked.
   8. At the Recovery Console Command Prompt, type “fixmbr” and verify that you want to proceed.
   9. Remove Windows XP Setup CD from CDROM.
  10. Type “exit” to restart your computer.

I borrowed the verbiage of the steps from this website.

[http://ebestagent.com/wordpress/windows-tips/uninstall-grub-or-lilo/](http://ebestagent.com/wordpress/windows-tips/uninstall-grub-or-lilo/)

---

### Post by jtclicker on 2008-03-05
great! thanks I'll try that. Talk about a fast response!

---

