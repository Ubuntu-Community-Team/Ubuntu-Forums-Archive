---
title: "Uhh, quick question on compiling a kernel in ubuntu"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by sheeep on 2006-11-14
The directions for installing linux-wlan-ng-0.2.5.tar.gz tell me to compile a Kernel. I've read a little and see that there are two ways to do it.

One being here, where you download the kernel to the /usr folder

[http://linuxplanet.com/linuxplanet/tutorials/202/1/](http://linuxplanet.com/linuxplanet/tutorials/202/1/)

And another that was mentioned where you can do it off the distribution cd. I haven't found any tutorials detailing this.

Would the above mentioned download-to-folder method work? Any advice? Something better to do?

Thanks.

---

### Post by schrombot on 2006-11-14
You probably won't want to compile a whole new kernel for that one module. Just run ```
sudo apt get update
```and then
```
sudo apt-get install linux-wlan-ng
``` from a command line and you will have what you are looking to install, with all dependancies included.

---

### Post by bodhi.zazen on 2006-11-14
Friends don't let friends [compile kernels](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html)

[HOWTO: Kernel Compilation for Newbie](http://doc.gwos.org/index.php/Kernel_Compilation)

---

