---
title: "Installation question"
date: 2007-05-16
forum: Apple Intel Users
---

### Post by squeezy on 2007-05-16
Would it work at all if I installed Ubuntu on a clean Mac hard drive, and then installed OS X afterwards?

---

### Post by benanzo on 2007-05-16
yes, but it's tricky.  OS X wants to do some very peculiar things with how the disk is partitioned otherwise it will give you some errors and won't install.  It is still strongly recommended to install OS X first and let it do whatever it wants to the disk, then install Ubuntu, since it can be far more forgiving with the partitioning.

---

### Post by ronocdh on 2007-05-16
> **benanzo said:**
> yes, but it's tricky.  OS X wants to do some very peculiar things with how the disk is partitioned otherwise it will give you some errors and won't install.  It is still strongly recommended to install OS X first and let it do whatever it wants to the disk, then install Ubuntu, since it can be far more forgiving with the partitioning.
Seconded. And by installing OS X first, you'll be able to grab any necessary firmware updates for your hardware; can't do that in Ubuntu. I highly recommend you maintain a small OS X installation for this reason. You can pare down the size of it by removing unwanted packages, such as foreign languages and iLife applications.

---

### Post by squeezy on 2007-05-16
Thanks a lot for answering my question. The reason I was asking is because I'm running an Intel Mini, 1.66  model, and I have failed miserably getting Ubuntu to install with rEFIt. I have followed the Macbook Ubuntu install guide exactly and still have GRUB issues (it wont install properly).

But to make sure I'm understanding this correctly. if I did choose to install Ubuntu first, and then OS X, any fireware updates for OS X wont be able to be installed?

---

### Post by benanzo on 2007-05-16
The issue about the firmware updates only arises if you decide not to have OS X installed at all.  He was just making the point that only OS X can apply firmware updates to your machine.  The issue about GRUB not installing correctly is symptomatic of the problems we were having in the early days of installing Linux on the Mac-Intels.  Without getting too technical, the reason we don't have those problems anymore (or shouldn't) is because when Apple updated OS X to 10.4.6 they updated the EFI (low-level motherboard OS) to include support for booting operating systems requiring a BIOS (32-bit Windows and most standard Linux versions.)  It just emulates a BIOS environment so your system would install and boot without error.  It seems to me that you possibly haven't done that update?  I would recommend doing a basic OS X install and running all the updates.  Then try to install Ubuntu again.

If you still have problems we can help, otherwise you can just install Ubuntu the old fashioned way using LILO as the bootloader, not GRUB.

---

### Post by squeezy on 2007-05-16
Thanks for the quick reply! I'm up to date with software updates and am running 10.4.9.

Using LILO for the bootloader instead of GRUB is something new I've heard. Is it any easier to get Ubuntu installed using that method? I don't care what bootloader I user, whether it be GRUB, LILO, or rEFIt.

I remember the main problem during installation was trying to figure out which drive was what. All the drives are SATA (so sda and such in Ubuntu), but during installation is got nothing but hda. I don't remember how, but I got it all to work finally.

Anyway, back to the matter at hand. Is there a tutorial for using LILO? I would love to get Ubuntu running on my Mini, but it's been such a pain in the neck to get working.

---

### Post by benanzo on 2007-05-17
Using LILO requires a few extra steps in the LiveCD environment after you have done the install.  Frankly I am a little surprised that you're getting errors from GRUB if your firmware is fully up to date.

Do you recall what the error was when you installed?  Did you get a GRUB error when it installed or when you tried to boot into Ubuntu the first time?  Honestly it is preferable to use GRUB over LILO, since it is the standard Ubuntu bootloader.  I think we can figure out the problem with GRUB instead of recommending LILO at this point.

---

### Post by ronocdh on 2007-05-17
> **benanzo said:**
> Using LILO requires a few extra steps in the LiveCD environment after you have done the install.  Frankly I am a little surprised that you're getting errors from GRUB if your firmware is fully up to date.

Do you recall what the error was when you installed?  Did you get a GRUB error when it installed or when you tried to boot into Ubuntu the first time?  Honestly it is preferable to use GRUB over LILO, since it is the standard Ubuntu bootloader.  I think we can figure out the problem with GRUB instead of recommending LILO at this point.
Please give us more info about the GRUB error, squeezy! Also, are you sure you're using the Feisty i386 version rather than, say, Edgy or Dapper? The latter two don't play well with EFI systems, but Feisty added support. You can see the popular kludge used to install GRUB on the Intel Macs before Feisty [here]("https://help.ubuntu.com/community/MacBook").

Good luck, and let us know what's up.

---

### Post by squeezy on 2007-05-17
I was running an Edgy version, that may be why! It was Ubuntu Ultimate 1.2. Hopefully that will be the cause of my problems. I'm downloading a new ISO right now for Fiesty Ubunutu 7.04. This will work, right? Also, if you could point me in the direction of the tutorial I need, it would be greatly appreciated. I know there are a few floating around and I want to make sure I get the right one.

