---
title: "Minimal install ibook G3 PPC"
date: 2009-02-18
forum: Apple Hardware Users
---

### Post by ringsofsaturn on 2009-02-18
Hello,

Have recently installed 8.04 server with XFCE desktop on a ibook G3 PPC, 
500mhz/192 MB RAM after reading somewhere it would be a faster system than using Ubuntu alternate with XFCE. Did go that route previously and it does seem quicker the way it is configured now.

My question is: should I have installed the Ubuntu minimal (think I have term correct) install instead for a speedier system? The main use for the ibook is a sort of "netbook" but need Abiword (or the like - could use Google Docs though) and a basic photo viewer/editor plus a CD ripper. I know more RAM would be desirable and will buy some when I can find it within my restricted budget.

Thanks.

---

### Post by kerry_s on 2009-02-18
you should go the minimal route, if you don't need no server services, not sure what the server installs, but just on the off chance it could be serving you up. :lolflag:

you should ditch the desktop though, a window manager would be faster, if your lazy "lxde" is openbox all dressed up, should be faster than xfce4. you should have no problems running what you want, including openoffice. 
i use jwm on 450mhz 256mb ram and got all the stuff, i have the light stuff like abiword, but also have openoffice if i need more, there plenty of light image viewers, i use feh, mtpaint instead of gimp, etc...

you should have no problems with those specs.

---

### Post by mkvnmtr on 2009-02-18
I think the server disk has an option to allow you to just install the command line and not the server stuff but I have never used it. I have installed from the minimal disk a couple or times. Once on powerpc on a system I didn't need to be minimal and once this week on an old acer I have for a back up. Looks like xdce4 is going to be fine. I would download the minimal disk. It is a very quick download, Less than 14Mb.You can save your home file and replace it in your new system and have everything the same. The only thing i save from my home file is the .mozilla and .mozilla-thunderbird files so it is very quick to put them in a new system.

---

### Post by ringsofsaturn on 2009-02-19
Thanks kerry_s and mkvnmtr for your replies.

Am assuming with a "minimal install" I can pick the apps/packages I want to install. Am I right?

Will wireless be handled in the same way as my present system? I use a ZyXEL USB adapter at present and found it easy to get it up working in Ubuntu (Tried Debian Etch/Lenny before and couldn't get it running (the wireless)). Couldn't get display working correctly either. Sorted that issue by copying details from my xorg.conf file from 6.06 which installed fine. Again, am assuming I'll have to do same with minimal install. 

Is the speed of the system on-line determined by (in part) the amount of RAM available and/or the "weight" of the browser used? I realise bandwidth is an issue here as well. 

Thanks for your help and I'm sorry if the questions seem naive and "dumb" :).

---

### Post by kerry_s on 2009-02-19
> Am assuming with a "minimal install" I can pick the apps/packages I want to install. Am I right?

yes, same as you did with server, you'll be at command line and just apt-get what you want, i recommend dumping xfce4> 
**sudo apt-get install xorg lxde firefox synaptic**

> Will wireless be handled in the same way as my present system? I use a ZyXEL USB

yes, it uses the zd1211 firmware? if so i don't know why you would have a problem in debian, there you just add the non-free repo and apt-get install zd1211-firmware.

> Couldn't get display working correctly either

for the new xorg, i find it best to use it to make the xorg.conf, you have to run it as root so in ubuntu use that failsafe/rescue mode(the second boot option) after install and run> **X -configure**
it will create a /root/xorg.conf.new from the scan, just copy that.> **cat /root/xorg.conf.new > /etc/X11/xorg.conf**

> Is the speed of the system on-line determined by (in part) the amount of RAM available and/or the "weight" of the browser used? I realise bandwidth is an issue here as well.

hmm, yes :p 

> Thanks for your help and I'm sorry if the questions seem naive and "dumb" . 

no such thing as a dumb question, it's dumb not to ask if you don't know. ;)

---

### Post by ringsofsaturn on 2009-02-19
Thanks for the reply kerry_s. Am grateful. Do you know where I can find checksum for minimal iso? Have searched for it but to no avail.

Also when I looked into this minimal iso "thing" I found an installation guide with a pictorial guide but foolishly didn't bookmark it. Have you seen this and if so, any ideas where? Again have searched but no joy. Perhaps I need a trip to the opticians :D

Many thanks again.

Will attempt the new install this weekend and post back here with results.

---

### Post by mkvnmtr on 2009-02-19
When I google Minimal install Ubuntu en English right off the bat there are three tutorials. They are not for powerpc but it doesn't matter. Read all three and follow the one that you are the most comfortable with. I installed xfce4 but I have heard others say that lxde so I think next time I will try it.

---

### Post by kerry_s on 2009-02-19
> **ringsofsaturn said:**
> Thanks for the reply kerry_s. Am grateful. Do you know where I can find checksum for minimal iso? Have searched for it but to no avail.

Also when I looked into this minimal iso "thing" I found an installation guide with a pictorial guide but foolishly didn't bookmark it. Have you seen this and if so, any ideas where? Again have searched but no joy. Perhaps I need a trip to the opticians :D

Many thanks again.

Will attempt the new install this weekend and post back here with results.

don't worry about the checksum, it's only 14mb, if you want to be sure you can use the check disk after you boot it.

the steps are the same as any x86 install, doesn't matter that your doing it on ppc.

sure: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by ajmctaggart on 2009-02-20
Kerry S is well aware of this already, and it seems like you're on your way.  In case you get into any trouble or want some other perspective, I posted something similar about my experience trying to get a Pismo as quick as possible, while still retaining a "desktop" feel...

[http://ubuntuforums.org/showthread.php?t=511293&page=1]("http://ubuntuforums.org/showthread.php?t=511293&page=1")

Good Luck, 

I would love to throw Ibex on a g3 iBook, except I'm too messy for a white computer...

---

### Post by ringsofsaturn on 2009-02-21
Can I some how remove "bits" from the server install to turn it into a minimal one?

Or not?

Thanks

---

### Post by boydrice on 2009-02-21
Hello,

Here is where the minimal ubuntu iso's are [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

here is a great walk-through of a minimal install
[http://wiki.dennyhalim.com/ubuntu-minimal-desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop)

BTW I have found that Ubuntu 8.04.1 works great on my G4 ibook.  Ibex, not so much.

---

