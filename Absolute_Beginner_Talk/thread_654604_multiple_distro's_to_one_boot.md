---
title: "multiple distro's to one /boot?"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by anthonie on 2007-12-31
Hi,

I want to give Gentoo another shot, but the last time I tried it, I ended up in a jungle of GRUB mumble, basically because I had so many destro's installed on my machine that I could no longer figure out how everything should be configured. Then I screwed up a partition that had nothing to do with the whole thing in the first place and got rid of all the other distro's, apart from ubuntu. 

So, from what I heard, it is advisable to create a seperate /boot partition for ubuntu (already installed). Would I just search for the partition and then point the Gentoo installer to that same /boot partition? 

It sounds very odd, to my ears, So basically I'd like to have some advise/pointers as to how a combination of multiple distro's would work.

---

### Post by meindian523 on 2007-12-31
Sounds interesting,would be possible if you could point Grub to the proper kernel for each distro,only doubt is "If you change the name of the kernel file for distro1 and point Grub to it correctly,does it affect other parts of the system,meaning to say would you have to change something(s) else too?"

---

### Post by louieb on 2007-12-31
1st time I dual booted two Linux distros (Fedora and Ubuntu)  I let them share the same /boot partition. It was a bad idea. problems every time one or the other had a kernel update.  

Now I let each distro put its grub in its root partition. One distros Grub is loaded by the MBR. The other distros Grub is chainloaded or  has a configfile entery in the  1st GRUB. Hope that makes some sense.  

More info on chainloading and the configfile option here.  [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by odiseo77 on 2007-12-31
I don't think you can share your Ubuntu's /boot partition among distros. You probably want to install Gentoo's grub on Gentoo '/' partition (or Gentoo's /boot partition, if you have one) and then edit your Ubuntu /boot/grub/menu.lst in and add the proper entry for gentoo (that's what I do for multibooting different OSs; however, the last time I tried gentoo, for some reason it wouldn't want to install grub on its '/' partition but on the MBR, so I had to do some extra tricks ir order to boot it).

---

### Post by anthonie on 2007-12-31
I think I had that same problem with Gentoo and Grub. How did you manage it to boot normal?

---

### Post by odiseo77 on 2007-12-31
> **anthonie said:**
> I think I had that same problem with Gentoo and Grub. How did you manage it to boot normal?

I don't remember quite well because it was many months ago. I think the problem was gentoo's menu.lst file was not there, so I had to mount my gentoo partition from Ubuntu, check the kernel and the initrd files and copy the lines for them to Ubuntu's menu.lst (or maybe I chrooted gentoo and installed grub from there? I'm not sure). (In case something goes wrong, you might want to use [SuperGrub]("http://freshmeat.net/projects/supergrub/"); I haven't used it, but seems to be very useful for these situations) :)

---

### Post by anthonie on 2007-12-31
Gracias! Just downloaded and will look into it when my second Gentoo attempt also fails :)

---

