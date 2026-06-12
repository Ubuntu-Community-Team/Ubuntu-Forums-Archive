---
title: "Problem with upgrading to fix the faulty update"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by bmzhang on 2006-09-15
Hey there
I'm pretty new to Linux or any of this coding, I installed ubuntu a few days ago and it was working just fine and everything, just then i updated it by downloaded the files it asked me to, so i did, and as you heard from the notice it now won't go past the log in screen. I followed the instructions by going into the terminal (I think, not great with the terminology) and logged in and entered password, typed in sude apt-get update, but thats where I can;t get past. I can;t remember the exact message but its something like error with the public key A714EB8 TD1B1415, I could be wrong with that public key but before when it was working whenever I tried to reload the add/remove software thing it would always pop up with that message saying problem accessing a site becuase there was no pubkey.

Please help, its mid night right now and although I'm in no rush I really would like to fix this before i go to bed, so tired, so so tired.

Thanks for reading

---

### Post by Najand on 2006-09-15
Hmmm if it is a matter of gpg public keys, you need to import suitable ones... Write down the numbers it ask for and replace KEY in the following command with them and run this command in terminal to import them:
```
gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -
```

---

### Post by bmzhang on 2006-09-16
I tried the code above... I don't know what happened but the first line went ok I think, but when i enter the 2nd line it doesn;t do anything but say apt-key add- (file) or something like that.

Also I'm using ctrl+alt+F1 instead of just Crtl+F1, other wise it doesn;t do anything. Thank you for your time!

---

### Post by bmzhang on 2006-09-16
umm whoops the Ctrl+F1 thing is kinda irrelevant, I think i was reading it from somewhere else, but yeah 2nd line doesn;t do antyhing, I think I imported the key...
clueless here

---

