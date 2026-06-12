---
title: "stuff that should be pre-installed and work out of the box"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by obb2007 on 2007-05-25
using ubuntu for about 2 weeks.... here is what i think must be pre installed to use right after the installation- especially if you want to get the mainstream users (and my aunt) and i write this with tremendous respect for the amazing work you're doing here:

1- video card drivers installed, enabled and optimized - i know it's easy and takes a few minutes, but most average users won't touch if it's not pre installed. at least run a wizard during the installation to make it work once you start using the system.


2- media codecs (i know, it's all about licensing, but still) same goes for RAR support and firefox plugins 

3-  some gui for grub. startup manager...etc.

thanks

---

### Post by Ek0nomik on 2007-05-25
Even in Windows you have to install video card drivers by downloading a file in most cases.  Ubuntu's support for video card drivers increased dramatically in 7.04

Yeh, media codecs are kind of a pain, but again, even in Windows you have to download plenty of codecs.  RAR Support can be installed very easily with a single command, and RAR support does not come standard in Windows.

For editing partitions, there is always GParted.  For startup, Preferences/Sessions.

---

### Post by vtel57 on 2007-05-25
> **obb2007 said:**
> using ubuntu for about 2 weeks.... here is what i think must be pre installed to use right after the installation- especially if you want to get the mainstream users (and my aunt) and i write this with tremendous respect for the amazing work you're doing here:

1- video card drivers installed, enabled and optimized - i know it's easy and takes a few minutes, but most average users won't touch if it's not pre installed. at least run a wizard during the installation to make it work once you start using the system.

No can do because the video card manufacturers (and other hardware manufacturers) will not participate/coordinate/cooperate with the GNU/Linux community to standardize hardware drivers. There's no $$$ in it for them and there's no MEGA corporation pressuring them to do it.

> 2- media codecs (i know, it's all about licensing, but still) same goes for RAR support and firefox plugins 

Codecs are a similar situation to hardware drivers. Most are proprietary protocols (many owned by Apple or Windows) whose owners are not willing to cooperate with the GNU/Linux community.

> 3-  some gui for grub. startup manager...etc.

thanks

What's so difficult about editing the text configuration file that controls GRUB? It's the simplest thing to do. Oh, and there is a GUI for startup... Bootup Manager.

Have FUN! :)

---

### Post by darkworld on 2007-05-25
> Codecs are a similar situation to hardware drivers. Most are proprietary protocols (many owned by Apple or Windows) whose owners are not willing to cooperate with the GNU/Linux community.

How does the lastest distro of Mandriva, Mandriva Spring 2007, do this then? Because on an installation I did a week ago the DVD's played straight off, out of the box so to speak.

---

### Post by Atomic Dog on 2007-05-25
> **Ek0nomik said:**
> Even in Windows you have to install video card drivers by downloading a file in most cases.  Ubuntu's support for video card drivers increased dramatically in 7.04


Well one of the most common video cards in laptops (Intel 950) is still not auto detected and installed.  I had to do some searching to find the driver (which is now found in synaptic).  These little things do turn off the "regular users" which really need a more secure OS like linux. 

Not knocking linux.  I install it on workstations at work that only need terminal server access, but end users want simple and easy use and riight now anything that requires command line usage is not ready for prime time.

---

### Post by Ek0nomik on 2007-05-25
> **Atomic Dog said:**
> Well one of the most common video cards in laptops (Intel 950) is still not auto detected and installed.  I had to do some searching to find the driver (which is now found in synaptic).  These little things do turn off the "regular users" which really need a more secure OS like linux. 

Not knocking linux.  I install it on workstations at work that only need terminal server access, but end users want simple and easy use and riight now anything that requires command line usage is not ready for prime time.

Yeah, you are completely correct.  I guess I just don't have any friends personally that buy a Intel 950 graphics card.  ;)  So I live in a slightly biased world.

---

### Post by vtel57 on 2007-05-25
> **darkworld said:**
> How does the lastest distro of Mandriva, Mandriva Spring 2007, do this then? Because on an installation I did a week ago the DVD's played straight off, out of the box so to speak.

Who knows? Special licensing arrangements, maybe? Kind of like the Novell/Microsoft pact? Or a disclaimer somewhere about use in the United States? Most proprietary codecs are legal in countries other than the U.S. If you have commercial codecs installed on your GNU/Linux system, and you live in the U.S., you're in violation of the law.

Better watch out... BIG BROTHER is coming for you! ;)

---

### Post by Atomic Dog on 2007-05-25
> **Ek0nomik said:**
> Yeah, you are completely correct.  I guess I just don't have any friends personally that buy a Intel 950 graphics card.  ;)  So I live in a slightly biased world.


