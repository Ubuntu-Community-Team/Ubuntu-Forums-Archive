---
title: "Why can't I install Ubuntu, driving me crazy!"
date: 2007-04-05
forum: Apple Intel Users
---

### Post by wisammy on 2007-04-05
Ok, I've tried several different ways of installing Ubuntu 6.10 

I have a macbook first gen with 1gb of ram

The live disc works fine, I am using Parallels for OSX to run Ubuntu. I install and it seems to work fine, the first time I put Ubuntu on my external HD, once I install and try to run it for my first time, the screen just goes black. never loads

So then I thought maybe it was an issue with having Ubuntu on an external drive, so now I have it on my main internal drive, I run the live disc, install, same problem, black screen and nothing ever happens..


what do i do!!!!

thanks!

---

### Post by phidia on 2007-04-05
I'm wondering if somehow there's a problem with fbdev output.

Does the system/hard drive sound like it's booting up? An indication of that might be the numbers lock light lighting up or a usb mouse's led light coming on.

Ahhh forget all that and check out post # 25 from this thread: [http://ubuntuforums.org/showthread.php?t=233243&page=3](http://ubuntuforums.org/showthread.php?t=233243&page=3)

---

### Post by wisammy on 2007-04-05
I don't see how post #25 relates to my problem... I am seriously feeling like there is no way to get ubuntu running on my mac, this is a bummer :(

---

### Post by Chrisj303 on 2007-04-06
Right, so your trying to Dualboot? If YES then check this out :

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Follow it to the TEE and you'll be fine.!

It's important that you read through the guide over and over before you begin, make sure you understand what your doing. I was a little gung-ho on my first attempt and hosed it all up!
Also, if you think you may want to install windows as well in the future, then your probably better of taking the plunge and doing a TripleBoot.
Once youve installed ubuntu, you can't install windows very easily at all.

Good luck,
chrisj303

---

### Post by cyberdork33 on 2007-04-06
Guys, he is trying to install ubuntu in parallels.

I suggest using VMWare Fusion Beta if you want a VM. It is much nicer with linux. I think the solution to getting Ubuntu to work in Parallels has something to do with the amount of RAM in the VM (Too Much makes it go to the black screen). You'll have to check around though for sure. I know I saw it in the forum somewhere.

---

### Post by Chrisj303 on 2007-04-06
Oh Sorry!, my bad!  - ehm, in that case - have you tried installing the OS from the .ISO? I'd try that first. If that fails then definitely try VMware Fusion Beta - i installed ubuntu feisty 64-bit edition just a couple of days ago with no hassle whatsoever - i can vouch for that one personally.
It may also be worth re-downloading the OS - it may just be corrupt.  I'm using the pretty much the same hardware as you, the only real difference is the RAM - i'm using 2gb's, but i'm damn sure that won't make a bit of difference.

Good luck, and sorry for the confusion!

chrisj303

---

### Post by wisammy on 2007-04-06
I actually got it running, it had to do with the amount of Ram I allocated.. I had to much I guess 256 is the most you can use... my problem now is that it is not using the whole screen, it doesn't seem like a resolution issue, its as if ubuntu thinks I have a 12 inch monitor or something... any ideas?

---

### Post by m2cconsulting on 2007-04-17
im having a similar problem with ubuntu on parallels on windows xp. it worked until i downloaded about 200 mb of updates (once it was installed) and now when i boot paralles i just get a blank screen. what gives?

---

### Post by mscman on 2007-04-18
> **wisammy said:**
> I actually got it running, it had to do with the amount of Ram I allocated.. I had to much I guess 256 is the most you can use... my problem now is that it is not using the whole screen, it doesn't seem like a resolution issue, its as if ubuntu thinks I have a 12 inch monitor or something... any ideas?

While I'm not sure about your RAM issue (i have ~300Mb allocated on my machine, same specs as yours), the fullscreen problem is in fact a resolution issue. For some reason, Ubuntu defaults to a 1024x768 resolution no matter what. I wish it would automatically detect for the gfx card or at least provide an option in the installer, but we'll just have to wait for that.

In the meantime, you can get your full 1280x800 resolution by editing the xorg file either manually or by running the dpkg-reconfigure command as follows:
```
sudo dpkg-reconfigure xserver-xorg
```This command will send you to an xorg configuration screen. Just accept the default settings until you get to a screen with a lot of resolutions listed. Highlight the 1280x800 setting and press the spacebar to activate it. Then continue through the dialogue until it asks to write the changes and allow it to do so. You'll then have to restart the virtual machine or press ctrl+cmd+delete to restart the xserver.

One important thing to note about the xorg configuration utility is that you may need to use the TAB key to select OK if the scrollbar is highlighted. Let me know if you have any issues understanding what I just said :)

---

### Post by julianbond007 on 2007-04-20
I wanted to ask any of you which download did you use to install ubuntu on your MacBooks? I am also running parallels with Vista installed.

