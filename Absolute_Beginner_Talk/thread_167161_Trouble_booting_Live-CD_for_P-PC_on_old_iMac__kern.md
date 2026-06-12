---
title: "Trouble booting Live-CD for P-PC on old iMac : kernel panic"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by Theo-Ubu on 2006-04-27
Hello,

I'm so excited to try this new thing called Ubuntu Live-CD, but my first attempt on a very old iMac failed.  I press and hold down the "C" key while starting it, and it starts the Ubu loading process, but a ways into it... after a lot of text scrolls by, it ends with a "kernel panic : attempted to kill init, rebooting in 180 seconds"... or at least that's the best I can remember it.

I also tried typing in something at the first command-line prompt about video=ofonly, but that essentially led to the same thing.

Can anybody suggest something new to try, or explain the problem if it has been noted before?

Thanks!
Theo

---

### Post by 3rdalbum on 2006-04-27
I think we'll need to know the specifications of your iMac. How much memory does it have? Exactly which iMac is it? Also, if you could write down the last couple of lines of the kernel messages, it might help. (i.e. what appears above the "kernel panic" message)

The very early iMacs had an expansion slot. If you've got anything plugged into it, you should try unplugging it in case this is causing problems. I don't know much about the Linux kernel but it might help to unplug all USB devices other than the keyboard and mouse.

---

### Post by Theo-Ubu on 2006-04-28
This system is pretty basic.  32Mb of ram, 6Gig HD, etc.  Your very first, tray-loading iMac that came on the market.

Your ide about USB conflicts was a good one.  I had the mouse chained through the keyboard, so I tried plugging it into the other standard USB port on the side of the machine and trying another boot.

This time, it went through the same routine however and ended on the kernel panic message again.  This time however I took note of the message lines above this one and they read "Error -3 while docompressing!!", interspersed every other line with a string of stuff I can't memorize and type out to you.  They started with 65.XXXXXXXX XXXXXXXXXXXXX, kind of like that.

So, do you think this disc-burn didn't work out perhaps?  It was downloaded on a high-speed connection, so it seems unlikely it could have become corrupted?

Thanks!

---

### Post by Belathor on 2006-04-28
Did you use the Beta 2 Disk? It was just released today to fix the problems the first beta live-cd was having.

Good luck!

---

### Post by Theo-Ubu on 2006-04-28
Well... no.  I didn't even know about that.   What were the problems reported?

---

### Post by Theo-Ubu on 2006-04-29
So..., I tried adding 64Mb more to the base of 32Mb and that was the key to letting the Live-CD load-up and proceed past the decompressing error.

The load gets pretty far along; as far as the ubuntu logo with the progress bar under it.  It then goes back to text mode, but then eventually goes blank and keeps reading and reading the CD for ages.  I lose patience with wating for it to finish and go to a desktop past two hours somewhere.

Anybody have an idea why it might be going blank like this and not completing the load?

---

