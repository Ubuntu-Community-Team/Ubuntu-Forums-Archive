---
title: "News: Bootcamp won't be downloadable any more"
date: 2007-10-13
forum: Apple Intel Users
---

### Post by buschi on 2007-10-13
Hi all!

I read at [pctipp.ch]("http://www.pctipp.ch/news/betriebssysteme/41142/apple_boot_camp_bricht_die_zelte_ab.html") that as soon as Apple ships the new operating system (which includes Bootcamp), they won't provide the free download any more.

I don't know if that's true, just wanted to let you know...

Best,
Sebastian.

---

### Post by wdo_will on 2007-10-13
I'll make sure to save a copy if that is true, although, knowing Apple, I expect they'll figure out a way to stop it from working...

---

### Post by russell.h on 2007-10-14
The Boot Camp Utility (or whatever its called) will stop working on October 31st or thereabouts, assuming you have one of the last two versions. If you have an earlier version it stopped working September 31st I believe. You can check the EULA that you agreed to when you installed it for the exact details which I forget.

---

### Post by Hairy_Palms on 2007-10-14
forced upgrades anyone, seriously this is why ill never support apple...

---

### Post by wdo_will on 2007-10-14
Hmm... I hope this doesn't kill my Windows install, even though I use rEFIt to get to it; the utility itself is entirely pointless, as I have a Windows driver CD and I don't need to burn another one, and I partititon with a combination of the OS X command line and gParted on Ubuntu.  I wonder if there is any way that the Boot Camp program installed on Windows would mess it up.

I was planning on getting Leapord pretty soon anyway, though.

---

### Post by dmber on 2007-10-14
> **russell.h said:**
> The Boot Camp Utility (or whatever its called) will stop working on October 31st or thereabouts, assuming you have one of the last two versions. If you have an earlier version it stopped working September 31st I believe. You can check the EULA that you agreed to when you installed it for the exact details which I forget.
so wait a minute....

is there a way for me just have ubuntu on my macbook?

something about changing refit?

---

### Post by russell.h on 2007-10-14
You could just have Ubuntu on your macbook if you were to get rid of all the partitions the other Operating Systems are on. 

Just to clarify, the "Boot Camp Utility" stops working, but that shouldn't stop you from using your windows installation. Go ahead and make a drivers CD and keep it in a safe place now. Then you can use rEFIt to install Windows from now on, and you're good to go.

Also, with regard to the "forced upgrade", that was my initial reaction, really nearly any beta of a proprietary software will expire when the software is released. Of course I still think Boot Camp ought to just be a free utility, but obviously thats not for me to decide.

---

### Post by cyberdork33 on 2007-10-15
Your current partitions should be fine. You just won't be able to use the boot camp utility anymore... You can use the resizeVolume command in OSX, or use gParted to resize your OSX partition still.

---

### Post by mnml on 2007-10-15
for now i am booting from the EFI frimeware and I don't know why It takes more than 20seconds :D
Can I remove it and define my Ext3 partition as the boot partition? And is there a safe way to do that?

thanks

---

### Post by kingborel on 2007-10-16
Remember that Boot Camp was officially 'in beta', and not a full release ;)

---

### Post by mnml on 2007-10-16
They could release it as an opensource soft

---

### Post by cymacyma on 2007-10-16
I think that Apple coms are repeating what they did in 80s~90s. I wish Steve LOOKs  knows power of diversity and wide view of the future world. 

Only one way can make LOOKs proudly, but when the way is blocked, They will soon vanish once again...

---

### Post by cyberdork33 on 2007-10-16
> **mnml said:**
> They could release it as an opensource soft
There is no need. The bootcamp utility is not needed. An OSX terminal command (the one that the utility uses) and Gparted are both available and can resize partitions.

---

### Post by cyberdork33 on 2007-10-16
> **mnml said:**
> for now i am booting from the EFI frimeware and I don't know why It takes more than 20seconds :D
Can I remove it and define my Ext3 partition as the boot partition? And is there a safe way to do that?
You cannot 'remove' the EFI it is embedded in the computer hardware. If you are atalking about removing the EFI hard drive partition, you can do that, but would likely not change anything. (The EFI partition is used for firmware updates.)

---

### Post by mnml on 2007-10-16
> **cyberdork33 said:**
> There is no need. The bootcamp utility is not needed. An OSX terminal command (the one that the utility uses) and Gparted are both available and can resize partitions.

Bootcamp is made for people who don't even know what is a terminal, but you are right it's not hard to make a similare soft

---

### Post by mnml on 2007-10-16
> **cyberdork33 said:**
> You cannot 'remove' the EFI it is embedded in the computer hardware. If you are atalking about removing the EFI hard drive partition, you can do that, but would likely not change anything. (The EFI partition is used for firmware updates.)

yes but i don't even use osx anymore i wonder what's on the 3megs ^^(cf screen)

---

### Post by cyberdork33 on 2007-10-16
> **mnml said:**
> yes but i don't even use osx anymore i wonder what's on the 3megs ^^(cf screen)
Like I said, the EFI partition is only used for firmware updates. There have been several people that have removed it (and even totally reformatted their hard drive to the normal MSDOS partition format).

---

### Post by russell.h on 2007-10-16
Apple increased the student price of Leopard to 113 bucks up from 80ish. Damn now I'm in a bad mood.

---

### Post by mnml on 2007-10-16
don't ask me why everybody get in the tpb !

---

