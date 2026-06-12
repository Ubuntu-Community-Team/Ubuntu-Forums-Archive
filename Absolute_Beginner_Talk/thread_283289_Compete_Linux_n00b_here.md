---
title: "Compete Linux n00b here"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by ryodoan on 2006-10-24
I want to start off by saying I am sorry if I repeat stuff found in other threads in the forum, but I did do some searching and came up empty, this thread is the culmination of a series of frustrating failures.

To start off with I have installed Ubuntu Linux 6.06 (LTS).

Problem #1:

I have an eMachine that has onboard graphics, but also has an aftermarket nVidia GeForce fx 5500 PCI 128 mb video card (yes, that is straight up PCI card).  I have no idea how to install the drivers for this, so I am running off onboard graphics right now, not a bid deal but switching hte moniter cables between a windows boot up and a linux boot up is a little annoying.


Problem #2:

I am currently in college and my dorm requires us to use Cisco Clean Access agent to login if you have a windows computer. This is a network program the runs on your computer and lets you connect to the network, really anoying.  If you have linux or a mac you apparently need to log into a website instead.  This would not really be a problem except when it tries to redirect me to the site firefox gives me this error: > you have recieved an invalid certificate. Please contact the server administrator or email correspondent and give them the following information: Your certificate contains the same serial number as another certificate issued by the certificate authority. Please get a new certificate containing a unique serial number.

So I cant connect to the internet to trouble shoot the problem even.


Problem #3:

When using the ethernet cable to connect to the dorm network failed, I decided to try and connect to the schools wireless which for some reason doesnt require the special clearance. But I soon realized I had another problem.  I have a wireless USB dongle from netgear (54 mbps Wireless USB 2.0), however I dont have drivers and i couldnt get it to work correctly... ubuntu recognized that i had a wireless device connected but wouldnt connect to anything, this could just be my ignorance of the operating system acting up though...

Thanks for any help that can be given, please be gentle.... I am a complete noob at linux...

---

### Post by meng on 2006-10-24
1. I wonder if you could start off by disabling the onboard graphics in your BIOS. Then Ubuntu can start the X server using the 'nv' driver (you may need to run "sudo dpkg-reconfigure xserver-xorg" to select the 'nv' driver, and subsequently you can install nvidia drivers (search the forums for tips).

2, 3. I don't know.

---

### Post by po0f on 2006-10-24
ryodoan,

I can only help with the first problem (I own the same board, doesn't PCI suck? :)).

You will most likely have to add *agp=off* to your boot options.  For some reason Ubuntu's kernels haven't liked my video card being on the PCI bus, and between doing this or booting from the onboard video to install, I chose this.  You will have to edit /etc/modprobe.d/blacklist and add two entries:
```
blacklist intel-agp
blacklist agpgart
```

This prevents the problematic modules from being loaded at boot time.

Now to get the driver, you will have to install [this package](http://packages.ubuntu.com/dapper/x11/nvidia-glx) to get NVIDIA's binary, proprietary driver (I think you have to enable the universe repositories to get this package).  The page I linked to says you have to run this command to enable it:
```
$ sudo nvidia-glx-config enable
```

I just manually edited my xorg.conf and switched out "nv" for "nvidia".

---

### Post by towsonu2003 on 2006-10-24
> **ryodoan said:**
> 
Problem #2:

I am currently in college and my dorm requires us to use Cisco Clean Access agent to login if you have a windows computer. This is a network program the runs on your computer and lets you connect to the network, really anoying.  If you have linux or a mac you apparently need to log into a website instead.  This would not really be a problem except when it tries to redirect me to the site firefox gives me this error: 

So I cant connect to the internet to trouble shoot the problem even.


I used to have the same problem with umbc's wireless network. the second step below (accept certificate temporarily after cleaning the cache and restarting Firefox) solved my problem. 

I would first try to to go to that site after restarting firefox and cleaning the cache. second, I'd try going there with a new profile. when it asks if you wanna accept the certificate (if it does), choose "accept *temporarily*" (*not* indefinitely). If that doesn't work, send an email to the IT department of the school to report the problem. Don't forget to tell them
1. what is the exact problem
2. what is your hardware (give model of computer) and software (tell them you're using Linux and Firefox)
3. which steps did you try to solve this problem

Also, *very* *very* *very* gently remind them that the current problem is denying you access to a network you have the right to connect. again, very gently :mrgreen: 

If they deny your request, well than it's up to you if you wanna take that to a higher place in your school's bureaucracy. 

In the meantime, if you really need to connect, you could use ie4linux (good thing it exists) to run Internet Explorer (ew) to connect to their network.

PS. File a bug report to the appropriate version of your running kernel (package name is linux-source-2.6-xx, to get the "xx" part, run uname -r from cli) at [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

Without bug reports, there is no way the developers will know that your specific hardware isn't running out of the box (except if they are using it too, in which case you'd be extremely lucky).

---

