---
title: "How to re-install GRUB on a Macbook Pro?"
date: 2012-03-07
forum: Apple Hardware Users
---

### Post by skullmunky on 2012-03-07
I have a Macbook Pro (6,2) set up to triple boot OSX, Ubuntu, and Windows XP.  I use the windows partition rarely, but naturally I eventually got a rootkit trojan on it and the repair utility had to wipe the MBR and so GRUB doesn't load anymore. 

the rEfit menu still shows all 3 partitions, but booting to linux just hangs with a black screen and blinking cursor.  

My layout is pretty typical:

/dev/sda1: 100MB EFI
/dev/sda2: OSX
/dev/sda3: Ubuntu
/dev/sda4: Windows
/dev/sda5: swap

I originally installed GRUB on /dev/sda3 when I installed Ubuntu. 

I'm now trying to reinstall GRUB but can't quite seem to get it to work.  I can boot into a live CD (ubuntu or system rescue CD), mount my linux partition, start the GRUB shell, and go through what I think are the right commands, but all I end up with is an additional Linux option in rEfit that also doesn't boot.  

Most GRUB tutorials also start with 
```

find /boot/grub/stage1

```

which fails for me; I don't have a stage1.  Does this have to do with the version of GRUB?  

I know the boot process on Apple hardware is a little trickier than on normal PC hardware so does anyone have a walkthrough on how to do this specifically for the mac? 

thanks!

---

### Post by skullmunky on 2012-03-19
still struggling with this one ... 

I booted to the 11.10 live cd and did this:

```

sudo mkdir /mnt/sda3
sudo mount /dev/sda3 /mnt/sda3
sudo grub-install --force --root-directory=/mnt/sda3 /dev/sda3

```

Most instructions say to install to /dev/sda, the MBR, NOT to a partition; but since the installation instructions on Mac always say to install GRUB to the Ubuntu partition, I did the same here.

At boot, I get two Linux options in the Refit menu.  Both get to GRUB Stage2, but then drop me into the grub> shell.  The version on both is 0.97.  

Soon I suppose I'll give up, back up my partition, wipe it and reinstall, but I'm sure this is a trivial thing to fix :/

---

### Post by acc61287 on 2012-03-19
Install your grub again  Try this link:
[https://www.facebook.com/note.php?no...80733381981929](https://www.facebook.com/note.php?no...80733381981929)

---

### Post by skullmunky on 2012-03-19
I tried it again.  And also tried installing GRUB2 to the MBR, just for kicks.  Now my two options in refit are worse.

Boot Linux from HD just gives me a black screen with blinking cursor (i think that's expected, actually).

Boot Linux from Partition 3 gives me a penguin icon for a little while, then the black screen with the blinking cursor.

---

### Post by skullmunky on 2012-03-24
I re-installed Ubuntu, and still can't boot it ... I still just get a black screen with a blinking cursor before GRUB loads :(

---

### Post by skullmunky on 2012-03-25
After re-installing ubuntu, I still couldn't boot.  Using the Partition sync tool in Refit, (aka gptsync), I got this error:

```

Analysis inconclusive, will not touch this disk.

```

From here I figured the best thing would be to somehow rebuild a fresh MBR.  Turns out that fdisk was able to do that for me:

```

fdisk -u /dev/sda

```

I was quite pleased to discover that after all this hacking and slashing on this drive I haven't lost any data, including a fresh install of a new Kubuntu version.  :popcorn:

---