Meany.  It's a laptop.  Gimme a break!


...and I can still plat FEAR at 800x600.

---

### Post by irish_flu on 2007-05-25
I gotta go with the first reply's thoughts:

- It was no more difficult to find and install the Nvidia-made drivers for my video card in Ubuntu Linux than it was in Windows.

- Same with codecs; what windows comes with out of the box is great for mp3 and wma/wmv, but won't play hardly any of my movies (which are a mix of avi and quicktime); I have to install Quicktime, Divx, and Xvid at a minimum on my Windows machine;  Flash is also not installed out of the box for my browser in Windows.  IMHO the only codec support I personally care about that's native in Windows but not Ubuntu is mp3.

Also, I don't think that somebody who can't install a video card driver or a media codec cares too much about their Grub options or needs a startup manager.  :)

---

### Post by obb2007 on 2007-05-25
sure, windows is terrible with drivers and codecs, that's one of the reasons i tried linux. in windows at least you get the driver with a cd or from the manufacturer website. it's harder to find the right driver with linux. anyway, i have higher demands from linux, it suppose to be bettr.

---

### Post by irish_flu on 2007-05-25
> **obb2007 said:**
> sure, windows is terrible with drivers and codecs, that's one of the reasons i tried linux. in windows at least you get the driver with a cd or from the manufacturer website. it's harder to find the right driver with linux. anyway, i have higher demands from linux, it suppose to be bettr.

OK I can see that point.  I probably shouldn't be happy with "no worse than Windows".  ;)

Still, I can't blame Linux for the manufacturers failing to include stuff for the OS on their driver CD.  I had that problem for years when I worked with Macs too, so maybe I'm just used to it.

---

### Post by darkworld on 2007-05-25
> **vtel57 said:**
> Who knows? Special licensing arrangements, maybe? Kind of like the Novell/Microsoft pact? Or a disclaimer somewhere about use in the United States? Most proprietary codecs are legal in countries other than the U.S. If you have commercial codecs installed on your GNU/Linux system, and you live in the U.S., you're in violation of the law.


Sounds like a pretty good reason to move to another country.

---

### Post by vtel57 on 2007-05-25
> **darkworld said:**
> Sounds like a pretty good reason to move to another country.

Trying to find one with a climate as pleasant as Sunny Florida (minus the hurricanes, of course ;) ) is the problem. :)

---

### Post by irish_flu on 2007-05-25
> **darkworld said:**
> Sounds like a pretty good reason to move to another country.

Having to install codecs with a "wink and a nod" seems like a pretty weak reason to leave a country, IMHO.

---

### Post by johnny4north on 2007-05-25
here is what you are referring to - Mint - [http://linuxmint.com/](http://linuxmint.com/) peace bros...;)

---

### Post by Atomic Dog on 2007-05-25
Ubuntu also doesn't support DRM.  I can't watch MLB tv.  That sucks. 

...of course DRM sux for many other reasons.  I guess I'll always have to have a dual boot system for those *few* things I have to run in Windows.  98% Ubuntu vs Windows use is pretty good.

---

### Post by irish_flu on 2007-05-26
> **Atomic Dog said:**
>   I guess I'll always have to have a dual boot system for those *few* things I have to run in Windows.  98% Ubuntu vs Windows use is pretty good.

I have always thought that it's pretty much impossible for an OS to be all things to all people, anyway.  IMHO that's a big part of why Windows is big and has so many security holes and such.

I like Linux for some (most) things, I like Windows for some things, etc....

---

### Post by Atomic Dog on 2007-05-26
> **irish_flu said:**
> I have always thought that it's pretty much impossible for an OS to be all things to all people, anyway.  IMHO that's a big part of why Windows is big and has so many security holes and such.

I like Linux for some (most) things, I like Windows for some things, etc....

Exactly.  But all things being equal, I found myself using Ubuntu far more than Windows shortly after installing.  There is something about it that is easy to use for general purpose stuff.

---

### Post by sarum on 2007-05-26
I was hoping that this would be a list of things we'd all like to find on the next  issue; and I suppose it is. I've been useing Ubutnu for a year now, and as  a pensioner/sole user I stick with it because of  this forum and others.
BUT - a grandchild gave me his old box and I installed 'Puppy' - has anyone out there tried it?
Well may be not. But it's a live CD and straight off connected to the 'net'(linmodem).
It asked me my e-mail address and password.
My ISP provider, and their number.
I have an icon on my desk top to click on and after awfull noises..............I'm on line.
On Ubuntu, I have to do.............and I get on line.
So, can someone tell me how to click on something to dial up (external modem, it works but 4 or 5 clicks before..).
Thanks for replies

---

