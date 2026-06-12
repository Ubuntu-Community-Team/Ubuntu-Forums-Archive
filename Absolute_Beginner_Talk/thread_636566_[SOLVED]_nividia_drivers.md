---
title: "[SOLVED] nividia drivers"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by watnazn on 2007-12-09
Hey,
I'm a real newb to Ubuntu, i just started using it yesterday. I first got interested because of compiz fusion because it looks good. I have a nvidia fx 5500 (i know its old) and the drivers weren't installed in Ubuntu. I am currently using VirtualBox in Windows Vista and it works very well. My friend told me to install Envy, and that didn't work, or I probly did something wrong. I also tried downloading the driver from the nividia website, but im a newb, so I haven't warmed up to terminal yet.
Can anyone help?
thank you.

---

### Post by nikoPSK on 2007-12-10
install [nvidia-glx-new]("apt:nvidia-glx-new") (click)

---

### Post by FuturePilot on 2007-12-10
Unfortunately Compiz doesn't work in a Virtual Machine.

---

### Post by GSF1200S on 2007-12-10
> **watnazn said:**
> Hey,
I'm a real newb to Ubuntu, i just started using it yesterday. I first got interested because of compiz fusion because it looks good. I have a nvidia fx 5500 (i know its old) and the drivers weren't installed in Ubuntu. I am currently using VirtualBox in Windows Vista and it works very well. My friend told me to install Envy, and that didn't work, or I probly did something wrong. I also tried downloading the driver from the nividia website, but im a newb, so I haven't warmed up to terminal yet.
Can anyone help?
thank you.

As said above me, 3d accel doesnt work in a VM. It doesnt work for us using windows for 3d stuff, and it doesnt work for Ubuntu in a VM.

I believe their are some LiveCD's that will let you try out compiz fusion without installing a Linux OS (check out Sabayon). If you want to dual boot, thats also an option- you would keep windows and install Ubuntu on the side. Alternatively, you can just mess with the other options on Ubuntu in your VM and see how you like it...

Have fun ;)

---

### Post by FuturePilot on 2007-12-10
I believe you can boot the live CD and install the driver. Then you just have to log out and log back in and it should be working. And your hard drive never gets touched.

---

### Post by bumanie on 2007-12-10
I am not an expert on this, but I don't think that nvidia-glx-new will work for your card because, as you say, it is an old card. I think you need to go to the nvidia site and download the driver from this page [http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)  (which for your card should be NVIDIA-Linux-x86-100.14.19-pkg1.run)
You will firstly need to have build-essential installed. To do this go to terminal and type sudo apt-get install build-essential.
Agree to nvidia's terms then download the driver to your desktop.
I have an older card and had to stop x server before I could install the driver, I used the below method.
In terminal type
sudo /etc/init.d/gdm stop --> enter
then cd ~/Desktop --> enter
then sh NVIDIA-Linux-x86-100.14.19-pkg1.run --> enter
then sudo /etc/init.d/gdm start
All going well, your driver should be installed
If this works please mark your post as solved, if there are problems, please post again and someone will try and help.

---

### Post by GSF1200S on 2007-12-10
> **FuturePilot said:**
> I believe you can boot the live CD and install the driver. Then you just have to log out and log back in and it should be working. And your hard drive never gets touched.

Pretty crazy.. I would imagine it just keeps the kernel loaded in RAM and reloads X.. I know I read about Sabayon doing the compiz on Live thing, but im not sure which download version it is or Id post a link...

---

### Post by watnazn on 2007-12-24
Thanks for the replies.

---

