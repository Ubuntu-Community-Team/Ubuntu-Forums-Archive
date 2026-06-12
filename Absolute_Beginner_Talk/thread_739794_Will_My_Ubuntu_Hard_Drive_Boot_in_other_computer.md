---
title: "Will My Ubuntu Hard Drive Boot in other computer?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by hunter_te on 2008-03-30
Okey, i am going to my cousins place and i just wanted to show off my ubuntu.

His config is almost similar to mine but he lacks a graphic card. 

So do i have to disable my restricted drivers in my PC before i take out the hard drive OR will ubuntu program itself while its booting in my friends system?

Thanks in advance.

Regards :)

---

### Post by c-ron on 2008-03-30
Don't think there will be much to show off if he doesn't have a video card ;-)
Why not just show him the LiveCD?

Or, you could leave your system running at home, and use remote desktop sharing and make a VNC connection to it from his house (assuming he has internet access).
[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

It would be easier than reconfiguring grub to boot using new drive mappings, editing xorg.conf to load X, changing numerous other settings....

---

### Post by wormser on 2008-03-30
It is not a good idea.  Just show him the liveCD and [youtube videos of Compiz]("http://www.youtube.com/results?search_query=compiz&search=Search&sa=X&oi=spell&resnum=0&spell=1").

---

### Post by BaffledMollusc on 2008-03-30
Interesting question. I'm guessing yes, it'll work fine. I'm basing this on the fact that I've heard people do it with other linux distros, so I presume it'll work fine with Ubuntu as well.

I suspect that part of the boot process and firing up the kernel involves probing the hardware and loading relevant driver modules, so, in theory, provided all the hardware is supported by the kernel drivers, you should be able to stick your hard drive into anything and have it work.

---

### Post by ramjet_1953 on 2008-03-30
You need to consider this:

When you installed Ubuntu, part of the install process was that your hardware was detected and the necessary drivers were loaded.

Chances are, that your friend's computer has different hardware and it will not work.

Things like kernel panic and black screens are entirely possible.

Regards,
Roger :cool:

---

### Post by hunter_te on 2008-03-30
Thank u all for replying.

Well, as C-ron said, there wont be much to show without a gfx card....i have only recently put a gfx card and the only difference is, i can enable all effects without crashing compiz.

A few effects worked fine with onboard-video.

I think i am gonnna try this and let know everyone here about that experience...

---

