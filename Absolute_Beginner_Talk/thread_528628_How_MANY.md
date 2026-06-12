---
title: "How MANY?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-08-18
Can someone tell me how many files load during the boot?
I just installed 7.04 from the alternate cd so I could solve my ATI graphics problem.
I have been waiting for about 30 minutes for the gui to load, but no such luck yet. Why is this taking so long? Is it a common boot?


BTW. I am booting from recovery mode because I thought it stalled during regular boot, I am just watching all the files scroll down the screen. Like MATRIX  :popcorn:

---

### Post by nitro_n2o on 2007-08-18
AFAIK, there aren't many files to be loaded... there are some services and some essential boot files, plus the kernel. You shouldn't be seeing matrices of lines filling up the screen while booting..
did you checksum the cd u downloaded? 
if your pc is 32bit usual computer.. then make sure that the alternate cd isn't the 64bit edition

---

### Post by nitro_n2o on 2007-08-18
From where did u get you avatar btw :) it looks  cool

---

### Post by poscaman on 2007-08-18
r u sure there is no hd issue?

---

### Post by pgar23 on 2007-08-18
>  		From where did u get you avatar btw :smile: it looks  cool
I got it from googling "ubuntu logo"

and its not really matrices, I was joking about the movie the matrix and...nvm (lame joke)

but newayz i will download alternate cd from ubuntu site. jus to be double sure.
thanks.

---

### Post by nitro_n2o on 2007-08-18
> **poscaman said:**
> r u sure there is no hd issue?
yeah a hard  drive issue might cause this.. u r right :) 

so can u get anything from the output and post it here?

---

### Post by nitro_n2o on 2007-08-18
> **pgar23 said:**
> 
but newayz i will download alternate cd from ubuntu site. jus to be double sure.
thanks.
Still, you should checksum... :) it's a good habit to checksum everything

---

### Post by pgar23 on 2007-08-18
ps. i got the alternate cd from [http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)
shouldnt that be reliable? I didnt checksum because I thought since it was mainstream site that it would be correct.

---

### Post by pgar23 on 2007-08-18
i might have a hd issue. I installed hoary hedgehog couple days ago. and WINXP no longer working. I was going to resolve that issue after installing Ubuntu because I am so excited to use it. but to no avail yet. how do I check if I am using the right alternate cd. and also how do I check If I have a hd problem as I have no OS on the comp I am trying to install Ubuntu.

---

### Post by nitro_n2o on 2007-08-18
> **pgar23 said:**
> ps. i got the alternate cd from [http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)
shouldnt that be reliable? I didnt checksum because I thought since it was mainstream site that it would be correct.
all right.. that sounds cool :) but i didn't say that your problem is because of a fake CD :) it seems that your download is good.... 
1- r u sure that you have downloaded the right version to your system? 
2- can u tell if there is a hard drive issue? 
3- when u installed your system, did you use the full disk (the maximum continuous space option)?

---

### Post by nitro_n2o on 2007-08-18
> **pgar23 said:**
> i might have a hd issue. I installed hoary hedgehog couple days ago. and WINXP no longer working. I was going to resolve that issue after installing Ubuntu because I am so excited to use it. but to no avail yet. how do I check if I am using the right alternate cd. and also how do I check If I have a hd problem as I have no OS on the comp I am trying to install Ubuntu.

What do u mean by you don't have OS on the computer? 
if you downloaded the PC(intelx86) and you have some intel 32bit processor the cd is fine... 
you may want to boot from the liveCD and check your disk

---

### Post by pgar23 on 2007-08-18
1. Once again how do I check if hd issue? (no OS, if there is method without using OS i will use)
2. I just double check to make sure i use correct version and I did.
I am using Dell Optiplex GX60 and I downloaded i386.ISO version
3. when I installed, I have XP so I dual boot with use continuos free space(guided partitioning)

---

### Post by nitro_n2o on 2007-08-18
here is a  topic on how to the check the disk [http://ubuntuforums.org/showthread.php?t=426356](http://ubuntuforums.org/showthread.php?t=426356) i'd use fsck to do it, but there are other options 
I'm not sure why... but using that guided install never worked for my system.. i had to partition manually!!! 
Save ur self some steps and get the liveCD.. ur ATI will eventually work when u install using the LiveCD.. it just needs a little bit of configurations

---

### Post by pgar23 on 2007-08-18
when i did the sudo tune2fs -c 1 /dev/sda2 (mine is on sda2)
it says setting maximal mount count to 1

is that what it should do?

---

### Post by mikewhatever on 2007-08-18
The recovery mode in Ubuntu has no gui. All you get is the black screen with command prompt. This is handy for fixing problems or installing video drivers. If you want gui, boot into the regular mode.

---

### Post by pgar23 on 2007-08-18
> **mikewhatever said:**
> The recovery mode in Ubuntu has no gui. All you get is the black screen with command prompt. This is handy for fixing problems or installing video drivers. If you want gui, boot into the regular mode.

I cant boot regularly for some reason. it keeps listing tons of files down the screen. when I try to boot. I boot regular mode, except edited the splash out of kernel line so i could see where my problem was, but it never stalls on any line, it just keeps listing files.

---

### Post by mikewhatever on 2007-08-18
Have you tried installing an ATI graphics driver? See, installing Ubuntu with the Alt CD only solves gui problems during the installation. Once Ubuntu is on your HDD, you still have to deal with the graphics card. You can try envy to install the ATI driver in recovery mode [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
> wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb)
This will download the deb file to your home directory. Then follow --


sudo dpkg -i envy*.deb

Make sure that all the dependencies were installed by typing:

sudo apt-get install -f 

Then start envy

sudo envy -t

---

### Post by pgar23 on 2007-08-18
i would do that, but i dont have internet access on that comp yet and also Ubuntu isnt even installed properly yet. lol sorry for postin such bs, but your workin with a noob.

---

### Post by pgar23 on 2007-08-18
> See, installing Ubuntu with the Alt CD only solves gui problems during the installation. Once Ubuntu is on your HDD, you still have to deal with the graphics card.I read here [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
it says to install ubunu using alt cd then boot, why would he say to boot from Alt Cd if it doesnt benefit my situaion with the graphics card? (no accusations implied)
I am having a problem booting even from the alt cd and live cd. I have tried both and no success thus far. The only way I was able to install ubuntu so far was from the hoary hedgehog cd I have and I couldnt install certain drivers on that so I could get my wireless internet working. That is why I opted to download Feisty Fawn and proceed from there.

---

### Post by pgar23 on 2007-08-18
is there a code that will skip the reading of my graphics card and will automatically boot so I can follow the HOWTO from here [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by mikewhatever on 2007-08-19
> **pgar23 said:**
> i would do that, but i dont have internet access on that comp yet and also Ubuntu isnt even installed properly yet. lol sorry for postin such bs, but your workin with a noob.

What do you mean it is not installed yet? Here is a quote from your initial post in the thread:
> I just installed 7.04 from the alternate cd so I could solve my ATI graphics problem.

---

