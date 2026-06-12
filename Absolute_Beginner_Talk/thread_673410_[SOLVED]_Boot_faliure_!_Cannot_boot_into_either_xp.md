---
title: "[SOLVED] Boot faliure ! Cannot boot into either xp or ubuntu :("
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by genbuntu on 2008-01-20
Well, I was shocked to discover this morning that my laptop failed to boot. It was working fine until yesterday. 

It came with Windows XP pre-installed , after which I installed Ubuntu fiesty and have been using the latter since many months now. At the time of installation I chose to let windows bootloader be the default one and added a couple of lines to get the GRUB boot option. With that I was able to boot into either windows or ubuntu successfully.

Now when my computer starts it fails to recognize any OS and gives the error : "Missing Operating System" . :confused:

So then I tried booting from a 'puppy linux' cd I had and it boots fine (from which I am writing this message :) ) , which indicates that the hardware is working fine (thank God ) .

But I have no idea what happened to my ubuntu and xp , although I can see the data files in the partitions .  :(

Pls. advise. 
Thanks.

---

### Post by frup on 2008-01-20
Were you able to mount the drive? It's possible you have a hard drive failure UNLESS you can fix the problem from the bios (change the drive priority etc).

---

### Post by kellemes on 2008-01-20
I'd get [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to fix your Grub-bootloader.

---

### Post by genbuntu on 2008-01-20
Yes , all the partitions mount successfully and I am able to access the files inside, so I guess the hard-drive is fine.

Hmm.. I've heard about super grub disk, thx :) but will have to download and burn it from elsewhere. 
Is there anything (commands etc. ) I can do to verify / change in my computer before I go on with the super grub disk ? . Can I manually change something in the boot files etc .. , possibly it might have gone corrupted ?

---

### Post by genbuntu on 2008-01-22
Well, I downloaded and used the Super grub disk and let it automatically fix the boot loader . :) So now my system is back to normal . Thanks for your advices .
Hmm... I still wonder what was the cause of this problem and what made the boot loader fail ; whether it was a virus (highly unlikely) or a software installation ( I didn't install any independent new software since past many days but could have been one of those updates) ..

---

