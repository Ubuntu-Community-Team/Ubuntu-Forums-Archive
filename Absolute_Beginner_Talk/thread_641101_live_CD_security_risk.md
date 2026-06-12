---
title: "live CD security risk"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by raxx on 2007-12-15
This might be a dumb question, but I cant find an answer using google. Can a linux box be "hacked" by using a live CD to manipulate or read files stored on the HD? I am rather new at linux so I might be missing something. Thanks.

---

### Post by mellowd on 2007-12-15
> **raxx said:**
> This might be a dumb question, but I cant find an answer using google. Can a linux box be "hacked" by using a live CD to manipulate or read files stored on the HD? I am rather new at linux so I might be missing something. Thanks.

Yes, if you have the right tools

---

### Post by raxx on 2007-12-15
"Yes, if you have the right tools"

Ok, so is there a way that I can counter the threat of these tools?

---

### Post by mellowd on 2007-12-15
> **raxx said:**
> Ok, so is there a way that I can counter the threat of these tools?

Well the best defense is to stick the server under lock and key, if that isn't possible you could encrypt the hard drive. Ubuntu gives you this option when you install off the alternative CD

---

### Post by raxx on 2007-12-15
> **mellowd said:**
> Well the best defense is to stick the server under lock and key, if that isn't possible you could encrypt the hard drive. Ubuntu gives you this option when you install off the alternative CD

Thanks again for the reply. Where do I get the alternative CD?

---

### Post by mellowd on 2007-12-15
On the ubuntu site you can get them. Just be sure to download the alternative CD as opposed to the live CD. There is no live cd version for server so it is already the 'alternative'

---

### Post by raxx on 2007-12-15
> **mellowd said:**
> On the ubuntu site you can get them. Just be sure to download the alternative CD as opposed to the live CD. There is no live cd version for server so it is already the 'alternative'

Ah I see it now..thanks ;)

---

### Post by lespaul_rentals on 2007-12-15
You can also use the "chmod" command to change access rights.

---

### Post by PointyWombat on 2007-12-15
Another option is to make the CDROM drive a non-bootable device in the BIOS  then password protect the BIOS.

---

### Post by sloggerkhan on 2007-12-15
lock your bootloader, lock your bios, encrypt your hardrive, and keep your computer locked in a vault.

Also, windows systems are also vulnerable in the same way to live cds, if not even more so.

---

### Post by PointyWombat on 2007-12-15
Further to my last, unless you prevent users from booting from other media, like a CD, floopy, or a thumb drive, they may not be able to read your files if you encrypt them, but they'll still be able to make them unusable (destroy) them quite easily.

---

### Post by raxx on 2007-12-15
> **sloggerkhan said:**
> lock your bootloader, lock your bios, encrypt your hardrive, and keep your computer locked in a vault.

Also, windows systems are also vulnerable in the same way to live cds, if not even more so.

Can a harddrive be encrypted after I install ubuntu using the live CD? Is there a util built into ubuntu or do I need to download something? Thanks.

---

### Post by lespaul_rentals on 2007-12-15
Actually, to be honest, the only completely immune computer from such an attack would be a computer that was not plugged into the wall, disassembled into seperate components, and each individual component locked into seperate vault.  There's really no way to 100% protect your system, but encryption, chmod, smart BIOS setup, and choosing your friends wisely will make you 95% safe.

> **raxx said:**
> Can a harddrive be encrypted after I install ubuntu using the live CD? Is there a util built into ubuntu or do I need to download something? Thanks.

I don't think this will work.  If it does work you run the risk of data corruption.

---

### Post by raxx on 2007-12-15
> **lespaul_rentals said:**
> Actually, to be honest, the only completely immune computer from such an attack would be a computer that was not plugged into the wall, disassembled into seperate components, and each individual component locked into seperate vault.  There's really no way to 100% protect your system, but encryption, chmod, smart BIOS setup, and choosing your friends wisely will make you 95% safe.



I don't think this will work.  If it does work you run the risk of data corruption.


Thanks. I think the "live CD attack" needs more attention since everyone has access to them and few  security books that Ive read talk about it. I think most people install a firewall and choose really good passwords never thinking that someone with a liveCD can bypass all of that security.

---

### Post by lespaul_rentals on 2007-12-15
> **raxx said:**
> Thanks. I think the "live CD attack" needs more attention since everyone has access to them and few  security books that Ive read talk about it. I think most people install a firewall and choose really good passwords never thinking that someone with a liveCD can bypass all of that security.

You know what I think?  I think people believe in "security" when no such thing exists.  I don't care how bulletproof your firewall is or how many characters your password has.  The "LiveCD exploit" may need to be addressed in some cases, but seriously, think about it: they fix that, something else will come up.  There will **always** be a hack for something.  It could be invincible against LiveCD attacks but a hacker could discover a buffer overflow in a program they are using.

Heck, even think about a world with no LiveCDs.  My supervisor at work needed my help recovering some data from her computer.  It was an NTFS drive, with all those crazy "secure" NTFS permissions.  What a load of bullcrap.  I had to hook up the hard drive to my IDE channel, select "ownership permissions" andd bam, I had full access to her files.  Good thing there's that security!

It will **always** be cracked.  It will **always** be hacked.  I personally don't find anything too bad with the LiveCD deal, because I keep malicious people away from my computer.

---

### Post by mellowd on 2007-12-15
True, but it's still best practice to lock it down as much as you can first anyway

---

