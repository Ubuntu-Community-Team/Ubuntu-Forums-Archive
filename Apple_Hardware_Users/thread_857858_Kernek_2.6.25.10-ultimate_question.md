---
title: "Kernek 2.6.25.10-ultimate question"
date: 2008-07-12
forum: Apple Hardware Users
---

### Post by guzzos on 2008-07-12
Hello, I have just installed the new kernel 2.6.25.10-ultimate along with the mactel-patches.  Everything looks fine but when I invoke System Monitor it only shows one cpu.  Is it ok? or something went wrong during compile?

I have a MacBook 4,1 running Ubuntu Hardy 8.04. 2GBRan 160GB Hard Disk

Thanks for any info.

---

### Post by pravinbravi on 2008-07-13
Hi,

Can you give a small how-to on the mactel patch for this new kernel.  I would wanna try it. Coz my backlight and other sensors don't seem to work out of the box in the current configuration of Hardy.

Thank you,

Pravin

---

### Post by guzzos on 2008-07-13
Well, the information needed to get the mactel-patches came from here:
[http://ubuntuforums.org/showthread.php?t=442941](http://ubuntuforums.org/showthread.php?t=442941)

1.  Follow steps 9 and 10 of the above link and hopefully you will have the patches in place, which is '/usr/src/mactel-patches-2.6.25'. The existence of those patches tells me that the 2.6.25 kernel needs these patches for the macbooks, but I am not sure, maybe the new kernel is just enough.

2. Download and install the program KernelCheck Hopestar from [http://kcheck.sourceforge.net/]("http://kcheck.sourceforge.net/")

Once installed, run it and click on 'Get Kernel Information'. It will tell you what version of kernel you are running and which is the latest version available from [www.kernel.org](www.kernel.org). 

3. In the 'New Kernel Patch Options', select 'custom patch'

4. Then click on the 'Program' tab in the upper corner and select the 'Build New Kernel' option. 

5. The program will start to get and compile your new kernel, and at some point, it will stop and open a terminal window which you will use to apply your mactel-patches. I had to apply the patches one by one using 'patch < /usr/src/mactel-patches/2.6.25/<patchname.patch> -p1', since the apply command described in point 11 from the original guide does not works for me.

6. Once you have finished applying your patches 'exit' the terminal window with the 'exit' command, then the program will continue and finish compilation in about 2 hours. This is the time it took on my MacBook 4,1.

This kernel runs faster in my machine than the generic one I was using. Maybe it is just because it was compiled on my machine and probably I would get the same performance speed compiling a previous version.

I hope this little guide serves you.  Since I am a newbie in patching kernels, I am not sure if the patching I did was correct, but after restarting my machine everything looks fine.

Good luck!

---

### Post by master_kernel on 2008-07-14
Are you sure multi-threading was enabled in your kernel configuration?

---

### Post by guzzos on 2008-07-14
Well is nice to know about you.  First of all I want to congratulate you for such an exceptional program (KernelCheck).  

Since I am a newbie I don't know how to enbable mutli-threading in the kernel configuration.  Can you show me how to do it or point me where to go.

My hardware is a MacBook 4,1 with the Broadcom 43xx rev(3)
My big frustration is not having WiFi with WPA2 on this machine.

Thanks,

---

