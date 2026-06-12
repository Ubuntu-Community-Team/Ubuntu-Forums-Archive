---
title: "Quad boot with ubuntu from windows boot manager...problems"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by xShad0w on 2007-04-24
After tons of googleing and frustration and re installation I still can't figure it out but I think I have at least found the problem, I  have been trying for a couple weeks to get a quad boot going with windows xp, windows vista, mac osx86 and Ubuntu 7.04, I know right lots of stuff, the setup is
 
HD1 Windows Xp

HD2
Partiton1 Windows Vista Primary
Partition2 Mac OSx86 logical
Partition3 Ubuntu Primary
Partition4 Swap Primary

I am trying to get all of this to work using the windows boot manager that windows vista installs because I'll always have windows but its a hassle to work with grub
So far I have Xp working, vista working, and mac working (major woot), but Ubuntu just wont boot up, after the install of Ubuntu, windows vista wouldn't boot so i did a reinstall, then re added the mac osx entry and the Ubuntu entry into bcdedit, after that everything returned back to normal except Ubuntu still wouldnt boot, and at this point grub wasn't loading anymore so i have to use the live cd to access my Ubuntu install, but i used this guide 

[http://www.canerten.com/dual-boot-linux-and-windows-with-windows-boot-manager/](http://www.canerten.com/dual-boot-linux-and-windows-with-windows-boot-manager/)

and something similar to try and get it working with windows vista boot manager

It says the partition has to be primary and it is but when i choose the entry in the boot manager i just get a blinking underscore looking sign and nothing happens, I converted the swap and install partitions to logical and same thing. The problem I think is that both of the partitions are last on my second hard drive, well past the 1024 range and since there primary, they aren't bootable, but i thought that since windows boot manager will handle it they will still be bootable at primary, so if anyone knows the solution to my problem PLEASEEEEE help me thanks so much in advance and thank you for reading my long topic.

---

### Post by crispy_420 on 2007-04-24
Just an idea but doesn't Windows always want to be on the master drive (not secondary)?

Try both versions of windows on the primary drive and OSX and Ubuntu on secondary. Maybe also use grub as a boot manager. Also if remember correctly a company called Acronis has a multi-boot system selector cheap.

[http://www.acronis.com/homecomputing/products/diskdirector/](http://www.acronis.com/homecomputing/products/diskdirector/)

Looks like it supports every version of windows including vista and linux. 

As a side note, what kind of hardware are you running this on?

---

### Post by xShad0w on 2007-04-25
I could try that but i didnt think that it would matter because windows is still in the 1024 bootable range of the harddrive, ill have to see about that, and yea i know that grub would definitely work for all four but I wanted to use windows boot manager incase i ever took off linux and then am stuck with grub, and i use dell dimension 5150 

pentium 4 3.0ghz ht
1gb ddr2
x850xt ati sapphire

umm thats all i can think of on the top of my head o and

hd1 : western digital 250gb
hd2 : seagate 80gb

dont know the model numbers or anything like that in the specifics but thats the base setup

---

### Post by xShad0w on 2007-04-25
Another thought just came into my head, what if in the windows boot manager i clicked ubuntu, and then it loaded up grub and from there i loaded up linux, do you think thats possible, i dont know if that will solve the problem tho because as ive read online windows boot manager can load up linux but the placement is the real issue

---

### Post by adrian15 on 2007-04-26
> **xShad0w said:**
> i used this guide 

[http://www.canerten.com/dual-boot-linux-and-windows-with-windows-boot-manager/](http://www.canerten.com/dual-boot-linux-and-windows-with-windows-boot-manager/)


Have you missed this step perhaps?

On the installation screens, for the boot loader, select the partition itself as the partition (don’t select mbr). 

adrian15

---

### Post by xShad0w on 2007-04-26
This seems like it deffiniatly could be the solution but the regular install doesnt have that option, looked around and it seems the alternate install might have that option so im downloading it, and as soon as it is done i'lll try it out

---

### Post by crispy_420 on 2007-04-26
How do you have OSX running on non-apple hardware?

---

### Post by adrian15 on 2007-04-27
> **xShad0w said:**
> This seems like it deffiniatly could be the solution but the regular install doesnt have that option, looked around and it seems the alternate install might have that option so im downloading it, and as soon as it is done i'lll try it out

Yo do not need to reinstall it again. You can use [Super Grub Disk]("http://supergrub.forjamari.linex.org") for it.
Advanced -> grub -> Restore grub to a partition

adrian15

---

### Post by xShad0w on 2007-04-27
Well i already removed it but i'll reinstall with the regular disk, i tried the alternate and it was just too many options and stuff that i couldnt deal with, i need the gui so once i do that ill try the super grub disk, if it works ill post results, thanks so far for your input guys, o and cripsy_420, google mac osx86

---

### Post by xShad0w on 2007-04-27
Ok so now im getting grub read error, and since i reinstalled ubuntu i get grub before windows boot manager, but yea i went into super grub thingy and did restore grub to partition, selected my ubuntu partition (right?), and then i did the guide using the dd.exe, and now when i select ubuntu from windows boot manager i get GRUB read error, there are a couple things that i could have messed up on , well one thing, on the dd.exe i selected the wrong partition but i doubt that since none of my other partitions would really say grub read error so im fairly sure i did that, yea so i think i did everything right but it still doesnt work, any advice now?

---

### Post by adrian15 on 2007-05-02
> **xShad0w said:**
> Ok so now im getting grub read error, and since i reinstalled ubuntu i get grub before windows boot manager, but yea i went into super grub thingy and did restore grub to partition, selected my ubuntu partition (right?), and then i did the guide using the dd.exe, and now when i select ubuntu from windows boot manager i get GRUB read error, there are a couple things that i could have messed up on , well one thing, on the dd.exe i selected the wrong partition but i doubt that since none of my other partitions would really say grub read error so im fairly sure i did that, yea so i think i did everything right but it still doesnt work, any advice now?

Super Grub Disk -> Boot & Tools -> Boot Partition -> Select Ubuntu partition

Do you see Grub or an error ?

adrian15

---

### Post by xShad0w on 2007-05-02
I actually havent worked on this in a while but thanks for your post, i will get back to you with what happens next asap

---

