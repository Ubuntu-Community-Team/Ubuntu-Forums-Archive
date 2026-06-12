---
title: "Security of Linux file system"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by RChickenMan on 2006-11-18
This question is out of sheer curiosity.  It has always been my impression that one of the key ingredients in Linux's legendary security is the file system itself (i.e. the strict ownership/permission associated with each and every file).  However, isn't this, to some extent, undermined by the fact that one can boot up a live CD, mount the hard drive, and do whatever they please via the super user of the live system?

---

### Post by LLRNR on 2006-11-18
Just a quick thought on this: The Live CD superuser do thing is something really good to do yourself with your own PC in case of an emergency. Anyway, if you _don't_ want this to happen in an institution, office, school etc., it's quite simple: The sysadmin might simply disable CD booting from BIOS and lock BIOS with a good password... What do you think of this?

---

### Post by 23meg on 2006-11-18
If someone can boot with a live CD on your system, you're pwnt in any case, even if you have the most secure operating system. That's not a software security issue, it's a physical security issue.

---

### Post by kinematic on 2006-11-18
i don't see how.....someone with malicious intent can't remotely boot your live cd ;)

---

### Post by cantormath on 2006-11-18
that is why people put passwords on there bios.......and change the boot order from cd to harddrive...

---

### Post by skymt on 2006-11-18
You're absolutely correct. One well-known Linux/Unix security proverb is "physical access is root access". There's no way, other than encryption, to prevent full access to the information in a computer if the attacker can spend time alone with the box.

---

### Post by RChickenMan on 2006-11-18
Yeah, that is certainly one solution.  What about the possibility of physically removing the drive?

As a side note, I have used this technique myself to repair a messed up ubuntu installation.  It was this experience that prompted me to post this.

EDIT:  Man, I love these forums!  During the time it took me to post my reply to the first person who responded to the topic, four other people posted!!!

---

### Post by PriceChild on 2006-11-18
If you're really worried, you can encrypt your entire filesystem.
> **kinematic said:**
> i don't see how.....someone with malicious intent can't remotely boot your live cd ;)I'd be impressed if anyone with extremely hAxOrz skills could ssh in, get the computer to put a live cd in itself, then reboot into a live cd.

THEN re-log in again... by ssh into the Live CD, even though the live cd doesn't really have any real account & password, before reading your files.

---

### Post by 23meg on 2006-11-18
Even if you disable recovery mode access and put a BIOS password, if the offender wants your data or access to your system badly enough, assuming they're standing in front of your box with noone else preventing them, they can smash your box open and remove your BIOS battery and reset it, or take out your HD.

It all comes down to physical security, from which *you* are responsible, not your OS.

---

### Post by ewl1217 on 2006-11-18
You have four options here:
[LIST]
[*]Only allow the BIOS to boot from the hard drive and password-protect the BIOS (but you're out of luck if you forget the password)
[*]Encrypt the hard drive or at least sensitive data (but someone could just delete it from a Live CD)
[*]Do both (although it may be overkill)
[*]Just trust that no one will mess with it (assuming that this is a computer at your house, and not in a public place)
[/LIST]

---

### Post by PriceChild on 2006-11-18
> **ewl1217 said:**
> Only allow the BIOS to boot from the hard drive and password-protect the BIOS (but you're out of luck if you forget the password)Nope, just remove the battery on the motherboard for 10 seconds, put it back in and password's disappeared! :)

---

### Post by RChickenMan on 2006-11-18
Good discussion.  Just to reiterate, I have no security concerns for my personal system at all.  I don't use a password at all in Windows (even for admin).  I was just throwing the idea out there, so I can have some come backs if someone points this out during one of my "Linux is superior" rants.

---

### Post by 23meg on 2006-11-18
Encryption isn't the ultimate solution either, since if the offender has physical access, they can take out your HD, take it home and decrypt it with brute force using their network of supercomputers.

---

### Post by LLRNR on 2006-11-18
Ewl1217's got a point here:
[quote="ewl1217"]Just trust that no one will mess with it (assuming that this is a computer at your house, and not in a public place)[/quote]

If this is not the case, as others already said, then it's just a matter of physical security: Either lock your room with 10 locks and 2 metal doors... either... the supervisers of the computers in a public institution _are_ paid for keeping their eyes open, right?

---

### Post by K.Mandla on 2006-11-18
Yup. As I was told once, "If someone has physical access to your computer, all bets are off."

---

### Post by aidanr on 2006-11-18
if you want to be really anal about securing your pc, use something like [this]("http://www.pcguide.com/ref/hdd/op/formTrays-c.html") and throw it in a safe when the pc's not in use

---

### Post by 23meg on 2006-11-18
I know someone who was hired to develop proprietary software for a company, to be used by that company only, and he carried not one but three HDs that contained redundant copies of his work with him all the time. He only plugged them into the computer when working on the software; they never stayed at home.

---

### Post by cantormath on 2006-11-18
> **RChickenMan said:**
> Yeah, that is certainly one solution.  What about the possibility of physically removing the drive?

As a side note, I have used this technique myself to repair a messed up ubuntu installation.  It was this experience that prompted me to post this.

EDIT:  Man, I love these forums!  During the time it took me to post my reply to the first person who responded to the topic, four other people posted!!!

you can encrypt the info on the drive ,easily up to about 4096 bit encryption, in several ways.  There are lots of encryption tools for linux.
also, lock the tower, or are they gonna take the tower?

---

### Post by 23meg on 2006-11-18
> **cantormath said:**
> 
also, lock the tower, or are they gonna take the tower?
Why not?

---

### Post by redbluemangle on 2006-11-18
Once to get my room mate back for a previous prank I took a screenshot of his desktop and made it his wallpaper then killed explorer.exe He wouldn't reboot because he was downloading a really big file (pron) and didn't want to start over. He now practises secure computing :D

---

