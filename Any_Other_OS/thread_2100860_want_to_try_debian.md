---
title: "want to try debian"
date: 2013-01-03
forum: Any Other OS
---

### Post by boregard on 2013-01-03
Hello, i am wanting to try debian 6.0.6 first without installing.but every time i boot the live cd all i get is a black screen with white text. can anyone help me with which option i should choose to try it first without installing. thanks

---

### Post by lukeiamyourfather on 2013-01-03
The live mode doesn't always work which is why they have alternate modes (GUI installer, command line installer). If you can post the errors it would help but it might not be worth your time to troubleshoot if you can just install it to try it out, maybe on a spare disk?

---

### Post by ld114 on 2013-01-03
My experience is that Debian isn't really well suited to trying out on a live cd - the full set of drivers will probably not be there, hence your black screen with white text. Debian iso images are primarily installers, and during the install process you often have to download and add the necessary wifi and other drivers for your system. If you have a newer pc (ie less than two or three years old) it can also be problematic running Debian without installing software from the Debian backports repository - depending on the components of the pc (for example installing Debian 6.0.6 on an intel sandy bridge processor was problematic for me without installing a newer linux kernel and newer version of xorg etc from the debian backports repository).

All the same I like Debian stable, it is a very robust distro, and worth exploring and using. I would suggest that the best way to try it out is to use a virtual environment (eg with virtualbox) and run the standard Debian installer there.

---

### Post by BBQdave on 2013-01-03
> **ld114 said:**
> If you have a newer pc (ie less than two or three years old) it can also be problematic running Debian without installing software from the Debian backports repository - depending on the components of the pc (for example installing Debian 6.0.6 on an intel sandy bridge processor was problematic for me without installing a newer linux kernel and newer version of xorg etc from the debian backports repository).

+1 - if you have newer hardware, you may want to consider Debian 7 - wheezy testing. Debian 7 net install cd pulls in Gnome 3 as the desktop environment. So if you want to check out a similar Gnome 3 DE, try Fedora 17 Live CD. You can test Gnome 3 with out installing.

If you have newer hardware and want Gnome 2 - Linux Mint MATE is your friend :)

---

### Post by boregard on 2013-01-03
Thanks everyone for your replies. may just give  Debian 7 net install a try. I have heard netinstalls can be problematic though.

---

### Post by mips on 2013-01-04
> **boregard said:**
> Thanks everyone for your replies. may just give  Debian 7 net install a try. **I have heard netinstalls can be problematic though.**

Only if you install via wi-fi in some instances.

---

### Post by boregard on 2013-01-04
much thanks to all replies. ill mark thread as solved. peace

---

### Post by MadmanRB on 2013-01-04
Yeah debian can be a little tricky if you dont know where to start or try out.
Personally I have always used the net installer as it needs less disks, but that too can be tricky if you dont have hardware that debian is compatible with.

---

### Post by #1udancqSHv% on 2013-01-04
I had the same issues running the live cd, but ended up creating a new partition for it. I'd certainly recommend persisting, I'm really enjoying tinkering with it. Good luck! :)

---

### Post by kiyop on 2013-01-04
> **boregard said:**
> Hello, i am wanting to try debian 6.0.6 first without installing.but every time i boot the live cd all i get is a black screen with white text. 
In such case, it is useful to posting the concrete URL where the iso file is downloaded and the concrete error messages (written in white text).

Adding "nomodeset" to kernel option sometimes helps if graphical issue causes the problem.

---

### Post by mips on 2013-01-05
> **boregard said:**
> may just give  Debian 7 net install a try.

I would also go with Debian 7/Wheezy as it's currently in 'frozen' state and will probably released soon.

---

