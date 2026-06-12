---
title: "Windows on Ubuntu"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Holmes89 on 2007-07-30
I have Ubuntu running on the same system as Windows XP Media Center Edition and since I just switched there are some applications I still would like to use. I hate having to restart my computer to get to my Windows partition to run programs like iTunes, is there a way I can run Windows virtually as I'm running Ubuntu (sort of like parallels in OS X)? If so how?

---

### Post by felicity on 2007-07-30
Yes, you should check out [VirtualBox]("http://www.virtualbox.org/"), it's a great and fast program to run Windows within Ubuntu.

---

### Post by Brian96 on 2007-07-30
I accomplish this with VMWare Server, which is in the repositories. However, you must have a separate license for Windows (in addition to the one for your existing install). If you are comfortable with only having Ubuntu on the "bare metal," you could get rid of your native Windows install and only run it in WMWare inside Ubuntu.

There are howtos on here to help you get VMWare set up (although it is pretty straightforward). Someone even found a way to get to their native Windows install through VMWare in Ubuntu, but I haven't tried it.

---

### Post by oilchangeguy on 2007-07-30
probably the only way, would be to uninstall windows (back up your files first). and install it with one of the virtual machine software that's available. (you'll have to uninstall it as your main machine, because you have to use a legal copy on your virtual machine, as with any paid os, you have to deal with their requirements for use).

---

### Post by Holmes89 on 2007-07-30
> **felicity said:**
> Yes, you should check out [VirtualBox]("http://www.virtualbox.org/"), it's a great and fast program to run Windows within Ubuntu.

Can I use my existing partition without losing anything? And what exactly do I need to do if I'm running Feisty?

---

### Post by felicity on 2007-07-30
Yes you can use your existing partition without it destroying anything. You just have to have room on your drive for however large you want the virtual machine to be. VirtualBox just stores a .vdi file which contains the virtual Windows installation on your drive, so it doesn't affect whatever else is on the drive. You pretty much just install the .deb for your OS on the VirtualBox website, then start it up and give it some info regarding what size you want your new Windows virtual machine to be, and insert the windows disk to install it.

---

### Post by Brian96 on 2007-07-30
> **Holmes89 said:**
> Can I use my existing partition without losing anything? And what exactly do I need to do if I'm running Feisty?

