---
title: "Boot from USB?"
date: 2009-04-11
forum: Apple Hardware Users
---

### Post by hachaboob on 2009-04-11
Is there a way to boot from an Ubuntu USB Startup Disk yet?

---

### Post by cyberdork33 on 2009-04-11
> **hachaboob said:**
> Is there a way to boot from an Ubuntu USB Startup Disk yet?
I assume you are on an Intel Mac...?

What exactly are you trying to accomplish? you can boot from USB with grub-efi.

---

### Post by jeyaganesh on 2009-04-12
Should one install software like 'boot camp' to run Ubuntu just through USB? I mean just having Ubuntu in USB instead of installing on Mac. If so I can use Ubuntu in my MacBook Pro and iMac at work.:)

---

### Post by cyberdork33 on 2009-04-13
> **jeyaganesh said:**
> Should one install software like 'boot camp' to run Ubuntu just through USB? I mean just having Ubuntu in USB instead of installing on Mac. If so I can use Ubuntu in my MacBook Pro and iMac at work.:)
Well, you don't really "install" bootcamp...

Check out the Intel Mac FAQ and you will find the section about booting from external devices (booting via EFI). It isn't perfect yet, but it has made a lot of progress.

---

### Post by hachaboob on 2009-04-13
I want to boot from an Ubuntu USB Startup Disk. I have a couple of Mac OS X paritions and an Ubuntu partition. I don't like having to burn CDs because they are too slow.

I am currently using Refit as a bootloader but I will look at grub-efi if it doesn't inconvenience me.

---

### Post by cyberdork33 on 2009-04-13
> **hachaboob said:**
>  I am currently using Refit as a bootloader but I will look at grub-efi if it doesn't inconvenience me.
rEFIt is not a bootloader. You will likely need rEFIt AND grub-efi. and judging from your last post, it is not what you want to deal with.

good luck.

---

### Post by hachaboob on 2009-04-14
I am going to try grub-efi when I can compile it successfully.

checking whether `gcc' generates calls to `__enable_execute_stack()'... configure: error: gcc failed to produce assembly code

---

### Post by cyberdork33 on 2009-04-14
> **hachaboob said:**
> I am going to try grub-efi when I can compile it successfully.

checking whether `gcc' generates calls to `__enable_execute_stack()'... configure: error: gcc failed to produce assembly code
you have to install the build-essential package in order to compile, but the latest binaries are posted in the "Boot via EFI" thread that I pointed you to.

---

### Post by hachaboob on 2009-04-14
I am trying to build it on a mac brother.

---

### Post by pxwpxw on 2009-04-14
> **hachaboob said:**
> I am trying to build it on a mac brother.

Mac OSX libraries wont compile grub2, if thats what you mean. You need linux, or use the binaries.

---

### Post by dmizer on 2009-04-14
Is this what you're looking for? [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by jeyaganesh on 2009-04-15
> **dmizer said:**
> Is this what you're looking for? [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

There, they have only for Windows and Linux machines. From reading other websites, I think it is some what easy to get Ubuntu installed in USB. I have to read more to know how to boot it from Mac.

---

### Post by dmizer on 2009-04-15
> **jeyaganesh said:**
> There, they have only for Windows and Linux machines. From reading other websites, I think it is some what easy to get Ubuntu installed in USB. I have to read more to know how to boot it from Mac.

They also have howtos on creating a bootable USB drive from a live CD.

---

### Post by steffi on 2009-04-18
Yes you can create a bootable USB from a live CD which is what Ubuntu allows but that then needs an addtional customized Boot CD to recognise the USB device you want to boot from.

I'm trying to do the the following and would appreciate anything you can suggest.

I want to boot a kernel on my MacBook Pro that will have CONFIG_IDE_TASK_IOCTL=y defined so that I can use hdparm to erase my Intel X-25M drive and return it to fresh state.

I started by building a USB flash drive from the Live CD but I have yet to be able boot from it since the customized Boot CD doesn't appear to boot for me. I'll probably try this again but I double checked what I was doing and it should have worked the first time.

Once I can boot from my USB Flash Drive I can then build a new kernel that has CONFIG_IDE_TASK_IOCTL=y set and then I'll be able to use hdparm the way I want.

Is there any way to boot Linux over USB without Reefit or an additional Boot CD? 

Can Reefit recognise USB Flash Drives and boot from them?

I'm willing to install Reefit at least temporarily because I know I can easily uninstall it later.


> **dmizer said:**
> They also have howtos on creating a bootable USB drive from a live CD.

---

### Post by pxwpxw on 2009-04-18
> **steffi said:**
> Yes you can create a bootable USB from a live CD which is what Ubuntu allows but that then needs an addtional customized Boot CD to recognise the USB device you want to boot from.

I'm trying to do the the following and would appreciate anything you can suggest.

I want to boot a kernel on my MacBook Pro that will have CONFIG_IDE_TASK_IOCTL=y defined so that I can use hdparm to erase my Intel X-25M drive and return it to fresh state.

I started by building a USB flash drive from the Live CD but I have yet to be able boot from it since the customized Boot CD doesn't appear to boot for me. I'll probably try this again but I double checked what I was doing and it should have worked the first time.

Once I can boot from my USB Flash Drive I can then build a new kernel that has CONFIG_IDE_TASK_IOCTL=y set and then I'll be able to use hdparm the way I want.

Is there any way to boot Linux over USB without Reefit or an additional Boot CD? 

Can Reefit recognise USB Flash Drives and boot from them?

I'm willing to install Reefit at least temporarily because I know I can easily uninstall it later.

If you just want to install and run linux from an external drive, you can do that by installing to the usb and installing gru.efi also to an hfsplus partiton on the usb and booting that.
See the grub.efi bootloader link.s

---

