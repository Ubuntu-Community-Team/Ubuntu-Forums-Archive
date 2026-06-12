---
title: "should I change my 386 kernel?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2006-08-25
I don't know much about the kernel but from what I ve read 
on the net:
1. Ubuntu installs the 386 kernel by default
2. 386 a general kernel that covers most cpu's.
3. If I install another kernel I ll boost my performance.

Please tell me which of the above is correct or not and why.
Since 586 seems to cover most cpu's made in the last 5-7 years 
why isn't that the default kernel used?

Also if I can boost the performance which kernel should I install (and how).

I have a laptop with a Pentium M 2.0 Ghz (last summers Centrino platform) and a desktop with a Celeron at 2.4 Ghz (dont have more specs on the Celeron at the moment)

---

### Post by Bachstelze on 2006-08-25
All three sentences are correct. For Pentiums and Celerons, 686 kernel is the way to go but don't expect +20% performance :)

---

### Post by az on 2006-08-25
> **geokok1981 said:**
> I don't know much about the kernel but from what I ve read 
on the net:
1. Ubuntu installs the 386 kernel by default
2. 386 a general kernel that covers most cpu's.
3. If I install another kernel I ll boost my performance.

Please tell me which of the above is correct or not and why.

1. yes
2. yes, well it uses instructions that are common to all x86 CPUs.
3. If you install a kernel that is better suited to your CPU, you will see an improvement, although many people claim it is not noticeable.  I think it is more impressive on older hardware (like a 500 MHz machine)

> **geokok1981 said:**
> 
Since 586 seems to cover most cpu's made in the last 5-7 years 
why isn't that the default kernel used?

Also if I can boost the performance which kernel should I install (and how).

I have a laptop with a Pentium M 2.0 Ghz (last summers Centrino platform) and a desktop with a Celeron at 2.4 Ghz (dont have more specs on the Celeron at the moment)


There are a few CPUs that do not use 686 instructions (VIA C3, for example).  AFAIK, if the kernel was built for 586, the performance would be *worse* than for 386.

Use the 686 kernel for you Pentium and Celeron.

sudo apt-get install linux-686

---

### Post by geokok1981 on 2006-08-25
Sorry to bother once more, but:

1. Isn't 686 for 64 bit cpu?
2. What are the chances of breaking my system?Should I be happy enough 
with 386 and leave things alone?

---

### Post by ewl1217 on 2006-08-25
*1. Isn't 686 for 64 bit cpu?*

No, there are separate 64-bit kernels.


*2. What are the chances of breaking my system?Should I be happy enough with 386 and leave things alone?*

You can install the 686 kernel and keep the 386 kernel. If the 686 kernel doesn't work, then there's the 386 kernel to fall back on.

---

### Post by az on 2006-08-25
> **geokok1981 said:**
> Sorry to bother once more, but:

1. Isn't 686 for 64 bit cpu?
2. What are the chances of breaking my system?Should I be happy enough 
with 386 and leave things alone?

1. no.

2.  It won't break.  You have the right CPU.  And even if you install the wrong kernel, you just have to boot the old kernel (it is added to your grub menu you see at boot time.) and then remove the faulty one.

---

### Post by geokok1981 on 2006-08-25
Ok I am about to try it so one last question (sorry guys!).

I have an ati mobility x700 256mb and i use the drivers from the repos
xorg-driver-fglrx.
Do I have to do anything to get X running after updating the kernel?
Is there something else I have to do afterwards in general?

---

### Post by Drenhead on 2006-08-25
Not trying to hijack your thread, but i am interested in this also.  I tried loading the 686 kernel, but when I boot up with it, my mouse and keyboard don't work.  Am I doing something wrong?

---

### Post by Bachstelze on 2006-08-25
> **geokok1981 said:**
> 
Do I have to do anything to get X running after updating the kernel?
Is there something else I have to do afterwards in general?

Most likely, you will have to reinstall your drivers the same way you did the frst time.

---

### Post by Drenhead on 2006-08-25
I didn't install any drivers.  I just installed kubuntu from the disk and they worked fine.  How can I install the drivers if the keyboard won't work?

---

### Post by geokok1981 on 2006-08-25
Ok people......IT HAS BEEN DONE!!!!
This is what I get at the terminal:

```

~$ uname
Linux
~$ uname -r
2.6.15-26-686

```

Screen resolution is 1400x1050 so I guess I dont have to do anything 
with the vga drivers.I did everything through synaptic.Really excited.
A million thanks for your help!!!:-D

---

