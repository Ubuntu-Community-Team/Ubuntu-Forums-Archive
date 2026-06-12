---
title: "Parallel kernel in the AUR"
date: 2009-01-27
forum: Arch and derivatives
---

### Post by crimesaucer on 2009-01-27
I made this AUR package using the ABS kernel26 files.


I modified the name from "-ARCH" to "-ARCHparallel" in everything including the official -ARCH patch.


I also used the "make menuconfig" command so you can customize for your hardware specs.


kernel26parallel: [http://aur.archlinux.org/packages.php?ID=23467](http://aur.archlinux.org/packages.php?ID=23467)

---

### Post by smartboyathome on 2009-01-27
I may try this later to see if I can get gobohide to work with it. :)

---

### Post by crimesaucer on 2009-01-27
> **smartboyathome said:**
> I may try this later to see if I can get gobohide to work with it. :)

Just substitute the "-ARCHparallel" _patchset name with the "gobohide.patch".... and add the patch to the same "patch -Np1 -i" line.


And change all of the names to something like "-Gobo" and "26Gobo" in all of the other files as well.... don't forget the Local Version of the .config to =("-Gobo").


That is what I do with the -mm patch and have done with the -zen sources patch for the last 5 months. (I stopped using -zen for personal reasons). EDITED to keep this technical.

---

### Post by crimesaucer on 2009-01-28
Anybody else try this yet?

---

### Post by COLiNx86 on 2009-01-28
Sorry, I'm a noob, but What is a parallel kernel and what benefits would I get from using one?

---

### Post by crimesaucer on 2009-01-28
> **COLiNx86 said:**
> Sorry, I'm a noob, but What is a parallel kernel and what benefits would I get from using one?

A parallel kernel is a kernel that can be built and installed alongside your other kernel(s).

pictures:

[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-27-11.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-27-11.png)
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-28-7.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-28-7.png)
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-29-6.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-29-6.png)
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-30-1.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-30-1.png)


This way you can build different kernels with different settings and have a choice in your Grub menu to login to different kernels..... all of this without overwriting anything having to do with your default kernel.

---

### Post by smartboyathome on 2009-01-28
Well, this sucks. I don't know which did it, but I installed then uninstalled the parallel kernel (build failed but it still built the package) then updated the kernel to 2.6.28.2 (because I noticed it was available). Now I don't got a livecd which can read EXT4 and it won't boot (bad executable format). >.<

---

### Post by COLiNx86 on 2009-01-28
> **crimesaucer said:**
> A parallel kernel is a kernel that can be built and installed alongside your other kernel(s).

pictures:

[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-27-11.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-27-11.png)
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-28-7.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-28-7.png)
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-29-6.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-29-6.png)
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-30-1.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-30-1.png)


This way you can build different kernels with different settings and have a choice in your Grub menu to login to different kernels..... all of this without overwriting anything having to do with your default kernel.
Oh ok, that makes since. I'll try this then as soon as I get some time.

---

### Post by crimesaucer on 2009-01-28
> **smartboyathome said:**
> Well, this sucks. I don't know which did it, but I installed then uninstalled the parallel kernel (build failed but it still built the package) then updated the kernel to 2.6.28.2 (because I noticed it was available). Now I don't got a livecd which can read EXT4 and it won't boot (bad executable format). >.<

That's lame. I doubt it was my package (I hope not)..... most likely something to do with how you went about installing ext4..... 


When you say the build failed, what do you mean. Can you give me the errors message or better details? 


And how did you customize your kernel in the "make menuconfig"..... 


Also, did you try that gobo-patch like you had said you were going to try.... and if you patched with the gobo-patch..... did you patch it over the vanilla kernel and the correct version (not on top of the -ARCHparallel patch), and did you edit the rest of the files correctly....


..... and when the build failed, what did the error message say and then how/why did you install it? Or was there no build error and only a failed boot up?


And when you uninstalled it then this particular package should of only uninstalled the "-Archparallel" and "26parallel" files/directories with out touching the -ARCH files..... leaving behind your perfectly working -ARCH kernel26...... without any different files being changed..... that's the way it's been for me for the last 5 months of various mistakes when trying too many new things while optimizing..... 


I also don't have any idea about the ext4 issue..... I haven't tried using it yet because it's so new and all I keep hearing about in the forums are the horror stories of people reinstalling and the complicated instructions that are needed to switch from ext3 to ext4..... I figured I would wait until a while until it was the default file system rather that the newest file system. (or until they release the new CD so I can just format it as ext4 during the install)

---

### Post by smartboyathome on 2009-01-28
> **crimesaucer said:**
> That's lame. I doubt it was my package (I hope not)..... most likely something to do with how you went about installing ext4.....

It is not EXT4, I have had that on my comp for a week or so and no problems.


> **crimesaucer said:**
> When you say the build failed, what do you mean. Can you give me the errors message or better details?

