---
title: "Blue G3 and initrd.img-2.6.8.1-5-powerpc"
date: 2005-03-03
forum: Apple PPC Users
---

### Post by SocketMouth on 2005-03-03
Hello Ubuntu PPC Community,

I have a blue and white G3 300mhz that im trying to get Ubuntu 4.10 Warthog working with. Using a guide I found [here](http://ubuntuforums.org/showpost.php?p=42546&postcount=14)  on ubuntu forums I managed to get my ubuntu system up and running. I need some upgrades so I went ahead and updated my ubuntu system using synamptic but of course this overrid the hackjob on the initrd and Im back to not booting. I can use Ubuntu 4.10 cd and boot into the installer using expert mode but after I excute a shell I cant seem to figure out how to mount my hard drive. Has anyone had sucess with a G3 and initrd.img-2.6.8.1-5-powerpc? Any help getting my system up and running would be greatly appreciated.

---

### Post by farruinn on 2005-03-04
The same thing happened to me.  I wasn't clever enough to figure out how to get to the point in the install such that the previously installed (and unbootable) partition was mounted to /target so I ended up reinstalling entirely.  When I did my updates I believe I checked the initrd file to see if the patch had been incorporated and it had, unfortunately it didn't seem to help me at all... For every kernel since then I've had to replace the loadmodules file in the initrd.img.  I'm sure there is a way to mount the install so you can apply the hack, but I don't know how...

-Nathan

---

### Post by DirtDawg on 2005-03-04
I've got a little red imac g3 and everything installed just fine. I haven't upgraded anything through synaptic, though. I just wiped the drive completely and asked Ubuntu to partition the entire drive on install. Worked like a champ.

---

### Post by SocketMouth on 2005-03-04
Well, I would really like to use Ubuntu and it has to be on this Blue and White G3. What is the initrd package name in synamptic because then I can uncheck for upgrade.

---

### Post by farruinn on 2005-03-04
[QUOTE=SocketMouth]Well, I would really like to use Ubuntu and it has to be on this Blue and White G3. What is the initrd package name in synamptic because then I can uncheck for upgrade.[/QUOTE]

Um, I don't see how that's going to help you... what I've had to do is modify the loadmodules file in the initrd.img while in Ubuntu (modprobe loop first, then follow the hack as before).

---

### Post by SocketMouth on 2005-03-06
farruinn: I meant once I reinstall Ubuntu so it doesent upgrade the initrd. Anyways I found a bunch of packages using search in synamptic and locked them. When will this problem be fixed? Does Hedgehog have this problem?

---

### Post by farruinn on 2005-03-12
I just installed from the hoary preview CD and this problem seems to have been eliminated =)

---

