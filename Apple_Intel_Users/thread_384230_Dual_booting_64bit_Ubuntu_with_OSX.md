---
title: "Dual booting 64bit Ubuntu with OSX"
date: 2007-03-14
forum: Apple Intel Users
---

### Post by H264 on 2007-03-14
Hi, I recently installed the 32 bit version on my AMD 2400 box I put together. I was very impressed with the instulation, esp. because it was my first Linux attempt, very nice first impression :)

I was impressed enough to try to install on my iMac I recently got. I tried following [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) tutorial, but it looks like (in step 6 in the tutorial) that the debian package is a 32 bit application... because when I downloaded it, the install button was not there? Hmm. I need ideas, I'v been up till.. well, it's ~5:00 right now and I can search anymore.

Don't try to sell me on the 32 bit version either, I would like to (someday) develop for it should I ever migrate from Java to C/C++/Objective-C/something else (programming is fun :)

Good night ;)

---

### Post by viciouslime on 2007-03-14
You could try feisty, it's not supposed to be for production machines but i have been using it for 2 months without any problems and it hits beta very soon anyway. The mac support in feisty is waaaaaaaaaaaaay better than that in edgy and you can just install it like you would on any laptop, except that you need refit.

---

### Post by cyberdork33 on 2007-03-14
Could go get the sources ([http://ftp.debian.org/debian/pool/main/r/refit/](http://ftp.debian.org/debian/pool/main/r/refit/)) and port to 64-bit linux... although I think that would be a lot of trouble...

The issue is that, currently, gparted screws up the MBR partition table, so you have to sync it before installing the bootloader. If you install 7.04, then it will not screw up the partition tables during install, so you can get the tables synced after you partition, then start the installer...

---

### Post by H264 on 2007-03-14
meh, that's not what I want to hear... so basically my choices are to (attempt) to port the refit package, or to install 7.04?

---

### Post by cyberdork33 on 2007-03-14
I really don't know how else to do it...

Just FYI, you will be limited in choice of application using the 64-bit edition over the 32-bit... I wouldn't really recommend using a 64-bit OS unless you are building a server. 

All this Linux on Intel Macs business is all still very new, there are very limited options to getting everything working. Maybe there is someone out there that knows the answers, but that is not me... Good luck.

Throwing out an idea... Maybe you can boot a 32-bit live cd, do your partitions, and image a 64-bit install onto the partition. That really doesn't sound any easier to me though.

---

### Post by H264 on 2007-03-14
I'll try 7.04 first.
I don't really see that in limiting my choices... I could not install and what I could do would not be hampered at all... but I like challenges, so 64 bit it is :)

What is special about Mac hardware? is it the EFI booting sequence? Other than that I don't think they are too much different (I'm probably wrong)

---

### Post by cyberdork33 on 2007-03-14
there are not drivers for a few bits and pieces of mac hardware... thats all... the EFI stuff is a bit of a pain at times, but rEFIt makes that a bit easier.

Good Luck with 7.04

---

### Post by H264 on 2007-03-14
ok, well I will download it tomorrow. Will let everyone know how it goes.

---

### Post by H264 on 2007-03-16
well, it did getpast the actual install with out a problem. Now that rEFIt (the boot manager for OSX) is properly installed and 7.04 installed with no complaints, it still does not work (suprised? :P )

when rEFIt loads and I can select OSX or Linux or a boot CD if in the drive, I get the folowing error when I select Linux:
"No bootable device -- insert boot disk and press any key"

Is something not quite lined up with rEFIt and 7.04?

---

### Post by cyberdork33 on 2007-03-16
I guess I really can't figure anymore unless you give more info about the install. Did you tell it to install grub to the linux partition rather than the MBR?

---

### Post by H264 on 2007-03-16
How do I do that? All I know is that Ubuntu installed on the right partition :P

---

### Post by H264 on 2007-03-16
Nevermind, I figured out how to install GRUB on another partition. Still does not help, I get the same error when from the rEFIt menu select Linux to boot from....

Wait a sec...

WOOT!!!!!!!!!!!!!!!!!!

sorry, I selected the partition icon below the OSX and Linux ones as I was typing this. It then asked me if I wanted to update the MBR (y/n) I presses 'y' and it said it updated alright. I then loaded OSX to make sure it worked, then restarted only selected Linux, and it WORKED! Sweet.

sounds like 7.04 is the only one that will work with the 64bit version on a mac.

For anyone else that wants to do it, I installed GRUB on to the Linux partition, not the MBR. For me it installed Linux on partition#3 and the swap on partition#4, so before you click "install" on the last step, click "advanced" and for me was (hd0,2) (0 points to partition#1, 1 points to partition #2) if left as (hd0) it will install onto the MBR. Maybe someone else can experiment with the same steps, only installing GRUB onto the MBR or different partitions...

I'm happy now :)
Thanks

---

### Post by the.dark.lord on 2007-03-22
> **H264 said:**
> How do I do that? All I know is that Ubuntu installed on the right partition :P

And how did you partition it?

---

### Post by cyberdork33 on 2007-03-22
> **H264 said:**
> For anyone else that wants to do it, I installed GRUB on to the Linux partition, not the MBR. For me it installed Linux on partition#3 and the swap on partition#4, so before you click "install" on the last step, click "advanced" and for me was (hd0,2) (0 points to partition#1, 1 points to partition #2) if left as (hd0) it will install onto the MBR. 

As far as I know that is the best way to do it when using rEFIt. you can't install things to the MBR because, well, EFI doesn't read that. This is what I did even for Edgy.

---

### Post by H264 on 2007-03-23
Ah, ok :-} I just never (untill a few days before I tried to get it on my iMac) installed Linux before. I did not see any guides forinstalling 64bit, so I posted the question here :) And I'm too stubborn to give up, unless there is Absolutly no other way...

Thanks for being around :)

---

### Post by cyberdork33 on 2007-03-23
Glad you got it working...

@the.dark.lord
I responded to your other thread...

---

