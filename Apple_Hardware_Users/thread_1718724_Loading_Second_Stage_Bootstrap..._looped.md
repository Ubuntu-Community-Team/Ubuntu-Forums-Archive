---
title: "Loading Second Stage Bootstrap... looped"
date: 2011-03-31
forum: Apple Hardware Users
---

### Post by Gladian00b on 2011-03-31
I am having problems with an Xserve G4 that I barely installed Ubuntu 10.04 Server Edition on.  The Ubuntu installation process went just fine, but when I did a reboot, pressing 'L' at the Yaboot prompt, it shows the mac finder folder with the blinking question mark after it echoes 'Loading Second Stage Bootstrap'.

I looked up solutions relating to this, including Open Firmware reference guides, but didn't find these resources very helpful.  Is there a way I can fix this, such as a CD that can let me mount the media in a recovery console, and configure the 'yaboot.conf'?

---

### Post by Gladian00b on 2011-04-07
_Any_ reply would be greatly appreciated.

---

### Post by linuxopjemac on 2011-04-07
Hope this helps:
[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

---

### Post by Gladian00b on 2011-04-13
I finally fixed it!  Had a huge deal to do with Open Firmware.  But first, you will need a live cd that will actually burn ([10.04]("http://cdimage.ubuntu.com/ports/releases/lucid/release/"))  It took me three weeks to figure this out, but it required some special parameters in the yaboot.conf

```
**sudo nano /etc/yaboot.conf**
```

```
  # Simple yaboot.conf 
  boot=/dev/sda2  
 ** ofboot=hd:2**
  **# device=hd: **
  partition=3 
  magicboot=/usr/lib/yaboot/ofboot 
  timeout=50 
  root=/dev/hda3 
```

I added ofboot=hd:2 and commented out device=hd: , hd:2 being the second partition containing the bootstrap, after using devalias in Open Firmware.

I then performed this (please notice -C as a capital C, instead of -c):

```
**sudo mkofboot -C /etc/yaboot.conf**
```

It will then ask you if you want to make an HFS something [sorry, I am doing this from memory].  Type in a complete yes, and press enter.  

If your bootstrap partition isn't the second partition, but is on another partition, please use this instead:

```
**sudo** **mkofboot -b /dev/sdaX -C /etc/yaboot.conf**
```

X being the number of the partition.  Then use:

```
**sudo ybin -v -C /etc/yaboot.conf**
```

or

```
**sudo ybin -b /dev/sdaX -C /etc/yaboot.conf**
```

then type in 

```
**sudo reboot**
```

and voila!  It should boot the Second Stage Bootstrap and display yaboot.

---

