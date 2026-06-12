---
title: "ibook g4 partitioning problem"
date: 2007-03-10
forum: Apple PPC Users
---

### Post by indica on 2007-03-10
hey,  i'm totally new to the forums, but i've been running ubuntu on my desktop for quite some time.
i got fed up with my giant windows laptop awhile back and decided to look for something smaller and more me. 
i settled on an ibook g4, hoping to put ubuntu on that as well since i've heard it takes well to it, and i finally recieved it late last night.

i'm having partitioning problems during install though.  it gives me an error and won't allow me to finish the partitioning.  

i'm at work right now so i can't give all the details right now, and will come back on to do that as soon as i get home.

has anyone encountered this problem and has suggestions on how i can solve it, preferebly without the mac os disk that i don't have?

---

### Post by kmoffat on 2007-03-10
I have a g4 933mhz ibook, and had some problems installing. I booted the live ubuntu 6.10 cd and used gparted to wipe the drive, since the original OS was unbootable. At that point I rebooted and ran the install from the desktop icon, selecting the automatic entire drive option (something like that). The partitioning was successful, giving me one unknown type (apple partition info, I think), one /boot, one ext3 root and a swap partition. 

I do get frequent disk errors during boot while fsck is run, but generally one manual running of fsck.ext3 fixes it. 

Wireless required an install of some firmware, but I found an easy how-to somewhere on this website.

Hope this helps a bit.

---

### Post by indica on 2007-03-10
thanks ken! i'll try that as soon as i get home

---

### Post by indica on 2007-03-10
thanks ken, that did work and it's installing now!

now onto these wonderful wireless problems i'm hearing sooooo much about :)

---

### Post by kmoffat on 2007-03-10
The fix for my wireless was pretty simple, an install of a fwcutter package, and maybe a simple firmware download. (It's been a little while)

---

