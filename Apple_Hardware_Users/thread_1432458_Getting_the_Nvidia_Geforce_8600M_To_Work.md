---
title: "Getting the Nvidia Geforce 8600M To Work"
date: 2010-03-17
forum: Apple Hardware Users
---

### Post by shinderhizzle84 on 2010-03-17
Hello everyone. First of all, I'd like to thank the developers of this fine OS for all their commitment and hard work. I know it sounds slightly cheesy being in a first post, but when all versions of Windows for some reason refuse to install on your Boot Camp-partitioned mac and Linux does, you know that's something special :P

Anyways, let me get straight to my point.

I own a Macbook Pro, it's not super new, it's about two years old. I don't know which model it is, sorry, but I think for some reason that it is about a year after the Santa Rosa.

Anyways, I run an Nvidia 8600M GT graphics card, but when I first loaded up Ubuntu after a highly successful installation, the device hardware program or whatever it's called said my nvidia graphics card, in addition to my broadcom wireless adapter, weren't in working order.

Normally this would be fine, but I've pretty much installed Linux on my computer solely to play video games. I've already installed Wine, though.

Anyways, I'm by no means a computer genius like I'm assuming most of you all are. I'm also a complete n00b to Linux, making things even more difficult.

Can somebody please link me or write me a STEP-BY-STEP GUIDE on how to activate the Nvidia 8600M GT drivers for my machine? Obviously it would be quite a wasted day if I could not do the only thing that I installed Linux for....

Also, when I step-by-step, I REALLY MEAN step by step. Don't say "install this kernel" or "run this .run file", as I have NO IDEA HOW TO.

Thanks so much, I am really, very very frustrated and would appreciate any feedback I can get on this situation.

By the way, free virtual forums popcorn for whoever can help me out with this :P

:popcorn:

---

### Post by alexmurray on 2010-03-17
Run the Hardware Drivers program from the System->Administration Menu - this should list both the Nvidia driver for your GPU and the Broadcom driver for wireless - for the Nvidia driver it will probably suggest a few options, pick the recommended one which should also be the newest driver (185). 
Highlight this and click the Activate button in the bottom right and it will install the driver. Then do the same for the Wireless driver too (this will also probably suggest 2 options, pick the STA one not the B43 one).

Then simply reboot and you both should now be working.

