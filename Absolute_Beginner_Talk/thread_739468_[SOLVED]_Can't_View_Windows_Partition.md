---
title: "[SOLVED] Can't View Windows Partition"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by azurepancake on 2008-03-29
I've recently installed Ubuntu on my Toshiba P206-S6307 and everything is working just dandy. But there is one single issue I am having and that is, I can't find the files on my Windows XP Pro partition. As you can see, I am dual-booting with Ubuntu Gutsy and Windows XP Professional.

 I had Ubuntu installed on my desktop once in the past with the same dual-boot setup. I was then able to access my Windows partition by going to /media/sda1 or something similar. When I do this on my laptop, I have the /media/sda1 subdirectory, but there is nothing in the sda1 folder. I know Windows is present and working, I can boot into it from Grub with no problems.

Any idea on what I can do to somehow view my Windows partition? I'd greatly appreciate any advice. Thanks!

---

### Post by Daveth on 2008-03-29
sound like the windows partition is not being mounted. This guide tells you how to fix it- not too tricky to follow:)

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by azurepancake on 2008-03-29
Thank you very much for the link. I followed the instructions and ran into an issue. After creating the /windows directory and editing the /etc/fstab file, I attempted to run sudo mount -a, in which the following response occurs: 

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /windows ntfs-3g defaults,force 0 0

I'm not quite sure what to do from here. Any ideas?

Thanks again

---

### Post by azurepancake on 2008-03-29
Excellent! I have it up and working now.

While reading another post I was reminded that the last time I accessed Windows, it did not shut down correctly due to my laptops dieing battery. So I went in and properly reboot it, loaded Ubuntu and ran sudo mount -a. 

It works now!

Thanks very much for your assistance.

---

### Post by Daveth on 2008-03-30
no problem, glad you got it sorted.

---

