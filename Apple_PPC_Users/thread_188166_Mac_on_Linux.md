---
title: "Mac on Linux"
date: 2006-06-03
forum: Apple PPC Users
---

### Post by unicycler on 2006-06-03
Has anyone successfully put Mac on Linux? I have tried before, and mol itself was running, but I could not get another OS to load. What is the best tutorial for MOL besides their website, because it did not help me.

---

### Post by MetalMusicAddict on 2006-06-03
It looks like there are 2 choices the RMP (use Alien to install) or the repo to add to your sources.list. 
```
deb http://people.debian.org/~jensen woody/
```

It seems like the project is dead though.

---

### Post by ubuntubrian on 2006-06-03
I have MOL running OS X 10.3.9 on my TiBook G4 installed with synaptic. I used the Ubuntu tutorial:
[https://wiki.ubuntu.com/MacOnLinuxHowto](https://wiki.ubuntu.com/MacOnLinuxHowto)
and had no problems, fired OS X right up with networking and most everything works. Skype doesn't work tho and I heard that was a problem. What OS do you have running on your other partition? MOL needs to "see" that to run an OS.

---

### Post by fjs on 2006-06-04
Yellow Dog say MOL does not work with nVidia graphics. I cannot use it with Dapper or YDL 4.1 on an iMac G4.

---

### Post by yojimbo-San on 2006-06-04
fjs, do you have a reference for that?

I have an nVIDIA GeForge4 440 in my iMac; MoL works under X (xorg using the 'nv' driver), and does work on a console; but with only 8bit color, which isn't nice at all.

---

### Post by EuroCity on 2006-06-05
[QUOTE=MetalMusicAddict]It seems like the project is dead though.[/QUOTE]

Yes, this could indeed be a worrying aspect of MOL for the future: for example, its [main site](http://www.maconlinux.org) hasn't been updated for ages, now; and the mailing lists don't seem to be all that much "alive", either.

So, will MOL still continue to be developed, especially within the Ubuntu PPC "vision"?

For example, one might want to know if there will be a Mac OS X 10.5 "Leopard" patch for MOL, enabling it to work also with the next revision of OS X; and, in general, to know if it will continue to work reasonably well with OS X 10.4.x and previous versions, before letting Linux take control over OS X in a window...

---

### Post by yojimbo-San on 2006-06-05
MoL is still alive; see [http://lists.maconlinux.org/pipermail/mol-general/2006-May/004163.html](http://lists.maconlinux.org/pipermail/mol-general/2006-May/004163.html) for a response to the same question recently. Basically the most active developer has no write access to the website at the moment.

But they are very quiet :-)

-jim

---

### Post by fjs on 2006-06-05
Yellow Dog:

MOL (Mac-On-Linux): MOL does not function with Apple G5 computers nor with any computer that uses NVidia graphics cards. The former is an issue of emulation and requires a rebuild of MOL, the later an issue of graphics card support. We are working to resolve these as quickly as is possible ... 

footnote

[http://www.terrasoftsolutions.com/support/hardware/breakdown/index.php?hw_cat_id=5](http://www.terrasoftsolutions.com/support/hardware/breakdown/index.php?hw_cat_id=5)

---

### Post by yojimbo-San on 2006-06-06
Thanks fjs. Despite the Yellow Dog comments, MoL *does* work with my G4/nVIDIA GeForce4 ... however, only at 8bit color when fullscreen; which is basically unuseable. It works fine under X windows though, although I'm not sure how to size the window that opens up.

They may be right in asserting that it doesn't work to their standards; but it does work.

---

