---
title: "Question about Dual Boot and partations."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by ladaowner on 2007-12-12
Hello,

Let me start by explaining that I installed Ubuntu as a fresh installation and wiped away my Windows setup.  Over the past few days I have built and trashed my system plenty of times while learning the ins and outs of Ubuntu.

My question is now that I have a descent installation of Ubuntu I need to daul boot with Windows (for the iPhone).  How do I go about loading Windows on the same HD without killing the Ubuntu setup as it took way to long to build.

I was thinking I could using partition magic for DOS and resize the ubuntu partition to make room for Windows then reload Windows from the CD then replace grub and and hack it to show Linux and windows and everything would work.

Is this guide any good to achieve this? 

[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs")

or does anyone eles have a better guide?

---

### Post by 720iD on 2007-12-12
this sounds like great fun! 

you could look at - gparted-Clonezilla Live CD might be what your looking for clone and partition your drive from live cd or ram

---

### Post by bumanie on 2007-12-12
I believe the problem you'll have is that windows mbr will overwrite grub. You will have to reinstall grub via a live cd.

---

### Post by logos34 on 2007-12-12
> **ladaowner said:**
> or does anyone eles have a better guide?

This is what you're looking for:
[http://www.apcmag.com.au/5459/dualboot_ubuntu_and_windows_xp](http://www.apcmag.com.au/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by gaelfx on 2007-12-12
Yes, the problem you will have is Windows kicking Grub out of the MBR. I wrote some instructions for someone else about how to resolve this issue, not realizing that it wouldn't be an issue for them since they installed Windows BEFORE Ubuntu, so my suggestion is that you remove Ubuntu, install Windows, and then reinstall Ubuntu afterwards. If there is some reason you don't want to do this, then, as bumanie said, you will have to reinstall Grub via a livecd. To do that, follow these instructions: 
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
Afterwards, you will probably want to make sure Windows shows up in your Grub menu, so you should do something like this:
> **gaelfx said:**
> If you open Terminal after installing (it's in Applications -> Accessories -> Terminal), you should type this:
```
sudo fdisk -l
```
This command is Super-user Do (sudo) fdisk -l, which tells you about your partitions, which is basically telling you how your system has named the parts of your disk that hold Windows and which parts hold Ubuntu, etc.
The one that holds Windows is probably the first line you see that has HPFS/NTFS under the heading 'System'. At the beginning of the line, it should say something like /dev/sdaX, where X is a number, in your case, probably 1. Let's just say that it is 1.
Next, you should do this:
```
sudo gedit /boot/grub/menu.lst
```
This is a long file and it may seem hard to read, but you can read some of it if you want, you may learn some useful things. At the end of the file, there should be a line that says "### END DEBIAN AUTOMAGIC KERNELS LIST". Before this line, enter this:
```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```
Remember that X from before? Well, this is where it matters most. We have assumed that X=1. If X=2, then enter this:
```
title Windows XP
root (hd0,1)
makeactive
chainloader +1
```
So basically, you should really enter this (replacing X-1 with the appropriate value):
```
title Windows XP
root (hd0,X-1)
makeactive
chainloader +1
```


It worked for me, which means there is a chance it will work for you, but like I said before, best way is to let Ubuntu do this itself by installing it after Windows.

---

### Post by ubutufan on 2007-12-12
There are many ways to dual boot a system even if you have installed ubuntu first. The ways described by other people are working. they have worked on my laptop before.
What is correct -UNQUESTIONABLY- is that xp installation will take over the mbr. No doubt. Even so, you may follow the suggested implementations or if you like use xp boot to dual boot into both systems. It takes some easy to do hacking on the xp boot.ini file

---

### Post by ladaowner on 2007-12-13
Big thanks to everyone that posted a reply.  Looks to be a big job so might have fun over the weekend.

@ubutufan

You got a guide for hacking the XP boot.ini file as that would be the easist option.

---

### Post by ingram on 2007-12-13
Best way  of dealing with windows xp ini is to not install windows. 

I know you said you need it for your phone but you gotta wonder if it is really worth it. Have you check possible alternatives that might be accessible through ubuntu or linux in general ?

[http://www.hackitlinux.com/50226711/how_to_use_your_iphone_on_linux.php](http://www.hackitlinux.com/50226711/how_to_use_your_iphone_on_linux.php) Not sure how up to date that is though it might be of some help.

---

### Post by ctyc on 2007-12-13
It is usually easiest to install the windows on a fat32 partion first then install Linux.
Keep it simple

---

### Post by rsambuca on 2007-12-13
> **ctyc said:**
> It is usually easiest to install the windows on a fat32 partion first then install Linux.
Keep it simple

Yikes!  Rather use ntfs.

---

### Post by ladaowner on 2007-12-13
The first time I tried Ubuntu I already had Windows pre-installed and the LiveCD re-partitioned my Windows (NTFS) drive and loaded both, with grub handling the dual boot.  I subquently killed this setup trying to update the nvidia drivers and thought I would just start over with a plain simple single boot of Ubuntu.

The problem is I have spent 5 + days going through various guides tweaking everything and I am reluctant to have to start over again when I do not really know what I am doing with ubuntu.  The aim is to keep Ubuntu and put Windows back on by the easiest method.

To answer the question about iPhone yes it only works with Windows or Mac, there is no Linux support todate unless you hack your iPhone about and use Bluetooth to send the music and video to it.

---

### Post by ingram on 2007-12-13
That article seems to imply that you can use an Iphone  with wine without hacking anything. Also wine is pretty available last I checked.

I am not telling you that if you install windows the world will end,but at the same time I cant say with a 100% certainty that if you jump off a 6 story building you will die, still I wouldn't try it.
:tongue:

---

### Post by ladaowner on 2007-12-14
yeah you are correct, Windows is utter rubbish.  If there was choice then of course I wo not use it but the only option I have for the iPhone is a dual boot.  iTunes 7.3 might be hackable with Wine but the iPhone does not work at present therefore leaving the only option of a daul boot.  I am hoping someone like DVD Jon might be able to hack the encryption used on the USB port then some one could write the code to link it to Linux.

At the weekend I am going to attemp those beasty put grub back/daul boot instructions, not looking forward to the prospect of the 10 page hack but still got to be done.

---

### Post by rsambuca on 2007-12-14
Or perhaps next time buy a linux compatible phone! :)

---

### Post by rkd on 2007-12-14
You might try using Virtualbox to create a virtual machine into which you install XP, then install iTunes into that XP.  I don't know that iTunes/iPhone will work successfully when XP is running inside Virtualbox, but it might be worth a try. If it doesn't work, you can always give up on it and switch to the dual boot approach. 

One advantage to the Virtualbox approach is that there would be no danger of messing up the Ubuntu partitions or Grub, since the XP installation would be into the virtual machine, and so wouldn't be fiddling with the real disk.  Another advantage is that you wouldn't have to stop Ubuntu in order to switch to XP for the iPhone tasks -- XP would be running as a guest OS under Ubuntu.

Let me repeat that I don't know that you can get the iPhone stuff working this way.  It certainly is true that it almost certainly will work if you go the dual boot route, so if you think a guaranteed result is worth the hassle of setting up dual boot, that might be the best choice for you.  But if you'd like to avoid the dual boot setup, it might be worth trying Virtualbox.

I did a search for virtualbox and iphone in the forums and one of the threads might be helpful:

[http://ubuntuforums.org/showthread.php?t=588246](http://ubuntuforums.org/showthread.php?t=588246)

It is quite long, and I haven't looked at much of it, but it might help you if you want to go the virtual machine route.  There are also three threads started by the same guy who couldn't get his iPhone to work with Virtualbox, but it wasn't clear whether it couldn't be done or he just couldn't figure it out (and I think he said that he had an unlocked iPhone, which might have complicated matters).

---

### Post by ubutufan on 2007-12-14
> **ladaowner said:**
> Big thanks to everyone that posted a reply.  Looks to be a big job so might have fun over the weekend.

@ubutufan

You got a guide for hacking the XP boot.ini file as that would be the easist option.

Hi
Yes there is actually a very good and detailed guide that I personally followed. The link is
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

You would need to be careful and I suggest that you read the whole article first. All of it.

Where I come from (obviously like most other people-the MS world), I had no intention giving up my working operating system XPSP2. So after trial and error on numerous occasions I came across Miller's how-to. And I made it work.

Miller talks about a rescue disk. You would/should be looking for GPARTED. Once you download and burn the GPARTED iso you are safe enough to follow Miller's how-to. My tip here is that when you boot the GPARTED iso disc, go for the VESA driver option, because it WORKS.

For the past year or so I have set up at least 10 desktops and laptops to work the dual boot, using either the MS bootloader or GRUB. I tell you all of them are equally as stable. There is really no advantage, at least not to my knowledge.

The thing you really need to pay attention is where you install GRUB. This is the last section in UBUNTU installation, before you press the button "install". There is a box down-right that says "Advanced". Press it and in the box opening you need to write BY HAND where you want grub installed. For this to work, you want grub installed at the UBUNTU partition. If you don't understand it but do something else, you are on your own.
I will be around during the weekend
Have fun.

---

### Post by woodslanding on 2007-12-14
Okay, I have a question:

Does anybody know how to uninstall grub in order to use the boot.ini method that Matthew Miller mentions??  I just wiped my old ubuntu install, and am redoing it after repartitioning.   Having reformatted the old ubuntu disk, I can't start either os--it seems that grub is still installed to the mbr, and I'm guessing that if I don't reinstall it there I will have a royal mess.

So can I change this after the fact??  I prefer the windows boot system.

If not, I can live with it.

---

### Post by woodslanding on 2007-12-14
I should mention I have XP on partition 1, and am installing Ubuntu to partition 2.

I guess I should have restarted XP before clearing the old Ubuntu partition, but I didn't know....

---

### Post by logos34 on 2007-12-14
> **woodslanding said:**
> Okay, I have a question:

Does anybody know how to uninstall grub in order to use the boot.ini method that Matthew Miller mentions?? 

Don't use that guide...Try [Wingrub]("http://users.bigpond.net.au/hermanzone/p9.html") if you must use windows bootloader (and I'm not really a fan of windgrub either)

---

### Post by ubutufan on 2007-12-15
> **woodslanding said:**
> Okay, I have a question:

Does anybody know how to uninstall grub in order to use the boot.ini method that Matthew Miller mentions??  I just wiped my old ubuntu install, and am redoing it after repartitioning.   Having reformatted the old ubuntu disk, I can't start either os--it seems that grub is still installed to the mbr, and I'm guessing that if I don't reinstall it there I will have a royal mess.

So can I change this after the fact??  I prefer the windows boot system.

If not, I can live with it.

Your XP disc will do the job for you. Once booted, go for R>Recover.
That's all I will tell you because this is a UBUNTU forum. Google a bit.

By the way I did some checking on the wingrub.exe The commands for the ms system are correct. But I don't know/have not tried how solid this exe.is

I would not play around with my MBR. Miller's how-to is perfect for newbies of any operating system.

---

