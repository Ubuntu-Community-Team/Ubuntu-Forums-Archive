---
title: "Vinux 3.1"
date: 2010-12-10
forum: Assistive Technology &amp; Accessibility
---

### Post by Rodney9 on 2010-12-10
[http://vinux-development.blogspot.com/2010/12/better-late-than-never.html](http://vinux-development.blogspot.com/2010/12/better-late-than-never.html)

Vinux 	Tony Sales has announced the release of Vinux 3.1, an Ubuntu-based distribution designed for blind and visually impaired computer users: "I am pleased to announce that Vinux 3.1 is now ready for download. It is currently available as a CD or DVD in both 32-bit and 64-bit editions (USB and Virtual Machine editions will follow shortly). It has been a long time coming, but hopefully it will be worth the wait. On top of all the usual Vinux goodies, new features include a Quick Start Guide for beginners (Ctrl+Alt+Q), Autokey-GTK which can insert text automatically as you type based on pre-defined abbreviation, the Parcellite Clipboard Manager which allows to paste text from the clipboard history, X-Tile which allows to tile windows automatically, Gnome Media Player as an accessible front-end to VLC.

---

### Post by Megaptera on 2011-12-05
> **Rodney9 said:**
> [http://vinux-development.blogspot.com/2010/12/better-late-than-never.html](http://vinux-development.blogspot.com/2010/12/better-late-than-never.html)

Vinux 	Tony Sales has announced the release of Vinux 3.1, an Ubuntu-based distribution designed for blind and visually impaired computer users: "I am pleased to announce that Vinux 3.1 is now ready for download. It is currently available as a CD or DVD in both 32-bit and 64-bit editions (USB and Virtual Machine editions will follow shortly). It has been a long time coming, but hopefully it will be worth the wait. On top of all the usual Vinux goodies, new features include a Quick Start Guide for beginners (Ctrl+Alt+Q), Autokey-GTK which can insert text automatically as you type based on pre-defined abbreviation, the Parcellite Clipboard Manager which allows to paste text from the clipboard history, X-Tile which allows to tile windows automatically, Gnome Media Player as an accessible front-end to VLC.

I know it was a spammer that revived this nearly one year old thread,(may be spam deleted by now) but this Ubuntu-based version is worth a bit of publicity from time to time - I've linked to it on two other forums. :)

---

### Post by redhalo79 on 2012-04-16
Hi
I recently installed Vinux on my pc which has win 7 on it but after installation, it loads straight into Vinux instead of letting choose which Os to boot into, how do I fix that.  I split my HD to allocate 500GB for Win 7 and 500GB for Vinux.
 Thanks
Red Halo

---

### Post by Megaptera on 2012-04-16
Hi,
I hope you were aiming at a dual-boot?

If you can access the terminal in Ubuntu (Ctrl+Alt+t) please try 'sudo update-grub' without quotes. If password asked for remember no * are shown when you enter it.
See if that adds Windows to your choices at boot.

If not ...
If the word 'Wubi' is unfamiliar to you that means you were not installing Ubuntu within Windows and we are talking about a traditional dual-boot.

That being the case, could you post the info as desribed here please? It's a way of showing clearly what is where on your hard disc: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)  and put the results in this thread please.

---

### Post by redhalo79 on 2012-04-16
Ok let me give it a try.  Oddly enough, I decided to remove the partition and when I did and i rebooted hoping Win 7 would come back but got grub rescue error.  What I want to do is remove Vinux partition and set up Ubuntu alongside Windows.

---

### Post by redhalo79 on 2012-04-16
Update, so right now I installed Vinux via the Live cd I have so that I can at least load into windows.  If I am deleting the Vinux partition and recouping the drive space that was prev used by Vinux then why would I be prevented from loading into Win 7 if that is the only OS on the HD?  Its a little frustrating but I am learning a lot.

---

### Post by Megaptera on 2012-04-17
The linux boot loader called 'Grub' will have over-written the Windows boot loader (it does that).
If you want to reassert the Windows boot loader in Windows 7: Guide with screenshots -
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

