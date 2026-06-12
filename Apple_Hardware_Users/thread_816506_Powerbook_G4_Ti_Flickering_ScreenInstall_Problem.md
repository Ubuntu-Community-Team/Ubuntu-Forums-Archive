---
title: "Powerbook G4 Ti Flickering Screen/Install Problem"
date: 2008-06-02
forum: Apple Hardware Users
---

### Post by Tiger658 on 2008-06-02
Hi I have been using Ubuntu for a while on Intel machines, and I just got my 1st mac to play with. So i decided to install the Ubuntu on it (It is a Powerbook G4 Ti Gigabit). and when I popped in the live CD expecting it to just boot and install, but when i got past the boot loader the screen started "flickering" (little white "flickers" flashing across a black screen). so i tried the other boot option, and all i got was a black screen with a little white line in the upper right corner. I gave up after a few more tires of the same thing, I had diagnosed the problem as a bad install disk. So I got online and got the alt install, I put it in and it installed correctly. so I boot it up, and when I get to where the ubuntu symbol would come on to the screen the flickering starts again. Now I can hear the drive working as it would if it were booting up. but the screen keeps on flickering. when the drive calms down i can hit the function keys to get to the terminal. so i know the system is working.

If anyone has some help it would be appreciated. I have looked through the forums and haven't found the answer. If someone needs my exact specs i would be glad to give them. But it is just a Powerbook G4 Ti Gigabit.

Thanks, Tiger

---

### Post by stream303 on 2008-06-02
I believe you have a radeon video card.

Can you try passing some kernel parameters at boot time, such as with the live cd:

```
live video=ofonly
```
or perhaps:
```
live video=radeonfb:1152x768-24@60
```

** Change those 1152x768 values to match your screens native resolution **

---

### Post by Tiger658 on 2008-06-03
Both of those codes gave this output > /pci@f2000000/mac-ia@17/ata-4@1f000/disk@0:11,\\live: No such file or directory so they didn't work.

Tiger

---

### Post by stream303 on 2008-06-03
To get past the live-cd video issue, have you tried downloading the "alternate" iso images, which are not live, but use text/ncurses for installation instead?   You still end up with a full gui, it just bypasses some issues like this.

---

### Post by Tiger658 on 2008-06-03
Yes that is what I used to install, I have it on my hdd but still have the same problems...

Tiger

---

