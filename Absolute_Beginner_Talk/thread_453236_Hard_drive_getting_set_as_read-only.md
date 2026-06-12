---
title: "Hard drive getting set as read-only"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by dbvanhorn on 2007-05-24
I have a large HD which keeps getting set to read only.

I posted on this a couple weeks ago, but didn't really get anywhere.
I see now, in the mount options, where if there is an error, the system will remount as RO.

This gets triggered during long file copies, where I'm sending a bunch of data across. 
Running several copies at once makes it worse.

Thing is, the drive passes any diagnostics I can throw at it.

What can I do?  I can't live this way.

---

### Post by Soybean on 2007-05-24
Hmm. I don't have an answer for you, but my first thought is that if there's an error happening, there's probably an error log somewhere. Maybe dmesg, or somewhere in /var/log/

If you can't find the error, you could try adding "debug" to the list of mount options for your drive, then remount it and try to make it break again to see if it gives a message somewhere. Then, if that doesn't work, switch "errors=remount-ro" to "errors=panic", and try to get it to break again. That'll make it so that instead of remounting read-only, it crashes your whole system instead. Which is obviously worse, but hopefully a kernel panic will at least have a helpful message associated with it. ;)

Oh, alternately, if you feel like living dangerously, just set "errors=continue" -- your hard drive won't get mounted read-only anymore, but you won't know what may or may not be going wrong with it.

---

### Post by hellmet on 2007-05-24
Please paste the fstab code, and point us to the drives you are talking about.
Help us help you.

---

### Post by Carlos Santiago on 2007-05-24
I had the same problem with Ubuntu 6.10.
I switch to Feisty and up to now it is working fine!

---

