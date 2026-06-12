---
title: "installation failing"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by thaKing on 2006-12-24
i have downloaded ubuntu desktop 6.10 and burned to a CD...installed the cd, rebooted windows, ubuntu screen comes up and i select "Start or install unbuntu" from the menu...it takes a while and then the message comes up "Failed to start X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? Yes No"...

do i need to download and burn another copy?

---

### Post by taurus on 2006-12-24
Try to download and burn the alternate CD.  It works better then the desktop CD/LiveCD...

---

### Post by spockrock on 2006-12-24
system specs, also try using boot using safe gfx mode, then all else fails use the alternate disc to install.

---

### Post by thaKing on 2006-12-24
> **taurus said:**
> Try to download and burn the alternate CD.  It works better then the desktop CD/LiveCD...
i will try and download that...i think i've found the link for that...hopefully that will work...

[quote=spockrock]system specs, also try using boot using safe gfx mode, then all else fails use the alternate disc to install.[/quote]
intel 3.2GHz, 3GB RAM, 160GB HDD...i have pretty stout settings, i doubt that is the issue...

---

### Post by Sef on 2006-12-24
> intel 3.2GHz, 3GB RAM, 160GB HDD...i have pretty stout settings, i doubt that is the issue...

You got good specs.  The Live CD does not handle video cards as well as the alternate cd.  Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") to see how to install the alternate cd.  If you are not dual booting, just ignore the part about setting up a shared partition.  The rest will apply.

---

### Post by spockrock on 2006-12-24
> **thaKing said:**
> i will try and download that...i think i've found the link for that...hopefully that will work...


intel 3.2GHz, 3GB RAM, 160GB HDD...i have pretty stout settings, i doubt that is the issue...

whats your gfx card?  if x is failing to start it might be that which is causing your problem.

---

### Post by thaKing on 2006-12-24
> **Sef said:**
> You got good specs.  The Live CD does not handle video cards as well as the alternate cd.  Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") to see how to install the alternate cd.  If you are not dual booting, just ignore the part about setting up a shared partition.  The rest will apply.
thanks for the link....since i'm new to linux and ubuntu, i'm wondering if this beyond my knowledge of linux...

[quote=spockrock]whats your gfx card? if x is failing to start it might be that which is causing your problem.[/quote]
i'm using a RADEON X600 card...

---

### Post by taurus on 2006-12-24
> **spockrock said:**
> whats your gfx card?  if x is failing to start it might be that which is causing your problem.
And that's why there is the alternate CD in case the desktop CD/LiveCD can't handle the graphic card properly.

---

### Post by spockrock on 2006-12-24
when you boot up, there should be an option to boot in graphical safe mode, see if that helps, otherwise as mentioned try the alternate disc.

---

### Post by spockrock on 2006-12-24
> **taurus said:**
> And that's why there is the alternate CD in case the desktop CD/LiveCD can't handle the graphic card properly.

yes but there is also the boot using graphical safe mode option on the desktop cd, I thought instead of downloading and burning another disc thaking might like to try that option, its a possible 5 mins to try, and if it works it safes him bandwidth and another disc.

---

### Post by thaKing on 2006-12-24
> **spockrock said:**
> when you boot up, there should be an option to boot in graphical safe mode, see if that helps, otherwise as mentioned try the alternate disc.

oohhh...i like that idea, just because i'm no linux expert and looking over the link provided above, it seems a little more daunting to use the alt cd...i may try the safe mode first and see if that works...

---

### Post by spockrock on 2006-12-24
> **thaKing said:**
> oohhh...i like that idea, just because i'm no linux expert and looking over the link provided above, it seems a little more daunting to use the alt cd...i may try the safe mode first and see if that works...

dont worry, the alternate disc may look daunting its not, its really simple to use, thats what I first used, 7800gt would artifact and lock up, without the nvidia drivers.

---

### Post by thaKing on 2006-12-24
> **spockrock said:**
> dont worry, the alternate disc may look daunting its not, its really simple to use, thats what I first used, 7800gt would artifact and lock up, without the nvidia drivers.

well, it looks like i'll be using the alt disc...tried safe mode and same result....

---

### Post by thaKing on 2006-12-24
hopefully someone is still here and can answer my next question...i've downloaded the alt cd and began the installation...prior to this, i used partition magic to set up my partitions (C drive is Win, X drive is a networked partition i created on the drive, and there is free space - 30 GB - left that i wanted to install ubuntu on)...should i choose "Use the largest continuous free space" to use the 30 GB i have free on my HDD?

---

### Post by thaKing on 2006-12-24
> **thaKing said:**
> hopefully someone is still here and can answer my next question...i've downloaded the alt cd and began the installation...prior to this, i used partition magic to set up my partitions (C drive is Win, X drive is a networked partition i created on the drive, and there is free space - 30 GB - left that i wanted to install ubuntu on)...should i choose "Use the largest continuous free space" to use the 30 GB i have free on my HDD?

ok, took a shot and installed it on the free space...everything went smoothly....however, after installation i reboot and i get the same error...x is failing to start...it will only allow me to view the error log and that is it....how do i get past this and get ubuntu installed properly?

---

### Post by taurus on 2006-12-24
Boot into recovery mode from GRUB menu and at the prompt, run

```
dpkg-reconfigure xserver-xorg
startx
```

---

### Post by thaKing on 2006-12-24
> **taurus said:**
> Boot into recovery mode from GRUB menu and at the prompt, run

```
dpkg-reconfigure xserver-xorg
startx
```

apparently my vast knowledge of computers and windows did not prepare me for this...i entered what you said and it took me through a process of questions regarding keyboard, mouse, resolutions, monitors, etc, etc...i thought i entered everything correctly but alas, it gave me another error...i will have to mess with this later, as it's getting late and i've spent several hours on this already...

---

### Post by taurus on 2006-12-24
If you're not sure about a question, just use the default.  Otherwise, you can also run this command before startx...

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by spockrock on 2006-12-24
> **thaKing said:**
> apparently my vast knowledge of computers and windows did not prepare me for this...i entered what you said and it took me through a process of questions regarding keyboard, mouse, resolutions, monitors, etc, etc...i thought i entered everything correctly but alas, it gave me another error...i will have to mess with this later, as it's getting late and i've spent several hours on this already...

hmmm.....you may have to install ati video card drivers...that might fix your x woes.

---

### Post by thaKing on 2006-12-24
> **taurus said:**
> If you're not sure about a question, just use the default.  Otherwise, you can also run this command before startx...

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

tried that as well...same result...this is so frustrating...here is the error i get after running the command:
fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known precessed) with 0 events remaining.

what do i do? i'm completely new to linux and not sure what to do to get this installed...i'll try updating drivers as suggested by spockrock, but what else can i do?

---

### Post by spockrock on 2006-12-24
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

use that to give you a hand on how to install the binary ati drivers, its a simple enough process.

---

### Post by thaKing on 2006-12-25
> **spockrock said:**
> [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

use that to give you a hand on how to install the binary ati drivers, its a simple enough process.

that did it!!! (although i really don't know what i did) thanks to everyone who assisted...

one quick question - usernames for ubuntu (or maybe linux in general) can only consist of lowercase letters? i tried a mixture of upper and lower and it said it had to be all lower - or something to that effect....

---

