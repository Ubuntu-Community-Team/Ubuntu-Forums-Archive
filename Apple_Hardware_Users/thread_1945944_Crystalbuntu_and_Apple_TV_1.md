---
title: "Crystalbuntu and Apple TV 1"
date: 2012-03-23
forum: Apple Hardware Users
---

### Post by helios16v on 2012-03-23
I'm trying to install Crystalbuntu on my Apple TV 1, I have just used AtvCloner 0.2 to clone the 40GB HDD over to a new 320GB HDD, I then used AtvPatchstick to install XBMC on the original OS X install, however it is going horribly slow with major sound and video issues due to slow down.

Now I'm sitting at the Crystalbuntu install with XBMC auto install but I'm having a problem and have no idea what to do, I saw some other threads about other people having the same error I'm having with no answers so I decided to make a fresh thread for some new information.

> How to make a USB stick for XBMC on ATV internal harddrive with USB installstick
1. [http://download.stmlabs.com/atv-images/installer/installer.img.gz](http://download.stmlabs.com/atv-images/installer/installer.img.gz)
2. unpack with betterzip
3. open Terminal
4. type: diskutil list
5. search your usb stick normal it is disk1
6. type: diskutil umountDisk /dev/disk1
7. type: dd if=installer.img of=/dev/disk1
8. wait until get a input prompt, put USB in ATV, power off,on wait
9. time for tricky part, a config file is missing and must be written on linux
10. wait for install failure on ATV, you get a login prompt, login with user/pass ATV
11. type: sudo -s
12. type: cd /
13. echo ubuntu > .distro
14. power off,on wait for a full install, remove USB and wait for XBMC install.

I get to step 14 where when I power it off by unplugging the Apple TV, plug it back in to turn it on without unplugging the USB hub as instructed but it just decides it's done with Linux and boots back into the original OS X install on the hard drive as if nothing has happened. No matter how many times I try this I get the same thing and I'm left with a dead flash drive each time so I need to reinstall the Crystalbuntu file each time this happens for it to work again right up till step 14 where it all goes wrong.

Is there perhaps some commands I'm missing or something? I followed the steps exactly even using some other methods of extracting the .gz file and trying each extraction method with the same result each time.

In a few hours when I get a new flash drive install ready I'll write down the [FAIL] error that I get on what is suppose to be the installation part.

---

