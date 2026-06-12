---
title: "Gain root without root password (locally)"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by glotz on 2006-05-17
This was a little surprise for me, though I'd share this with you: [http://makuchaku.info/amnesty/#gainrootwithoutlogin](http://makuchaku.info/amnesty/#gainrootwithoutlogin)

Note that even if you set BIOS boot order to boot HDD before CD and a BIOS password and a GRUB password, your harddisk can be removed from your computer and accessed on another system or your BIOS battery removed to reset BIOS password. Without physical security there's no security. Encrypting ones disks could help fight this I think... :-k

---

### Post by aysiu on 2006-05-17
Anyone who has physical access to your computer essentially has root access if she knows what she's doing.

---

### Post by glotz on 2006-05-17
Are there other means yet available?

---

### Post by NoUse on 2006-05-17
"Boot access is root access"

---

### Post by aysiu on 2006-05-17
[QUOTE=glotz]Are there other means yet available?[/QUOTE] Lock down your computer with a huge bolt lock that can't be easily cut. Make the CD-ROM drive inaccessible, too.

---

### Post by nocturn on 2006-05-17
The only way arround this is to use encrypted partitions.

You could encrypt swap with a random key and /home with one that you have, which you need to type at boot time.

---

### Post by nocturn on 2006-05-17
BTW, this is not Ubuntu/Linux specific.  All OS's suffer this problem, including Solaris, OS X and Windows.  

If you have sensitive data, encrypting it would be wise.

---

### Post by glotz on 2006-05-17
Good point nocturn! (the non-os-specificality) Does anybody have practical advise or experience concerning encryption? Would it slow me down or consume CPU or memory or something like that?

---

### Post by Cirrocco on 2006-05-17
wow...

I've got like 4x80gb hard drives stuff with things I don't want anyone getting into.

is there an encryption that once authenticated allows all applications to access the encrypted files?

---

### Post by steve.horsley on 2006-05-17
[QUOTE=Cirrocco]wow...

I've got like 4x80gb hard drives stuff with things I don't want anyone getting into.

is there an encryption that once authenticated allows all applications to access the encrypted files?[/QUOTE]

That's one helluva porn collection!;-) 

When you create an encrypted partition, that partition cannot be accessed until the password/key is supplied by the user. Once the key has been supplied, the partition is accessible just like any other partition so you don't have to give a password for each individual file. I've never used one so I don/t know the details, but I guess on Linux you would be asked for a password when you give the "mount" command.

---

### Post by redistributer on 2006-05-17
Naturally it would slow you down depending on the level of encry (56 bit, 128 bit, 256 bit, etc etc) would define the speed. just keep in mind if someone can get your data (encrypted or not) they are more than likley smart enough to de-crypt it as well. Security is a process that can always be penitrated reguardless of the level. You can do anything you would like to protect your data, just keep in mind it won't stop a breach it will only slow it down. 

If you're really scared you can just log everything that comes in and out of your network via setting up a good linux firewall / router, that way if some un-auth person slips in you can trace them back from ip to ip to provider, to mac, to phone, to address, to name. 

Every ssh connection posts a gpc fingerprint of the computer that connected, so typically a short draw hacker will shell himself 2 - 3 times on average, this means if you can get the cooperation of the administrators for those 2 - 3 networks the hacker passed through you can find out his name, address, telephone number.

If you can prove to the ISP of the final ip you found relates to a security breach then they will find out the ip to mac relation of the ip and give you some info on the person. You can then contact the proper authorities to assest the situation. Depending on the delicacy of the information that was passed through these networks will determine the outcome of the situation.

Don't expect to get help if it's just some m4a-s and some jpgs that were on your drive though. 

You could also create revolving passwords that change every 30 seconds, but then you would need a device that can play back those numbers for you so you would know what they were. 

Anyways there are lots of solutions to increase the amount of time it would take to steal information, you just have to be creative and do things others are not.

---

### Post by glotz on 2006-05-17
It's true that no encryption is unbreakable but as long as it's just too expensive in time or money for the attacker it'll work. In a real life attack scenario you should expect bone breakers rather then code breakers... :)

---

### Post by GaFFy on 2006-05-17
Paranoid anyone?

Just like the lock on the door to your house or car it is only there to keep honest people honest.  If a criminal wants in, he finds a way.

If your data is important enough to need high security then the person who thinks it is important enough will find a way.

Chances are you dont and they wont.

Enjoy your paranoia.

---

### Post by gr0kzer0 on 2006-05-17
If people you don't trust live in your house and you have sensitive material on your computer, you have to accept that if they can get *physical* access to the box, they can get *into* your box. GnuPG is a good open source encryption program.  Not infallible, of course; but using a long enough key will make it almost unbreakable.

What you need, though, is proper *physical* security.  A damn good lock on the door.  Maybe dig a deep hole, throw the computer in, then fill the hole with concrete. :)

Or maybe move in with people you trust to not go rooting through whatever it is you're hiding.

---

### Post by glotz on 2006-05-17
GaFFy, you work for an insurance company, right? ;)

---

### Post by Al3xanR0 on 2006-05-17
[QUOTE=nocturn]The only way arround this is to use encrypted partitions.

You could encrypt swap with a random key and /home with one that you have, which you need to type at boot time.[/QUOTE]

Chances are if someone has gained physical unauthorized access to your machine, your machine is the victim of theft. That being the case, even if your were to recover it before some crack addict sells it for a rock or two, this will do you no earthly good.

---

