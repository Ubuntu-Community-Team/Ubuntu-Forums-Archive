---
title: "Asus g73jh Cant Boot from USB"
date: 2012-02-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by bloodbruise on 2012-02-17
I recently installed Ubuntu for only the second time in my life recently. First time was many versions back. I have an Asus G73JH with 2 physical hard drives. On my primary drive I had the MBR and windows 7 installed. On the secondary drive i had Ubuntu installed.
The MBR that was installed was Grub 1.99.

I used a program on Ubuntu called Gparted (A Partition editor) to make some changes to my primary hard drive with windows on it. When i originally installed windows a while back, i cant remember why not but i had a small 40gb partition that was in front of the main win 7 os partition. So i used GParted to extend that partition backwards. 

Before i go on i know that what i did is considered not to 'smart' to do. The reason i did it is because i knew that windows would not start afterwords, but i also knew that if i used my windows 7 installation disk i could do system repair and it would fix it. ( i have had my own share with screwing with windows to much)

So after using gparted of course windows did not boot and so i put in my windows 7 installation disk and was going to boot from it. Unfortunately i was unable to boot from my disk, for whatever reason im still not sure why. I was also unable to boot from my windows 7 installation flash drive. 

I know that both the disk and the flash drive work perfectly, i tested them after on another computer that is working fine, and both booted properly from the bios. 

I then was poking around in ubuntu and was able to mess with the MBR's a bit. On my primary drive i reset the MBR to the windows 7 default MBR. on my slave drive(the drive with the ubuntu installaton) i installed grub so that way i could choose from my bios what hard drive to start, thus what MBR to start thinking that possibly Grub was overriding my bios and making me unable to boot from cd or usb.

I then found out that what i did, did not help at all, i still can NOT boot from either win 7 cd or usb... Whats odd is i can boot from my live ubuntu usb.....

I have tried taking my slave hard drive(ubuntu installation) out and just booting the master, i have tried resetting my bios, i have properly set up the bios to boot from usb, and or cd and still nothing. 

What makes it worse in my mind is i know that BEFORE i installed ubuntu, and grub was installed as the MBR i WAS ABLE TO BOOT FROM USB and/or CD/DVD!!!! 

What the bloody heck is going on here? Anyone have any idea? I really dont want to have to whipe my main hard drive.

Oh btw, i can mount my master hd(broken windows installation) in ubuntu and view all of its contents, so i HAVE taken a backup of all important data. but i still dont want to have to whipe my master drive, that is the worst case scenario for me. 

If anyone can please help, that would be great. Thank you.

---

### Post by @gu79 on 2012-02-17
Hi. Take it easy, as long as yo don't delete anything, things can be fixed. I think you are a little bit confused. First, It doesn't matter what you have done to the partitions or what OS you've installed, you should be able to boot from CD or USB anyway. In my asus N55SF the "ESC" key shows me the boot menu to choose where to boot from. Otherwise, enter the setup and select a proper boot order. The proof is that you can boot the Ubuntu Live CD.

The small partition that you mention before the windows might be the RECOVERY partition. In my machine, pressing F8 while booting, makes the laptop to boot from that partition to recover the original windows installation (factory). If that's the case and you want to recover that, you should give it its original size (if you want to delete it, you can make a backup of that partition using clonezilla).

So, I guess that you couldn't boot the installed Ubuntu (you didn't say that nor the ubuntu version). If you can, tell me as that would be the easiest way to solve the problem (reinstalling grub in the proper place). Otherwise, you could fix the problem using [this guide]("http://ubuntuforums.org/showthread.php?t=1581099") to restore grub (a little bit advanced). But, if you couldn't boot the Ubuntu partition at all, then the easiest way is to install Ubuntu again. 
Keep in mind that if you have two drives, one will be showns as **/dev/sda** and the other as **/dev/sdb**. If you are installing Ubuntu in **/dev/sdb1** (the first partition of the second drive), grub must be insalled in **/dev/sda** (**/dev/sda1** is the recovery partition and **/dev/sda2** the windows partition). That way, it will be the first to take control of the boot process and will show you the windows loader (from sda2) the recovery (sda1) or ubuntu (sdb1) to choose from.

---

