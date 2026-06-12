---
title: "Fresh Install of 8.04 on Macbook 4,1, Wireless card not working."
date: 2010-04-05
forum: Apple Hardware Users
---

### Post by MeNtuxRoKinU on 2010-04-05
Good morning,

        I have a MBP, 4,1. 2.4G, 4G RAM, 200G HD. I was running Ubuntu 9.10 on a 2nd partition that I created using Disk Util. Originally, I installed 8.04 on the 2nd partition, and upgraded to 9.10. Everything went fine, with the exception of the trackpad sticking intermittently. I was actually very satisfied about the install, and was using it frequently. Alas, the temptation to complicate my life grew too strong, so I downloaded the 10.04 alternate install 64Bit version to take a spin with. 

        Being one to test then install, I loaded 10.04 in a virtual machine using VMware, and was very happy with how everything was going. I then bit the bullet, wiping out my old 9.10 partition, and installing using the text version of 10.04 that I downloaded (wanted to make sure there was no issues with the graphics card). This is where my trouble began. 

        I installed 10.04 to disk, and again everything looked great. New GUI was impressive, as well as the updated branding (kudos, this was long awaited). There was a slight issue with Grub2 and rEFIt. Apparently either the updated version or ubuntu or Grub2 creates its own EFI partition (on my machine, sda3), so I installed it to sda4 when prompted. A little bit of a lag for boot up, and an error with the rEFIt partition editor was no big deal to me, as I could still boot into linux. 

       The main concern was the fact the after downloading the wireless card driver I was unable to connect to my wireless network. I thought that the problem may be the fact that my network has WEP enabled, so I tried several different unlocked networks also. No luck. I was a little bummed about that, then all of a sudden X started crashing on me, as well as another error associated with the boot splash screen? Not being used to all these issues, and wishing that everything worked right again, I decided to re-install 8.04, and give the developers more time on 10.04. 

       Once again I wiped, reinstalled and rebooted. 8.04 is up and running beautifully (as usual), and everything looked great. That is, untill I enabled the Broadcom STA wireless driver. Again, the same issue with 10.04. Can't connect to any network!! How is it that one day I can have a wireless card that works, and the next doesn't? The only thing I can think of is that I recently downloaded and installed the Mac OSX 10.6.3 update. Could this have anything to do with it? I noticed that in OSX, that my trackpad is sticking a little, so I definitely think that they need to revisit this update. But could it effect the wireless card? Any help would be greatly appreciated! Thanks!

---

### Post by linuxopjemac on 2010-04-05
try with wicd:

```
sudo apt-get install wicd
```

---

### Post by MeNtuxRoKinU on 2010-04-06
> **linuxopjemac said:**
> try with wicd:

```
sudo apt-get install wicd
```


This returned 

E Couldnt Find package..

Any other suggestions?

---

### Post by linuxopjemac on 2010-04-06
Maybe you are right, I checked and wicd is only available in Jaunty, Karmic and Lucid...

Why don't you install Karmic Koala ?
[https://help.ubuntu.com/community/MacBook4-1/Karmic](https://help.ubuntu.com/community/MacBook4-1/Karmic)

---

### Post by MeNtuxRoKinU on 2010-04-06
> **linuxopjemac said:**
> Maybe you are right, I checked and wicd is only available in Jaunty, Karmic and Lucid...

Why don't you install Karmic Koala ?
[https://help.ubuntu.com/community/MacBook4-1/Karmic](https://help.ubuntu.com/community/MacBook4-1/Karmic)


I would, but doesn't Karmic come with grub2? I'm trying to get around grub2, as rEFIt doesn't seem to like it (I believe because it creates it's own EFI partition that can't be synced?) Had major issues with rEFIt and Grub2 with my 10.04 install. Couldn't get the MBRs to sync, tryed putting Grub on sda3 and 4. Kindof a nightmare.

---

### Post by MeNtuxRoKinU on 2010-04-07
Upgraded to 8.10, problem solved!

---

### Post by linuxopjemac on 2010-04-07
Great!

---

