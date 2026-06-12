---
title: "Booting ubuntu on an external HD from a vista computer"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by _Silhouette_ on 2008-04-13
Okay, I know there's lots of threads out there that are similar, but I don't see any that are quite the same  issue, that I can understand, anyway!

So I have ubuntu installed on an external hard drive, and I'd like to boot it up from my laptop (normally Vista). I would also like some extra clarification on the whole master boot record thing. Will I only be able to use ubuntu on this computer? Will I only be able to boot vista if the external hard drive is plugged in? Please explain everything to me so I can understand it. :) Thanks!

---

### Post by stuart brogan on 2008-04-13
what does your BIOS allow you to boot from? For instance if when booting I press F2 and enter the BIOS I can set the boot order, Although I haven't tried it I have noticed that my bios allows for network boots etc. There are some good websites devoted to booting from thumb drives and how to do it, That would probably be a lot easier than what you are trying to do. 

Although I hope some *nix ninja proves me wrong.

I understand that this kind of circumvents your question, this is typically the way I do things, (path of least resistance) If you are hell bent on doing this you might look into this.
[http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/)

if the external drive is firewire look here

[http://www.ibm.com/developerworks/linux/library/l-fireboot.html](http://www.ibm.com/developerworks/linux/library/l-fireboot.html)

I have not tried any of these methods and recommend Googling for a while before you begin.

---

### Post by _Silhouette_ on 2008-04-13
> **stuart brogan said:**
> what does your BIOS allow you to boot from? For instance if when booting I press F2 and enter the BIOS I can set the boot order, Although I haven't tried it I have noticed that my bios allows for network boots etc. There are some good websites devoted to booting from thumb drives and how to do it, That would probably be a lot easier than what you are trying to do. 

Although I hope some *nix ninja proves me wrong.

I understand that this kind of circumvents your question, this is typically the way I do things, (path of least resistance) If you are hell bent on doing this you might look into this.
[http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/)

if the external drive is firewire look here

[http://www.ibm.com/developerworks/linux/library/l-fireboot.html](http://www.ibm.com/developerworks/linux/library/l-fireboot.html)

I have not tried any of these methods and recommend Googling for a while before you begin.

I don't know what my BIOS allows, since the only thing I've been able to get into is the "advanced boot options" for Vista or "choose which OS to boot" in which Vista is the only one that appears. I have not seen anything that lets me set boot order or anything like that.
And yes, I'd like to do it from the hard drive, so I could actually save things on the same drive as the OS.

---

### Post by _Silhouette_ on 2008-04-13
Also, how do I install grub? The only thing I found is grub legacy, but it's a .tar.gz file, which I have no idea how to use. I want vista to be the default OS unless I choose ubuntu, and I want to make sure Vista can still boot even without the hard drive plugged in.

---

### Post by _Silhouette_ on 2008-04-16
Solved. Used BIOS to boot ubuntu on new laptop.

---

### Post by hovzio on 2008-04-17
I used ubuntu on external drive for some time but it soon became bothersome. I have a toschiba satellite a 200 with a vista install. Then i installed ubuntu gutsy on the ext. hd via live cd. Grub automatically installs itself unless specified otherwise. It all worked fine I guess except... that i could not boot vista without the ext. hd being plugged in. I searched for a long time on fixing this and I Know it has something to the do with the Mbr but was unable to fix it. If the drive was not plugged in I got " Grub error 21". I assume this is because grub is located on that darn ext. drive. I do not know how to change this and was not able to figure it out. I ended up partitioning my internal hd and have succesfully installing both os on it. I searched and searched but was not able get a solution but I am rather new to linux so that doesn't mean much.

---

