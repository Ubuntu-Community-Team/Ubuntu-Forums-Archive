---
title: "command prompt won't accept password"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by tzorched on 2007-07-05
This is driving me up the wall.  I had Ubuntu LTS installed, I was learning to unpack tarballs, I had updated Firefox, I had just installed Flash Player for linux, and I was going to start learning to configure a firewall when I got blindsided by this bug.  When I go to the terminal and try to run any kind of command that needs to use sudo, I'm asked for the password and I find I can't type anything.  Nothing.  The only key the works is the enter key and, of course, I'm told that I didn't enter the correct password.  I've tried everything.  I went so far as to completely unistall linux (I've got Ubuntu running on a secondary drive, the primary drive has my Windows XP OS.) run the Windows XP Recovery Console to get rid of GRUB completely, format that hard drive entirely and reinstall.  I get the same problem.  I tried using a different keyboard, that didn't work.  I tried looking into my BIOS to see if I had shut off USB support, nothing out of place.  I've tried using different keyboard layouts, I've tried different character encodings.  Nothing.

If I use the sudo command in a terminal, I find I can't type anything when I'm prompted for my password.  My keyboard works 100% every single other time.  It's only when I'm trying to use the sudo command that I get stuck. And I have no idea how to fix it.  If anyone has any suggestions at all, or if they've had this problem and knows how to fix it, I'd be very grateful.

Thank you.

---

### Post by geek_Man on 2007-07-05
When you use sudo, it doesn't display anything when you type in your password, but it's still working.

---

### Post by ed_d on 2007-07-05
Right, it doesn't echo the characters. Sometimes I wish it would give some kind of feed back, but it doesn't. I have just grown used to it by now.

---

### Post by tzorched on 2007-07-05
Thanks ed-d and geek_man.  It was a combination of my not knowing how ubuntu works and having the bad luck to type in my password wrong.  Geez, you've saved me some major headaches.

---

