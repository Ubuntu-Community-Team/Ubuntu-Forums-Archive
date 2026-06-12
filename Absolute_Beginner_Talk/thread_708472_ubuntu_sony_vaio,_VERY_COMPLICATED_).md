---
title: "ubuntu sony vaio, VERY COMPLICATED :)"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by nymlord on 2008-02-26
ok so,. the problem is not with anything in ubuntu, thats working just fine, the only real problem is, is that, after my laptop is restarted about 24 times, it goes into this scan when being booted. a percentage metre starts and it goes all the way up to 51.1 %, and then stops, after that all i can do is use root@ script, but i have no idea what to type or what to do. so i just always end up reinstalling the whole OS.. 

its getting on my nerves and i dont know what to do,. if i didnt explain anything clear enough, please ask.

thank u :popcorn:

---

### Post by Therion on 2008-02-26
Well it IS related to Ubuntu actually.  If, when you installed Ubuntu, you used ext3 as the (default) filesystem then every 30 times you boot your computer it will do a filesystem check using the command "fsck".

So you're saying your PC starts doing this disk check and then freezes up solid at the 51% mark, correct?

---

### Post by stevejesus on 2008-02-26
I think you have hard disk trouble.

---

### Post by Therion on 2008-02-26
Have a LiveCD handy?  If so, drop everything, find it, boot to it and then from the terminal re-run fsck: 

```
sudo e2fsck -C0 -p -f -v /dev/sda1
```With any luck your hard drive will pass this check and break you out of the endless loop you're stuck in now.
Remove the LiveCD and see if you can boot normally.

---

### Post by nymlord on 2008-02-26
thats exactly it! fsck something something, and it happens after it freezes, i reboot and then, the 51.1 % thing comes up. ok ill try that. thank u!

---

### Post by nymlord on 2008-02-26
wait, am i supposed to enter this in the console when its stopped at 51.1 ? because, right now i just finished from installing ubuntu AGAIN, so it wont happen till i restart 30 times.. or should i just write it in the terminal now ?

---

### Post by Therion on 2008-02-26
Wait, wait, wait... You reinstalled?  You mean *totally* reinstalled from the ground up??  Just now??

---

### Post by thisiam on 2008-02-26
not sure but if he was to use ext2 instead of ext3 would it still do the check after said # of reboots?

---

### Post by nymlord on 2008-02-26
yes i just totally installed. :P so im supposed to w8 for the thing to happen ok. aight. thats cool

---

### Post by Therion on 2008-02-26
Okay, well that's one way to attempt to solve the problem.  

fsck *will* run itself every 30 restarts however -- it's built-in to Ubuntu.  It is, I believe, possible to disable fsck so it never occurs automatically, but I'm not sure how to do that and I certainly wouldn't suggest it.

---

### Post by nymlord on 2008-02-26
ok. well, ill try waiting for the fsck problem to come up, and then when it does enter the code, if that doesnt work, i guess ill try disable the fsck. thank you

---

### Post by nymlord on 2008-03-01
> **Therion said:**
> Okay, well that's one way to attempt to solve the problem.  

fsck *will* run itself every 30 restarts however -- it's built-in to Ubuntu.  It is, I believe, possible to disable fsck so it never occurs automatically, but I'm not sure how to do that and I certainly wouldn't suggest it.


ok so it happened, and i tried entering the code that u gave me and nothing happened so had to reinstall the os again.. anyways, im not sure if im doing it rite, i entered the code in the startup, where it gets stuck, im guessing im supposed to do it on the live cd while booted ? :S

---

