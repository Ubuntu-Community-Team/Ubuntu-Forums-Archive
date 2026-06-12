---
title: "Graphics drivers for linux?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by IronicLogic on 2007-12-20
Hi,

I recently installed ubuntu Gutsy on my pc, and there were no problems with the install. For some reason I cannot get it to run any advanced display options. The pc is an Acer power 2000 which I bought in Japan, so I've had to get all the drivers online to replace the Japanese versions. The pc specs are: Core 2 Duo E4400 2GHz; 1 GB DDR2; onboard graphics with 946GZ chipset.

Are there any Linux drivers that I need, or which drivers can I install to get this hardware operating correctly?

---

### Post by SOULRiDER on 2007-12-20
What kind of video card is it? You will have to install ATI and NVidia drivers by yourself, but Intel drivers are installed by default. 

BTW, dont even bother looking for your drivers, open synaptic and install the drivers you need from there. Check outt hsi link, it might be of some help.
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by IronicLogic on 2008-02-27
Hi, thanks for the suggestion but I'm still stuck with limited graphics functionality. The graphics is on-board the Intel chipset (946GZ) so it's not nVidia or ATI but a (budget) Intel component. The specs are: 128MB GMA 3000 graphics chip (embedded in Northbridge). Any suggestions about how I can get compiz to run the cube?

Thanks

---

### Post by jan quark on 2008-02-27
go to 

system > preferences > appearance > visual effects

select extra.

Do you get any error messages?

---

### Post by Cope57 on 2008-02-27
Onboard graphics card can utilize the generic driver built into the Linux kernel. If you do not have a nVidia or ATI video card, and only a built-in chipset, how can we help you?
A simple thing you should do is upgrade your current software using the terminal, console, konsole, or whatever they call them with your distribution....

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
This will give you the latest kernel with the latest driver on the kernel for you.

You want performance? You may have to purchase a performance video card.
Otherwise you are stuck with what you have. A onboard video card with onboard video performance.

The [Ubuntuguide]("http://ubuntuguide.org") has quite a bit more information for you that might help you out.

---

### Post by IronicLogic on 2008-03-17
That's not really what I'm after, as I thought my posting made clear. I don't *want* to spend loads of cash for fancy graphics cards nor do I want ultra-spiffy performance. Getting compiz to work - even just a little - would be great. So, the question is: does compiz run under a generic on-board system at all? I assumed that it would at least cope with a special effect or two...

The error I get says that the desktop effects cannot be enabled. Period.

Btw, what are the minimum requirements for compiz to run - I assumed 128 MB on-board graphics memory would be okay. My other specs all seem fine: 1 GB system memory, 2 GHz Core2Duo. I've upgraded to the latest drivers, too, so that's not the problem.

---

### Post by NightwishFan on 2008-03-17
I assume Compiz could run on half those specs. :)

(Im using a Nvidia Geforce 6150se Nforce 430 128mb integrated)

---

### Post by IronicLogic on 2008-05-13
Not sure what the problem was - but now that Heron is out everything is working like a charm. Very mysterious.

---

### Post by atomkarinca on 2008-05-13
> **IronicLogic said:**
> Not sure what the problem was - but now that Heron is out everything is working like a charm. Very mysterious.

Maybe a better driver for your graphics card was added to the latest kernel.

---

