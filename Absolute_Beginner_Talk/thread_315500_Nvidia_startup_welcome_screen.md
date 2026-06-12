---
title: "Nvidia startup welcome screen"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by moonliter on 2006-12-09
I have intalled latest nvidia drivers and every time before starting ubuntu 
there is nvidia welcome screen.Please how can I remove it

---

### Post by PurplePenguin on 2006-12-09
I haven't done this myself, but I did find [a link]("http://www.cs.cornell.edu/~djm/ubuntu/") which shows the before and after layout of your /etc/X11/xorg.conf:

```
(optional) Disable the nVidia splash screen:

        sudo gedit /etc/X11/xorg.conf

Change:

        Section "Device"
	     Identifier	         "NVIDIA Corporation ..."
	     ...
        EndSection

to:

        Section "Device"
	      Identifier	 "NVIDIA Corporation ..."
	      ...
	      Option		 "NoLogo"	"true"
        EndSection

```

---

### Post by moonliter on 2006-12-09
Thanks a lot for help it works!!

---

