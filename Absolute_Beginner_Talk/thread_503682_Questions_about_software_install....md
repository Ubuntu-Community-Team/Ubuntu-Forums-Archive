---
title: "Questions about software install..."
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by User X on 2007-07-18
I am trying to configure my wireless network which is a whole new thread all in itself but I wanted to see if I am having a problem with Firefox, so I downloaded the .deb file of opera and stuck it on my flash drive.  Went to the Ubuntu computer and plopped it onto my desktop.  Double clicked the .deb file and I got an error saying something along the lines of incompatible file, or incomplete package...?  Anyway my question is how am I supposed to install stuff if it always seems to be missing something?  I am getting quite frustrated with Ubuntu - I want to work it out though.  I should be able to just double click a *.deb file to install it correct?

---

### Post by bobbocanfly on 2007-07-18
You should just be able to double click a deb file and have gDebi (i think thats what its called) pop up and ask if you want to install it. Have you tried getting a .deb from another source? Might just be a defective download.

---

### Post by mlentink on 2007-07-18
In principle, yes.
But your .deb might depend on other things to be already installed. Just like some packages in Windows depend on DirectX or something, and complain when it isnt installed. Since I dont use Opera, I dont know if that is the case here.

---

### Post by bobbocanfly on 2007-07-18
> **mlentink said:**
> In principle, yes.
But your .deb might depend on other things to be already installed. Just like some packages in Windows depend on DirectX or something, and complain when it isnt installed. Since I dont use Opera, I dont know if that is the case here.

Normally debs will list dependencies and will try to install them along with opera. But as i said before this could just be a dodgy deb.

Also having the wrong dependencies shouldnt stop the actual installation, it would just stop you running Opera once it was installed.

If you get another deb file off the net and that doesnt work you might wanna reinstall the deb installer (i think its gdebi, google it) and try it.

---

### Post by az on 2007-07-18
> **User X said:**
> I am trying to configure my wireless network which is a whole new thread all in itself but I wanted to see if I am having a problem with Firefox, so I downloaded the .deb file of opera and stuck it on my flash drive.  Went to the Ubuntu computer and plopped it onto my desktop.  Double clicked the .deb file and I got an error saying something along the lines of incompatible file, or incomplete package...?  Anyway my question is how am I supposed to install stuff if it always seems to be missing something?  I am getting quite frustrated with Ubuntu - I want to work it out though.  I should be able to just double click a *.deb file to install it correct?

GNU/linux or Ubuntu is different than windows.  It is not a binary-compatible OS.  That means that the way a program interfaces with the OS is not the same between versions.  Since each distribution may run different versions of programs, you cannot take a program that is compiled for one distro and think that it will work in all other distros.

This is because the software interfaces at the source code level.  It has to do this.  This is how it is developed and this is how it can outperform proprietary apps.  Not to mention that there are a lot of security issues with having a stable ABI like in windows (you have to scan for things that can cause you trouble instead of dissabling the security hole).

For most of the users, this is not a problem, since the distribution takes care of distributing the programs.  If you stick to your disto, you can reliable get the precmopiled software that works.  You also have the freedom to use any application you want by compiling it from source.

In your case, you are not connected to the internet and therefore cannot fetch the packages you need.  There are some solutions coming down the pike.  One is to create a way for you to download the packages you want along with their dependencies from an online web application.  This would allow you to download the software from a computer that is connected to the net and then bring them to your non-networked Ubuntu computer.

Another solution is to provide staticly-linked apps - a program that has all the shared-libraries self-contained.  This is a waste of ram.  If Linux aps were built like this, the ram requirements for running Ubuntu would exceed Windows Vistas.  Let's not forget that Opera is a non-free application that cannot be distributed by any one other than their publishers.  That doesn't help you here, either.

---

