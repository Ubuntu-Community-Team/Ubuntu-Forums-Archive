---
title: "Ubuntu on my iMac? (please read message)"
date: 2010-06-03
forum: Apple Hardware Users
---

### Post by sushiboy on 2010-06-03
Hello everyone!

I own an iMac installed with Mac OS X Snow Leopard. I also have Windows 7 installed via Boot Camp. Now my question would be, how can I install Ubuntu 10.04 with my setup? I don't want to totally remove and reinstall all my settings over again just to make way for the installation of Ubuntu. Are there partition apps that can repartition my Macintosh drive and not touch the existing files in it? Basically what I want is to maintain my Mac OS X, Windows 7 Boot Camp and install a new Ubuntu.

Any help is appreciated. Thanks!

---

### Post by Bachstelze on 2010-06-03
> **sushiboy said:**
> 
I own an iMac installed with Mac OS X Snow Leopard. I also have Windows 7 installed via Boot Camp. Now my question would be, how can I install Ubuntu 10.04 with my setup?

1) Boot from OS X DVD
2) Shrink OS X partition in Disk Utility, and create partition in the free space (will be between the OSX and Win partitions)
3) Boot from Ubuntu CD and install Ubuntu. There are a few quirks here:

* In the Ubuntu partitioning tool, you will need to first delete the partition you created in DU and then create a new Linux partition instead (this is because DU cannot create Linux partitions).

* The Ubuntu installer will complain about no swap partition. Continue anyway, you can create a swap file later if you need swap (e.g. for hibernation)

* At the last screen of the installer, you must click the "Advanced" button, and tell the installer to install GRUB on your Ubuntu partition instead of the MBR. Normally, your Ubuntu partition should be /dev/sda3.

4) When Ubuntu is done installing, boot in OS X and install [refit](http://refit.sf.net), it will make your life much easier.

When you reboot you should have the refit screen with OS X, Linux and Windows (if it doesn't appear, try pressing the Option key at boot and select refit).

---

### Post by sushiboy on 2010-06-03
In step number 2, will it not erase my existing Mac OS X system? And can I use 3rd party apps for it example iPartition?

---

### Post by Bachstelze on 2010-06-03
> **sushiboy said:**
> In step number 2, will it not erase my existing Mac OS X system? And can I use 3rd party apps for it example iPartition?

I've always done it with DU, and it does not erase anything in OS X or Windows. Don't know about any other app.

---

### Post by sushiboy on 2010-06-03
This is what my setup looks like:
[IMG]http://img338.imageshack.us/img338/7574/58665578.png[/IMG]

So when I reboot with my Mac OS X DVD I will go to Disk Utility, will I choose **"Mac OS X"** or **"1 TB WDC ..."** ?

After choosing I will go to the tab **"Partition"** is that correct?

Also, example I successfully installed Ubuntu, and later on I installed Parallels on my iMac, will Parallels detect Ubuntu as well as Windows 7?

---

### Post by Bachstelze on 2010-06-03
> **sushiboy said:**
> 
So when I reboot with my Mac OS X DVD I will go to Disk Utility, will I choose **"Mac OS X"** or **"1 TB WDC ..."** ?

Choose your entire drive ("1 TB WDC...").

> **sushiboy said:**
> After choosing I will go to the tab **"Partition"** is that correct?

Yes, then drag the "delimiter" between your OS X and Windows partitions upwards to shrink your OS X partition to the desired size. When you're done with that, click the plus sign to create a partition in the empty space.

> **sushiboy said:**
> Also, example I successfully installed Ubuntu, and later on I installed Parallels on my iMac, will Parallels detect Ubuntu as well as Windows 7?

No idea, I don't use Parallels.

---

### Post by sushiboy on 2010-06-03
> **Bachstelze said:**
> Yes, then drag the "delimiter" between your OS X and Windows partitions upwards to shrink your OS X partition to the desired size. When you're done with that, click the plus sign to create a partition in the empty space.

Can you suggest how much GB should I partition for Ubuntu? I'm new to this so I don't know how much space Ubuntu needs.

---

### Post by derekeverett on 2010-06-03
Ubuntu doesn't "need" much space at all. The entire OS takes up less than 5gb. Depends on how many files etc. you want to store there.

Have you looked at virtual machines at all?

When I had a mac, VMFusion worked ok for me. I couldn't get it to work with my superdrive but honestly, I didn't try that hard either.

---

### Post by derekeverett on 2010-06-03
Here's a thought... but I'm not sure if this would work. Hopefully someone else could clarify if this could work or not.

What about booting your mac into windows and then installing Ubuntu using the wubi installer?

If this works, when you boot your mac and select Windows, then you should get the windows boot loader asking if you want Windows or Ubuntu.

If it worked, the advantages would be that you won't have to partition anything. And if you want to remove Ubuntu it is as simple as removing it from the control panel's add/remove programs and then you have all your Windows hard drive space back.

I wonder if that would work?

---

### Post by sushiboy on 2010-06-03
> **derekeverett said:**
> Here's a thought... but I'm not sure if this would work. Hopefully someone else could clarify if this could work or not.

What about booting your mac into windows and then installing Ubuntu using the wubi installer?

If this works, when you boot your mac and select Windows, then you should get the windows boot loader asking if you want Windows or Ubuntu.

If it worked, the advantages would be that you won't have to partition anything. And if you want to remove Ubuntu it is as simple as removing it from the control panel's add/remove programs and then you have all your Windows hard drive space back.

I wonder if that would work?

Wow that sounds pretty easy and less risky. But is it proven/tested to work? So Wubi is a program for Windows, yes?

---

### Post by derekeverett on 2010-06-03
> **sushiboy said:**
> Wow that sounds pretty easy and less risky. But is it proven/tested to work? So Wubi is a program for Windows, yes?

Wubi is an installer that builds a vitual partition within Windows and allows you to choose Ubuntu or Windows when you boot your machine. And like I mentioned... it removes easily via the Control Panel.

I have used it before on my Windows machine and it works nicely. 

I don't see why you couldn't use it on your windows partition on the mac. It would just be a bit of a goofy booting process. When you start your machine you would have to choose Windows. Then when you get the windows bootloader you would have to choose Ubuntu.

If it worked that would sure be a lot less hassle.

---