Someone on here has posted a howto that describes how to get to an existing Windows installation using virtual machine software (I can't remember which one; VMWare Player comes with Ubuntu, and VMWare Server is in the Ubuntu repositories). The problem with this method is that Windows thinks it is installed on two separate machines, and after you boot into each of them back and forth, it red flags your installation as bootleg.

The EASIEST way is one of the following: You have TWO valid Windows licenses (in which case you can leave one installation alone and add another in Ubuntu on a VM) OR You are comfortable erasing Windows from your harddrive and reinstalling it as a VM in Ubuntu.

---

### Post by Acglaphotis on 2007-07-30
I think kvm is faster than virtualbox but thats just me.

---

### Post by felicity on 2007-07-30
Oh, sorry, I thought you meant use your existing partition by itself. I see now that you want to use your existing partition as the virtual machine itself. You might check out Brian96's suggestion for that. Another option is to just create a new Windows virtual machine, then copy the files you want to save from your older Windows installation into the new one.

---

### Post by Holmes89 on 2007-07-30
How about this Xen? The Wikipedia article says that you could boot off of an existing partition, has anyone tried it? [http://en.wikipedia.org/wiki/Xen](http://en.wikipedia.org/wiki/Xen) "Xen may also be used on personal computers that run Linux but also have Windows installed. Traditionally, such systems are used in a dual boot setup, but with Xen it is possible to start Windows "in a window" from within Linux, effectively running applications from both systems at the same time."

---

### Post by anewguy on 2007-07-30
You use your existing Windows partition with VMWare or VirtualBox either one.  From my experience, having tried them both, I would say it is easier to set up in VMWare.  VMWare Server itself is free, and allows you set up your virtual machine quite easily.  Yes, a registration number is required, and that registration number is also free.  With VMWare Server you can set up to use your existing Windows partition right from the GUI, whereas with VirtualBox, I was only able to do it via command lines (there my be a GUI way, but I never found it).  With either, you will want to install the vm tools to the virtual machine you create.

There are some caveats:

- You will need to re-activate Windows even though it is on your existing partition

- If you try to boot Windows stand-alone, you will need to re-activate Windows, which you will need to do again when you go back to the virtual machine.  Microsoft only allows this a few times then they start to wonder what you are up to.

- You will be presented with the boot menu, and if you select anything other than Windows from that menu, particularly if you select Ubuntu again, you will destroy your installation and will need to reinstall everything again.  This selection must be made EVERYTIME you boot.

That's a few that I know from my experience (read as "I did this and these boo-boo's happened").  There is at least 1 moderator on this forum who is an expert on virtual machines and I am sure he will let you know what he thinks on your idea as well as suggestions and caveats he may have.:)

---

### Post by Brian96 on 2007-07-30
> **anewguy said:**
> You use your existing Windows partition with VMWare or VirtualBox either one.  From my experience, having tried them both, I would say it is easier to set up in VMWare.  VMWare Server itself is free, and allows you set up your virtual machine quite easily.  Yes, a registration number is required, and that registration number is also free.  With VMWare Server you can set up to use your existing Windows partition right from the GUI, whereas with VirtualBox, I was only able to do it via command lines (there my be a GUI way, but I never found it).  With either, you will want to install the vm tools to the virtual machine you create.

There are some caveats:

- You will need to re-activate Windows even though it is on your existing partition

- If you try to boot Windows stand-alone, you will need to re-activate Windows, which you will need to do again when you go back to the virtual machine.  Microsoft only allows this a few times then they start to wonder what you are up to.

- You will be presented with the boot menu, and if you select anything other than Windows from that menu, particularly if you select Ubuntu again, you will destroy your installation and will need to reinstall everything again.  This selection must be made EVERYTIME you boot.

That's a few that I know from my experience (read as "I did this and these boo-boo's happened").  There is at least 1 moderator on this forum who is an expert on virtual machines and I am sure he will let you know what he thinks on your idea as well as suggestions and caveats he may have.:)

Not to hi-jack, but could you explain your third bullet point again? What boot menu do you mean--GRUB? This is the kind of potential hose-up that scared me from trying this method. I'm not the only one who boots my machine, and I'd hate for somebody else in my family to face killing the system.

---

### Post by anewguy on 2007-07-31
> **Brian96 said:**
> Not to hi-jack, but could you explain your third bullet point again? What boot menu do you mean--GRUB? This is the kind of potential hose-up that scared me from trying this method. I'm not the only one who boots my machine, and I'd hate for somebody else in my family to face killing the system.

Yes - if you have a dual-boot system, you will be presented with the GRUB menu to select which operating system you want to start.  There is a way somewhat around this:  edit the GRUB menu list file and change the default to Windows.  I did this once, and then hated it because I want to use Ubuntu as my main OS, yet if I just let my PC power on and boot up it would go back to Windows.  So it can get to be a catch-22 deciding which way you want to go.

You just need to be very, very aware of what you are doing when you boot your virtual machine using a physical partition.  As an example, if you accidently let it boot your Ubuntu in the virtual machine while you are actually running the same Ubuntu, you can actually mess up the Ubuntu partition so you have to reinstall.  

There are other posts about this - some suggest making the GRUB default timeout something larger - like 30 seconds or more.  Anyway you do it, you just need to be very careful.:)

---

### Post by Brian96 on 2007-07-31
Sorry to belabor the point, but how did selecting Windows in GRUB hose up your system?

I currently run a dual boot XP Home and Ubuntu system (actually triple boot with a partition in which I test other distros). In Ubuntu I also have a VM with XP Pro. I have toyed with using VMWare to run my XP Home partition, but don't fully understand the potential fatal errors that exist with this.

I'd like to have only one Windows on my system. The problem is that there have been times that having a separate setup on bare metal has saved me when I've had issues with Ubuntu. On the other hand it is a pain to reboot to get back to Windows. Anyway, I'm rambling.

---

### Post by hfw on 2007-11-15
I haven' tried this yet, but this is the best link I've found for using VM Ware to boot an existing partition.  It does seem to require VMWar Workstation though, which is not free.

[http://www.vmware.com/support/reference/linux/rawdevices_linux.html](http://www.vmware.com/support/reference/linux/rawdevices_linux.html)

I'd love to know if it works if anybody tries it.

-hal

---

### Post by Duck2006 on 2007-11-15
> **hfw said:**
> I haven' tried this yet, but this is the best link I've found for using VM Ware to boot an existing partition.  It does seem to require VMWar Workstation though, which is not free.

[http://www.vmware.com/support/reference/linux/rawdevices_linux.html](http://www.vmware.com/support/reference/linux/rawdevices_linux.html)

I'd love to know if it works if anybody tries it.

-hal

Thanks been looking for some thing like that for a wile

---

### Post by markharding557 on 2007-11-15
one way to get rid of xps pain in the **** activation is to use a hacked version with your genuine licence'iv'e done this for years for conveinence

---

