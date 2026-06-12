---
title: "need help with wireless card"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by pete_zahuat on 2008-01-29
I have a dlink (dwl-650 ver P1 802.11b) wireless card.  When I plug the card in only one light out of the two lights up. Ubuntu recognizes the card but I cannot get any internet access.   Where can I get a driver for this and is there a painless way of getting it working right?

---

### Post by pete_zahuat on 2008-01-29
anyone????

---

### Post by spiderbatdad on 2008-01-29
[http://kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html)

---

### Post by pete_zahuat on 2008-01-29
Is there a guide to setting this up?  I'm completely new to linux.

---

### Post by pete_zahuat on 2008-01-29
Can anybody help me?

---

### Post by macogw on 2008-01-30
You have to do as this post says first: [http://sin613.blogspot.com/2007/02/i-win.html](http://sin613.blogspot.com/2007/02/i-win.html)

Then as this one says:  [http://sin613.blogspot.com/2007/02/i-win-again.html](http://sin613.blogspot.com/2007/02/i-win-again.html)

The second should be easy enough to follow.  The first...not so much.  I'd say try ghex (it's in the repos) for doing as the first one says.

---

### Post by pete_zahuat on 2008-01-30
Do you have any idea where "m000Bc7100" would be at?  I'm sure that if I find that I can figure out the rest.

---

### Post by pete_zahuat on 2008-01-30
I guess what I'm really looking for is "hostap_cs.ko".  Any ideas where to look??   I'm completely new to this stuff.

---

### Post by macogw on 2008-01-30
Mine is here:
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/hostap/hostap_cs.ko

---

### Post by pete_zahuat on 2008-01-30
Umm... wow hex editing is way to advanced for me.  I did find a website with some instructions for the wireless card:

[http://ubuntuforums.org/archive/index.php/t-429547.html](http://ubuntuforums.org/archive/index.php/t-429547.html)           (just scroll down to the bottom)

The only problem is that soulglo83 says:

1. [http://www.red-bean.com/~proski/firmware/](http://www.red-bean.com/~proski/firmware/) (download the primary.tar.bz2 and the 1.8.2.tar.bz2 files, then extract the pm010102.hex from the primary.tar.bz2 and the rf010802.hex from the 1.8.2.tar.bz2 archive, extract them to /etc/firmware and then 'sudo chown your_username /etc/firmware/*' and 'sudo chmod 644 /etc/firmware/*').

I cannot find the /etc/firmware file.  I went to 'places,computer,filesytems,etc', looked for 'firmware' but I could not find it.  Am I looking in the wrong place?

Sorry to bug you soo much, but I really want this wireless card working.

---

### Post by macogw on 2008-01-30
that should probably be /lib/firmware/

---

### Post by pete_zahuat on 2008-01-30
I hope these will be my last 2 questions on this issue... 

soulglo83 says "extract the pm010102.hex from the primary.tar.bz2 and the rf010802.hex from the 1.8.2.tar.bz2 archive, extract them to /etc/firmware and then 'sudo chown your_username /etc/firmware/*' and 'sudo chmod 644 /etc/firmware/*')."

1.  I did find that file (lib/firmware), but in the firmware, there is a file that reads '2.6.22-14-generic'.  Should I put the two .hex files into that folder or just leave them in the original 'firmware' folder?

2.  I found out that the only way I could move the .hex files was being logged in as root.  Do I need to be logged into root in order to run these commands "'sudo chown your_username /etc/firmware/*' and 'sudo chmod 644 /etc/firmware/*')." ?

Thanks for being so patient with me

---

