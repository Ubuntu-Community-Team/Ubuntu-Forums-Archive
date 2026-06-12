---
title: "Does ubuntu work with 4GB memory?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by videocheez on 2008-04-10
I have been using Ubuntu for nearly a year on 3PC's.  I started with Fiesty and am now running Gutsy. The comp that I am having troubles with is my main box a dual boot XP pro system.  I recently increased my memory from 2GB to 4GB.  XP is cool with it and I have had no problems. Ubuntu is very sluggish and wont even load all the way.  If i take the memory out and try load ubuntu again, everything works fine. Is there any thing that I can set-up while its working with 2GB to work fine when I use 4GB.  What do you think is going on.  Has anyone heard of this problem.  When is the new release due?  Perhaps the problem will go away in the next update.

Thanks in advance,

VC

---

### Post by UpSignal on 2008-04-10
hum, that's one question i would like to know either. i'm planning to increase my laptop to 4 GB

---

### Post by thisismalhotra on 2008-04-10
How are you upgrading to 4gb, you know you should always have pairs, so if you are upgrading use 2 X 2gb sticks or 4 X 1gb sticks..

On other note, XP actually is using only 3.2 - 3.5  gb of your 4gb memory and any 32 bit OS would do the same. If you really want to use 4gb memory you will have to upgrade to a 64 bit system...

I know of cases of people using XP and vista, in which there computer would slow down after upgrade to 4gb.

HTH, or else keep posting

---

### Post by clarknova on 2008-04-10
Hardy is due out in 14 days. I've been using the beta and my personal experience is that it so far has fewer problems than even the initial release versions of feisty and gutsy.

As for your memory problem, I can only speculate it has something to do with the memory addressing limit of 32-bit operating systems. Although XP runs fine with 4 GB, it is likely that only 3.2GB or so is usable. This is an inherent limitation of 32-bit OSes, be they windows, linux or otherwise.

If you're thinking of upgrading to hardy, why not try a 64-bit install? There's been lots of discussion of 32 v 64 bit, but the drawbacks to 64 bit are fading fast. The only wrangling I've had to do on mine is to tell the package manager to ignore the architecture mismatch when installing my printer drivers and lightscribe software. Even flash and java are a non-issue, they just work. And if you want to use all of your 4 GB of RAM, then a 64-bit OS is your only option.

db

---

### Post by warp99 on 2008-04-10
Ubuntu 32-bit can use up to 4GB of memory. If you want to use **more** than 4GB of memory then you need to install the 64-bit version. The desktop kernel according to this thread does not support 4GB:

