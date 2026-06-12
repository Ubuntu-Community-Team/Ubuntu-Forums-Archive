---
title: "Too many Ubuntus"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Link360 on 2007-03-18
When my system boots up and it gives me the option of which operating system i want to use (Ubuntu or Windows XP) I have 3 different Ubuntu options. They look like this

Ubuntu,Kernel 2,6.15-28-386
Ubuntu.Kernel 2,6.15-27-386
Ubuntu.Kernel 2,6.15-26-386

I think it may because of the "sudo apt-get dist-upragde" command but im not sure. I did it once when following a tutorial to install beryl. I think thats when the second one came up. Then i did it again yesterday because i hadnt been on ubuntu in a while so i wanted to get everything updated. Thats when the third Ubuntu option came up. Here are the questions....

Is this because of the "sudo apt-get dist-updgrade" command?
What exactly does that command do?
Can I delete the two options I dont need?
If its not because of the "sudo apt-get dist-upgrade" what is it?

Thanks for your help.

---

### Post by foots2015 on 2007-03-18
These automatically show up when you upgrade to a new kernel version. Yes they can be removed, but i don't know how.

---

### Post by fjf314 on 2007-03-18
The following link will show you how to only have one of the kernels displayed in the GRUB menu.

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_display_only_one_kernel_on_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_display_only_one_kernel_on_GRUB_menu)

Note that this will *not* actually remove the older kernels, they just won't show up in the list.  If you want to remove older kernels, you can use the following commands.  Also note that it's recommended that you keep at least one older kernel as a backup:

```
ls /boot/vm*
rm <oldest kernel>
```

---

### Post by Sam Clemens on 2007-03-18
That's a really bad way to remove a kernel that's been installed as a package.  Much better would be to 

 dpkg -l linux*

in a large term and apt-get remove the packages by name.

Or use Synaptic to do it without resorting to a terminal.

This will probably update the grub menu anyway, without manual fiddling.

It's important not to remove your running kernel of course.

---

### Post by fjf314 on 2007-03-18
I'll keep those in mind.  I found the method I listed via Google a couple of months ago and used it, I didn't realize there was a better way.  Thanks for the heads up!

---

### Post by Sam Clemens on 2007-03-18
No problem. The rm method will remove the kernels and grub will notice but it will leave all the modules and other stuff in /lib/modules/kernelversion.  It'd be worth opening up Synaptic and removing your old kernels/modules.

---

### Post by lamer1 on 2007-03-18
Greetings,

I always remove old kernels when I verify that the new one i working properly therefore, I've decided to write a simple tool that lists installed kernels and allows me to remove. This tool just reads /boot/grub/menu.lst and extracts installed kernel skipping (recovery mode) ones and non Ubuntu kernels.
It makes a list and displays it. It calls apt-get --purge -y remove selected-kernel to remove the kernel.
I've used it on my Feisty Ubuntu and it removes the kernels. Not sure about others.

It is written in Java.

to run

tar -xvf kernel.tar.gz

java kernel.KernelRemover

to compile

javac kernel/KernelRemover.java

Hope it's useful

---

