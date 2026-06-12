---
title: "please help with ndiswrapper"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by Tomas Galli on 2006-08-02
I´m traying to install ndiswrapper. i´m following the instructions from many places. 
this is what i'm doing

1)download and unpack ndiswrapper
2)uname -r (to see my kernel) Is 2.6.15-26-386
3)download the linux-2.6.15.tar.bz2 kernel source (i think is the one i need, i don find one         called exactly like my kernel:2.6.15-26-386
4)unpack linux-2.6.15.tar.bz2 in /usr/src
5)make a simbolic link with
   sudo ln -s /usr/src/linux-2.6.15  /lib/modules/2.6.15-26-386/build
6)go to /home/m y n a m e/modules/ndiswrapper (here was where .tar.bz2 file automatically extracted in)
7)and then 
 sudo make (i made aldo sudo make install)
  
and this is what i get:

Can't find kernel sources in /lib/modules/2.6.15-26-386/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make: *** [prereq_check] Error 1

Please help

I nee ndiswrapper to install windows drivers for my Nexxt usb wifi adapter. It have the sis163U chipset


Thank´s and sorry my english (cheers from argentine)

---

### Post by Dr. Nick on 2006-08-03
You try the precompile version of ndiswrapper in the repos?

sudo aptitude install ndiswrapper-utils

When messing with kernel hearder/sources you have to be exact, the safest bet would be to install them using the ubuntu repos to make sure you get the correct version, but if you build ndiswrapper from source as you are trying to do you will have to re-build it each kernel upgrade. 

Using ndiswrapper-utils from the repo will avoid that aswell, also ndisgtk is a gui to configure ndiswrapper that can be installed from the universe repo

---

### Post by Tomas Galli on 2006-08-03
Thank´s for the answer!

I understand what you mean. I did not had installed ndisgtk. Now, i got it
but nothing happens when i select a .inf file (i check with many sis163u.inf files from Win 98, 2000, xp) but nothing, i click "install driver" and no errors, but there is no driver listed in the "installed drivers" and tha&#347; all...

Thank&#347;

---

### Post by Dr. Nick on 2006-08-03
If you have ndiswrapper-utils and ndisgtk and selecting a .inf file doesnt do anything then you may be missing the .sys files, Where are you getting the drivers from? You need a .inf file and a few corresponding .sys files in the same folder for it to work I believe

---

### Post by TFX360 on 2006-08-04
> **Dr. Nick said:**
> If you have ndiswrapper-utils and ndisgtk and selecting a .inf file doesnt do anything then you may be missing the .sys files, Where are you getting the drivers from? You need a .inf file and a few corresponding .sys files in the same folder for it to work I believe

Jup, you do, I mean he does.


```

**ndiswrapper -i xxxxxx.inf**

```

Check if it worked via:


```

**ndiswrapper -l**

```

You should get:

**yourdriverinfname                driver present, hardware present**

blacklist native driver (if any) in /etc/modprobe.d/blacklist


Kind regards,


TFX

---

### Post by Tomas Galli on 2006-08-05
Thank&#347; u both for answsering. I,m working so hard at the momet on another things,, i&#314;l try what u are saying and i&#314;l tell u


Thank&#347; again

---

### Post by TFX360 on 2006-08-30
> **Tomas Galli said:**
> Thank&#347; u both for answsering. I,m working so hard at the momet on another things,, i&#314;l try what u are saying and i&#314;l tell u


Thank&#347; again


Still busy or have you tried it yet?

---