---

### Post by ronocdh on 2007-05-17
> **squeezy said:**
> I was running an Edgy version, that may be why! It was Ubuntu Ultimate 1.2. Hopefully that will be the cause of my problems. I'm downloading a new ISO right now for Fiesty Ubunutu 7.04. This will work, right? Also, if you could point me in the direction of the tutorial I need, it would be greatly appreciated. I know there are a few floating around and I want to make sure I get the right one.
The guide I linked to in my post does have a trick that will let you install GRUB with Edgy. But you are welcome to use Feisty as well, and you won't have to use the trick there.

---

### Post by squeezy on 2007-05-17
Thanks! I'm going to go ahead with Feisty because the DVD I have has a hell of a time booting into the Live CD properly. I usually have to go through 3-5 reboots before my screen will show anything. I'm downloading Feisty 7.04 right now. But all I need to do is follow the instructions on the first part [here]("https://help.ubuntu.com/community/MacBook")*7.04*, right?

---

### Post by squeezy on 2007-05-18
Alright, I have it installed! I still have a problem, though (of course). 

So I installed Ubuntu, everything went smooth. I rebooted, and nothing, blank screen. I booted back into OS X (had to use an install disk), and messed around with rEFIt, couldn't get it working, so reinstalled it. When I rebooted after reinstalling rEFIt, I got the rEFIt menu, and it had both OS X and Linux in there. I clicked on the linux icon, and it loaded Linux, but with no display. My sound kicked in, I even heard it log in, but no display.

I always had the problem with the Live CD not displaying until a few tries later, is this the same case? I only gave it three tries and gave up.

---

### Post by squeezy on 2007-05-19
Good new, i got it to boot finally, it just need a few more tires. It runs great, I got Beryl installed and everything. I am having a display problem though. It's currently at 1280x1024. I would like to get it to 1440x900. Can anyone help me with that?

---

### Post by ronocdh on 2007-05-19
> **squeezy said:**
> Good new, i got it to boot finally, it just need a few more tires. It runs great, I got Beryl installed and everything. I am having a display problem though. It's currently at 1280x1024. I would like to get it to 1440x900. Can anyone help me with that?
Try ```
sudo dpkg-reconfigure xserver-xorg
```
This will allow you to manually specify the resolutions you can choose from. It'll also let you pick a keyboard layout, like Macintosh, in case you're currently using US English or something (this has been problematic for some people here, so I figured I'd mention it). If you're comfortable with your keyboard, you can do
```
sudo dpkg-reconfigure -phigh xserver-xorg
```That should save you some time.

---

### Post by Chrisj303 on 2007-05-19
^ The Mac MINI's use the Intel 950 graphics card, so surely squeezy could just use synaptic package manager, and downoad '915 Resoultion'?

Thats what i did, with my macbook (also Intel 950 graph card)



*By the way, hi squeezy! - you may reconise me from demonoid (TR_606)

Glad you (finally) got ubuntu installed!

---

### Post by ronocdh on 2007-05-19
> **Chrisj303 said:**
> ^ The Mac MINI's use the Intel 950 graphics card, so surely squeezy could just use synaptic package manager, and downoad '915 Resoultion'?
Aaaaaannd that's what I get for not reading the whole thread. Yes, Chrisj is right, grab 915resolution and you should be OK. I thought I heard someone say earlier that 915res is included in Feisty? I have an ATI card so I didn't pay close attention. :redface: I guess I misheard.

---

### Post by squeezy on 2007-05-19
> **ronocdh said:**
> Try ```
sudo dpkg-reconfigure xserver-xorg
```
This will allow you to manually specify the resolutions you can choose from. It'll also let you pick a keyboard layout, like Macintosh, in case you're currently using US English or something (this has been problematic for some people here, so I figured I'd mention it). If you're comfortable with your keyboard, you can do
```
sudo dpkg-reconfigure -phigh xserver-xorg
```That should save you some time.



I actually did that last night, got help on another forum, and completely messed up my xorg.conf file. I didn't know what (dammit what was it..) vendor I suppose, my card was. (It had a long list, and didn't have auto detect or Intel listed). So I pressed Esc on everything I didn't know what was about. 

Now when I boot into Ubuntu, I can login just fine, but when the desktop shows, beryl loads, but everything is white. The cube and and stuff works, but it's ALL white. I can't see anything.

> ^ The Mac MINI's use the Intel 950 graphics card, so surely squeezy could just use synaptic package manager, and downoad '915 Resoultion'?

Thats what i did, with my macbook (also Intel 950 graph card)

I also tried installing that 915 resolution before I did all this, and just couldn't figure it out.

If someone could give me instructions on how to restore my xorg.conf file, I would greatly appreciate it. Also steps on using 915 would be great.

I also want to go ahead and thank everyone so far for all their help, I really appreciate it!

What's up TR!

---

