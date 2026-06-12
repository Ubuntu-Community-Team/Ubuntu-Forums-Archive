---
title: "Backing up Windows..?"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2005-12-03
I want to make the conversion to Ubuntu from a Windows XP Lappy. My Dad doesn't like the idea of re-formatting the HD because I'll loose Windows, and once it's gone, it's gone - And Windows doesn't come cheaply! My question is, is there a way that I can back up Windows ( just the operating system ), so that, should I NEED to re-install it, I could? Dual boot is not an option!

Thanks, 

Jimmey

---

### Post by mlomker on 2005-12-03
You don't have a Windows CD?  Even machines that come preloaded usually come with system restore CD's or they can be requested from the manufacturer.

There are ways to back it up but you'd have to have a disc or somewhere to back it up to.  You can boot a Knoppix CD and use the **partimage** tool to back up an entire partition but it still uses a lot of space (perhaps half of space after compression).

---

### Post by Kvark on 2005-12-03
Uhm, didn't you get an install CD or restore CD when you bought Windows?

There are countless situation where you need to reinstall windows, when you can't remove some virus or spyware or when the virus messed up the whole system, when a hard disk chrashes, when there is so much junk gathered over time that everything goes way too slow, or when someone makes a mistake and breaks the whole thing. So if you got windows with the laptop then they really should have given you a restore CD with it too.

---

### Post by Jimmey on 2005-12-03
I must have...*coughs* lost it =-(
Could I not back it up onto a RWable DVD?

---

### Post by mlomker on 2005-12-03
[QUOTE=Jimmey]Could I not back it up onto a RWable DVD?[/QUOTE]

That depends upon your hardware setup.  A disk imaging tool would need a hard disk partition other than the one that you are backing up to save the image to (and it'd need enough free space).  Partimage can be configured to save the image into chunks small enough to fit on your disc, so that shouldn't be a problem.

---

### Post by philipMac on 2005-12-03
Honestly mate, you should probably request a new Win CD off the manufacturer. Seriously, with all due respect to Windows... ahem... you regularly need to nuke the system when it gets so clogged with root kits, spyware, and misc other crap, that it becomes unusable. Not that Windows is prone to that sort of thing. Heaven forend! I am just talking hypothetically here. 
Do your best to get your hands on one. Otherwise try copying a Windows CD off another person, and use your ID code on your machine. 
And, if none of those things work... your old man might want to start getting to grips with the big penguin. Because... that Win install wont last forever. :???:

---

### Post by KermitJr on 2005-12-03
Use partimage to ghost the drive/partition.

ALso, you don't have to remove windows... just resize the partition and install ubuntu along side it.

---

