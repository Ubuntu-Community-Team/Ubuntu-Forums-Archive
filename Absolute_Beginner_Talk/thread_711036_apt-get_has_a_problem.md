---
title: "apt-get has a problem"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by arjayes on 2008-02-29
Hi 
There seems to be some problem with apt-get ...  I tried installing a couple of packages from a CD and their dependencies were not met ... I tought apt-get install -f would clear it up but .. it gives me the following error 
> 
03:43 PM:$ sudo apt-get install -f 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on hplip (>= 2.7); however:
  Package hplip is not configured yet.
 hpijs depends on hplip (>= 2.7.12-0ubuntu2~gutsy1); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 hplip
 hpijs
E: Sub-process /usr/bin/dpkg returned an error code (1)


any idea what he problem is ??

---

### Post by JoshuaRL on 2008-02-29
I think you might have a problem with dpkg.  Could you try:
```

sudo dpkg-configure -a

```

---

### Post by jan quark on 2008-02-29
```
sudo dpkg --configure -a
```

now it is correct :)

---

### Post by Teber on 2008-02-29
> **jan quark said:**
> ```
sudo dpkg --configure -a
```

now it is correct :)

needed to apply that one after a fresh install of ubuntu and adding software. it should work wonders!

---

### Post by arjayes on 2008-02-29
This is what i got 
> 

05:19 PM:$ sudo dpkg --configure -a
[sudo] password for arjayes:
Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on hplip (>= 2.7); however:
  Package hplip is not configured yet.
 hpijs depends on hplip (>= 2.7.12-0ubuntu2~gutsy1); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 hplip
 hpijs


the output of "apt-get install -f "doesn't change

---

### Post by kesman on 2008-02-29
Why are you installing sofware from the cd? I bet there's newer and better working ones in the repositories.

---

### Post by quinnten83 on 2008-02-29
if you're still installing from the same CD than it won't change either.
I think it says that the files on the cd are not complete.
try to see if you can either install the dependencies or search the web for another version of the packages on the CD.

---

### Post by quinnten83 on 2008-02-29
there is a hplip website.
try googling it. i don' t remember the url from the top of my head..

---

### Post by jan quark on 2008-02-29
I think kesman is right

just try to install the software you need via synaptic
the dependencies will be installed automatically with the applications

---

### Post by arjayes on 2008-02-29
I did a fresh install of ubuntu . and because i didn't want to install all the packages again from the net i backed up the .deb s on a CD .. i tried
[quote ]dpkg -i *[/quote] in the folder containing all the .deb s . obviously  some of the packages failed to install because of broken dependencies .
can the dependencies be automatically installed ?
and why do i get the same error every time i do apt-get anything ?
how do i get rid of that error . If that's cleared i then i could install the rest of the dependencies without any problem  .

what exactly does the error message that comes when i try 
> 
dpkg --configure -a 
or >   sudo apt-get install -f 
what is wrong with 
cupsys, hplip& hpijs ?

---

