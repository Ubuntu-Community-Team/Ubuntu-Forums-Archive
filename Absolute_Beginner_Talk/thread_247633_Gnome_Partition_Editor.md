---
title: "Gnome Partition Editor"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Surf Man on 2006-08-30
When I go into the Partition Editor from System-> Administration-> Gnome Partition Editor it won't allow me to resize the partions. How do I get into these options? I want to enlarge the size of my swap partition. I don't have windows or any other OS. Thanks.](*,)

---

### Post by Omnios on 2006-08-30
Try Gparted and or Qtparted, im not shure if the gnome partition editor can partition a hard drive yet lol. Anyways I had the most success with QTparted but Gparted should handle a linus partition with no problem. Its in synaptic

---

### Post by Surf Man on 2006-08-30
I can get into the program but the options are greyyed out to resize.

---

### Post by nazgulord on 2006-08-30
Hi,

I think you can't resize them because they're mounted. Try using a LiveCD like Knoppix which has QtParted on it.

nazgulord.

---

### Post by blent07 on 2006-08-30
dang, nazgulord just beat my to it. but yeah, you can't resize anything that's mounted, and I seriously wouldn't try unmounting it. But I downloaded GParted and burned it to a LiveCD, and it works great. However, if you have to resort to using command line, it probably won't work from the LiveCD, that I had to do in linux. But you're not doing ntfs, so nevermind.

---

### Post by blent07 on 2006-08-30
oh, and i forgot, if you have trouble displaying it, (when booting from the livecd, you'll be asked for display settings) just go with the lowest depth (8) and i saw no difference in resolution. 

that had me confused for five minutes. and that's five minutes I coulda had a resized partition!

---

### Post by Surf Man on 2006-08-31
I downloaded the livecd disc from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). I increased size of swap from 512 mb to 1.4 GB. It seems like my foxfire browser slowed down after increasing size of swap. Is this a coincidence related to internet service provider?

---

### Post by Abstract on 2006-08-31
I'm jumping on the bandwagon and saying get the GParted livecd. It works great and I've used it more than once so its worth the cost of a CD. Which isn't much anyways.

---

### Post by blent07 on 2006-08-31
> **Surf Man said:**
> I downloaded the livecd disc from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). I increased size of swap from 512 mb to 1.4 GB. It seems like my foxfire browser slowed down after increasing size of swap. Is this a coincidence related to internet service provider?

I can't tell you about if/how the swap size change affected it, but I seriously doubt it had anyhting to do with your service provider. In changing the swap size, you may have indirectly affected some of your other files in some manner. Unless your provider's messing with their equipment, then it wasn't them.

---

