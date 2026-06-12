---
title: "[SOLVED] Amarok won't start"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Bubtottle on 2007-05-18
Hello, I am new to Linux, am using kubuntu and have encountered a problem with amarok.

Amarok was working but would not play FLAC files, a problem as my entire collection of files is in FLAC. In order to solve this, I searched on various forums and it seemed that the answer was to upgrade Amarok. However, once upgraded, when I click on amarok, a window appears for about a quarter of a second which I believe says 'Updating database' and then nothing happens. When I look at ksysguard, amarok is not shown. There is no amarok logo in the system tray. I decided to launch amarok from the terminal and got this response:


```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
declan@375-Shrews:~$     
``` 

If anyone understands what this means and what I should do, PLEASE tell me.

---

### Post by starcraft.man on 2007-05-18
Ok.... I have no clue what the gobbledy goop means... I also am somewhat limited in what I know about Kubuntu, but seems to me that since it only happened when you upgraded and since it worked before (i assume that), that the cause was something went wrong with when you upgraded. Soooo.... I think the easiest way is to remove it completely (I hope thats possible in kubuntu... not sure >>) and then reinstall.

Open up a terminal (should be somewhere in the menu under accessories) and put this command in:

```
sudo aptitude remove --purge amarok
```

Should get it all out. Then I'd suggest you put it back in, I dunno if you had to compile for your new version or it was in the repos, just use whatever means the guide you read suggested :).

Hope that works out for you, and hope someone doesn't post 5 minutes after and say I am completely wrong >.>. I try my best. Good Luck.

---

### Post by Bubtottle on 2007-05-18
Tried that, reinstalled and still have same problem; Amarok closes almost immediately.

---

### Post by jiminycricket on 2007-05-19
Have you tried removing the amarok settings in ~/.kde/share/apps/amarok ?  I've forgotten whether --purge completely removes that.  Are you installing Amarok from a normal Ubuntu repository?  How did you upgrade it?

---

### Post by Bubtottle on 2007-05-19
YES!!! :-D

Deleted folder 'amarok' and reinstalled and now it works! \\:D/

Thank you so much! Just one thing; Amarok still won't play FLACs. Do you know any way to make it?

Don't worry; found extra codecs, Amarok plays FLAC now. \\:D/

---

### Post by Lievre on 2007-05-25
Well, I had the same problem and the same solution worked for me...
... don't really understand all these linux stuffs...:-k

---

### Post by Sparkster185 on 2007-05-25
To get rid of those BAD DEVICE DRIVER messages, there's a simple solution.  Refer to this thread:

[http://ubuntuforums.org/showthread.php?p=1264009](http://ubuntuforums.org/showthread.php?p=1264009)

---

