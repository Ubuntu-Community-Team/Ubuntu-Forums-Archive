---
title: "Error: no such devices found  grub rescue"
date: 2011-01-09
forum: Any Other OS
---

### Post by andy123456 on 2011-01-09
Okey so I wanted to install linux mint 10 on my external hard drive. I  inserted the live cd and after starting up there was an icon that said  install linux mint which I used to install linux mint. ( I guess that  this means I installed it with wubi right?).
After installing it and  removing my hard drive windows 7 did not want to boot anymore this error  message came up      error: no such device found ( and then some  numbers and letters) grub rescue>       . Now I managed to repair  grub on the external hard drive  ( I don't know if it is grub2 or grub).  So when I boot the computer without the external hard drive It shows me  the error and when I plug in the external hard drive it gives me the  choice to boot from linux mint 10 64-bit and windows 7. Now Windows 7  works but in order to start it I would always need this external hard  drive and also I did this on my sisters computer and she definately does  not want to have that external hard drive to boot the computer and  choose windows 7 on the list ll the time. Can I remove grub somehow so  windows 7 boot loader will be booting because I don't need linux mint on  this computer at all. Can someone help me I just want the computer to  be the same as it was before. Also I do not have a recovery cd for the  computer just the live cd. The computer is an acer aspire AM1641-E3570A .  Any help would be greatly appreciated!! Also I am a noob with linux.

---

### Post by bcbc on 2011-01-10
You installed the grub bootloader on your internal drive. It looks for it's modules/menu etc. on the external drive in the ubuntu partition. That's why you can't boot with it unplugged.

So what you need is a windows bootloader back on the internal. You can either pop in a windows disk and boot to a win repair prompt: bootrec.exe /fixmbr

or install lilo from Ubuntu. 
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Both will work. You just want to check that when you boot your external it doesn't switch the drive order i.e. confirm /dev/sda is your internal drive.
You'll get a big warning screen when you install lilo. You can ignore this as it relates to booting linux not windows.

---

### Post by andy123456 on 2011-01-10
Thank you so much!!!!! I tried the command to install lilo before on the linux live cd because I saw a thread about it but for some reason it did not work. So because before I posted the thread I downloaded a windows 7 repair cd and by going choosing the command I typed in             bootrec.exe /fixmbr     and it worked perfectly. I did not even have to wait long 1 second and it said it did it successfully. I really appreciate that giving good short method and easy description.  

For anybody who has the same problem and sees this thread you can download windows 7 repair cd from here:      [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)  they also show you the steps to make the cd. You don't need to download this and make a cd out of it if you did not loose your recovery cd.

Anyways thank you very much!!:P:D:P

---

### Post by AkulaFB on 2011-05-03
Hi guys, the exact same thing happened to me, and I executed the same command and it worked! THANK YOU :)
I still get the menu on startup for choosing Windows7 or Ubuntu. I want to take that off though (ie uninstall ubuntu), but how? It's not in my installed programs in windows. How do I take it off? I just want windows now like before. (Ill use linux on another comp).

---

### Post by bcbc on 2011-05-03
> **AkulaFB said:**
> Hi guys, the exact same thing happened to me, and I executed the same command and it worked! THANK YOU :)
I still get the menu on startup for choosing Windows7 or Ubuntu. I want to take that off though (ie uninstall ubuntu), but how? It's not in my installed programs in windows. How do I take it off? I just want windows now like before. (Ill use linux on another comp).

Generally you should create a new thread for help so others see it.

Download and run easyBCD to remove the boot entry for Ubuntu (seems to be the easiest),
OR
go to a command prompt as administrator (right click on CMD, choose run as administrator) and run bcdedit.exe. This should list the boot manager entries; then highlight and copy the GUID corresponding to Ubuntu, then run: bcdedit /delete {GUID}
(I typed that from memory, so check first with: bcdedit /h )

PS [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

