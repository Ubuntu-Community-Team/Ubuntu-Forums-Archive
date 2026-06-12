---
title: "Compiling for idiots? Webcam drivers, taking blind stabs."
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Wartooth on 2007-01-26
I have a cheap little, horrible webcam that I'd like to see if I can make work, just for something else to do/learn with Ubuntu. 

I found this, which seems like it may support my webcam: [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

However, I haven't even the slightest idea as to WHAT on Earth I am to do.  I've searched the boards, I've searched the Wiki, there seems to be nothing that really makes it clear as to what to do to someone as completely in the dark as I am. 

I've sort of botched my way around blindly, trying to use this as a reference: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) But, to be honest, most of this stuff makes little sense to me as well, so I've no idea if these instructions are really of any use. 

I extracted spca5xx to /usr/local/src, based off a guess from the CompilingEasy page, it said something about running ./configure  I am simply typing things in and hoping it makes more sense to the machine than it does to me.  Typing in ./configure just gave me this: 
bash: ./configure: No such file or directory

Stumbling on, I just typed in "sudo make" and was presented with this: 
Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/local/src/spca5xx-20060501 CC=cc modules
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

And at this point I have given up and am beyond lost.  IS there something out there that can explain this with a little bit of hand-holding or something?  Or is this one of those things you're expected to "just get" after X amount of time?  What am I missing here?

:confused:

---

### Post by kvonb on 2007-01-26
The first thing you need to do is install the "build-essential" package, like so:

```
sudo apt-get install build-essential
```

then:

```
sudo apt-get install linux-headers-`uname -r`

```


That will give you all the compiling stuff you need :).

What make/model of webcam is it?  Most of the drivers are already built into Edgy, just to save yourself some bother :).

If it's a USB camera, try this:

```
lsusb
```

That should tell you the camera type.

Webcams are a big headache in Linux unfortunately, the manufacturers won't release drivers or access to their code so it's hit and miss.

Regards, KEv :)

---

### Post by PriceChild on 2007-01-26
Firstly could you tell us what cam it is?

You can install some cams without having to compile a thing...

---

### Post by az on 2007-01-26
The spcax webcams work fine since Dapper.

The module is already included.

---

### Post by Wartooth on 2007-01-26
It's a horrible little still/webcam combo that I got on a whim as I can't pass up craptacularly cheap gadgets :D

lsusb tells me :
Bus 002 Device 002: ID 093a:010e Pixart Imaging, Inc.

It is also known as a MARScam and a few other things.  

I already tried Easycam, and it did not recognize the camera.  However, when I plug the camera in, it is immediately recognized for it's still abilities, though that's not what I'd like to get working, of course.  :)

So, this driver package seems to be about my only hope with this little thing. 

I'd already done:
sudo apt-get install build-essential

But had not yet done:
sudo apt-get install linux-headers-`uname -r`

So I am doing that now, and much text is scrolling by in my Terminal window. :)

I appreciate the kind responses.

---

### Post by Wartooth on 2007-01-26
Does this:
Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/local/src/spca5xx-20060501 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /usr/local/src/spca5xx-20060501/drivers/usb/spca5xx.o
  CC [M]  /usr/local/src/spca5xx-20060501/drivers/usb/spcadecoder.o
  LD [M]  /usr/local/src/spca5xx-20060501/spca5xx.o
  Building modules, stage 2.
  MODPOST
  CC      /usr/local/src/spca5xx-20060501/spca5xx.mod.o
  LD [M]  /usr/local/src/spca5xx-20060501/spca5xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'

mean it worked?

---

### Post by az on 2007-01-26
> **Wartooth said:**
> It's a horrible little still/webcam combo that I got on a whim as I can't pass up craptacularly cheap gadgets :D

lsusb tells me :
Bus 002 Device 002: ID 093a:010e Pixart Imaging, Inc.

It is also known as a MARScam and a few other things.  


You will have to google around.  The spcaxx driver works and so your webcam probably uses a different driver.  Compiling that driver again is not going to help you.

Look around to see if your particular device is supported somewhere.
Ex:
[http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6](http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6)
[http://www.kaiser-linux.li/index.php?title=PAC7311](http://www.kaiser-linux.li/index.php?title=PAC7311)

---

### Post by Wartooth on 2007-01-26
So, you're saying Dapper basically already had this driver package installed, so what I was doing/did/intended to do was simply redundant, and if it didn't work upon plugging in, then I needed to look beyond the spca driver, right?

Hm.

---

### Post by jonbue on 2007-01-26
have you tried setting up a ekiga account and using that to test if you get a image from the cam? thats how i did it worked fine for me

---

### Post by az on 2007-01-27
> **Wartooth said:**
> So, you're saying Dapper basically already had this driver package installed, so what I was doing/did/intended to do was simply redundant, and if it didn't work upon plugging in, then I needed to look beyond the spca driver, right?

Hm.

To be sure, open a terminal, run

tail -f /var/log/messages

and then plug the device in for the first time since you booted.  Post the output.  That will display what the kernel is doing when you plug in your device.  If it loads a module, then it is either a bug or a misconfiguration issue.  If nothing happnes, it's because the chipset of the device does not have a linux driver in Dapper.  In that instance, you would need to find one and compile it,

---

### Post by Wartooth on 2007-01-27
Jan 27 10:59:28 blackbox kernel: [17179847.956000] usb 2-2: new full speed USB device using uhci_hcd and address 2

Is what it gave me.  And, the GUI brought up the "Camera Import" window, telling me that a camera has been detected.

---

### Post by az on 2007-01-27
> **Wartooth said:**
> Jan 27 10:59:28 blackbox kernel: [17179847.956000] usb 2-2: new full speed USB device using uhci_hcd and address 2

Is what it gave me.  And, the GUI brought up the "Camera Import" window, telling me that a camera has been detected.

No webcam driver is being loaded, so it's not an spcax type device.

Good luck!  There seem to be a few webcam drivers in development.  Perhaps they will soon become stable and be included by default into the kernel.

If you come across a driver that wors for your camera, please file a bug report and describe what it is and what you used to get it working.

---

### Post by Wartooth on 2007-01-27
Ah, well, 'twas but a cheap thing that I hoped to use in a bit of a learning experience.  At least I think I've learned a bit.  If I do get it working, I'll be sure to file. 

Thank you for the help!  :)

---

### Post by xSauronx on 2007-01-27
> **Wartooth said:**
> Ah, well, 'twas but a cheap thing that I hoped to use in a bit of a learning experience.  At least I think I've learned a bit.  If I do get it working, I'll be sure to file. 

Thank you for the help!  :)

i had a problem getting a webcam to work today and got it resolved

check the multimedia forum for my thread

i thought i needed spc5xx, and also tried gc-usb i think

turned out i ended up using one called gspca to get it to work

see if anything there can help
and paste the id of your lsusb output into the search bar on these forums, and on google with "linux driver" appended after the id and see if you can get anywhere else

---

