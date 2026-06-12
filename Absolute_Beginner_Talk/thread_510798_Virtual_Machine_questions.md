---
title: "Virtual Machine questions"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Zeikcied on 2007-07-27
I have a few questions regarding virtual machines.

1. Is it possible to use a virtual machine to run my WinXP partition?  Or must it be a virtual disc image?

2. If it must be a virtual disc image, is there any way to create such an image from my existing WinXP install?

3. If I happen to use a virtual machine that uses my actual hardware instead of virtual hardware (I'm fairly certain some exist), would it be possible to play Windows games with similar performance as pure Windows?

Thanks.

---

### Post by Koybe on 2007-07-27
I think you should find your first two questions here : [http://ubuntuforums.org/showthread.php?t=380699](http://ubuntuforums.org/showthread.php?t=380699)

For the last, I've never heard of such a possibility, but someone else will answer better then me ;)

---

### Post by anewguy on 2007-07-27
Yes, you can run a VM off an existing partition, so you can run your existing Windows partition.  Be aware of a few things first:

- when the VM boots, it will show your grub menu - if you select the wrong entry, or worse yet it default to your Ubuntu installation, you will hose yourself greatly.  You have to be aware of this EVERYTIME you boot th VM

- Windows will want to re-activate because of the VM "hardware" shows as really changed hardware.

- My experience has been that once you run and re-activate Windows in the VM, you can't go back to just booting Windows without going into safe mode and deleting the VM addons.

- My experience has also been that once you run and re-activate Windows in the VM, it will ask to re-activate if you try to boot Windows alone.  Microsoft get's a little upset about this re-activation business and only wants to allow "x" times before they make life a little difficult for you.

- My experience VMWare Server would be the way to go to this

- Don't expect Windows in a vm to perform like stand-alone Windows, especially in games.  The graphics in the vm's aren't really up to that, yet.

That's my experience.:)

---

### Post by Zeikcied on 2007-07-27
> **Koybe said:**
> I think you should find your first two questions here : [http://ubuntuforums.org/showthread.php?t=380699](http://ubuntuforums.org/showthread.php?t=380699)

For the last, I've never heard of such a possibility, but someone else will answer better then me ;)
Those directions seem a bit complicated.  I guess I could figure it out if I actually read it completely.  But at the first glance, it looks complex.

Anyway, I thought VMs like Xen ran on the actual hardware and didn't virtualize it.

But, I guess I don't really know if any VMs have support for 3D acceleration.  Though it would be nice.

---

### Post by AceofSpades19 on 2007-07-27
if you have a mac you can get VMware Fusion and run 3d games but if you don't have a mac, your outa luck

---

### Post by bodhi.zazen on 2007-07-27
> **Zeikcied said:**
> 3. If I happen to use a virtual machine that uses my actual hardware instead of virtual hardware (I'm fairly certain some exist), would it be possible to play Windows games with similar performance as pure Windows?

Thanks.

Well your performance will be very similar to what you get if you boot a virtual machine (hard drive).

Virtual machines provide virtual hardware so the performance is the same regardless.

If you would like a different how to :

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

---

### Post by Zeikcied on 2007-12-04
I'm bringing up this old thread of mine, because I don't want to make the same mistake I did when I made this.  (See, I had asked the same questions months before I made this thread, but simply forgot about it, and made this thread.)

I'm thinking again about moving my Windows partition to a virtual machine.  I've used Kubuntu exclusively for a year now.  I have two Linux back-ups (the Kubuntu Gutsy LiveCD and a 128 Meg USB thumb drive with a small version of Linux installed on it), so I no longer need Windows in case Kubuntu won't boot.  But I like having Windows, if only because I feel I may need various system32 files for programs installed via Wine.  I know of at least one program where I needed some of those files, but I don't know if they were regular Windows files, or installed by that program when I used it on Windows.

Anyway, I'm looking through the "Comparison of virtual machines" on Wikipedia, and it seems the best options I have are QEMU and VirtualBox.  I'm hoping for two things.  One, that I can make a virtual machine from my current Windows installation (thus being able to delete the partition, but having a virtual clone of the OS), and two, avoid any messy re-activation requests.  Thus, I'd rather have as little hardware virtualization as possible.

I don't know how easy either of these steps are with QEMU or VirtualBox, if even possible at all.  I know for a fact that I cannot use Xen, as I use the non-free NVIDIA drivers, and Xen seems to hate those.

---

