---
title: "how do i make windows see my ubuntu partition?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by cpu_medic on 2008-03-03
i need to make my windows be able to write to my ubuntu partition. i am trying to install envy for my vid card drivers on my desktop, but i dont have internet on the desktop, nor will it see my cdrom drives. so if i write envy to the disk itself, will i be able to install the .deb under the console?

---

### Post by Joeb454 on 2008-03-03
Try this out: [ext2fsd]("http://sourceforge.net/projects/ext2fsd") :)

Hope it helps...and yes as long as you write to the Ubuntu partition (you might need to fiddle the permissions etc if it's over a network, I'm not sure :))

---

### Post by alzie on 2008-03-03
Or try this  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) to let ubuntu see your windows partition

---

### Post by mikewhatever on 2008-03-03
> **cpu_medic said:**
> i need to make my windows be able to write to my ubuntu partition. i am trying to install envy for my vid card drivers on my desktop, but i dont have internet on the desktop, nor will it see my cdrom drives. so if i write envy to the disk itself, will i be able to install the .deb under the console?

fs-driver --> [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Joeb454 on 2008-03-03
Ubuntu 7.10 can automatically read Windows partitions, it just needs telling where they are...either way you can get your file to the Ubuntu machine :)

---

### Post by cpu_medic on 2008-03-03
ok, um ive tried ext2fsd and i can see the drives, however it says there are 0 bytes free, and i havent even been on the gui yet.

---

### Post by cpu_medic on 2008-03-03
what is the driver update cd? and how do i get it?

---

### Post by ryanhaigh on 2008-03-03
Use the ext driver from fs-driver.org, once installed you go into control panel and setup what it calls ifs drives by assigning your ubuntu partition a drive letter and that is it, go to my computer and you will have access to your ubuntu data (be careful there are no permission restrictions) if you have a separate home partition just use that and don't mount the / partition. 

Performance is not as good as native filesystem and uses some CPU but is the easiest solution I have found.

---