---

### Post by mscman on 2007-04-20
> **julianbond007 said:**
> I wanted to ask any of you which download did you use to install ubuntu on your MacBooks? I am also running parallels with Vista installed.
I'm using the alternate install disc for x86 machines, same disc to do a native install on a macbook.

---

### Post by Gipetto on 2007-04-20
For what its worth - I too ran into the 256mb Ram limit issue...

---

### Post by dr.wong on 2007-04-20
Hey everyone, today I decided to finally join the Linux community, so I have downloaded the Ubuntu version!

Yay for me!! haha

I have a core duo 20" iMac running Parallels, I DO NOT have windows on my machine!

I am trying to intall ubuntu (Feisty Fawn) with Parallels, but when I go through the setup process it does not give a kernel or version for Ubuntu! Which one should I choose??
 
(I downloaded the ISO which is on my Mac's HD)

Options : 
Red Hat
Debian
Fedora
SUSE
Mandriva
Xandros
Other Linux Kernel 2.4
Other Linux Kernel 2.6
Other Lunux

I have tried the bottom three to no avail, also I have checked that my RAM is no more than 256MB for the OS.

It starts the installation then says "Unable to locate RSDP, please wait..."

Then it goes black and does nothing...

Any suggestions??

---

### Post by ronocdh on 2007-04-21
> **dr.wong said:**
> Hey everyone, today I decided to finally join the Linux community, so I have downloaded the Ubuntu version!

Yay for me!! haha

I have a core duo 20" iMac running Parallels, I DO NOT have windows on my machine!

I am trying to intall ubuntu (Feisty Fawn) with Parallels, but when I go through the setup process it does not give a kernel or version for Ubuntu! Which one should I choose??
 
(I downloaded the ISO which is on my Mac's HD)

Options : 
Red Hat
Debian
Fedora
SUSE
Mandriva
Xandros
Other Linux Kernel 2.4
Other Linux Kernel 2.6
Other Lunux

I have tried the bottom three to no avail, also I have checked that my RAM is no more than 256MB for the OS.

It starts the installation then says "Unable to locate RSDP, please wait..."

Then it goes black and does nothing...

Any suggestions??
Unfortunately Parallels doesn't have up to date Ubuntu support. Try [VMWare Fusion]("http://www.vmware.com/products/beta/fusion/"), as that seems to produce considerably more success stories. You'll have to register to get a beta serial number, but it's at no charge.

Good luck to you.

---

### Post by dr.wong on 2007-04-21
What a pitty, I really like the way that parallels works, but if VMWARE works properly then that shall be my choice..

I wonder if they are going to update their compatability anytime soon?? hmm...

---

### Post by hajk on 2007-04-21
Ubuntu can certainly be installed in Parallels for Mac, but you may take heed of the following:

1. There have been problems with recognition of the CD-ROM device; this is a Ubuntu kernel issue, nothing to do with Parallels. A work-around is to configure the VM with Solaris/Other Solaris guest OS... strange, but it works! This has been discussed before on this forum.

2. You should limit the RAM in the VM to 512MB for the installation phase. It can be increased later if you have more than that available.

3. Better to use the "alternate" install CD, then use boot option: "install acpi=off". If necessary, you could also use the boot option "fb=false".

N.B. If you have Parallels for Mac build 3188, then the default VM grabs all remaining space on the HD. So, use a custom VM and give it like 8GB virtual HD. Furthermore, Bridged Ethernet should be chosen.

Good luck!

---

### Post by pachos7 on 2007-04-22
Awesome solution this one about using Solaris instalation it really works thanks a lot.

---

### Post by mscman on 2007-04-30
> **dr.wong said:**
> Hey everyone, today I decided to finally join the Linux community, so I have downloaded the Ubuntu version!

Yay for me!! haha

I have a core duo 20" iMac running Parallels, I DO NOT have windows on my machine!

I am trying to intall ubuntu (Feisty Fawn) with Parallels, but when I go through the setup process it does not give a kernel or version for Ubuntu! Which one should I choose??
 
(I downloaded the ISO which is on my Mac's HD)

Options : 
Red Hat
Debian
Fedora
SUSE
Mandriva
Xandros
Other Linux Kernel 2.4
Other Linux Kernel 2.6
Other Lunux

I have tried the bottom three to no avail, also I have checked that my RAM is no more than 256MB for the OS.

It starts the installation then says "Unable to locate RSDP, please wait..."

Then it goes black and does nothing...

Any suggestions??

When booting with a Solaris machine, I ran into the issue of the RSDP error as well. When the screen went black, I thought it was hosed, but I noticed the hard drive my ISO image was on (an external drive, so no other activity) was still reading away, so I let it sit and about a minute later, voila! The live CD was there. I didn't have time to go ahead and install, since I was simply looking into the issue for someone on  IRC, but it does seem to work just fine. Anyone else find this to be the case?

---

