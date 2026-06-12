---
title: "Wireless connection to net via USB thing"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-05-15
Hi, 

I've had Ubuntu running from the disk but I can't access the internet.  I've tried searching for relevant guides but can't come up with much. 

I have desktop with a USB wireless dongle which connects [wirelessly] to the router.  The dongle's made by Cable & Wireless and I don't have the disk it came with...  

Any links to a *simple* guide?  Tips?  

Thanks

---

### Post by rich.bradshaw on 2007-05-15
What is the chip inside it?

lspci
lsusb

will probably tell you if you look throught the results. (lists pci and lists usb).

Once you know the chip, google that instead, the chip is more important than the make.

You will most likely need ndiswrapper. Don't bother compiling it from source, just get it from the repo

sudo apt-get install ndiswrapper

then

ndiswrapper -i pathtowindowswirelessdriver

nidiswrapper -l

will see if it is installed

ndiswrapper -m

modprobe ndiswrapper

that's it, should work.

---

### Post by carusoswi on 2007-05-15
> **rich.bradshaw said:**
> What is the chip inside it?

lspci
lsusb

will probably tell you if you look throught the results. (lists pci and lists usb).

Once you know the chip, google that instead, the chip is more important than the make.

You will most likely need ndiswrapper. Don't bother compiling it from source, just get it from the repo

sudo apt-get install ndiswrapper

then

ndiswrapper -i pathtowindowswirelessdriver

nidiswrapper -l

will see if it is installed

ndiswrapper -m

modprobe ndiswrapper

that's it, should work.

So, if your connection to the net is broken (or in the OP's case never setup), will the commands you listed still work?  I just lost my wireless connection and have no way of accessing the net via Ubuntu (I can access via my XP Dual Boot, however).

Just curious.

Caruso

---

### Post by rich.bradshaw on 2007-05-15
If you have ndiswrapper installed, then yes.

If not, then I think ndiswrapper is on the CD, so you can get it from that somehow... It's described here somewhere.

Basically, the only command I am using that requires the internet is 

sudo apt-get install ndiswrapper

the rest are just using ndiswrapper to set it up.

---

### Post by aberadam on 2007-05-15
Thanks.  But how do get this program to Ubuntu without the internet?

---

### Post by aberadam on 2007-05-15
Oh, it's on the disk somewhere...

---

### Post by carusoswi on 2007-05-15
Well, ndiswrapper is on my machine, so, now I have to figure out how to get your instructions to my Ubuntu machine.  I guess I can do it the old fashioned way - by printing them on paper and trying to type them in - I'm a decent typist, but, invariably will mistype a character here or there.

Will give it a go.

Thanks.

Caruso

---

