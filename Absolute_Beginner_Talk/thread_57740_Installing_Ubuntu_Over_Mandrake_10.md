---
title: "Installing Ubuntu Over Mandrake 10"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by Unoone on 2005-08-17
I had a 3 disk set of Mandrake 10 that I downloaded way back. I installed it with ease. However, upon booting into the OS, I found that I was lacking install cd4 of the disk set. I'm on a dial up connection now until I get the dsl back up. So no easy updates online.

I installed Mandrake on a prepared ext3 partition with a prepared swap. I am using Windows XP so I set up a dual boot with Lilo.  

Can I use my existing ext3 partition, swap and Lilo for my new Ubuntu install? I would like to do this if I could. I'm afraid to mess up my dual boot structure or to ruin my Windows XP Boot.  Thanks for your help.

---

### Post by aysiu on 2005-08-17
You can install Ubuntu on the existing ext3 partition; you just have to answer "yes" when the installation process asks if you want to install Grub to the MBR.

However... since you're on dial-up, I'm not sure if Ubuntu is for you (sadly). Most of the software and updates for Ubuntu are online and sometimes require large downloads.

---

### Post by Unoone on 2005-08-17
[QUOTE=aysiu]You can install Ubuntu on the existing ext3 partition; you just have to answer "yes" when the installation process asks if you want to install Grub to the MBR.

However... since you're on dial-up, I'm not sure if Ubuntu is for you (sadly). Most of the software and updates for Ubuntu are online and sometimes require large downloads.[/QUOTE]

Should I stick with Mandrake and get a hold of cd4 for now?

It seems that once I get the final disk for Mandrake I can just download rpms, etc as I need them.

---

### Post by aysiu on 2005-08-17
[QUOTE=Unoone]Should I stick with Mandrake and get a hold of cd4 for now?

It seems that once I get the final disk for Mandrake I can just download rpms, etc as I need them.[/QUOTE] If you're downloading RPMs, it's the same as downloading .debs in Ubuntu. I just figured that since you have two extra CDs (full of software, I assume), that that's two extra CDs' worth that you don't need to download over dial-up.

---

### Post by Unoone on 2005-08-17
[QUOTE=aysiu]If you're downloading RPMs, it's the same as downloading .debs in Ubuntu. I just figured that since you have two extra CDs (full of software, I assume), that that's two extra CDs' worth that you don't need to download over dial-up.[/QUOTE]

Are you referring to Ubuntu? I already have the install cd. What more do I need? 

As far as Mandrake, I'm just trying to install my Nvidia drivers and video drivers, etc. All I'm getting in Mandrake now is dependency pop ups as the installer ask for cd4, who knows what it will ask for next. The kernel source was not even installed as this too is on cd4. The Nvidia driver install window sated that I didn't even have the kernel source. And I checked, I don't. I can't install the Nvidia drivers I downloaded in Mandrake.

None of the reviews mentioned this. This kind of makes Mandrake incomplete out of the box. I could fork over the little cash for the Mandrake Box Sets. It would be way better than downloading a Linux Distro and later on finding that some crucial operational elements are missing. Seems like bait and switch tactics to me. i didn't know that some Linux Distros rolled like that. I thought that as the game of some other OS.

My windows installs give me everything I need to get to work right out of the box. And all the crashes I can ask for.  

Is Ubuntu the same as Mandrake as far as basic driver dependencies for Nvidia? Or can I just down load the drivers for Nvidia an count on everything else being in my Ubuntu OS? This won't stop me form using Ubuntu. I'm just trying to get everything in order. I want to makes things as easy as possible. I have been using Knoppix with better ease than this current experience. I just want to get down with the real Linux thing. Thanks.

---

