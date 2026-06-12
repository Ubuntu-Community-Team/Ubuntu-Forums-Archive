---
title: "New to Ubuntu...Need Help in Installing Ubuntu on MacOSX"
date: 2018-06-05
forum: Apple Hardware Users
---

### Post by sekag on 2018-06-05
Hello there,

I am trying to install [COLOR=#800000]*ubuntu-18-04-desktop-amd64.iso*[/COLOR] on my 2017 MacBook Pro..Ultimately, I will use such installation to run iDempiere (ERP) with PostgreSQL.
The problem is that i get an error message as below: 

*      the following disk image couldn't be opened.*
**      unbuntu-18.04-desktop no mountable file systems**

Am i doing something wrong?

What is the proper way (the procedures) to correctly do this installation?

Also, my laptop has no usb port nor dvd drive when i start thinking about any dual boot solution.
Thanks 4 helping.
sekag

---

### Post by QIII on 2018-06-05
Moved to Apple Hardware Users.

Are you trying to install Ubuntu while OSX is running?

---

### Post by sekag on 2018-06-06
Yes...!
How else could I do the ubuntu installation?

---

### Post by QIII on 2018-06-07
A Linux distribution is an entirely separate operating system, not an application.  It is not installed from within another operating system unless it is being virtualized.

You must make sure there is unallocated space on the storage device enough for the Linux partitions by using Apple's partitioning manager (I don't know Apple, so I can't help there) and then boot the machine from some form of bootable Linux install medium.

---

### Post by robertarnold659 on 2018-06-10
There is a couple of ways to do this. However, one is more technical than the other.
[B]
Virtualbox method [/B]

First method I recommend is setting it up with virtualbox. Virtualbox is a free application that you can get for macOS and it will run linux virtually. I use this method because the other way is incredibly complex and I ran into a lot of problems with dual boot. This method won't put your computer at risk of dual boot issues. If you are interested in doing it this way follow these directions here: [https://www.simplehelp.net/2015/06/09/how-to-install-ubuntu-on-your-mac/](https://www.simplehelp.net/2015/06/09/how-to-install-ubuntu-on-your-mac/)

**Dual boot method**

Now for a dual boot install I recommend extreme caution, unless you plan on using Ubuntu primarily and you are running an old MacBook that has lost it's luster (the OS is crashing, freezing, etc...). you can follow the directions at the link below, but be sure to read the directions very carefully.
 
After your install you may experience some initial problems (i.e. no wifi adapter, keyboard might not work, track pad might not work, etc...)So here is a list of problems I encountered and ways to fix them. 

_- Keyboard and mouse not working_
---- You may need to get a external keyboard and mouse with USB connections during set up

_- I have no internet_
---- This is because the drivers for the Wifi adapter are not installed yet. Be sure to have a wired ethernet connection to your MacBook to give it internet then go to your applications menu then open software & updates. once the software & updates app is open, go to additional drivers and install the ones listed. (this process might fix your keyboard and trackpad problem too if you run into it.

-[U]&#8203; I can't get back to macOS
[/U]---- you need to edit the boot sequence in Ubuntu by making the macOS as the master boot. You can do this with the use of the efibootmgr command in terminal. I will post a link below on how to do this. I had to perform this step every time I logged into Ubuntu and had not found a way around it so if anyone else has more experience than me, that would be a great help.

-[U]&#8203; I can't get back to Ubuntu
[/U]---- For some reason the rEFInd boot manager doesn't work well. However I still recommend installing it. But, if you are trying to get back to Ubuntu, you can do so by restarting your MacBook and once you hear the chime when the hardware starts up, push and hold the **Option ** or **alt** key on your keyboard until you see the apple logo. This command will bring you to the Mac boot manager and from here you can select the partitioned drive with the Ubuntu OS installed on it. (this part is a little tricky sometimes and takes a little finesse)

**Directions for dual boot **
[https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733](https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733)
[B]
Examples on changing the efibootmgr
[/B][https://www.lifewire.com/change-the-efi-boot-order-efibootmgr-4028027](https://www.lifewire.com/change-the-efi-boot-order-efibootmgr-4028027)
[https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)
[http://manpages.ubuntu.com/manpages/trusty/en/man8/efibootmgr.8.html](http://manpages.ubuntu.com/manpages/trusty/en/man8/efibootmgr.8.html)

I hope this helps you. As I stated above, virtual box is probably the best way to go in my opinion. I use it with virtualbox and it works just fine without the hassles of setup problems.

---

