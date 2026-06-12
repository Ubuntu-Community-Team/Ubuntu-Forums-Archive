---
title: "MacBook shutdowns"
date: 2007-07-25
forum: Apple Intel Users
---

### Post by brertom on 2007-07-25
Hey there,
I have myself some difficult issues and I am wondering if anyone has the same problem or has solved this problem. Ok so i have a first generation MacBook and as may people know the first generations may have a random shutdown problem. Well for months I wasn't experiencing any of these random shutdown problems and I decided I wanted to install ubuntu. After awhile of being happy with ubuntu the random shutdowns started happening. Sadly I didn't dual boot ubuntu and mac os x so now I can't install the updated software to fix the shutdown problem. Any suggestions? Also I can borrow someones mac os x cd but I would much rather solve this problem without putting mac back on my computer. thanks for at least reading this I'd love to here suggestions.

---

### Post by russo.mic on 2007-07-26
Sorry Friend, but as i Understand it, the shutdown's happen because of a heating issue, and a firmware update is nessessary to fix it.  

Honestly, you probably want to put OSX on it anyway for the purpose of future firmware updates.  Good luck!

---

### Post by brertom on 2007-07-26
Alright thanks bud,
I just hope I can get a copy of mac osx so I don't have to buy it yikes.
Also when I put mac back on my comp will ubuntu be automatically deleted?

---

### Post by ryan86corolla on 2007-07-26
you may be able to boot from an external hd or another mac to install the firmware update.

---

### Post by misfitpierce on 2007-07-26
If you got friend with mac the discs that came with it put whole OS back on and can borrow discs... :) lol damn macs

---

### Post by Gen2ly on 2007-07-26
I definitely wonder if Apple will replace it.  I have the same computer and have been lucky.  Also you can set lm_sensors to your liking so that, say, your fan restarts more often.

---

### Post by brertom on 2007-07-27
hmm well sorry for all the questions but how would I do that? Also when I put the mac os x cd back on my computer will it just auomatically delete all the ubuntu stuff, will there be a partition option, or will I have to try and uninstall ubuntu or something like that?

---

### Post by cyberdork33 on 2007-07-27
> **brertom said:**
> hmm well sorry for all the questions but how would I do that? Also when I put the mac os x cd back on my computer will it just auomatically delete all the ubuntu stuff, will there be a partition option, or will I have to try and uninstall ubuntu or something like that?

It will wipe the drive. You can try to partition before installing with DiskUtility

---

### Post by russo.mic on 2007-07-28
As your installing, you might be able to partition the drive, but it'll probably wipe out whatever bootloader you've got on it.  Still, installing rEFIt afterwards should cure that, then you'd probably have to restore GRUB on the linux partition,  Might work.   

As far as setting the fan goes, you'd better do the firmware update.  I don't remember what it was, but there IS some problem in the machine that causes it to over heat.  I don't think just setting your fans to spin faster is a good enough solution.  

Backup, and give it a try.  Make sure to post back and tell us if it worked, as I'm curious if you can reinstall OSX and restore the bootloader myself.

Russo

---

### Post by brertom on 2007-07-28
will do, lets just hope my computer isn't done for :(

---

### Post by brertom on 2007-07-29
okay so heres an update.. a sad update. so I am actually on vacation with my family all summer but my uncle is with us and he has the mac os x cd for macbook pro soo i tried booting it up on my computer and installing it, but an error came up saying I can not install this software on this computer. Do you think this is because it is for the macbook pro and not the macbook, or is there further problems?

---

### Post by cyberdork33 on 2007-07-29
> **brertom said:**
> Do you think this is because it is for the macbook pro and not the macbook?

Yep

---

### Post by brertom on 2007-07-29
ok fewf

---

### Post by brertom on 2007-07-31
so theres absolutely no way to download the SMC firmware update on ubuntu?

---

### Post by cyberdork33 on 2007-07-31
> **brertom said:**
> so theres absolutely no way to download the SMC firmware update on ubuntu?
you might be able to download it, but installing it is another issue.

---