It failed because the gobohide patch gave errors (it wasn't up to date with the kernel).

> **crimesaucer said:**
> And how did you customize your kernel in the "make menuconfig".....

I used make gconfig, and I didn't customize it. I left it as default with the exception of adding the option for gobohide in the filesystem section.


> **crimesaucer said:**
> Also, did you try that gobo-patch like you had said you were going to try.... and if you patched with the gobo-patch..... did you patch it over the vanilla kernel and the correct version (not on top of the -ARCHparallel patch), and did you edit the rest of the files correctly....

I did do it over the vanilla version. Like I said, it was a compatibility error (something must have changed between 2.6.28 and 2.6.28.2 to break it).


> **crimesaucer said:**
> ..... and when the build failed, what did the error message say and then how/why did you install it? Or was there no build error and only a failed boot up?

It said it couldn't do all the patches (saved the reject). Then it continued building but I knew it was broken.


> **crimesaucer said:**
> And when you uninstalled it then this particular package should of only uninstalled the "-Archparallel" and "26parallel" files/directories with out touching the -ARCH files..... leaving behind your perfectly working -ARCH kernel26...... without any different files being changed..... that's the way it's been for me for the last 5 months of various mistakes when trying too many new things while optimizing.....

I uninstalled it, but I think it overwrote the /lib/firmware section.

> **crimesaucer said:**
> I also don't have any idea about the ext4 issue..... I haven't tried using it yet because it's so new and all I keep hearing about in the forums are the horror stories of people reinstalling and the complicated instructions that are needed to switch from ext3 to ext4..... I figured I would wait until a while until it was the default file system rather that the newest file system. (or until they release the new CD so I can just format it as ext4 during the install)

It was working fine (it is considered stable), it just needs more support from the livecds. :)

---

### Post by crimesaucer on 2009-01-28
> **smartboyathome said:**
> It failed because the gobohide patch gave errors (it wasn't up to date with the kernel).

> **smartboyathome said:**
> I did do it over the vanilla version. Like I said, it was a compatibility error (something must have changed between 2.6.28 and 2.6.28.2 to break it).



So it was the gobo-patch that had errors compiling due to kernel version, and not my -ARCHparallel patch..... For me, this AUR PKGBUILD works perfectly with the "-ARCHparallel patch"..... and if I were to use the "-mm1 rc2 patch", or the "-zen" patch, I would edit the kernel version that they are written for. (which is upsetting because the -mm patches seem to only be made for the rc kernels now: [http://www.kernel.org/pub/linux/kernel/people/akpm/patches/2.6/](http://www.kernel.org/pub/linux/kernel/people/akpm/patches/2.6/) ) 



> **smartboyathome said:**
> I used make gconfig, and I didn't customize it. I left it as default with the exception of adding the option for gobohide in the filesystem section.



The config/config.x86_64 files are the exact default config files for kernel26 "2.6.28-ARCH" (version 2.6.28.2-1)..... with only one change to the Local Version name = ("-ARCHparallel") instead of = ("-ARCH")..... I'm not sure about the patch you're using..... but this part in the menuconfig can get things messed up if you don't configure it correctly:

```

CONFIG_LOCALVERSION="-ARCHparallel"
CONFIG_LOCALVERSION_AUTO=y

``` 

And at the end of the build you need to make sure everything depmods correctly into: /lib/modules/2.6.28-"patchname"


and also make sure it's the same way for /usr/src/linux-2.6.28-"patchname"



> **smartboyathome said:**
> It said it couldn't do all the patches (saved the reject). Then it continued building but I knew it was broken.



This will cause problems..... I once built a -zen patch on a 2.6.27.5-1 vanilla sources when it was meant for 2.6.27 version..... it built and booted but still ran with bugs..... but even using my parallel install method it was easily removable without damage.



> **smartboyathome said:**
> I uninstalled it, but I think it overwrote the /lib/firmware section.



/lib/firmware shouldn't matter..... it's the exact same firmware that is included with every Linux kernel. If you don't use that hardware it wouldn't even matter.... and if you did use the firmware for "korg" or your PDA..... then it would be the exact same firmware blobs included in the new kernel..... even if you patched it with gobo (I think).



> **smartboyathome said:**
> It is not EXT4, I have had that on my comp for a week or so and no problems.

> **smartboyathome said:**
> It was working fine (it is considered stable), it just needs more support from the livecds. :)



I still don't know about it..... I've seen a bunch of "I had to reinstall" posts since ext4 came out.


My last thing to say is that you can post all of your files to show me how you have changed it to patch with your gobo patch.... and maybe I can build it to see what might have happened....

---

### Post by smartboyathome on 2009-01-28
I am going to try burning system rescue cd on my desktop and using it on my laptop to recover.

---

### Post by smartboyathome on 2009-01-31
Ok, double post, I know, but I wanted to let you all know that I am back on arch. I got bit by the same problem [this user]("http://bbs.archlinux.org/viewtopic.php?id=63565") got bit by.

---

### Post by crimesaucer on 2009-01-31
> **smartboyathome said:**
> Ok, double post, I know, but I wanted to let you all know that I am back on arch. I got bit by the same problem [this user]("http://bbs.archlinux.org/viewtopic.php?id=63565") got bit by.

No sweat. I was reading up on the conversion of ext3 to ext4 partitions and I think I'll just wait until they release the new CD.....

---

