---
title: "Linux/GNU Noob, few Questions."
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by DavidTyson on 2007-04-23
Hi everyone, I'm a long time Windows user, and have had a tiny bit of use in some Linux distros (red hat, which scared the hell out of me).

I hear that Ubuntu is probably the one for someone like myself.

Heres my situation.

I have my main PC, which is XP Pro.
My old PC, which is nothing at the moment, it has a P4 1.8Ghz, 512MB RAM, Gigabyte MB. 
I'd like to put Linux on my old PC, so I don't need to be ripped off by M$ for another lisence.

I want the old PC with Ubuntu to be connected to the internet via DSL modem/Router, and my new PC in my room to be connected via Wireless network from a Wireless Dlink router connected to my Linksys DSL modem.

Will I be able to set this up? Will it take me hours and hours to configure?

Basically I want my computer in my room to have internet access, but the ubuntu computer in the lounge to be able to access my music library and files over the wireless network off my PC in my room.

So it will be like this -

Internet - 
Linksys AG241 DSL Modem - Old PC with Ubuntu and D-Link DI-524 Wireless Router - 
New PC XP Pro via Wireless.
How hard is this going to be?

---

### Post by siciliancasanova on 2007-04-23
Shouldn't be too hard, the router is not dependent upon the operating system, so you can just hop into the router from Firefox in Ubuntu and make your wireless settings for the Windows machine to pick up on.  

Some people have had trouble networking but I take my computer everywhere and just change the workgroup and in about 30 seconds I'm up on the new network, I have had good luck with networking.  If it were the other way around where you were trying to run wireless on the Ubuntu machine you might run into more snags.

---

### Post by devnulljp on 2007-04-23
Should be a piece of cake. Install samba on the Ubuntu box and you'll be able to share your files between them too.

---

### Post by rich.bradshaw on 2007-04-23
I have mine set up much like this, and have no problems.

Ubuntu can "see" Windows shared files without any config. The other way round is pretty simple using Samba.

I use Tangerine in Windows to share my music library to Rhythmbox using the DAAP protocol - you just run it in Windows and it shares your library like iTunes does - very convenient.

---

