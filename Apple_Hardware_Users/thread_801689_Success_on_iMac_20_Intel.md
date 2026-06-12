---
title: "Success on iMac 20 Intel"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by i.t.guru on 2008-05-20
I have been using Ubuntu for a couple of years now. I have had my iMac 20 for almost a year and a half and use it frequently for work, which is web design and creating brochures and other promotional material for a non profit organization.
Needless to say, I have been very hesitant to install Linux of any kind on my iMac. Well, today I made that step after a short period of researching the rumors of heartache and despair. I downloaded the EFI multi boot app for Mac and install it and then used Bootcamp to delete my WindowsXP partition and then created a fresh one.
I booted to the install disk, which was easy since the disk showed up as a Windows install disk. Just hold down the alt/option key at boot time and select the cd and hit enter or click the arrow below it.
One thing to note is that some of the statements about these procedures may be off, unclear or just plain not true. The hardest part is the partitioning. There are some rumors about Apples loader complaining but that is not my case.

Once booted fully to the cd, open the partition manager from
System > Administration and delete the Fat32 partition you made with bootcamp, select the free space there which for me was around 80 GB and create your swap partition at around 1 or 2 GB, whichever you prefer

Remember to leave about the same amount of empty space before your partition as bootcamp does, which is about 128 MB. Mine alters during the process and changes to about 135 but it does not seem to be an issue. Now choose the remaining free space and create an ext3 partition. Once done, hit the apply button. After a short period, it will be complete.

Now you can start the Installer. Just do everything as usual with the exception of when the partitioner starts, choose the manual method. When the next screen appears, select the ext3 partition and assign it as / (root). It will automatically select the swap space during the install so just continue to the next step.

Once you get to the last screen, which confirms what you are about to do, click the advanced button at the bottom left corner of the Installer Window. Once it is open, click on the drop down menu for the boot loader installation placement and select the partition you used for / (root), which is either /hda3 or /hda4 but just make sure that you remember which is which. This will install the GRUB boot loader to the root partition, which will be automatically recognized by that handy dandy EFI boot menu you installed.

Click next and sit back while things take place. You will get the usual prompt to reboot, click reboot and then the cd will be unmounted and eject. Now hit enter to reboot and pay attention to you boot menu now or else you will end up back in Mac OS X, LOL.

From there on out, everything has been the usual so far. The only uncomfortable part was after installing the ATI fglrx driver, the boot slowed right in the middle and did a short creep for about 15 to 20 seconds. Also, my 3d screen savers start with a small distorted glitchy look but then kick in.

That is all for now. I am on Ubuntustudio8.04 right now making this post. I attached a snapshot below.
Nice... :)

---

### Post by Kimmik on 2008-05-21
Hi, I too have a iMac 20" (aluminum intel).
Everything works fine too, except the sound.

Does sound work on your machine?

I already tried the patches that people posted on this forum but it still doesn't work.

**Can anybody help?**

---

### Post by sayamindu on 2008-05-21
Does wireless work ? If so, how ?

---

### Post by cyberdork33 on 2008-05-21
> **sayamindu said:**
> Does wireless work ? If so, how ?
you have to use ndiswrapper. The method is the same as for the MacbookPro4,1.

[https://wiki.ubuntu.com/MacBookPro/Penryn#head-e5409d2a7a72b4cec1c51303bb2247a83a5659dc](https://wiki.ubuntu.com/MacBookPro/Penryn#head-e5409d2a7a72b4cec1c51303bb2247a83a5659dc)

---

### Post by cambron on 2008-05-21
i have the 20" imac intel core 2.

does it have a 64-bit processor ? i wanna get 64-bit ubuntu.

i keep coming accross some troubles with the keyboard that came with the imac, the keys are switched like m,j,k,l are the numberic keys. I just run accross all the top F1, F2, F3 and after a minute it starts to work fine.

i used Envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) to install the ATI drivers. I only use the imac for browser, openoffice, and running KVM virtual machine or virtualbox, it works fine for me.

camera works on the imac by following instructions from other posts.

sound still having problems after following steps from another post.

not sure about wireless

i had another question but forgot already

---

### Post by cyberdork33 on 2008-05-21
> **cambron said:**
> i have the 20" imac intel core 2.

does it have a 64-bit processor ? i wanna get 64-bit ubuntu.
You can use either 32 or 64 bit.

> **cambron said:**
>  i keep coming accross some troubles with the keyboard that came with the imac, the keys are switched like m,j,k,l are the numberic keys. I just run accross all the top F1, F2, F3 and after a minute it starts to work fine.Hitting f6 twice should switch the behavior. This is a bug in the kernel and is well known. Hopefully will be fixed soon.

---

