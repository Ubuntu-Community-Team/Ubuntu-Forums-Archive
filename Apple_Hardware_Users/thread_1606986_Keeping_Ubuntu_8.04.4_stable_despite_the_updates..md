---
title: "Keeping Ubuntu 8.04.4 stable despite the updates."
date: 2010-10-27
forum: Apple Hardware Users
---

### Post by Symbolix on 2010-10-27
Hi,
I have Ubuntu 8.04.4 on a MacBook Pro (Core Duo). The only reason that I am using this distro is because the latest ATI Catalyst drivers that provide OpenGL support for Linux are ATI Catalyst 9.3, And this is only compatible until Ubuntu 8.04.

So I have installed all the ATI drivers, and it seems like everything is stable. At this point I would like to ask the following question:

Which updates I should be installing and which I should not? I get update notifications, but I am worried that If I start to update things... I will break my ATI Catalyst 9.3 driver compatiblity.

Any ideas?
Thanks.

---

### Post by snkiz on 2010-10-27
8.04 is LTS is it not? just don't do a dist upgrade you should be ok. If you really worried then avoid kernel packages and X packages.

---

### Post by Symbolix on 2010-10-27
Hello snkiz,
Thanks. I think it is LTS. I have downloaded the alternate installer from here: [http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

So do you mean by just not updating to 9.04 or 10.04, I should be able to keep it stable? So I can do all these updates listed in the update notification (and possibly avoid kernel packages and X packages?)

None of these auto updates will not automaticly upgrade me to some other release? Right?

Thanks.

---

### Post by snkiz on 2010-10-27
Ya thats right, as long as you don't update to 8.10 you'll be fine. That being said the clock is running out on 8.04, hope natty brings you some luck with your driver.

---

### Post by kaldor on 2010-10-27
*sudo apt-get update && sudo apt-get upgrade* will refresh the packages and install the updates for you. As long as you _don't_ do *sudo apt-get dist-upgrade* you should be perfectly fine :)

Also, in your update manager's preference disable the distro upgrade feature. It's been since June that I used Ubuntu, but it should be pretty similar.

---

### Post by Symbolix on 2010-10-27
Thanks guys! I will try this very soon. 

What exactly is "natty"? And are there really going to be any porper ATI (X1600) drivers for Ubuntu 10.04? Also, why the time is running out for 8.04? As soon as I get it working properly and stable with my required applications, then it should be good for a while? Right?

Thanks.

---

### Post by snkiz on 2010-10-27
Natty is the version of Ubuntu in development (11.04) Lucid (10.04) is already out, as is Maverick (10.10)

Lucid may already have support for your card, I wouldn't know I'm not an ATI guy

I say the clock is ticking on 8.04 because support runs out in April 2011.
see here: [https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

---

### Post by Symbolix on 2010-10-27
Lucid (10.04) was not supporting it, and the applications using OpenGL were so badly crapping, I just had to go back some versions to get the OpenGL support working properly.

I do not think anybody will bother supporting ATI X1600. I just would like to be able to use it for a year or so, until I can afford a 15inch laptop with an NVIDIA on it, I hate ATI.

Thanks. 

All MacBook Pro (Core Duo) users are stuck with Ubuntu 8.04 I guess?

---

### Post by snkiz on 2010-10-27
meh.. you may have some luck with the Gallium3D drivers, but it appears ATI has left that card to legacy. (Witch for ATI is very bad.) 

BTW my research indicates that 8.10 was the last version with support for Catalyst 9.3, with your card requires.

---

### Post by Symbolix on 2010-10-27
Ah! This is getting very complicated, All I need is my 3D software running smoothly on OpenGL and a terminal. I will stick to 8.04 as far as it goes.

I have seen some people trying 8.10 with Catalyst... for some, it worked. For a majority of them it did not. Whereas it all was kind of ok for 8.04.

Wanted to play it safe. :)

Thanks for the valuable information.

---

### Post by Symbolix on 2010-10-30
> **kaldor said:**
> *sudo apt-get update && sudo apt-get upgrade* will refresh the packages and install the updates for you. As long as you _don't_ do *sudo apt-get dist-upgrade* you should be perfectly fine :)

Also, in your update manager's preference disable the distro upgrade feature. It's been since June that I used Ubuntu, but it should be pretty similar.

Ah!! This installed and upgraded everything. Now my ATI drivers are not working anymore :( How can I revert back to a compatible kernel and X ???

These updates installed hell of a lot of stuff!! :(

What is the way of avoiding this in the future if there is no going back? How can I understand if an update is going to affect my ATI driver compatibility???

Thanks.

---

### Post by Symbolix on 2010-10-30
Well, I went through some research. I think the major things like the kernel and the x.org version are still the same.
```
X Version 11    xorg-server 1.4.0.90    Xorg(1) 
```
```
2.6.24-28-generic
```

So I installed the ATI drivers again. And it seems like they work now. I think one of the updates reverted my x.org config file to its basics... so I lost the ATI functionality.

---

### Post by linuxopjemac on 2010-10-31
good you sorted that out!

---

### Post by Symbolix on 2010-11-01
Thanks! :)

---

### Post by avtolle on 2010-11-01
You likely had a kernel update in all your upgrading, which, if you had earlier manually installed the drivers, wiped out the driver installation, requiring you to manually reinstall them. So, if there are future upgrades, don't upgrade the kernel if you don't wish to reinstall the drivers; or, be prepared to reinstall the drivers.

EDIT: Even though the kernel shows the same, i.e.2.6.24.28-generic there has likely been an update (2.6.24.28.xx to 2.6.24.28.yy, where y>x). That's what I meant earlier, if confused anyone.

---

### Post by Symbolix on 2010-11-01
Yeah, you are right. I think it was:
2.6.24.26 -> 2.6.24.28 which still makes it compatible with ATI?!

I can see .26 and .28 both being listed in my GRUB menu.

---

### Post by snkiz on 2010-11-01
8.04 was before KMS for the drivers, so every time you update the kernel (Even for a simple abi bump.) you'll need to reinstall the drivers. LOL told you to watch those kernel updates, but glad you got it sorted out.

---

### Post by Symbolix on 2010-11-01
Ah Man! :) I watched them, but was not able to find any indication any where about if it is going to ruin my kernel or not :)

I still do not know what to do in the future, when an update appears... I guess I was lucky.

At least I learned to keep an eye on my kernel, and installed something called "Startup Manager" so I have fancy colours and fancy kernel lists at startup... At least I can revert to an old kernel at that stage if I need to.

---

