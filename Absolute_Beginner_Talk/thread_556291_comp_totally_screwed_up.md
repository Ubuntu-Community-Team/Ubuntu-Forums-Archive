---
title: "comp totally screwed up"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by mozzie on 2007-09-21
ok so i really messed up

i had installed win 98, win xp, ubuntu edgy eft and ubuntu fiesty fawn on different hard drives.
while booting that GRUB thing used to come and i used to select the operating system and everything was ok.
the other day i accidently formatted the hard drives with ubuntu in them. now that GRUB loading thing comes and it says" error 17 " and the computer refuses to let me boot into windows. i was just trying to reinstall ubuntu and i got myself into this huge mess.....
can someone tell me how to boot into windows.....i'll sort out the rest of the mess myself!!!1
pls  help......:confused:

---

### Post by Arthur Archnix on 2007-09-21
The simplest solution would be to download a grub live cd, which will allow you to reinstall grub to the MBR, thus giving you access to whatever OS's you haven't borked. Sounds like you didn't install to the MBR in the first place. All those warnings that made you do that... yeah...that's just so 1995. 

There's cautious, there's hermits in the woods with bomb shelters, then there's the people who tell you not to install to the MBR or your pc *might*, just *might, might* die a horrible death and make baby jesus cry.

---

### Post by kellemes on 2007-09-21
Super Grub Disk will fix all your problems..:popcorn:

---

### Post by LaRoza on 2007-09-21
Agree with the SGD, in my sig.

---

### Post by bliffle on 2007-09-21
GRUB has never solved my boot problems, Just yesterday I bailed on a project that I couldn't solve the boot problems on. Luckily, I have alternatives.

The GRUB instructions are hard to understand and navigation is weird.

Maybe I had a bad GRUB CD or maybe we need some better instructions on how to use it.

I'm not shy about writing an MBR, I used to have to do that on a W2K system every once in a while and they had a special Recovery Console for it. 

I downloaded the GRUB in  the sig, Maybe it'll work better or even be understandable.

---

### Post by bliffle on 2007-09-25
talking about GRUB, which I find frustrating, I guess that GRUB CD just provides a multiboot GRUB for that session, then when one removes the CD the GRUB is gone. So, I've concluded that one must write a GRUB to the MBR of the 1st HDD on the computer. I didn't see a way to do that using the GRUB CD itself, but the linux system on the HDD has a CLI command "grub-install" which should do it. Now I gotta check to see if the puny system on the CD has a "grub-install".

Navigating the GRUB CD is weird.

---

