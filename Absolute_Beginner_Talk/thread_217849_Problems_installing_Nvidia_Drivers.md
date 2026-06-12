---
title: "Problems installing Nvidia Drivers"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-07-17
I'm trying to install the [Nvidia AMD64/EM64T Linux Display Driver]("http://http://www.nvidia.com/object/linux_display_amd64_1.0-8762.html").  

I have downloaded the file to my system without any problems.  In the third step it tells me to

> Type "sh NVIDIA-Linux-x86_64-1.0-8762-pkg2.run" to install the driver.

So I went to the terminal and typed in "sh NVIDIA-Linux-x86_64-1.0-8762-pkg2.run", pressed enter but it gives me this:

> sh: NVIDIA-Linux-x86_64-1.0-8762-pkg2.run: No such file or directory :confused:

---

### Post by Jagot on 2006-07-17
It may sound like a stupid question but did you navigate to the directory in which the file is first?

---

### Post by fatsheep on 2006-07-17
> **Jagot said:**
> It may sound like a stupid question but did you navigate to the directory in which the file is first?

No I didn't, how would do I do that?

EDIT: It's on the desktop btw...

---

### Post by Jagot on 2006-07-17
```
cd ~/Desktop
```

---

### Post by fatsheep on 2006-07-17
That command works in the normal terminal, however the nvidia installer gives me an error when it starts up it saying I have to run it as root.  So I go to the root terminal and now the command > cd ~/Desktop gives me the following error:

> bash: cd: /root/fatsheep/desktop: No such file or directory

---

### Post by Jagot on 2006-07-17
Hmm.  Try:

```
cd /home/fatsheep/Desktop
```

---

### Post by cjm5229 on 2006-07-17
> **fatsheep said:**
> I'm trying to install the [Nvidia AMD64/EM64T Linux Display Driver]("http://http://www.nvidia.com/object/linux_display_amd64_1.0-8762.html").  

I have downloaded the file to my system without any problems.  In the third step it tells me to



So I went to the terminal and typed in "sh NVIDIA-Linux-x86_64-1.0-8762-pkg2.run", pressed enter but it gives me this:

 :confused:
 

After you have cd'd to desktop type 
```
sudo NVIDIA-Linux-x86_64-1.0-8762-pkg2.run
``` 
enter your password. 
Whnever you are told that you don't have permissions to do something, you need to sudo.

---

### Post by fatsheep on 2006-07-17
Ok I Cd'd to desktop and typed in the commmand but when I was asked for the password it wouldn't let me type anything in so I just press enter:

> fatsheep@fatsheep-desktop:~$ cd /home/fatsheep/Desktop
fatsheep@fatsheep-desktop:~/Desktop$ sudo NVIDIA-Linux-x86_64-1.0-8762-pkg2.run
Password:
Sorry, try again.
Password:


I should have mentioned in my last post that when trying to install the AMD64/EM64T Drivers I got this message:

> ERROR: this .run file is intended for the
Linux-x86_64 platform, but you appear to be
running on Linux-x86.  Aborting installation.


So which drivers should I try to install now?  Here are the two linux choices (excluding AMD64/EM64T): 

[LIST=1]
[*]IA32
[*]IA64
[/LIST]

---

### Post by digby on 2006-07-17
The driver thinks that you installed the 32-bit version of Ubuntu... did you?   Or is that an error?

---

### Post by Dinerty on 2006-07-17
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Step by step guide which works to install nvidia driver mate

---

### Post by fatsheep on 2006-07-17
> **digby said:**
> The driver thinks that you installed the 32-bit version of Ubuntu... did you?   Or is that an error?

Yea I installed the x86 version.

> **Dinerty said:**
> [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Step by step guide which works to install nvidia driver mate

Thanks, I followed the instructions there, now how do I tell if the driver is installed?

---

### Post by Jagot on 2006-07-17
> **fatsheep said:**
> now how do I tell if the driver is installed?

Issue this command in Terminal:

```
glxinfo
```

Near the beginning of the results should be the line that starts 'Direct Rendering'.  If it says Yes then it is installed.  If you haven't done so you'll need to restart the computer before the graphics driver will take effect.

---

### Post by fatsheep on 2006-07-17
I have already restarted and still get:

> direct rendering: No 

:confused:

---

### Post by Dinerty on 2006-07-17
There is a piece of code you can put in the terminal which displays it, however I don't know it, but you can go your 

System Settings > Display > Hardware, there it should say nvidia

Also in System > KinfoCenter , then check your graphics settings, should say something about your card and driver

---

### Post by fatsheep on 2006-07-17
I'm running a dual boot so when I start up I get these operating system options:

> 
ubuntu, kernel 2.6.15-26-k7
ubuntu, kernel 2.6.15-26-k7 (recovery mode)
ubuntu, kernel 2.6.15-26-386
ubuntu, kernel 2.6.15-26-386 (recovery mode)
ubuntu, kernel 2.6.15-23-286
ubuntu, kernel 2.6.15-23-286 (recovery mode)
ubuntu, memtest 86+

Other Operating Systems:

Microsoft Windows XP Home Edition


This seems a bit fishy, why are there three different kernels?  Perhaps this has something to do with my problem?


> **Dinerty said:**
> There is a piece of code you can put in the terminal which displays it, however I don't know it, but you can go your 

System Settings > Display > Hardware, there it should say nvidia

Also in System > KinfoCenter , then check your graphics settings, should say something about your card and driver

There is no System Settings and there is no "Display" menu under System>Preferences or System>administration. :confused:

---

