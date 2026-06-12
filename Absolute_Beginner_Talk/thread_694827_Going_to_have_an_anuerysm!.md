---
title: "Going to have an anuerysm!"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by opheliax on 2008-02-12
Okay, Ill sum everything up, first Im new to linux/ ubuntu, second I have always used vista. Okay so heres my dilema, the other day I shrank my partition in vista so that I could install Ubuntu. Everything went smoothly, I was able to get on to Ubuntu and play around with it, but all my important documents and programs are on the vista partition. So I ran some updates in Ubuntu and restarted my computer, to where it would load the Ubuntu logo, and then it would freeze, i fixed that thanks to some people on here that were nice enough to help. Now, I want to get back into my vista installation, so I try to but it doesnt show up in GRUB. So I go through see if theres a fix I try Super GRUB Disc, and that doesnt work, so I read about reinstalling the vista boot manager, so I tried that, only now I cant get into either of the OS's, it doesnt even load it just brings up a blank screen with a little underscore blinking in the corner to taunt me. Please someone help me I dont want to lose everything in vista!


UPDATE! I have just recently ran test disk and it came up with only one partition under linux and no other ones. So does this mean I lost my Vista Partition?

---

### Post by emarkd on 2008-02-12
What was your problem with supergrubdisk?  It's usually pretty good stuff for these sorts of problems...

---

### Post by opheliax on 2008-02-12
well now i dont have grub installed at all, so uh that might be a problem. The main problem is it isnt showing my windows vista partition in the boot options but it shows the space if I check the .lst

---

### Post by jhenager on 2008-02-12
I found this page by searching on Vista MBR.
[http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)
Hope it helps!

---

### Post by jhenager on 2008-02-12
Also found this:
Vista DVD has a folder named BOOT

Run bootsect.exe /nt60 c: (wherever your Vista install is) to restore the boot loader.

bootsect.exe /help for switches.

Hope you didn't have you anurysm yet!

---

### Post by bumanie on 2008-02-12
You should boot up the ubuntu live cd and reinstall grub via the live cd.
Follow this
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Hope it helps, if not visit here and read
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
It is probably the most extensive site on grub on the internet

---

### Post by opheliax on 2008-02-12
So i can run that from the DVD right that came with Vista?

---

### Post by jhenager on 2008-02-13
> **opheliax said:**
> So i can run that from the DVD right that came with Vista?

If you are talking about bootsect.exe, yes.

---

### Post by Sinkingships7 on 2008-02-13
try booting from the live cd (of ubuntu) and try to access your vista partition from there (places -> computer). that way you can at least try to recover your data, even if vista can't be brought back.

---

