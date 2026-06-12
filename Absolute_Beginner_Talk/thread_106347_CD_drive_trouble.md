---
title: "CD drive trouble"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Motoxrdude on 2005-12-20
Alright my cd drive used to come up on my desktop when i put a cd in, but now it doesnt. UNder disk manager when i put a cd in it recognizes it, how would i get the icon to start coming back, and is there another way of accessing it the cd? Thanks

---

### Post by Motoxrdude on 2005-12-20
nvm, fixed it. Some how it was disabled, so under disk manager i enabled it. Thanks for all the help you guys are awesome :)

---

### Post by Motoxrdude on 2005-12-20
OK now i actually have a problem. When i go to eject my cd drive it says:umount: only root can unmount /dev/hdc from /media/cdrom0
eject: unmount of `/media/cdrom0' failed
Any ideas?

---

### Post by bscbrit on 2005-12-20
To solve the immediate problem, in a terminal type

sudo eject

or

sudo umount /media/cdrom0

and your CD will be returned to your waiting hands....

As for why you haven't got permissions to eject the CD - I don't know.

---

### Post by Motoxrdude on 2005-12-20
hmm, that worked as a temporary fix, but i dont necesarily want to do that everytime. I have all the permissions checked off for my user in the user&groups. Weird though, it worked before that, and i dont remember changing anything.

---