[http://ubuntuforums.org/showthread.php?t=574494](http://ubuntuforums.org/showthread.php?t=574494)

But you can compile a new kernel that will support this limit or use the server kernel, but the server kernel does not include some modules that may be needed for certain desktop functions.

---

### Post by lolzlolz on 2008-04-10
im using 4gb in hardy beta, but they also worked in gutsy and feisty
just make sure you're using the 64bit version

---

### Post by bodhi.zazen on 2008-04-10
If you have the proper hardware (motherboard) the PAE kenel will support up to 64 Gb RAM (on i386)

[http://www.cyberciti.biz/tips/redhat-enterprise-linux-4gb-plus-ram-support.html](http://www.cyberciti.biz/tips/redhat-enterprise-linux-4gb-plus-ram-support.html)

In ubuntu , use the server kernel, you may need to compile your own 

[http://www.enterprisenetworkingplanet.com/netos/article.php/3710641](http://www.enterprisenetworkingplanet.com/netos/article.php/3710641)

The ubuntu server kernel is compiled with PAE support

[http://www.serverwatch.com/tutorials/article.php/3715071](http://www.serverwatch.com/tutorials/article.php/3715071)

> The 32-bit server kernel supports up to 64 GB of memory

You can run desktop applications on the server kernel (Gnome / KDE / XFCE / Fluxbox ) or recompile your own kernel.

---

### Post by stchman on 2008-04-10
> **videocheez said:**
> I have been using Ubuntu for nearly a year on 3PC's.  I started with Fiesty and am now running Gutsy. The comp that I am having troubles with is my main box a dual boot XP pro system.  I recently increased my memory from 2GB to 4GB.  XP is cool with it and I have had no problems. Ubuntu is very sluggish and wont even load all the way.  If i take the memory out and try load ubuntu again, everything works fine. Is there any thing that I can set-up while its working with 2GB to work fine when I use 4GB.  What do you think is going on.  Has anyone heard of this problem.  When is the new release due?  Perhaps the problem will go away in the next update.

Thanks in advance,

VC

32 bit OS can theoretically address 4GB of memory as 2^32 = 4GB.

If you want to fully utilize 4GB then the 64bit OS is your best choice.  I personally don't see a need for over 1GB of RAM with Ubuntu as it and it's apps are so efficient.

---

### Post by bodhi.zazen on 2008-04-10
> **stchman said:**
> 32 bit OS can theoretically address 4GB of memory as 2^32 = 4GB.

If you want to fully utilize 4GB then the 64bit OS is your best choice.  I personally don't see a need for over 1GB of RAM with Ubuntu as it and it's apps are so efficient.

There is 32 bit hardware that can support up to 64 Gb RAM. See my post just above yours.

You need to have the proper hardware though (not all 32 bit processors / motherboards will support this much RAM).

The primary reason for high RAM would be servers, particularly virtual servers.

---

### Post by stchman on 2008-04-10
> **bodhi.zazen said:**
> There is 32 bit hardware that can support up to 64 Gb RAM. See my post just above yours.

You need to have the proper hardware though (not all 32 bit processors / motherboards will support this much RAM).

The primary reason for high RAM would be servers, particularly virtual servers.

Not talking about hardware, I am taking of software.  A 32 bit OS can only directly address 4GB of memory at a time.

If I remember correctly there are ways to somewhat utilize >4GB with a 32bit OS, but I am not an expert in those matters.

---

### Post by bodhi.zazen on 2008-04-10
Memory is managed by the kernel

[http://kerneltrap.org/node/2450](http://kerneltrap.org/node/2450)

You may need to configure grub :

[http://howtoforge.com/make-your-xen-pae-kernel-work-with-more-than-4gb-ram-debian-etch-grub](http://howtoforge.com/make-your-xen-pae-kernel-work-with-more-than-4gb-ram-debian-etch-grub)

Again the main reason this is done is for virtualization or servers, ie virtual machines are in the RAM (XEN). Obviously "normal" desktop users do not use even 1Gb RAM in Linux, let alone 64 Gb.

---

### Post by philinux on 2008-04-10
> A 32 bit OS can only directly address 4GB of memory at a time

Not true microsoft solved this in windows 2000 server edition it can access lots more ram, memory fades as to how much. No pun intended. It uses 36 bit I think.

---

### Post by clarknova on 2008-04-10
Yes, both windows and linux can be made to use more that 4GB of RAM, but HIGHMEM has it's limitations and is less desirable than running native 64-bit. If you want to take advantage of HIGHMEM then, as stated above, you'll need to use a kernel that was compiled with support, i.e., the server kernel or one you've compiled yourself.

On the other hand, installing amd64 will actually take less time and give you less hassle in the long run. Yeah, we could sit and discuss the intricacies of getting more memory into 32-bit software, but Ubuntu-64 is great. Forward, brethren, always forward.

db

---

### Post by videocheez on 2008-04-15
> **bodhi.zazen said:**
> Memory is managed by the kernel

[http://kerneltrap.org/node/2450](http://kerneltrap.org/node/2450)

You may need to configure grub :

[http://howtoforge.com/make-your-xen-pae-kernel-work-with-more-than-4gb-ram-debian-etch-grub](http://howtoforge.com/make-your-xen-pae-kernel-work-with-more-than-4gb-ram-debian-etch-grub)

Again the main reason this is done is for virtualization or servers, ie virtual machines are in the RAM (XEN). Obviously "normal" desktop users do not use even 1Gb RAM in Linux, let alone 64 Gb.
Thanks for the advice.  Finally some one is pointing me in a direction that looks viable.  Every time I have previously posed this question, the thread always migrated towards the discussion that windows or 32bit OS's can only see 3.2GB of memory.  Do you have any ideas of what to set up in grub to utilize max memory 32bit OS allows? I just don't want remove memory every time I boot Ubuntu.

Thx in advance,

VC

---

### Post by bodhi.zazen on 2008-04-16
You have to install the server kernel and re-compile grub. See the link on Xen.

---

### Post by videocheez on 2008-04-16
> **bodhi.zazen said:**
> You have to install the server kernel and re-compile grub. See the link on Xen.
Ok.  This sounds a little bit scary but I am willing to try so that I can use Ubuntu again.  
This however is my problem and this is where I need a bit of advice.  With 4GB of memory in my computer, Ubuntu fails to completely load and is nearly unresponsive.  With 2GB memory, Ubuntu loads just fine.
Do you suggest that I load Ubuntu with 2GB memory make the grub changes, turn off my computer, put in 4GB then restart to see if the grub fix works?  Will changing grub screw up my dual boot set-up?  When I first installed Ubuntu a year ago, it took me a month to set up dual boot with my set-up and I have not wanted to mess with grub since.  Please let me know answers to these questions when you get a chance.

Thx in advance,

VC

---

### Post by clarknova on 2008-04-19
I'm not sure why you would have to recompile grub. update-grub wouldn't do the trick? Even if I'm wrong on that point you don't really have anything to lose by installing the server kernel and attempting to boot from it. If the new kernel really cripples your system then just reboot and select your old kernel from the grub menu and you're back in shape.

If you install the server kernel via apt-get or synaptic it will automatically update grub to include the new kernel in the grub boot menu. It really shouldn't kill your dual-boot setup at all, and although I've been wrong before (and it is getting late here ;^), I just don't see any need to do anything fancy like compile things or put your setup at risk (assuming the server kernel works for you--if not, then get ready to learn how to compile a kernel. (It's not that bad)).

And yes, do the server kernel install while running on 2GB of RAM, then go back to 4GB when it's time to reboot and test.

db

---

### Post by bodhi.zazen on 2008-04-19
In a nut shell, the version of grub in the ubuntu repos was compiled without enabling the option to boot to high memory. See the Xen link for details.

I can not confirm this at the moment, I do not have the hardware.

---

### Post by videocheez on 2008-04-22
> **clarknova said:**
> I'm not sure why you would have to recompile grub. update-grub wouldn't do the trick? Even if I'm wrong on that point you don't really have anything to lose by installing the server kernel and attempting to boot from it. If the new kernel really cripples your system then just reboot and select your old kernel from the grub menu and you're back in shape.

If you install the server kernel via apt-get or synaptic it will automatically update grub to include the new kernel in the grub boot menu. It really shouldn't kill your dual-boot setup at all, and although I've been wrong before (and it is getting late here ;^), I just don't see any need to do anything fancy like compile things or put your setup at risk (assuming the server kernel works for you--if not, then get ready to learn how to compile a kernel. (It's not that bad)).

And yes, do the server kernel install while running on 2GB of RAM, then go back to 4GB when it's time to reboot and test.

db

It worked. :) Thanks for the suggestion.  Ubuntu lives.  I was able to install the server via synaptic as you suggested and I did not have to fool with the complicated task of compiling.  Now when the Ubuntu update comes out in a few days, should I install the server version?

---

### Post by clarknova on 2008-04-22
> Now when the Ubuntu update comes out in a few days, should I install the server version?
Don't install the server version. I mean, you could, but then you would boot into a text login and have to install a bunch of packages from there to get back to your desktop. If you're going to do a fresh install of hardy, just install the desktop version and then use synaptic to add the server kernel from there. You may have to go back to 2GB of RAM to get to that point.

On the other hand, why do a fresh install when you can just upgrade? When 8.04 is released synaptic should offer to upgrade you to the new release. This will save you reformatting everything and losing all your files and settings, and you won't have to open your case to fiddle with RAM.

That said, I have had issues on a couple machines upgrading to hardy beta from 7.10 and 6.06 where my xserver wouldn't configure correctly after the upgrade. I know somebody who had the same issue and he worked it out. Me, I just reinstalled fresh, but then my /home directory is on a separate partition so I don't stress too much if I have to format the root directory. Sometimes it's just easier than chasing upgrade bugs.

db

---

