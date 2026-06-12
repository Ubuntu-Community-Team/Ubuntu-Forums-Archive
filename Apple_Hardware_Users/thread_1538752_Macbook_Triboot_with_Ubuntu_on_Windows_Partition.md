---
title: "Macbook Triboot with Ubuntu on Windows Partition"
date: 2010-07-25
forum: Apple Hardware Users
---

### Post by superchef on 2010-07-25
Hi, I have ubuntu installed and running nicely on my netbook and I want to try installing it on my White Macbook 4,1 (2.4 GHz C2D, 2GB ram, 160GB HDD). I'd like to do a tri-boot of Snow Leopard, Ubuntu, and Windows XP.

I already have Snow Leopard installed on the entire disk. I was thinking that right after making another partition with bootcamp, I could boot into the ubuntu cd and repartition the bootcamp partition into 2 partitions (one for ubuntu and one for xp). Ideally, I want to have it installed in such a way so that when I turn on the machine, I have the usual mac boot loader (preferably not rEFIt) and I can choose windows or snow leopard. Snow leopard would boot per usual and if I choose windows, it would greet me with a grub screen where I could choose between xp or ubuntu. 

Sorry if this has already been posted elsewhere.

Thanks!

---

### Post by labaom on 2010-07-25
> **superchef said:**
> Hi, I have ubuntu installed and running nicely on my netbook and I want to try installing it on my White Macbook 4,1 (2.4 GHz C2D, 2GB ram, 160GB HDD). I'd like to do a tri-boot of Snow Leopard, Ubuntu, and Windows XP.

I already have Snow Leopard installed on the entire disk. I was thinking that right after making another partition with bootcamp, I could boot into the ubuntu cd and repartition the bootcamp partition into 2 partitions (one for ubuntu and one for xp). Ideally, I want to have it installed in such a way so that when I turn on the machine, I have the usual mac boot loader (preferably not rEFIt) and I can choose windows or snow leopard. Snow leopard would boot per usual and if I choose windows, it would greet me with a grub screen where I could choose between xp or ubuntu. 

Sorry if this has already been posted elsewhere.

Thanks!

Unfortunately refit is the only way to go. However, when refit loads by default it highlights Mac OSX apple. After 2 seconds, it automatically loads into Mac OSX so it really isn't that much of a downer is thats the reason you do not want refit. Also, I know a way when your booting Ubuntu to make grub timeout zero so it goes straight from refit to ubuntu instead of visiting the grub screen. But it is good to have it on one because if some thing went wrong you want access to grub. Anyways, I will be more than willing to help you if you AIM or something.

---

### Post by superchef on 2010-07-25
Thanks for your response!

I don't mind using rEFIt; the thing that turned me off from using it was that I read sometimes apple update can overwrite it with the original apple bootloader and it may mess things up. Is this the case?

Also, I've used bootcamp before so I know how to create a second partition, but how would I go about making a third partition for ubuntu (I was thinking ~20gb)?

---

### Post by labaom on 2010-07-25
> **superchef said:**
> Thanks for your response!

I don't mind using rEFIt; the thing that turned me off from using it was that I read sometimes apple update can overwrite it with the original apple bootloader and it may mess things up. Is this the case?

Also, I've used bootcamp before so I know how to create a second partition, but how would I go about making a third partition for ubuntu (I was thinking ~20gb)?

You have to use disk utility not bootcamp. It would be easier to discuss this via IM. Do you have AIM? I have never heard of that problem. If worse comes to worse you can always uninstall refit and then update.

---

### Post by Nopstnz8 on 2010-07-25
Actually the above isn't completely true. I was actually looking to do the same as the OP for months, because I didn't like the idea of rEFIt if I ever had to bring my MacBook Pro into service. Anyways, I saw a video last night and decided it was the perfect way to get everything how I wanted. I'm Tri-booting right now, with Ubuntu Lucid 10.04, Mac OSX Snow Leopard, and Windows 7 X64 natively on my MacBook Pro 5,5. What I did, since I already had Windows 7 on Bootcamp, was install an application called Wubi for Windows which is an app that lets you run Ubuntu on Windows without really partitioning Bootcamp, but putting the Ubuntu resource files in a separate folder from Windows. This works awesome. Exactly how I wanted with no problems, and 3D hardware acceleration for desktop effects works great too. Basically what Wubi does is emulate BIOS when selecting Bootcamp via the ALT key at startup, where you then select Win 7 or Ubuntu from the BIOS screen. Everything, including wifi drivers is working great, except for the exception of sound, which I'm working on currently. I even just got OSX multi touch support for the track pad which is a huge plus. Hope this helps. Here are some links I used for my install:

[http://www.youtube.com/watch?v=oWWT5igCloI](http://www.youtube.com/watch?v=oWWT5igCloI)

And Wubi:
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by superchef on 2010-07-26
@ Nopstnz8 I've heard of wubi but never really considered it. Thanks for the suggestion! I'll try it out when I get home from work.

---

### Post by superchef on 2010-07-27
I tried out wubi and it worked very well. I Had to resize my bootcamp partition to give more space to ubuntu using [this method]("http://raddevon.com/resizing-your-boot-camp-partition-without-reinstalling/"). Everything worked out of the box except wifi which I had to manually install drivers for. Also, the touchpad tracking was really slow so I had to change some settings.

Overall, it worked and I'm pleased with the results.

Also (because I'm an ubuntuforums newbie) am I supposed to put a "[solved]" statement in front of this thread's title?

Thanks for your help!

---

### Post by labaom on 2010-07-27
> **superchef said:**
> I tried out wubi and it worked very well. I Had to resize my bootcamp partition to give more space to ubuntu using [this method]("http://raddevon.com/resizing-your-boot-camp-partition-without-reinstalling/"). Everything worked out of the box except wifi which I had to manually install drivers for. Also, the touchpad tracking was really slow so I had to change some settings.

Overall, it worked and I'm pleased with the results.

Also (because I'm an ubuntuforums newbie) am I supposed to put a "[solved]" statement in front of this thread's title?

Thanks for your help!

What is the point of using Ubuntu if it isn't natively running. Yes Wubi is technically Native but its not as fast as actual install. You should highly consider tri booting with refit.

---

