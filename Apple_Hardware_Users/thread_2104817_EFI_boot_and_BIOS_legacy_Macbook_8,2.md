---
title: "EFI boot and BIOS legacy Macbook 8,2"
date: 2013-01-14
forum: Apple Hardware Users
---

### Post by LinuxBill on 2013-01-14
Just thought i would post this for anyone having temperature issues with Ubuntu 12.10 on their macbooks. And give my thoughts and setup information that seems to be very reliable and stable. 
 
I had decided that with OSX becoming more like iOS everyday that i wanted to move OS and keep my great piece of hardware. I love the screen and the quad core with 8GB of RAM is amazing. Good machine hampered by the poor OS...anyway!
 
I had the BIOS legacy boot working with reFIND but noticed that the temperatures were sitting at 70 - 80 idle. Which is not good for the laptop in my opinion. The fans were blazing away and it was making no difference. I did my research and it appeared that using the old BIOS legacy mode on your macbook which uses EFI caused issues with heat, due to graphics swtiching and other unkown reasons where making my CPU cores stay roasting hot.
 
I then installed the grub efi and edited my grub.cfg (which i will post once home from work). I kept the BIOS legacy working and installed the EFi version along side it in a different partition on the /dev/sda1 /boot/efi/EFI/ubuntu
 
This is where my 64 EFI image along with the grub.cfg are located this seemed different to everyone else's I had read about online, and i was having lots of trouble getting it to boot. I came very close to removing it all and starting again but i presisted and managed to get it booted. 
 
Now my temps are 40 - 50 idle and graphics switching works fine. But i have been booting with my radeon card disabled because i dont need it and intel built in graphics are perfectly fine for what I use the laptop for. Keeps it cooler and quieter on my desk. 
 
Also i have opted for another fan control package that doesnt get many mentions on the forums, its called mbpfan here is the link for its github. Its very good and seems to work with my model of macbook very well.
 
[https://github.com/dgraziotin/Fan-Control-Daemon](https://github.com/dgraziotin/Fan-Control-Daemon)
 
Some helpful articles are :
 
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)
[http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011](http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011)
[http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/)
 
These guys are alot more intelligent than me and their articles helped me alot! So many thanks if you reside on these forums somewhere! 
 
If anybody has any questions i will try my hardest to answer them. Also excuse my idiot spelling im sure there will be mistakes somewhere. 
 
Bill

---

### Post by ip3t on 2013-01-14
I've a question about EFI boot, even if it doesn't affect the temperature problem:
i've been trying to boot up ubuntu 12.10 amd64 and i386 version (not the Mac version) using rEFInd, but every time appear "missing operation system";

using the default mac boot manager everything seems to works..

do you have an idea about that?

ps. what OS's version did you use? 32/64 ?

---

### Post by LinuxBill on 2013-01-14
> **ip3t said:**
> I've a question about EFI boot, even if it doesn't affect the temperature problem:
i've been trying to boot up ubuntu 12.10 amd64 and i386 version (not the Mac version) using rEFInd, but every time appear "missing operation system";

using the default mac boot manager everything seems to works..

do you have an idea about that?

ps. what OS's version did you use? 32/64 ?

I used 64bit image to boot. The missing operating system would lead me to beleive that grub has not installed properly. I would suggest booting to a live CD and installing grub again and point it to the correct directory where you want to install.

I had this issue with Kubuntu before, i tried installing that but grub install failed during the OS install.

---

### Post by ip3t on 2013-01-15
i've been trying ubuntu with a live cd.. not installed yet.
However i found a possible bug in rEFInd, because when i boot from the Apple boot manager it shows me the EFI and BIOs compatibility option; rEFInd not.
i'm sorry,
obviously this is another kind of problem.

---

### Post by LinuxBill on 2013-01-15
> **ip3t said:**
> i've been trying ubuntu with a live cd.. not installed yet.
However i found a possible bug in rEFInd, because when i boot from the Apple boot manager it shows me the EFI and BIOs compatibility option; rEFInd not.
i'm sorry,
obviously this is another kind of problem.

