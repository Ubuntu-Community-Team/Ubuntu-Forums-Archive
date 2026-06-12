---
title: "tried Linspire-aaahhh!!!"
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by jdublu on 2005-09-19
i'm setting up a dual boot hard drive. i have xp home on one partition and made another partition for linspire, that I PAID for, but it will not do a full install. it loads some files and programs then stops and ejects the cd. i used partition magic to make the partitions. since linspire won't work, i'm presently downloading Ubuntu. will it install ok on another partition? please let me know.
thanks, Jim

---

### Post by TristanMike on 2005-09-19
Welcome to Ubuntu,

Yes, Ubuntu should install on your partition, be it the one you had desginated for Linspire, or a new one. Just follow the installation procedure. If you are working with a fresh partition, it is recommended that you auto partition your free space and off you should go. Everything should run smoothly.

Hope this helps.

---

### Post by jdublu on 2005-09-19
how do u mean autopartition. when i set up the partitions in partition magic i think that formated the partition for u? if so, will Linspire or ubuntu install on the formatted partition or how do i make changes to it so one of those OS's will install?

---

### Post by jdublu on 2005-09-19
AND!! after it finshed downloading I can't find it!!! while downloading it showed it going into temp files but i can't find it anywhere. do u know where i can find it?

---

### Post by mlomker on 2005-09-19
[QUOTE=jdublu]i'm setting up a dual boot hard drive. i have xp home on one partition and made another partition for linspire, that I PAID for,[/QUOTE]

If you paid and downloaded it online then request a refund right away.  You only get 14 days...I got burned by that one because I paid for Linspire before my PC arrived.

Linux doesn't pay any attention to drive letters and Windows cannot 'see' linux.  When you go to install Ubuntu it'll ask you to select a partition to put it on.  You'll probably have to be able to recognize which one it is by the size.

---

### Post by Kapre on 2005-09-19
[QUOTE=jdublu]AND!! after it finshed downloading I can't find it!!! while downloading it showed it going into temp files but i can't find it anywhere. do u know where i can find it?[/QUOTE]

Jdublu - Did you downloaded the ISO file? Look for the file with an .iso extension and then burn it on a CD (using NERO or whatever burning software you have).

K

---

### Post by mlomker on 2005-09-19
[QUOTE=jdublu]AND!! after it finshed downloading I can't find it!!! while downloading it showed it going into temp files but i can't find it anywhere. do u know where i can find it?[/QUOTE]

If you remember the name of the file you can search from a terminal:

```

sudo updatedb
locate filename

```

---

### Post by metiosarius on 2005-09-19
I would suggest posting your problem in the Linspire forums, regardless of the stigma that Linspire receives, it's actually a great, very helpful community. Also try submitting a support ticket. (The forums a generally better places for info though) If you are really upset, try contacting **"Kendall"** by using a PM in the forums, he is the *Community Liason* and is very good about taking care of problems like these. Even if the problem results in you wanting a refund.

 [Linspire Forums Link](http://forum.linspire.com)

---

### Post by mneptok on 2005-09-19
[QUOTE=jdublu]i'm setting up a dual boot hard drive. i have xp home on one partition and made another partition for linspire, that I PAID for, but it will not do a full install. it loads some files and programs then stops and ejects the cd. i used partition magic to make the partitions. since linspire won't work, i'm presently downloading Ubuntu. will it install ok on another partition? please let me know.
thanks, Jim[/QUOTE]

Be aware that sometimes (especially with older BIOS revisions) Linux gets pissy about it's /boot directory being outside of the first ~8.5GB of disk space. This is the "1024 cylinder limit" problem.

If you find you cannot boot Linux, it may well be that /boot is outside of where the computer can use it. Adjust partitions to allow /boot to reside within the forst 1024 cylinders.

Alternatively, if your BIOS supports LBA (Logical Block Addressing) then turn this on. This will often allow Linux to use a /boot directory outside of the 1024 cylinder limit.

---

### Post by TristanMike on 2005-09-19
[QUOTE=jdublu]how do u mean autopartition. when i set up the partitions in partition magic i think that formated the partition for u? if so, will Linspire or ubuntu install on the formatted partition or how do i make changes to it so one of those OS's will install?[/QUOTE]No, i mean with the Ubuntu installer, to get a preview of what your going to be getting into, go [here for the full install](http://mrbass.org/linux/ubuntu/install/) and [here for the partitioner](http://www3.telus.net/linux4u/ubuntu.html). 

You see Linux handles the filesystem differently than Windows. Your main space will get partitioned further into a "/" and "/swap", (the / is where all other files will be kept, and the swap acts as virtual RAM) and the Ubuntu installer will do this automatically for you, decide the sizes and such, this is the method you should choose for your FREE SPACE.[QUOTE=jdublu]AND!! after it finshed downloading I can't find it!!! while downloading it showed it going into temp files but i can't find it anywhere. do u know where i can find it?[/QUOTE]We're still talking about downloading an Ubuntu iso on a Windows machine? via IE or Firefox? You say it went into temp, is it possible that when prompted for the save, you said "open with" in which case it would get saved to a temp folder, otherwise, what I do in these situations is just start re-downloading the same file, and if it goes well, you will be prompted for a save spot before you actually start the download and it should be the same place you just saved the other file.

If your questions are about Linspire, then yes, I recommend checking thier site out.

---

### Post by rajsarkar on 2005-09-20
[QUOTE=jdublu]i'm setting up a dual boot hard drive. i have xp home on one partition and made another partition for linspire, that I PAID for, but it will not do a full install. it loads some files and programs then stops and ejects the cd. i used partition magic to make the partitions. since linspire won't work, i'm presently downloading Ubuntu. will it install ok on another partition? please let me know.
thanks, Jim[/QUOTE]
 Hi Jdublu,

I would suggest you to read relevant portions of ubuntu guide at [http://ubuntuguide.org/](http://ubuntuguide.org/) 

regarding hard drive partition and dual booting with Win XP. However, Ubuntu installation process is pretty simple and self explanatory. Hopefully you won't face any problem.

- Raj

---

