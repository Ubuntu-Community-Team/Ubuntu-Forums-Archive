---
title: "Can someone help me."
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by prophet of the pimps on 2006-01-13
Ok let me start of by saying that i always have been a fan of linux but i dont no jack about how it works. After frustating time with windows i finally decided to try out linux and finalised Ubuntu (5.04) as the linux of choice to put on my system.

Now my problem is that i have no prior ecperience with linux at all and after installing (which by the way was easier then i thought it would be) i got my system running ubuntu as my third os. now on windows i am well versed with all the customisation options but in ubuntu i dont know anything.

Let me start of at what problems that i have.

1) My ubuntu is installed on my second hard drive and the drive letter is I:. Its about 3.9gb. Now previously this drive was visble in windows but after installing Ubuntu the drive is no longer visable to windows xp or windows me. is i possible to allow windows to view the drive.

2) I am new to ubuntu so i dont know what the explorer system is suppose to look like but i know for sure that the rest of my partitions of Hard drive are not visible in ubuntu (all are Fat32). may be they are not mounted but i dont exactly know the command to do that. if there is a command then how do i make ubuntu permantely mount the rest of the partitions.

3) How do i change the boot sequence? i wanna make windows my default boot system because my family also uses the computer and they do not know how to operate linux so if they accidently boot into ubuntu they panic and hard boot the damn system (i know i should teach them but sisters can be so impaitent.)

Final question well its more of an enquiry. for a totaly linux noob like me would if be better if i move to the KDE version over the gnome one because the interface is something i am more used to and is the kde version easier to operate.

Please help me so i can be liberated from the windows hell in the future.

Thanks in advance to all those who reply.


"Power to the people and to Open Source:D "

---

### Post by aysiu on 2006-01-13
[QUOTE=prophet of the pimps]
1) My ubuntu is installed on my second hard drive and the drive letter is I:. Its about 3.9gb. Now previously this drive was visble in windows but after installing Ubuntu the drive is no longer visable to windows xp or windows me. is i possible to allow windows to view the drive.[/quote] Windows doesn't recognize Linux. I'm surprised the drive disappeared, though. When you go to Disk Information, you should be able to see it as a "healthy" unknown partition in Windows.

There's a tool to see Linux partitions from Windows, but I forget what it's called.

> 
2) I am new to ubuntu so i dont know what the explorer system is suppose to look like but i know for sure that the rest of my partitions of Hard drive are not visible in ubuntu (all are Fat32). may be they are not mounted but i dont exactly know the command to do that. if there is a command then how do i make ubuntu permantely mount the rest of the partitions. See the fourth link of my signature.

> 
3) How do i change the boot sequence? i wanna make windows my default boot system because my family also uses the computer and they do not know how to operate linux so if they accidently boot into ubuntu they panic and hard boot the damn system (i know i should teach them but sisters can be so impaitent.) Go to Applications > Accessories > Terminal. A DOS-like window will appear. In it, type these commands: ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
``` Very close to the beginning of the file, you'll notice a line that says *default 0*--that means boot the first entry by default. You want to change 0 to another number. For example, a typical grub order looks like this:

0 Ubuntu
1 Ubuntu recovery
2 Memtest
3 Other operating systems descriptor
4 Windows XP

So if you wanted to change the default from Ubuntu to Windows, you'd change ```
default 0
``` to be ```
default 4
```

> Final question well its more of an enquiry. for a totaly linux noob like me would if be better if i move to the KDE version over the gnome one because the interface is something i am more used to and is the kde version easier to operate. No one can say which interface is better for you. Frankly, I think it's better to stick with Gnome for now because most users here use Gnome, and you'll get better support for Gnome problems.

It is, however, quite easy to get KDE. Just ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
``` log out. Click on "Session" and select KDE. Then log back in.

---

### Post by prophet of the pimps on 2006-01-13
Thank you thank you thank you so much.

:D

I was reading this tutorial but couldnt make head or tails of it.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Edit to add: Just tried it and it worked. again it is simpler tehn i thought it would be. :p

Finally my sister os off my back for screwing around with the comp. I was in real hot water because she hated going through 2 boot screen. (grub and then the Windows one for shifting between me and xp)

Now i just have to add my network adapter, install my isp client, update firefox, get the geforce fx5200 drivers and then start mounting the hard drives and i willbe all set to enter the world of linux.

Hopefully the next time i will be replying using my linux OS.

Again thanks for your help. you have just gained a new recruite for the army of linuxiods.:D

---

### Post by ubuntu_demon on 2006-01-13
I moved this thread to the absolute beginners section

---

### Post by aysiu on 2006-01-13
[QUOTE=prophet of the pimps]
Now i just have to add my network adapter, install my isp client, update firefox, get the geforce fx5200 drivers and then start mounting the hard drives and i willbe all set to enter the world of linux.[/QUOTE] This may help: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by prophet of the pimps on 2006-01-13
i am downloading kubuntu right now so is it possible to switch to gnome later on and is there a way by which i can choose either kde or gnome at boot up.

---

### Post by aysiu on 2006-01-13
[QUOTE=prophet of the pimps]i am downloading kubuntu right now so is it possible to switch to gnome later on and is there a way by which i can choose either kde or gnome at boot up.[/QUOTE] ```
sudo apt-get install ubuntu-desktop
``` log out.
select session.
select gnome.
log in.

---

### Post by prophet of the pimps on 2006-01-13
Thanks. :D

---

