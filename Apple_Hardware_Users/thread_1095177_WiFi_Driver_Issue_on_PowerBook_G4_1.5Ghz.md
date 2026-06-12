---
title: "WiFi Driver Issue on PowerBook G4 1.5Ghz"
date: 2009-03-13
forum: Apple Hardware Users
---

### Post by Unix-Man on 2009-03-13
Hello I just finished a Dual boot of OS X 10.5 Leopard and Linux 7.10 Gutsy Gibbon. 
When im in Linux i cannot connect to my wireless network and when i try running the "Restricted Driver Manager" and try to enable the Driver for my WiFi card it gives me some error saying 

"The software source for the package bcm43xx-fwcutter is not enabled"    


I would really like some help with this WiFi issue because if i can't have internet on Ubuntu i have no reason to Dual boot it. 

Thanks Unix-Man

---

### Post by pytheas22 on 2009-03-13
Please boot to Ubuntu, plug your computer into the Internet via ethernet and run these commands:
```

sudo apt-get update
sudo apt-get install bcm43xx-fwcutter
```

You should be asked at some point if you want to download and install firmware automatically; say yes.  Then reboot and your wireless should work.

These steps will work in Ubuntu 8.04 and up.  I'm not positive about 7.10, but they should probably work there as well (is there a reason you're using 7.10 instead of a more up-to-date version of Ubuntu?).

---

### Post by Unix-Man on 2009-03-13
Yea the 8.04 version had a lot of issues and wouldn't allow me to change any settings and it would give me random error messages it was just really glitchy and not very stable 7.10 doesn't have many issues at all just this WiFi thing

Also thanks SO much this is the only answer i have gotten and i have made 3 posts about this issue :D

---

### Post by Unix-Man on 2009-03-13
All right i did the terminal command and this is what it came up with 



nick@nick-laptop:~$ sudo apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcm43xx-fwcutter
nick@nick-laptop:~$ 


Does that mean it can't find the package on the internet or on the Hard drive it's self?

---

### Post by pytheas22 on 2009-03-13
Sorry that didn't work.  It seems that the package it needs isn't in the repository.  You probably need to enable additional repositories (I don't remember which ones are enabled by default in 7.10).  But as an alternative solution, please try running these commands:

```
mkdir firmware
cd firmware
wget http://burnthesorbonne.com/files/bcm43xx-firmware.tar.gz
tar -xzvf bcm43xx-firmware.tar.gz
sudo cp *fw /lib/firmware
```

Then reboot.  Any luck now?  If not, we can try enabling the extra repositories.

---

### Post by Unix-Man on 2009-03-13
i cannot thank you enough, unfortunately i can't try this until tomorrow because im away from home but thanks you a million times for your help i'll let you know what happens with those commands

---

### Post by Unix-Man on 2009-03-14
Okay We tried commands and they didn't work even after we rebooted so i think we should try enabling the extra repositories 
Can you explain how?

---

### Post by pytheas22 on 2009-03-14
Sorry that didn't work.  To enable the package containing the bcm43xx-fwcutter package, go to System>Administration>Software Sources.  Under the 'Ubuntu Software' tab, you will have a list of software sources under the heading 'Downloadable from the Internet'.  Make sure that all the boxes in this list are checked (and in particular the box for the 'universe' repository, which I believe contains the package you need).  Then close the window.  If you're asked about reloading the sources list, say yes.  Then try running these commands again:
```

sudo apt-get update
sudo apt-get install bcm43xx-fwcutter
```

Hopefully it will work this time.

HOWEVER, I was thinking about this today and seem to remember that the bcm43xx driver in Ubuntu 7.10 did not support some wireless cards in certain Macs--even though it claimed the card, the card wouldn't work with it.  This has been fixed in later versions of Ubuntu, but I'm afraid that even with the bcm43xx-fwcutter package installed, your wireless card may not work.  If you still can't get your card working with the instructions above, please post the output of these commands so I can look up your exact wireless card model to see what the status of it is in Ubuntu 7.10:
```

lspci -nn
lshw -C Network
uname -rm
```

And also please let me know whether your Mac is Intel or powerpc-based.

If bcm43xx won't work, there are other ways to get the card running, so don't give up.  Sorry this is becoming so complicated; unfortunately, I'm a bit out of practice when it comes to Gutsy.

---

### Post by cyberdork33 on 2009-03-15
> **pytheas22 said:**
> And also please let me know whether your Mac is Intel or powerpc-based.
G4 = PowerPC

---

### Post by Unix-Man on 2009-03-15
GREAT!!!!! that worked it took a little bit of twisting but i got it working thanks guys

---

### Post by pytheas22 on 2009-03-15
Glad that worked, and sorry it took a few days.  I guess you were fortunate to have one of the Broadcom cards that was supported in Gutsy by bcm43xx.

---

### Post by fblud on 2012-08-03
I have an iBook G4 1.33Ghz and I'm having the same issue.  I tried all of the methods in the post with no joy.  **bcm43xx-fwcutter** isn't in the repository.

Yes, I went to Software Sources and made sure the 'universe' box (and all the other boxes) were ticked.  I tried to get and install it again.  Again, nothing.  Terminal still says its unable to locate it.  I tried a reboot for good measure.  'Unable to locate...'

I would really like to get this problem solved in the next fifty years.  It was mentioned that there 'other  ways' to get the card to work.  Do any of these involve coercion?  Obviously, I jest.  But, DA-YAM already.

I'm running Precise Pangolin 12.04.

Please help.  Thank you.


fb

---

### Post by pytheas22 on 2012-08-03
fblud: this thread is very old and the solution here no longer applies on modern versions of Ubuntu.  Please instead try installing the firmware-b43-installer package, which you can do by typing:

```
sudo apt-get update
sudo apt-get install firmware-b43-installer 

```
After that, reboot and hopefully things should work.  If not, please tell me the output of:
```

uname -a
cat /etc/lsb-release
ls /lib/firwmare
lspci -nn
sudo iwlist scan
```

---

### Post by fblud on 2012-08-11
Thanks for responding.  But, I figured it out myself.  I needed the b-43 and not the other one I was trying, bcm43xx.fwcutter.


Thanks again!

---

