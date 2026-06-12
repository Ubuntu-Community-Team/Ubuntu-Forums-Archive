---
title: "Ubuntu Installation: Blank Screen"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by csquisher on 2007-07-11
I've tried installing both Ubuntu and Xubuntu and the same thing happens with both. After selecting that i want to "Run and Install" on the main screen, and after the first loading bar finishes (something about kernels) the screen goes blank and nothing seems to be happening (CD and computer inactive). I've tried waiting for around half an hour but nothing happens, and I'm looking for any help you may be able to offer me!
Thanks.

---

### Post by taurus on 2007-07-11
What is the spec of your machine?  Sounds like the installer (LiveCD) is having a little problem with your graphic card.  Why don't you try using the alternate CD to install it on your machine instead?

---

### Post by Skidpad on 2007-07-11
edit: If you are attempting to try out Ubuntu, see my answer in the other thread, if not, try what Taurus has suggested and install straight away via the Alternate method.

---

### Post by kcsnare on 2007-08-08
I am having exactly the same problem (using an nvidia 8800GTX) and I suspect it's a video card driver problem, but am completely new to linux (first install attempt) and don't know where to go from here.  I downloaded the 64 bit version, and don't have an alternate cd or installation method as described.

What should my next step be?

---

### Post by kcsnare on 2007-08-08
> **Skidpad said:**
> edit: If you are attempting to try out Ubuntu, see my answer in the other thread, if not, try what Taurus has suggested and install straight away via the Alternate method.

Skid, Which other post are you referring to?  I'm trying to search your posts, but there's just so many...

---

### Post by Skidpad on 2007-08-09
> **kcsnare said:**
> I am having exactly the same problem (using an nvidia 8800GTX) and I suspect it's a video card driver problem, but am completely new to linux (first install attempt) and don't know where to go from here.  I downloaded the 64 bit version, and don't have an alternate cd or installation method as described.

What should my next step be?

The Alternate Desktop CD is on the same download page as the other versions - look down below the green "Start Download" arrow, and check the box.  You will get the text-based installer that way.

What are your system specs?  I've also read about people having trouble with the 64bit version, have you tried the 32bit?

---

### Post by splintercellguy on 2007-08-09
Did you try booting in Safe Graphics mode?

---

### Post by WebSiteGuru on 2007-08-09
> **splintercellguy said:**
> Did you try booting in Safe Graphics mode?

That cause the same problem too.  I  noticed that when I was trying to install both ubuntu and xubuntu on a second system ( HP that 's using RADEON X300).

---

### Post by kcsnare on 2007-08-09
Yes, safe graphics had the same result.  My system is currently in multiple pieces, but I hope to have it back together this afternoon.

Specs:

Intel Q6600
EVGA 680i mobo
4 gigs pc2 800
160 gig HD
evga Geforce 8800 GTX
creative x-fi elite

I'm going to try again when the system is ready, but I suspect I will be forced to do the text based install.  Can someone point me to a tutorial to this?  I will also have to repartition my drive (gonna dual boot) and suspect that text-based repartitioning is not easy.  Also, assuming the text based install is successful, I will need instructions on how to establish the graphical part afterwards (that's what we call a technical term right there...)

Anyway, in response skid, no I have not tried the 32 bit version.  I may do that, but as a last resort.  I am hoping to use this as an alternative to vista (the 64-bit version) and 32 bit will not allow me to utilize my full memory potential, so 64 bit seems the obvious choice.  Time will tell.

---

### Post by kcsnare on 2007-08-10
One of my friends recommended trying Gutsy Gibbon.  If my problem is driver related, would this help since 7.10 would have a newer driver library on the install package?

---

### Post by Skidpad on 2007-08-11
> **kcsnare said:**
> One of my friends recommended trying Gutsy Gibbon.  If my problem is driver related, would this help since 7.10 would have a newer driver library on the install package?
It might, but I don't know much about Gutsy.  Anyway, if its available as a LiveCd, you could try that and see.  

I think the real root of your problem is your computer - specs are insufficient!  You need more power!  (haha, that's just me and my jealousy talking.  Nice system!)

Here's the Installation page: [Installation Methods]("https://help.ubuntu.com/community/Installation")

Let us know how it goes.

---

### Post by caecus314 on 2007-08-11
I too have an evga Geforce 8800GTX, and I'm experiencing the same problem.  I was able to install 64-bit 7.04 using the Alternate Install CD.  It works fine in X using the default driver, but any time it would regularly show the bootsplash screen with the logo and the progress bar (startup and shutdown), my monitor gets no signal.

Also, I just tried installing the Nvidia binary drivers by means of [this]("http://ubuntuforums.org/showthread.php?t=432056&highlight=nvidia") post, but now when my system starts up, presumably after it has displayed the bootsplash screen, the monitor stays off.  I get no KDM prompt, and ctrl+alt+F1 does nothing.

I'm going to investigate this some more...

---

### Post by LurkerLito on 2007-08-13
> **caecus314 said:**
> I too have an evga Geforce 8800GTX, and I'm experiencing the same problem.  I was able to install 64-bit 7.04 using the Alternate Install CD.  It works fine in X using the default driver, but any time it would regularly show the bootsplash screen with the logo and the progress bar (startup and shutdown), my monitor gets no signal.

Also, I just tried installing the Nvidia binary drivers by means of [this]("http://ubuntuforums.org/showthread.php?t=432056&highlight=nvidia") post, but now when my system starts up, presumably after it has displayed the bootsplash screen, the monitor stays off.  I get no KDM prompt, and ctrl+alt+F1 does nothing.

I'm going to investigate this some more...

Doh this is the exact problem I am having. I installed Feisty fine with the regular 64bit install disc. To get around any graphics problems that I had with both my older computers 6800GT card and my new 8800gtx card, I had to press F4? and select a resolution of 1280x1024x32 from the menu and I could get the installer to work fine. Everything installed fine but when it rebooted I only got a blank screen. It seems as if when the first unbuntu loading progress screen comes up my monitor goes into powersave mode so no signal is coming to it. ctrl + alt + F1 or any ctrl + alt + F# press doesn't do anything. 

If I go into recovery mode I can access the system and have run dpk-reconfigure xserver-org and startx and the screen comes up and I can access the system through the xwindows system, but still all of this only works in recovery mode. Has anyone figured out what is going on? I am still working on it but so far I don't really have any ideas as to where else to look. I am pretty sure it might be related to the 8800gtx but I don't think it has to do with the xserver settings at all. It might have more to do with that unbuntu splash screen that is suppose to pop up on boot to show loading progress.

---

### Post by LurkerLito on 2007-08-14
Ok I solved my problem. It seems usplash was the cause. So I removed it to fix the system.

To test if this is your problem, boot into recovery mode. You should be able to get to a command prompt. Then do the following:

cd /boot/grub
nano menu.lst

now find the following section:
```

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=90cc752b-e5a9-46e8-9026-1b10ce4bb265 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

and edit the kernel line to read:
```

kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=90cc752b-e5a9-46e8-9026-1b10ce4bb265 ro

```
save the file and reboot.

Now if that works I recommend going editing the following line in your grub menu.lst file:
```
# defoptions=quiet splash
```
to read:
```
# defoptions=quiet
```

and that should take care of the problem. You can also choose to remove the usplash program and associated files if you want since you won't be using them.

---

### Post by Eluzion on 2007-08-14
LurkerLito - I had the same exact problem with my 8800GTS 640mb and I just followed your steps now everything works. ;) Just installed the latest nvidia drivers off nvidia.com as well. Thanks

---

