---
title: "Installing Ubuntu on Acer Laptop - Hangs"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by tarveller on 2006-08-18
I am new to Linux and trying to install Ubuntu on an old Acer Travelmate 512DX.  It has Win 98 SE installed.

I have downloaded ubuntu-6.06-desktop-i386 and burnt a CD.
When I start the laptop with the CD in, the initial Ubuntu screen comes up, and I can start the initial install:
Loading essential drivers ok
Mounting root file system  ok
Moving mount points  ok
Adding live CD user  

Then the screen clears and shows:
Uncompressing Linux... Ok, booting the kernel.

...and then nothing.
Am I missing something? I have found some reference to 'setting flags' with some Laptops, but I don't know where/when/how I would set them.

I would prefer to keep win98 on the machine, at least until I can be confident that I can get Ubuntu running, but it is not essential.

Any advice would be much appreciated.

---

### Post by Jjohn on 2006-08-18
Hi tarveller,
 I think you ran out of memory. You have to consider that ALL of the information  has to be decompresed from the c/d.
I have a newish Acer 1.8mhz proccesser and 512 mg ram the c/d runs for me but it is quite slow. If you think you have plenty of memory just try to reboot and see if the problem repeats check to see if you can see any hard drive activety.
That is as good as I know sorry...;)
Disregard this post I shot without looking at the target first.:mad:

---

### Post by tarveller on 2006-08-18
Thanks - I have since found that I need 128MB RAM to run the live CD - the laptop has 32MB.
Can anyone advise if/how I can install Ubuntu direct (ie not run off CD) if I reformat/partition the hard disk first?
I have found some references to people installing RedHat 7.1 and slackware on an Acer 512DX, but I was hoping Ubuntu would be a simpler option??!?

---

### Post by bodhi.zazen on 2006-08-18
Not .... enough .... RAM....

Your only hope is with the Ubuntu alternate CD and a server install. Then run a light desktop like Fluxbox or Icewm.

---

### Post by Jjohn on 2006-08-18
Redhat (now fedora core) is now way past version 9 and I doubt if you could install a desktop  in any Distro with the amount of memory you have available. If you do choose a server install, beware that all you might get is a command line until you get windows up.

---

