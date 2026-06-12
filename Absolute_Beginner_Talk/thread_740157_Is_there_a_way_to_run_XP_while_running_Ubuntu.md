---
title: "Is there a way to run XP while running Ubuntu"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by ticknubbs on 2008-03-30
I have a dual OS of Ubuntu and XP. Is there anyway I can run XP in a shell or with some program while in Ubuntu rather than restarting and going to XP from the grub menu and back and forth all day? Thanks for any help.

---

### Post by kellemes on 2008-03-30
[virtualbox]("https://help.ubuntu.com/community/VirtualBox")

---

### Post by marine63 on 2008-03-30
in windows xp i was able to install ubuntu on another harddrive with vmware workstation. i can run ubuntu in virtual machine and boot in to it as well. you could do the opposite for windows xp and do seamless but just a thought

---

### Post by Michael.Godawski on 2008-03-30
see also:

[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/)
[https://help.ubuntu.com/community/VirtualBox?highlight=%28virtualbox%29](https://help.ubuntu.com/community/VirtualBox?highlight=%28virtualbox%29)

---

### Post by Duck2006 on 2008-03-30
> **marine63 said:**
> in windows xp i was able to install ubuntu on another harddrive with vmware workstation. i can run ubuntu in virtual machine and boot in to it as well. you could do the opposite for windows xp and do seamless but just a thought

I find virtualbox the better, but it you want to run vmware yes they have a linux ver.

---

### Post by MattBD on 2008-03-30
> **kellemes said:**
> [virtualbox]("https://help.ubuntu.com/community/VirtualBox")

There's also several others (VMWare, QEMU etc). But I'd also recommend VirtualBox as it is probably the easiest to use. You can run Windows on Linux, or Linux on Windows, or try one Linux distro on top of anothe. I use VirtualBox on top of Windows to try out a lot of things I wouldn't want to do on a more permanent install, like messing around with different desktops.

It's in the repositories as virtualbox-ose.

---

### Post by Ken101 on 2008-03-30
innotek Virtualbox works very well for me.
I'm able to run Quickbooks and a few other aps when I need them.

---

### Post by ticknubbs on 2008-03-30
Sorry to be a complete newbie, but I have installed virtualbox and when trying to get it to run I am confused at the setup, and it talks about using the installation cd in the process??? Can somebody explain to me how I can set it up to just run the OS(XP in a different partition) on this hard drive without having the use the CD?

---

### Post by bumanie on 2008-03-30
I too think virtualbox is the best. I used the free home usage binary package because it includes usb support. The OSE doesn't support usb (at least it didn't last time I read about it).
Here's a good tutorial
[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

---

### Post by linuxbeatswin on 2008-03-30
> **Ken101 said:**
> innotek Virtualbox works very well for me.
I'm able to run Quickbooks and a few other aps when I need them.

Now this is a person who knows what they're talking about! I HIGHLY recommend Virtualbox. I use it and endorse it. The setup is easy, and installing new O/S's is pretty easy. (I'm doing exactly that while I'm typing!)

---

### Post by MattBD on 2008-03-30
As far as I know, there is no way you can boot from another hard drive partition using VirtualBox, nor in any of the other virtualization tools I mentioned. You can boot from an ISO image (running it like a live CD, only on top of the host OS), and even install it to the virtual machine, but I don't believe you can use it to boot from an existing partition.

You could install Windows onto VirtualBox, but that would be an entirely new install.

---

### Post by linuxbeatswin on 2008-03-30
> **MattBD said:**
> As far as I know, there is no way you can boot from another hard drive partition using VirtualBox, nor in any of the other virtualization tools I mentioned. You can boot from an ISO image (running it like a live CD, only on top of the host OS), and even install it to the virtual machine, but I don't believe you can use it to boot from an existing partition.

You could install Windows onto VirtualBox, but that would be an entirely new install.

Very true, it is a brand new install, and it takes some time, but it's pretty useful. Thanks for pointing out that you can't boot from another hard drive, that's something that sould have been mentioned before. I was a little confused about that as well when I used Virtualbox for the first time. Good eye.

---

### Post by marine63 on 2008-03-30
yes virtualbox is good but it can only use virutal hard drive created by virtual right?
i used vmware b/c it can install os on a physical hard drive (and a virtual hard drive) 
if theres a way to have virtual box to install os on a physical drive im so there and (i believe) the seamless mode is nice.
also i already knew there was a linux version of it

---

### Post by MattBD on 2008-03-30
> **marine63 said:**
> yes virtualbox is good but it can only use virutal hard drive created by virtual right?
i used vmware b/c it can install os on a physical hard drive (and a virtual hard drive) 
if theres a way to have virtual box to install os on a physical drive im so there and (i believe) the seamless mode is nice.
also i already knew there was a linux version of it

If VMWare can do that, then that's worth trying. I've not used it, only VirtualBox and QEMU, so I wasn't aware of whether VMWare has that kind of capability.

---

### Post by prshah on 2008-03-30
> **ticknubbs said:**
> but I have installed virtualbox and when trying to get it to run I am confused at the setup, and it talks about using the installation cd in the process??? Can somebody explain to me how I can set it up to just run the OS(XP in a different partition) on this hard drive without having the use the CD?

You're out of luck with Virtual Box there. Virtual box can only create and use virtual drives; not an actual physical partition.

But VMWare (commercial) will do the job for you; it will allow you to run your EXISTING XP partition in a virtual box.

---

### Post by Duck2006 on 2008-03-30
Then you set VirtualBox up you set it to use a physic drive with your win install on it, and it will use the win install you have already setup.

---

### Post by Calash on 2008-03-30
There is a way to run an install from a exsisting partion on a Virtualbox setup.  I think VMWare has a similar option as well (Note that Parallels for Mac can do this easly)

That being said it is not easy, and when I finally got it working with a OEM install on my Dell, it could not get the registration info from the BIOS and required me to reregister the install.

You can try it, but be warned that it is not easy and you may end up not being able to go back to using the partition outside of Virtualbox.  Here is a link I found that goes over the basics.

[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

If you do try this, be aware that it is possable to cause problems with both your XP install and, if you are not careful, your Ubuntu install.  Research it a lot before trying.

---

### Post by marine63 on 2008-03-30
yes i currently found this out after i written my last comment! i will try this and see if it works well.
can this be done with seamless?

---

### Post by Calash on 2008-03-30
Yes, once everything is setup and working it is no different than using a virtual hard drive.

---

### Post by marine63 on 2008-03-30
ty im sure ill have fun trying to make it work for me :(

---