### Post by az on 2006-08-25
> **Drenhead said:**
> Not trying to hijack your thread, but i am interested in this also.  I tried loading the 686 kernel, but when I boot up with it, my mouse and keyboard don't work.  Am I doing something wrong?

Install linux-686 and not just the linux-image-686 package.  That brings in the linux-restricted-modules you need too.

---

### Post by az on 2006-08-25
> **Drenhead said:**
> I didn't install any drivers.  I just installed kubuntu from the disk and they worked fine.  How can I install the drivers if the keyboard won't work?

What CPU do you have?  Use 686 for Pentium or Celeron and K7 for AMD.  At boot time, hit escape to reveal the Grub menu and pick a former kernel to boot.

---

### Post by xander848 on 2006-08-25
Hey Im about to install a 686 kernel also (on a pentium M). Im guessing that I will now get 686 kernel upgrages through the update manager right?

And is there any other time when i will need to do anything different ( like choose a specific program version) or can I do this and never really worry about it again?

---

### Post by Bachstelze on 2006-08-25
The only thing you'll have to worry about when changing your kernel is kernel-dependent stuff. Drivers, most of the time.

---

### Post by az on 2006-08-25
> **xander848 said:**
> 
And is there any other time when i will need to do anything different ( like choose a specific program version) or can I do this and never really worry about it again?

You can do that and never really worry about it again.

Once you boot into your new kernel, you can go and delete all the linux-image-386 packages and not install their updates for nothing.

---

### Post by elizleisndahizle on 2006-08-25
If your cpu supports hyperthreading I have read that it is best to install the SMP 686 kernel so the kernel supports the hyperthreading.  Just a suggestion.

---

### Post by Drenhead on 2006-08-25
Here are all the things I have installed for the 686 kernel.  I still can't get my mouse or keyboard to work at all.  Am I missing a package?

---

### Post by geokok1981 on 2006-08-25
I could bet my arm that everything loads faster now....
It should be more obvious to people that there are specific kernels
for their cpu's!!!

---

### Post by az on 2006-08-26
> **Drenhead said:**
> Here are all the things I have installed for the 686 kernel.  I still can't get my mouse or keyboard to work at all.  Am I missing a package?

What CPU do you have?

What kind of mouse and keyboard is it?  That's wierd that it worked at first and then stopped.

---

### Post by Drenhead on 2006-08-26
I have a Pentium IV 3 ghz with Hyperthreading.  The Keyboard came from Dell, and the mouse is a Microsoft wireless mouse.  They both work fine when I boot with the 386 kernel, but stop working as soon as I boot the 686 kernel.

Thanks in advance for all advice.

---

### Post by daou on 2006-08-26
Out of curiosity, is an "apt-get dist-upgrade" necessary/recommended after changing kernels?

I found one computer that I changed to 686 had some instability issues before the dist-upgrade.

---

### Post by az on 2006-08-26
Please boot into your 386 kernel and run

dmesg > file386

and then boot the 686 kernel and then do the same.  Waitaminute!  That won't work since your keyboard is borked!  Hmmm..

Does your keyboard work in recovery mode?

If so, boot into recovery mode and do that

dmesg > file686

and then attach the files to your next post.

It may be easier to use the log tool and look in the Xorg logs to see what is goig on.  You can look at the logs of past sessions if you go back...

---

### Post by Drenhead on 2006-08-26
I am able to boot into the 686 kernel using recovery mode and the mouse and keyboard work.  Here are the files you requested.

---

### Post by az on 2006-08-27
> **Drenhead said:**
> I am able to boot into the 686 kernel using recovery mode and the mouse and keyboard work.  Here are the files you requested.

They are not very telling.

What happens if you boot into the 686 recovery mode and then run

dpkg-reconfigure -phigh xserver-xorg

and then run

init 2

to get back into desktop mode.  I'm thinking Xorg handles your hardware differently with a 686 kernel and that will redetect it.  If that does fix the problem, please report a bug about it.  Be sure to include the working xorg.cong and the not-working one (it is renamed by time and date instead of deleted.

---

### Post by toasted on 2006-08-27
Did you install

Linux-686
or
Linux-686-smp?

The smp version may work better for you if you if you dont already have it

Edit:
If you are going to change... you will have to edit grub manually I think. When I have uninstalled a kernel with Synaptic it did not remove the grub entry anyway.....

---

### Post by az on 2006-08-27
> **toasted said:**
> Did you install

Linux-686
or
Linux-686-smp?

The smp version may work better for you if you if you dont already have it

Edit:
If you are going to change... you will have to edit grub manually I think. When I have uninstalled a kernel with Synaptic it did not remove the grub entry anyway.....

