---
title: "Problems with GRUB - total novice need help to evaluate switch to Ubuntu"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Cippa Lippa on 2007-03-12
Dear all

this is my first message as a Ubuntu (or Linux for that matters) user. And I really wanna see how good is this legendary "Ubuntu community" in helping the weak fella like me... :)
I am having some quite serious problems in installing Linux

I have a ECS laptop (pentium 4 - 2.4GHZ, 2GB RAM)
I have one internal harddrive (hda) with Windows XP on it and an external enclosure hard drive (sda) with 60 GB of free space on which I just installled Ubuntu.

After installing Edgy from the LiveCD and installing GRUB in /dev/sda I realized that Grub was giving me "error 17" when trying to boot to ubuntu and "error 13" when trying to booot to windows.

After reading some posts I did the following
booted to liveCD
opened terminal
sudo grub
find /boot/grub/stage1 (which gave me (hd1,0))
root (hd1,0)
setup (hd1,0)

after that the system booted correctly into Ubuntu and Windows but I get a horrible error message (error 21) from GRUB when I try to boot my laptop without the external drive connected.... :( 

This is pretty horrible since this means that I have to carry around my external in order to boot into my windows default OS.

Can you guys please help me out on this??? That would be so awesome.

---

### Post by mikewhatever on 2007-03-12
I think the problem is that first you installed GRUB to the MBR of /dev/hda, the Windows disk, and then reinstalled it to the MBR of /dev/sad, Ubuntu disk. Have you restored the hda's mbr? You can do that from windows recovery console by typing fixmbr. I would disconnect the external HDD while doing this. If you do not have the Windows CD, look here [http://www.users.bigpond.net.au/hermanzone/p18.htm#fixmbr](http://www.users.bigpond.net.au/hermanzone/p18.htm#fixmbr)
After you can boot Windows without the external HDD connected, set the BIOS boot order to boot fist from the external HDD and then from the internal one. This way, if the external HDD is connected, GRUB will load and boot both Ubuntu and Windows for you. If it is disconnected, the computer will boot into Windows from the internal HDD.

---

### Post by Cippa Lippa on 2007-03-14
Dear Mike

THANKS for taking the time to answer
I fixed the problem also thanks to you
So, basically what happened is that I used fixmbr the first time and I could boot in Windows but when I was plugging in the hard drive it was telling me GRUB error 13.
So I fiddled around a little more with the GRUB bash shell and the result was that I couldn't load anything anymore. Somehow I must have totally destroyed the MBR of windows because it wasn't even able to recognize that the main windows partition was formatted at all.
Solution was that I had to reformat windows (hence the delay in my answer). That was painful man...  Soo now I am more or less on track. The problem now was that Windows would be loading but Grub would give me a weird error upon selecting Ubuntu. I forgot it but it was about the tty and that job was turned off or something like this. I will come back here if I remember. BBy looking at the forums I had the idea of trying to start with the recovery mode of Ubuntu and then by reading the output I figured out that Ubuntu was trying to load from /dev/sdb and not /dev/sda. I just needed to change that in the second line of the Grub loader (also in the /boot/grub/menu.lst) and then it was loading fine... I guess this was the problem from day one.
From what I have seen the 90% of these problems with Grub are due to Grub pointing in the wrong direction. By fiddling with the destinations you should be able to get it to work

Hope it helps

Cippa

> **mikewhatever said:**
> I think the problem is that first you installed GRUB to the MBR of /dev/hda, the Windows disk, and then reinstalled it to the MBR of /dev/sad, Ubuntu disk. Have you restored the hda's mbr? You can do that from windows recovery console by typing fixmbr. I would disconnect the external HDD while doing this. If you do not have the Windows CD, look here [http://www.users.bigpond.net.au/hermanzone/p18.htm#fixmbr](http://www.users.bigpond.net.au/hermanzone/p18.htm#fixmbr)
After you can boot Windows without the external HDD connected, set the BIOS boot order to boot fist from the external HDD and then from the internal one. This way, if the external HDD is connected, GRUB will load and boot both Ubuntu and Windows for you. If it is disconnected, the computer will boot into Windows from the internal HDD.

---

