---
title: "Feisty on MBP 2.33, 2Gb RAM, 120GB HD???"
date: 2007-04-20
forum: Apple Intel Users
---

### Post by erkker on 2007-04-20
Hello All,

I Just bought a new MBP 2.33GHz, 2 GB RAM, 120 GB HD.  I have been playing around with linux since Dapper came out.  I have managed a desktop dualboot (edgy/XP), and XUbuntu is the only OS on my legacy gateway laptop.

I really want to dual boot OSX Tiger 10.4.9 and Feisty, but this is my personal work laptop and I cannot really afford to go thru 3 reinstalls and troubleshoots for a few months yet though I am not afraid of tweaking and a little command line.

Basically I was wondering what the state of the Feisty on a MBP was.  I know the version just hit public release.  I also have searched and seen several dual boot guides but most of them seem dedicated to Macbooks or MBP with slower processors etc etc  

Also I saw that feisty handles EFI better, but i found nothing really concrete about the changes.  Any news.  

I just want to be aware of hardware compatibility before I take the plunge, so I know if I need to wait for a few months so I can dedicate a few late nights to run all my favorite X software natively :)

thanks all

-E

---

### Post by ronocdh on 2007-04-20
> **erkker said:**
> Hello All,

...

Basically I was wondering what the state of the Feisty on a MBP was.  I know the version just hit public release.  I also have searched and seen several dual boot guides but most of them seem dedicated to Macbooks or MBP with slower processors etc etc  

Also I saw that feisty handles EFI better, but i found nothing really concrete about the changes.  Any news.  

I just want to be aware of hardware compatibility before I take the plunge, so I know if I need to wait for a few months so I can dedicate a few late nights to run all my favorite X software natively :)

thanks all

-E

I don't think the guides are at all invalidated because of your slightly newer hardware; MBP guides will work fine for you in that regard. I right now am triple booting with XP and Edgy, and to get that going I had to use the GRUB kludge made famous by [this guide]("https://help.ubuntu.com/community/MacBook"). Now, though, I hear Feisty does indeed install fine on EFI systems. Hurray!

I wouldn't worry about trashing your OS X install. Install [rEFIt]("http://refit.sf.net") and you should be all set. Choose your partitions wisely and worst case scenario, you won't have Feisty booting right away.

Good luck, and post back with your results!

---

### Post by ronocdh on 2007-04-20
> **ronocdh said:**
> I don't think the guides are at all invalidated because of your slightly newer hardware; MBP guides will work fine for you in that regard. I right now am triple booting with XP and Edgy, and to get that going I had to use the GRUB kludge made famous by [this guide]("https://help.ubuntu.com/community/MacBook"). Now, though, I hear Feisty does indeed install fine on EFI systems. Hurray!

I wouldn't worry about trashing your OS X install. Install [rEFIt]("http://refit.sf.net") and you should be all set. Choose your partitions wisely and worst case scenario, you won't have Feisty booting right away.

Good luck, and post back with your results!

I have a 2.16Ghz C2D MBP 15". I am going to wipe my Edgy partition tonight and throw Feisty on there. If you would like, I can post back with my results tonight or tomorrow morning and be your guinea pig. ;)

---

### Post by erkker on 2007-04-20
I will make a trade with you.  Post those results and I will try to post the results of my next project which is booting feisty from a 5-10 GB partition on my 30 GB usb ipod using rEFIt.  That way Linux will be self contained and if all else fails I reformat the fat32 partition on my iPod and and just drag all the files back.  I love Rockbox.  Who knows if I can make it work, but its worth a shot right???

-E

---

### Post by ronocdh on 2007-04-20
> **erkker said:**
> I will make a trade with you.  Post those results and I will try to post the results of my next project which is booting feisty from a 5-10 GB partition on my 30 GB usb ipod using rEFIt.  That way Linux will be self contained and if all else fails I reformat the fat32 partition on my iPod and and just drag all the files back.  I love Rockbox.  Who knows if I can make it work, but its worth a shot right???

-E
Killer deal. Bad news already: X failed to start. I was booting from the 64-bit CD, which I have verified twice, so it's a good burn. This is the same problem I was having [two weeks ago]("http://ubuntuforums.org/showthread.php?t=398959"), but I thought it to be a beta issue then. I am burning the alternate 64-bit iso now, and I'll give a spin with that and post back.

For those interested, the output I got when I tried to run **startx** after failing was:
```
Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) 
        on X server ":0.0" after 0 requests (0 known processed)
        with 0 events remaining
```
And then I'm back at the prompt. I got this same result even in the safe graphics mode on the Live CD.

---

### Post by balt on 2007-04-20
Chaps,

can anyone tell me how you got 7.04 to boot on your MBP's? I have a 17" MBP, 2.33 GHz, 2GB RAM, 160GB disk, but when I boot off the CD, it boots into a black screen.

Any ideas? Anyone out there with the same hardware that is NOT having this problem?

- Balt

---

### Post by ronocdh on 2007-04-20
> **balt said:**
> Chaps,

can anyone tell me how you got 7.04 to boot on your MBP's? I have a 17" MBP, 2.33 GHz, 2GB RAM, 160GB disk, but when I boot off the CD, it boots into a black screen.

Any ideas? Anyone out there with the same hardware that is NOT having this problem?

- Balt
I just tried installing from the alternate CD (64-bit). It worked in that I was able to get through the entire installation, GRUB and all (stuck it in the MBR for XP), and was able to boot into it from rEFIt. However, I just had a command prompt after the snazzy Ubuntu loading screen, and typing **startx** got me the exact same error message as above. I tried **sudo dpkg-reconfigure xserver-xorg** and manually specified what I needed; no go. Same error message upon trying to start X.

What is this madness?

---

### Post by ronocdh on 2007-04-20
Just found this neat info taken from michaels's [blog]("http://www.cs.helsinki.fi/u/jzshen/install_feisty.html"):
> 8.       My mac can’t start gdm, the following commands can get it work:

sudo apt-get install xorg-driver-fglrx

sudo depmod –a

sudo aticonfig –initial

sudo aticonfig --overlay-type=Xv

startx

9.       Double click the installer then go through. At the partition step, choose “Manually” to do the partition. When the partition table come, just edit mount point “/” at “/dev/sda3” and click “reformat”. As to the windows partition, I don’t choose to mount it automatically. Later, you will see the reason. Click “forward” button and ignore the warning of no swap!

10.   DO NOT migrate from some account from Windows XP, which may cause problems!

Going back down to try it now. Can't believe I didn't think of that.

---

### Post by ronocdh on 2007-04-20
> **ronocdh said:**
> Just found this neat info taken from michaels's [blog]("http://www.cs.helsinki.fi/u/jzshen/install_feisty.html"):


Going back down to try it now. Can't believe I didn't think of that.
It works, it works, it works! A thousand cheers to michaels. =)

Trackpad behavior is so irritating to me that it's unusable. Had to grab a USB mouse to post this. ;) I'll get on that shortly.

Hurray!:mrgreen: ):P

---

