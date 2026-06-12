---
title: "1st Install - Problems: No mouse, not a sudoer, can't change res"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by plugitin on 2006-08-30
Finally I got the balls to install Linux again. I had tried installing Fedora Core 4 a while back, but I kept getting problems and I uninstalled it. Now here I am with Ubuntu 6.06.1 and Windows dual-booted on my system. I'm so happy, except for a few problems. I have been searching around for about 3 hours now, and I have decided to just post all of my problems here and try to tackle them at once. Most of the time I know what I want/need to do, I just don't know the commands or how to do them. So if you all could help me I would appreciate it greatly.

First of all (and probably most important) my user is not listed as a sudoer. I had installed the setup in OEM mode (hey, it worked), and when I created a new user I gave it admin privilidges, rebooted, and deleted the OEM user. Now whenever I try to install a package or pretty much do anything it says I can't because I am not a sudoer. So, my question is after I boot into recovery mode how can I mount the partition (I have a SATA so = mount sda [?]), and fix this sudo config file.

Also, my mouse pointer doesn't show! I can't see it!!! I had a little fiasco with the Nvidia drivers, but after I got them fixed I cannot see the mouse for the life of me. How can I fix that.

Oh, and one more thing if you all don't mind. How can I make it so I can change the resolution to 1280x1024? The only options I get are 640x480, 800x600, and 1024x768, also the refresh rate is stuck at 85 Hz.

I would love it if someone please posted on how to fix all of these things. I know it is a lot, but I really want to get this working. Even with all of these problems that I am encountering ubuntu is a blast. Yeah, even without a mouse pointer, it rocks. So thanks in advance for any help I can get.
](*,) ](*,) ](*,)

---

### Post by jorn on 2006-08-30
I'm not quite sure of this:
> sudo mkdir /media/whatevername
sudo mount /dev/sda1 /media/whatevername
sudo fdisk -l    (to find the correct partition,sda1?)

---

### Post by kernelpanicked on 2006-08-30
Can't help ya with the X problem. There really isn't enough information posted to go by, but for sudoers, run visudo. Once your in the editor add this to the file.

```

yourusername    ALL=(ALL)   ALL

```

---

### Post by plugitin on 2006-08-30
Thanks for the reply. What information would you need to fix the problems wit h the mouse and display?

---

