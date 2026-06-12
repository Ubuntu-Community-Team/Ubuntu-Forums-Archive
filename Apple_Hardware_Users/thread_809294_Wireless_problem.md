---
title: "Wireless problem"
date: 2008-05-27
forum: Apple Hardware Users
---

### Post by speedemonV12 on 2008-05-27
Hi, my wireless was working just fine yesterday, i shut down my computer, and today when i booted into ubuntu, there is an error that flashes on the screen real fast, 

its something like this

ath0    no local ioctls           [failed]

so i continue to login, and i dont get any wireless options, and my wireless does not work.. any ideas what to do ?

im on a macbook pro. Thanks!

---

### Post by cyberdork33 on 2008-05-27
an update may have broken the madwifi drivers. Try recompiling them as in the wiki page for your mac.

---

### Post by speedemonV12 on 2008-05-27
hm.. been browsing through the wiki, kind of lost.. where is the recompiling information?

---

### Post by cyberdork33 on 2008-05-27
> **speedemonV12 said:**
> hm.. been browsing through the wiki, kind of lost.. where is the recompiling information?
Well you did not post which version of Macbook Pro you have, but since your output show ath0, I assume it is a first or second gen. Did you not have to compile madwifi already?

[https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927](https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927)

---

### Post by ibrastix on 2008-05-27
hey there,
similar things happened to me on my macbook, not the pro, so i thought i might share what i did to make it work again.

an update on Monday caused my Ubuntu (hardy on macbook) to say that no ath0 or eth0 extensions were available.

i just recompiled and reinstalled the mad-wifi and everything is fine now
to do this

1) download madwifi, if u don't already have it
2) go to the scripts folder and run ./madwifi-unload and ./find-madwifi-modules.sh $(uname -r)

3) go back to the main folder and using the terminal compile it using "make"
4) install it using "make install" (sudo)
5) add the new module by typing "modprobe ath_pci"

all ofcourse without the double quotes.

everything should be fine now

---

### Post by speedemonV12 on 2008-05-27
What version of madwifi are you using? The latest stable, or the latest snapshot? 

Also I got an error running the second script, and then continued to get errors for make. I was doing thus using the snapshot madwifi-ng-txpower-current.tar.gz pacage..

---

### Post by ibrastix on 2008-05-27
> **speedemonV12 said:**
> What version of madwifi are you using? The latest stable, or the latest snapshot? 

Also I got an error running the second script, and then continued to get errors for make. I was doing thus using the snapshot madwifi-ng-txpower-current.tar.gz pacage..
MadWifi v0.9.4, the latest stable.

for the errors in the make, make sure you have all the requirements, check the requirements at [http://madwifi.org/wiki/Requirements](http://madwifi.org/wiki/Requirements)

---

### Post by cyberdork33 on 2008-05-27
> **ibrastix said:**
> MadWifi v0.9.4, the latest stable.
Unfortunately, the latest stable code does not work on Macs (most anyway)... you have to checkout code with subversion, or download a snapshot as indicated in the wiki page.

---

### Post by Rog-Mahal on 2008-05-28
I have a 3rd gen. Macbook and if you're looking for a stable version, rv3545 in snapshots.madwifi.org/trunk works the best for me.

---

### Post by speedemonV12 on 2008-05-28
I have a second gen MacBook pro. Is there a way to completely remove the madwifi drive and then recompile it.. I don't understand why I am getting the make errors, since I compiled it once already before the update broke it.. Although I may have used subversion before. Is that easier? Problem is, I don't have Internet, so I have to download the driver in mac and then put it on a thmb drive in order to get it into ubuntu

---

### Post by cyberdork33 on 2008-05-28
> **speedemonV12 said:**
> I have a second gen MacBook pro. Is there a way to completely remove the madwifi drive and then recompile it.. I don't understand why I am getting the make errors, since I compiled it once already before the update broke it.. Although I may have used subversion before. Is that easier? Problem is, I don't have Internet, so I have to download the driver in mac and then put it on a thmb drive in order to get it into ubuntu

if you can post the errors, then we might be able to tell you the problem. 

Some of the code out there, just won't compile.

You can try doing 'sudo make uninstall' in the madwifi source directory, but that won't change you compiling errors.

---

### Post by speedemonV12 on 2008-05-28
ok so i connected through a wired connection and tried to install via subversion.. everything went fine till i ran this command. .. 

sudo sed -i~ 's/^exit 0/modprobe ath_pci\nexit 0/' /etc/rc.local

nothing happened.. terminal went to the next line and had this 

>

thats it.. 

then i get this when i run this command sudo iwpriv ath0 bgscan 0

ath0   no private ioctls..

---

### Post by speedemonV12 on 2008-05-29
anyone?

---

### Post by cyberdork33 on 2008-05-29
well, you probably won't actually see anything happen... this just adds a line into a script file. It looks like what it is "supposed to do is add "modprobe ath_pci" to the bottom of /etc/rc.local

Seems the command is formatted incorrectly or something though.

---

### Post by speedemonV12 on 2008-05-29
o, I took that command from the help.ubuntu link you gave me.. So what do I do now?

---

### Post by cyberdork33 on 2008-05-29
> **speedemonV12 said:**
> o, I took that command from the help.ubuntu link you gave me.. So what do I do now?
are you sure you did the command correctly? I think you may have copied a hidden character.

---

### Post by speedemonV12 on 2008-05-29
i didnt copy it, i typed it in.. tried it many times... what do i do !!! im dying without my Ubuntu

---

### Post by speedemonV12 on 2008-05-29
ok.. well i dunno what i did.. but now it works/... thanks for the help.. ill post here if i have any more problems.. thanks!

---

