---
title: "Cisco Client"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by MShadix on 2006-12-05
](*,) 

Ok... I'm trying to install the cisco vpnclient on my new setup here.  I have the books and am learning as fast as I can.

Cisco uses a shell script for the install.  I had to install the C++ compiler and all kinds of other stuff just to get past the first line.  

Now it is looking for the src directory.  In the Script I find:

if [ -d /lib/modules/`uname -r`/build ]; then
    KERNELSRCDIR="/lib/modules/`uname -r`/build"
elif [ -d /usr/src/linux-2.4 ]; then
    #redhat 7.
	KERNELSRCDIR="/usr/src/linux-2.4"
elif [ -d /usr/src/linux ]; then
    #redhat 6.2
	KERNELSRCDIR="/usr/src/linux"
else
	KERNELSRCDIR=""
fi

Well I don't have these directories. No /build and the /src is empty.

So I've been reading on installing Kernal Headers...  but I'm not sure how, or even if I should.

Any help would be appreciated.

---

### Post by dabbner on 2006-12-05
I had that running on an old install, but I don't remember how I got it going.  That was in my newb days, and a buddy helped me out a lot. Now I use vpnc. much more straight forward installer.  

sudo apt-get install vpnc

yeah, it's really that easy...

---

### Post by steve.horsley on 2006-12-05
Try: **sudo apt-get build-essential**

---