Im not sure if that is a bug, does reFIND support BIOS mode? It doesn't show on mine either. I actually have both refit and Refind installed. Which means if i want to go into legacy mode for anything the refit option is there in the reFIND boot selction which appear first. Its very good if EFI plays up dont need to live disc it.

---

### Post by ip3t on 2013-01-15
> I actually have both refit and Refind installed
rEFIind installation also includes rEFIT boot manager.

> Im not sure if that is a bug, does reFIND support BIOS mode?
rEFInd is a boot manager that support EFI and BIOS boot mode.

I've also tryed to launch the 64bit Ubuntu OS in EFI and BIOS mode from the default boot manager and rEFInd:
in any case when the control of boot loader (Grub2) returns to the OS the display goes black with some colored pixeled shape. (is it a incompatibility with my not-CPU-integrated graphics card?

with any other 32bit OS (BIOS mode) not... why? ..

---

### Post by LinuxBill on 2013-01-17
> **ip3t said:**
> rEFIind installation also includes rEFIT boot manager.


rEFInd is a boot manager that support EFI and BIOS boot mode.

I've also tryed to launch the 64bit Ubuntu OS in EFI and BIOS mode from the default boot manager and rEFInd:
in any case when the control of boot loader (Grub2) returns to the OS the display goes black with some colored pixeled shape. (is it a incompatibility with my not-CPU-integrated graphics card?

with any other 32bit OS (BIOS mode) not... why? ..

I wasnt aware that REFInd has refit in the installation. I don think it does. I installed it afterwards which is why i can now use it. 

Unfortunately i cant shed any light on your issues with booting there. I can advise you to try using the guide on rods book i linked in the OP, its very good for getting EFI working.

---

### Post by ip3t on 2013-01-17
don't worry, it's ok.
i think it's better (for me) start to understand properly how boot works on mac; whereas i've encountered too many problems about that, i'm not sure there is the right place to ask questions

however, thanks.

---

### Post by ip3t on 2013-01-22
some good news :

[LIST]
[*]seems to be an issue with live-usb; it doesn't work at all in some model of apple laptop (probably due to OS X 10.8.2 update)
[*]in the last 3-4 days i found other informations about the OS laoding stage expecially for mbp 5,1-3. [Here]("http://askubuntu.com/questions/71189/how-do-i-boot-the-live-cd-on-a-macbook-pro") [ [http://askubuntu.com/questions/71189/how-do-i-boot-the-live-cd-on-a-macbook-pro]("http://askubuntu.com/questions/71189/how-do-i-boot-the-live-cd-on-a-macbook-pro") ] there's the link refers to the ubuntu ask bar
[/LIST]

So,
i've managed to used the ubuntu live-cd and install it thanks to Rod Smith:
[LIST=1]
[*]download and burn theamd64+mac iso file
[*] booting the live-cd from the Apple boot manager (rEFInd seems don't work with live-cds)
[*] hold-down "shift"-key until boot GUI appears (that trick force Grub to show it!
[*]add *nouveau.noaccel=1* at the and of the boot kernel options or select the *nomodset* from the menu list (F6), once the boot GUI appear 
[*]proceed on installing ubuntu as Rod said
[/LIST]

some remarks:
[LIST]
[*]brightness and sleep function works fine using the BIOS compatibility mode
[*]in the tests I always reboot using the secondary graphic display adapter (nVIDIA GeForce 9600M GT);
[/LIST]

---

### Post by jo5 on 2013-09-30
Hello, I installed lubuntu 13.04 on my macbook pro 5,5 (aluminum), my system boots with refind (I can boot with refit too though).

I installed the fan control daemon, but my temperatures are still around 60 degrees celsius, and usually the fan barely blow at all. Touching the body, the laptop still feels hot for an idling machine.

---

