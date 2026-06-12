---
title: "virtual pc 7 help"
date: 2007-08-04
forum: Apple PPC Users
---

### Post by helloimamac on 2007-08-04
Help me! I keep trying to install Ubuntu 6.10 on my powerbook via virtual pc 7, but when it boots up, the virtual screen is at a crazy resolution and is unusable... 
When I try to install 7.04, the mouse doesn't work!! 
I've been searching google like crazy, can someone give me step-by-step instructions to install either 6.10 or 7.04, please??

---

### Post by Auria on 2007-08-04
Why are you using Virtual PC? You can just use the PPC version of ubuntu (assuming your computer is a PPC of course)

for downlaods see the FAQ it's a sticky in these forums

---

### Post by helloimamac on 2007-08-04
Okay, I think I figured it out! Nevermind!!

---

### Post by stmiller on 2007-08-04
Yeah Virtual PC is pretty much abandoned. Probably some hacks to get recent distros to boot on it out there somewhere.

---

### Post by xstanbx on 2007-08-08
Why do you say Virtual PC is dead?  Version 2007 is now out.
Also, I am having the same problem with both MS Virtual PC and MS Virtual Server 2007
I can get several other versions of linux (including solaris) to work fine but not Ununtu.
If i install workstation with safe video the video works but I have no mounse keyboard control, etc....
Any suggestions?

---

### Post by stmiller on 2007-08-08
> **xstanbx said:**
> Why do you say Virtual PC is dead?  Version 2007 is now out.


That Virtual PC 2007 you are thinking of is for x86 processors. Virtual PC for OS X PPC (a different project) is no longer being developed by Microsoft.

---

### Post by Auria on 2007-08-08
> **xstanbx said:**
> Why do you say Virtual PC is dead?  Version 2007 is now out.
Also, I am having the same problem with both MS Virtual PC and MS Virtual Server 2007
I can get several other versions of linux (including solaris) to work fine but not Ununtu.
If i install workstation with safe video the video works but I have no mounse keyboard control, etc....
Any suggestions?

can you please explain why you want to use virtual pc and not install the ppc version instead?

---

### Post by rccharles on 2007-08-09
> **xstanbx said:**
> Why do you say Virtual PC is dead?  Version 2007 is now out.
Also, I am having the same problem with both MS Virtual PC and MS Virtual Server 2007
I can get several other versions of linux (including solaris) to work fine but not Ununtu.
If i install workstation with safe video the video works but I have no mounse keyboard control, etc....
Any suggestions?

I remember having difficulty getting Ubuntu to work under Virtual PC for Mac.  I copied the /etc/X11/xorg.conf  file from a working Linux system running under Virtual PC to my Ubuntu system to get Ubuntu to work.  

/etc/X11/xorg.conf 

(xorg X Window System server configuration file)

Robert

---

### Post by EuroCity on 2007-08-10
In order to use Ubuntu Feisty or Gutsy x86 on Virtual PC 7 (an excellent program, BTW: a real shame that Microsoft discontinued it for the Mac!), you must start in safe video mode (see also above) and add this at the end of the F6-key boot options:

**i8042.noloop**

... which will activate the mouse on newer kernels.

I really hope Virtual PC 7.0.2 will remain fully compatible also with Mac OS X 10.5.x Leopard for PPC Macs (while a 7.0.3 update seems unlikely, but who knows...).

---

### Post by Railsbuntu on 2008-04-18
My install of Ubuntu 7.10 with VPC 7.0.2 always hang when validating the package zlib1g. Anyone experienced that problem? :(


EDIT: after 45min, it finally got through, it's a matter of being super patient...

---

### Post by Railsbuntu on 2008-04-18
Come on, damn it!

After 3 hours of isntallation, I get the following error message:

> No installable kernel was found in the defined apt sources.

You may try to continue without a kernel, and manually install your own kernel later. This is only recommended for experts, otherwise you will likely end up with a machine that doesn't boot.

Continue without installing a kernel?


Why is that happening? :confused:

---

