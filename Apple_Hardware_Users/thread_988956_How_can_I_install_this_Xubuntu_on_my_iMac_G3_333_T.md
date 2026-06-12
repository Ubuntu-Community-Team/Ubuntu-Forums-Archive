---
title: "How can I install this Xubuntu on my iMac G3 333 Tray Loader?"
date: 2008-11-21
forum: Apple Hardware Users
---

### Post by srk999 on 2008-11-21
Today I got a iMac G3 333 trayloader from a friend of mine. I need to know how I can install this (Xubuntu 6.06.1 Dapper Drake: [http://cdimage.ubuntu.com/xubuntu/releases/dapper/release.1/?C=S;O=A](http://cdimage.ubuntu.com/xubuntu/releases/dapper/release.1/?C=S;O=A)) Xubuntu on it.
I haven't upgraded any part since it seems pretty pricey. Also, the default OS it comes with is pretty slow.
Tried to install Ubuntu 7.04 as soon as I got the mac. But for some reason it won't boot from CD. BTW, the CD works on my laptop and I have used the same CD several times before.
Please help me out here.

---

### Post by stream303 on 2008-11-22
> **srk999 said:**
> I haven't upgraded any part since it seems pretty pricey. Also, the default OS it comes with is pretty slow.

You haven't upgraded it, but you may want to ask your friend if he knows if the hard drive was upgraded to something larger than the original spec was.  If so, you'll have to do a manual partition to keep the root partition below 8gb, typically 7gb to be safe.  some models have a 128gb root partition limitation, so perhaps keeping off the boundary at 125gb would be advised.

How much ram does it have?  This will determine if even doing an install will be worth it at all.  A 64mb machine isn't going to run Dapper or Feisty very well, unless you dig the commandline.  We're talking real-world operations, so you *may* be able to install, but be met by slow-as-molasses operation, again unless you just live in the cli.

> Tried to install Ubuntu 7.04 as soon as I got the mac. But for some reason it won't boot from CD.

We don't know what measures you took to boot it.  Did you try to boot it by holding down the "C" key just after powering on, and holding it down long enough to hear it do the boot from it?

> BTW, the CD works on my laptop and I have used the same CD several times before.

Do you mean that you've been able to install Ubuntu for PowerPC on another machine with it?  If so, the speed at which you burned it may be too fast for the model you are trying to boot from now.  I recommend a super-slow 1X or 2X burn speed.  As an iso burn burn too, not just a copy over.

Are you using CD-R's and not CD-RW's?

You may want to get more familiar with your machine's specs at

[http://www.everymac.com/](http://www.everymac.com/)

This will help you determine which instructions in the faqs and threads you'll need to follow in case you have to manually edit your config files after install.

---

### Post by srk999 on 2008-11-22
Its a iMac G3 333, factory specs.
> You haven't upgraded it, but you may want to ask your friend if he knows if the hard drive was upgraded to something larger than the original spec was.  If so, you'll have to do a manual partition to keep the root partition below 8gb, typically 7gb to be safe.  some models have a 128gb root partition limitation, so perhaps keeping off the boundary at 125gb would be advised. The hdd is 6GB, as came from the factory.

> How much ram does it have?  This will determine if even doing an install will be worth it at all.  A 64mb machine isn't going to run Dapper or Feisty very well, unless you dig the commandline.  We're talking real-world operations, so you *may* be able to install, but be met by slow-as-molasses operation, again unless you just live in the cli. It has 32 mb ram, as came from the factory.

> We don't know what measures you took to boot it.  Did you try to boot it by holding down the "C" key just after powering on, and holding it down long enough to hear it do the boot from it?
I was trying to boot a xubuntu 6.x PPC that I burned at 1x speed. I tried holding C, and also holding option+command+shift+del. none worked.


> Do you mean that you've been able to install Ubuntu for PowerPC on another machine with it?  If so, the speed at which you burned it may be too fast for the model you are trying to boot from now.  I recommend a super-slow 1X or 2X burn speed.  As an iso burn burn too, not just a copy over.no, but I was able to boot it.

> Are you using CD-R's and not CD-RW's?I am using a CD-R.

> You may want to get more familiar with your machine's specs at

[http://www.everymac.com/](http://www.everymac.com/)

This will help you determine which instructions in the faqs and threads you'll need to follow in case you have to manually edit your config files after install.
Its a iMac G3 333, factory specs.

---

### Post by stream303 on 2008-11-22
> **srk999 said:**
> It has 32 mb ram, as came from the factory.

That pretty much stops the project right there for any practical use unless you add more ram, a LOT more unfortunately.

> I was trying to boot a xubuntu 6.x PPC that I burned at 1x speed. I tried holding C, and also holding option+command+shift+del. none worked.

This could be due to the openfirmware boot-lockout feature being implemented by the previous owner(s).  Someone recently mentioned this, you'd have to search as I forgot to bookmark it.

---

### Post by srk999 on 2008-11-22
> **stream303 said:**
> That pretty much stops the project right there for any practical use unless you add more ram, a LOT more unfortunately.
This could be due to the openfirmware boot-lockout feature being implemented by the previous owner(s).  Someone recently mentioned this, you'd have to search as I forgot to bookmark it.
I think it's the boot-lockout. This is the only thread I found that has the mention of it. but it is for an intel based mac ([http://ubuntuforums.org/showthread.php?t=941240&highlight=lockout](http://ubuntuforums.org/showthread.php?t=941240&highlight=lockout)).
I was almost gonna post an ad on craigslist to give the mac out for free. but this is giving me hope that I can still use the mac the way I want (linux).

---

### Post by stream303 on 2008-11-22
Aha, you may be able to force it to boot with openfirmware.  A recent thread showed up:

[http://ubuntuforums.org/showthread.php?t=918247&highlight=openfirmware+boot](http://ubuntuforums.org/showthread.php?t=918247&highlight=openfirmware+boot)

Worth a shot if you aren't totally locked out of the cd.  I think the key is this line as at the OF boot prompt as the author mentioned:

```
boot cd:,\\:tbxi
```

If you do get more memory, make sure it is spec'ed for mac.

---

### Post by srk999 on 2008-11-22
I tired it. got into the openfirmware command prompt. put in the boot cd command. I get code=300 error. Looked into that. It seems that code comes up when u have a hdd larger than 8 gb. but my hdd is 6 gb. my mac 8.6 wouldnt boot if i had a hdd larger than 8gb. this is just insane. and I thought linux was hard.

---

### Post by stream303 on 2008-11-23
That's really odd, but yep the default-catch error 300 thing usually points to that.

Makes me wonder if perhaps your friend was using a larger drive, and then before he gave it to you, he popped the old 6gb back in.  If so, you may want to do an nvram reset.

Remember, the 32mb is really going to hurt you if it will install/run any sort of desktop at all - including Xubuntu.  Unless you add ram, about the only thing I'd suggest is to do a cli-only server install, and then do a very minimal X install on top.  This would actually be a very interesting project if you wanted to learn the command line by not having any other options. :)  Xterm will be your friend.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Works with ppc, although it initially discusses Intel.

---

### Post by srk999 on 2008-11-23
> **stream303 said:**
> That's really odd, but yep the 
Makes me wonder if perhaps your friend was using a larger drive, and then before he gave it to you, he popped the old 6gb back in.  If so, you may want to do an nvram reset.

I think you are right. The error went away after I reset the NVRAM holding Command+Option+P+R
Not when I input the command 
boot cd:,\\:tbxi
It works 
:guitar:

now if am at the ([http://ubuntuforums.org/showthread.php?t=918247&highlight=openfirmware+boot](http://ubuntuforums.org/showthread.php?t=918247&highlight=openfirmware+boot)) step.

*** Edit ***
hit a minor speed-bump:
this is what I get when I choose "server-powerpc" option. 
[[IMG]http://img224.imageshack.us/img224/437/dc081123001ro0.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img224.imageshack.us/img224/dc081123001ro0.jpg/1/w640.png[/IMG]](http://g.imageshack.us/img224/dc081123001ro0.jpg/1/)
[[IMG]http://img222.imageshack.us/img222/7809/dc081123002dp4.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img222.imageshack.us/img222/dc081123002dp4.jpg/1/w640.png[/IMG]](http://g.imageshack.us/img222/dc081123002dp4.jpg/1/)
sorry for the poor image quality.


there are several options for installation, but none of them indicate a cli-only server installation. although there is another option "ltsp-server-powerpc". i tried "install-powerpc" and "server-install-powerpc". both give me same message.

*** edit ***
here are the server related options:
ltsp-server-powerpc
server-expert-powerpc
server-powerpc

the same options exist for powerpc64. such as ltsp-server-powerpc64

*** edit ***
the error=300 is showing up again. even after the nvram resets. I think something is wrong with this mac at a deeper level.

---

### Post by stream303 on 2008-11-23
To me, it still looks like 32mb is not enough with those ramdisk errors.

Is this happening with a Dapper 6.06 server install, or with something like Intrepid which requires even more ram?  If so, perhaps fall back to Dapper.

OR, try the older Stable Debian Etch! 4.0r5.  When you go to install it you will be presented with the server options.  This *may* be small enough to work with your 32mb.

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

---

### Post by srk999 on 2008-11-23
> **stream303 said:**
> To me, it still looks like 32mb is not enough with those ramdisk errors.

Is this happening with a Dapper 6.06 server install, or with something like Intrepid which requires even more ram?  If so, perhaps fall back to Dapper.

OR, try the older Stable Debian Etch! 4.0r5.  When you go to install it you will be presented with the server options.  This *may* be small enough to work with your 32mb.

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)
I was trying Xubuntu Dapper 6.0.6.1.
Gonna try Debian Etch! 4.0r5 now.

*** edit ***
There are lots of CDs for powerpc [http://cdimage.debian.org/debian-cd/4.0_r5/powerpc/iso-cd/](http://cdimage.debian.org/debian-cd/4.0_r5/powerpc/iso-cd/)
or should I donwload the netinst? [http://www.debian.org/releases/stable/debian-installer/](http://www.debian.org/releases/stable/debian-installer/)

*** edit ***
downloading netinst. there is also a tutorial for PPC installation: [http://www.debian.org/releases/stable/powerpc/index.html.en](http://www.debian.org/releases/stable/powerpc/index.html.en)


*** edit ***
getting this error: > -1,/vmlinux: unable to open file: Invalid device
Is it telling me to do a partition for linux. Is that possible to do from the debian boot prompt?
the options are: install, auto, expert, rescue.

---