(Hopefully this is correct i am writing it from memory as I'm not in front of my Ubuntu machine atm).

---

### Post by 2hot6ft2 on 2010-03-17
First off welcome to the forum and to ubuntu.

I am not familiar with Mac' and Apple products and it makes me wonder when you say:
> **shinderhizzle84 said:**
> 
Anyways, I run an Nvidia 8600M GT graphics card, but when I first loaded up Ubuntu after a highly successful installation, **the device hardware program or whatever it's called said my nvidia graphics card, in addition to my broadcom wireless adapter, weren't in working order.**

I take it you're referring to System > Administration > Hardware Drivers

So I'll tell you how I would install the driver and where to get it **IF** it was a regular pc, but **[SIZE="3"]you should definitely wait for some of the other Mac users to step in and give their opinion before attempting these instructions on your Mac[/SIZE]**.

Ok, that being out of the way and understood.
Here's where to get the [graphics driver for the Nvidia 8600M GT graphics card]("http://www.nvidia.com/object/linux_display_ia32_190.53.html"). Screen clip at the bottom showing your card is under the Supported Products tab on that page.

Download it to your home folder. That's the folder when you click on
Places > Home Folder
You can download it to your Desktop if you prefer but MOVE it to your home folder once it's on the computer.

Once it's in the home folder you're going to reboot and as soon as grub starts loading press the Shift key. Right after the Mac screen or whatever it is on a Mac.
This should make the grub menu show up.
Choose Recovery Mode
A bunch of text will scroll by.
When you get to the choices choose Shell prompt (it will show the prompt almost immediately at the bottom of the screen)
Put your cursor at the prompt and use
```
cd /home/<yourusername>/
```
Where <yourusername> is the name you log in with without the arrows<>
then (that's a lower case LS)
```
ls
```
You should see the driver listed.
> NVIDIA-Linux-x86-190.53-pkg1.run
Then use
```
sh NVID
```
And hit the Tab button and it will complete the name for you, then hit Enter
(unless you WANT to type the whole name in)

Read each thing that shows up and agree (there will be a few and I don't remeber the exact options but you want to continue) using your arrow keys to choose. It will take a little while .
When it asks if you want it to replace Xorg select Yes

When it finishes and returns you to the Shell prompt type
```
reboot
```
And hit Enter
All done, the computer will restart.
You can go to System > Administration > NVIDIA X Server Settings
and see the nvidia settings but you wont be able to save any changes you make.

If you want to save any changes you can go to
Applications > Accessories > Terminal
and start it by using:
```
gksu nvidia-settings
```
(Anytime you use sudo, gksu or gksudo you will NOT see your password when you type it in. Just type it in and hit Enter).
and make changes and save them. 

That's how I do it.

And here is a guide for Broadcom wifi adapters
[[SOLVED] The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

---

### Post by shinderhizzle84 on 2010-03-17
> **2hot6ft2 said:**
> First off welcome to the forum and to ubuntu.

I am not familiar with Mac' and Apple products and it makes me wonder when you say:

I take it you're referring to System > Administration > Hardware Drivers

So I'll tell you how I would install the driver and where to get it **IF** it was a regular pc, but **[SIZE=3]you should definitely wait for some of the other Mac users to step in and give their opinion before attempting these instructions on your Mac[/SIZE]**.

Ok, that being out of the way and understood.
Here's where to get the [graphics driver for the Nvidia 8600M GT graphics card]("http://www.nvidia.com/object/linux_display_ia32_190.53.html"). Screen clip at the bottom showing your card is under the Supported Products tab on that page.

Download it to your home folder. That's the folder when you click on
Places > Home Folder
You can download it to your Desktop if you prefer but MOVE it to your home folder once it's on the computer.

Once it's in the home folder you're going to reboot and as soon as grub starts loading press the Shift key. Right after the Mac screen or whatever it is on a Mac.
This should make the grub menu show up.
Choose Recovery Mode
A bunch of text will scroll by.
When you get to the choices choose Shell prompt (it will show the prompt almost immediately at the bottom of the screen)
Put your cursor at the prompt and use
```
cd /home/<yourusername>/
```Where <yourusername> is the name you log in with without the arrows<>
then (that's a lower case LS)
```
ls
```You should see the driver listed.

Then use
```
sh NVID
```And hit the Tab button and it will complete the name for you, then hit Enter
(unless you WANT to type the whole name in)

Read each thing that shows up and agree (there will be a few and I don't remeber the exact options but you want to continue) using your arrow keys to choose. It will take a little while .
When it asks if you want it to replace Xorg select Yes

When it finishes and returns you to the Shell prompt type
```
reboot
```And hit Enter
All done, the computer will restart.
You can go to System > Administration > NVIDIA X Server Settings
and see the nvidia settings but you wont be able to save any changes you make.

If you want to save any changes you can go to
Applications > Accessories > Terminal
and start it by using:
```
gksu nvidia-settings
```(Anytime you use sudo, gksu or gksudo you will NOT see your password when you type it in. Just type it in and hit Enter).
and make changes and save them. 

That's how I do it.

And here is a guide for Broadcom wifi adapters
[[SOLVED] The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")


I got it to work, I think, thanks :D

Only problem is I did all of this so I could play Rome: Total War using Wine, and although I see success stories on their boards, I can't start a new campaign/battle or anything...I'm jsut stuck in the menus :(

I wish I could register at Wine's forums and let them know about this but their forums keep on saying I'm entering the incorrect confirmation code, which is bogus, because I've done it, like, 8 times now, and every time it's been correct...

Thanks for the help, though, I really do appreciate it.

---

