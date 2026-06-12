---
title: "Automatic Kernel Module Unloading"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by wickwire on 2006-06-01
Hello,

how can I set the system to automatically unload modules once a device using them gets disconnected? When I plug the devices, the modules are loaded, but when I unplug them, the modules remain, in a residual sort of way.

I've searched a lot in the forums, came up with some terms like hotplug, hal, dbus but I'm still unclear about this, they refer the auto-loading of modules, only - could someone point me to the solution, if available?

Thanks!

---

### Post by vidak on 2006-06-02
As far as I know this can be done with recompiling the kernel, if you really feel an urge to have those modules unloaded. :) 
This is a nice howto for compiling:
[https://wiki.ubuntu.com/KernelCompileHowto](https://wiki.ubuntu.com/KernelCompileHowto)
There is an option "Enable module unloading" in the config somewhere...
I'm not sure that the precompiled kernel has this option set or not... But the loaded modules don't really make sense in the computer's speed, I think...

Did I answer your question?

---

### Post by vidak on 2006-06-02
OK, just checked the kernel config:
under
Loadable module support  --->  
you find the following options:

[*] Enable loadable module support   
                             
   [*]   Module unloading       

   [*]     Forced module unloading    

   [*]   Module versioning support              

   [*]   Source checksum for all modules        

   [*]   Automatic kernel module loading

I am not sure which ones are enabled/disabled in the precompiled kernel...

---

### Post by wickwire on 2006-06-02
Thanks a lot for the reply, I'll give it a try! :)

The whole thing started with my USB modem: when I kill pppd, I have to disconnect and reconnect the modem, otherwise pppd won't be able to perform a second connection... I don't know why this is but trying to remedy things, I came up with the steps I have to take:

1- terminate pppd;
2- turn modem off / unplug from usb port;
3- manually unload two modules: usbserial and anydata;
4- manually reload usbserial;
5- plug modem / turn modem on.

Following these steps, the anydata module loads automatically and pppd will establish a successful connection.

However since it's annoying having to do this everytime the connection gets restarted, I am searching for ways to automate the process...

Thanks anyways!

---

### Post by wickwire on 2006-07-08
Uhmm I've built a custom kernel, activated the option but it doesn't solve the "automatic" module unloading bit:

I need some sort of feature that enables to clean up all unused modules, after disabling a device, or in my case, unplugging a USB modem... I've been reading about udev rules and modprobe but I'm not sure where to start...

---