Linux-686 is linux-686-smp.  The linux-686-smp packages exist for legacy reasons.

and you never need to edit grub by hand to add or remove kernels from the list- the package installation/removal does that for you.

---

### Post by toasted on 2006-08-27
> **azz said:**
> Linux-686 is linux-686-smp.  The linux-686-smp packages exist for legacy reasons.

and you never need to edit grub by hand to add or remove kernels from the list- the package installation/removal does that for you.

That is not my experience. I removed the 686-smp kernel and the entry was still in menu.lst. I had to remove it myself. Then when I reinstalled the 686-smp at a later date it did not reinstall itself in the menu, I had to add it back. 

Now, I dont mean to argue here but in Synaptic there are choices of kernels that include Linux-686  and Linux-686-smp  

Is this just due to not being removed yet?  Do I have the wrong one installed?

---

### Post by az on 2006-08-28
linux-686-smp exists for legacy reasons.  It depends on the linux-image-686 and linux-restricted-modules-686 packages.  

There is no linux-image-686-smp package.

---

### Post by toasted on 2006-08-28
I guess I just dont understand then
What is that in my picture in the previous post? I installed it... it works... how can this be if it does not exist?
Please explain as I would like to understand what you mean

---

### Post by az on 2006-08-28
linux-image-2.6.17-6-686 is the package that contains the actual kernel.  The kernel is the file with the kernel image that gets loaded into memory whrn you boot.

linux-image-686 is a package that contains nothing.  It just depends on the latest version of the linux-image-x.x.xx-x-686 package.  Since the version numbers of the kernel can change, you need a package who's version number does not change to bring in those new packages when you upgrade.

The linux-686 package depends on the linux-image-686 package and the linux-restricted-modules-686 packages.  It it undesirable to a lot of people to have those binary-only, proprietary restricted modules on their system.  That's why it's possible to remove the linux-restricted-modules package.  Doing that would remove the linux-686 metapackage, but not the linux-image-686 metapackage.

The linux-686-smp package does not depend on a linux-image-686-smp package because there is none.  The linux-image-686 kernel is already smp.  So the linux-686-smp package points to the linux-image-686 kernel.

---

### Post by toasted on 2006-08-28
> **azz said:**
>   So the linux-686-smp package points to the linux-image-686 kernel.

I understood this part (I think)
No matter which one you select you wind up getting the same package

I will have to read the rest a few hundred times  LOL

Thanks for taking the time!!

---

### Post by Drenhead on 2006-08-30
Well, this is getting frustrating.  I had to reinstall Kubuntu recently and now when I load the 686 Kernel packages, I can't get the keyboard or mouse to work even in the recovery console.  I am attaching a screenshot of what I have installed.  Am I missing a package that I need?

---

### Post by Drenhead on 2006-09-06
I forgot to mention that both my keyboard and mouse are PS/2 type connections, not USB.  Is there something that I need to install to get the PS/2 connections working with the Linux-686 kernel?

Please help!

---

### Post by Omnios on 2006-09-06
Qick note: I could not get lm sensors working with the 386 kernal. However after installing the 686 kernal for my system lm-sensors worked properly

---

### Post by az on 2006-09-06
> **Drenhead said:**
> I forgot to mention that both my keyboard and mouse are PS/2 type connections, not USB.  Is there something that I need to install to get the PS/2 connections working with the Linux-686 kernel?

Please help!

No, there is no reason why it should not work.  PS/2 connections require you plug them in before you boot.  That is a hardware limitation on most motherboards, and has nothing to do with the OS.

---

### Post by Drenhead on 2006-09-06
Hmmm...any other suggestion on what could be wrong?

---

### Post by jd65pl on 2006-09-06
just installed the 686 kernel, it is some improvement on 386 im running an acer 3003lc laptop with AMD Mobile Sempron 3000+ / 1.8 GHz i got 1gig of ram also.

Glad i found this post.

Thanks

J

---

### Post by Drenhead on 2006-09-06
Well, I finally got it working.  I had to disable the legacy USB emulator in my BIOS.  I found the solution after much searching!  Thanks for all help on this.

---

### Post by jd65pl on 2006-09-07
I've read something by the developers  on using different kernels. It went along the lines of changing the kernel makes no difference, it is mostly psychological. There may be only one kernel in Edgy. I'll post the info when I get home and can get to my web history!

J

---

### Post by jd65pl on 2006-09-07
Here is the bit from the developers on the different kernels

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html")

---

### Post by powder on 2006-09-07
Only gentoobies believe that architectural optimizations make a difference. ;)  The only reason I use the 686 kernel is for SMP.

---

