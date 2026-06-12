---
title: "DMA refuses to stay on after booting"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by annsachd on 2006-02-02
I can get it on so that when I watch DVDs it's not choppy but after booting up again it turns off and I have to turn it on again.

Is there a way to keep DMA on so that I don't have to keep turning it on all the time?

Thanks for the help.

---

### Post by Breaks on 2006-02-02
To get DMA to enable on boot what you need to do is the following:

```

sudo gedit /etc/hdparm.conf

```

add these lines at the bottom (change what comes after the "/dev/" part for whatever it is you want to enable it on, for example: /dev/cdrom0 etc.. ):

```

/dev/cdrom0 {
dma = on
}

```

But as i said, change what comes after the /dev/ part for whatever the device is that you wish to enable DMA on.

**:: Edit ::**

You might also want to check out the following thread:

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

Has some nice features for things such as doing this with a GUI, turning on num lock on boot etc.

---

### Post by annsachd on 2006-02-03
Unfortunately what you have only locks up my DVD drive when you insert a disk.

I guess there's something more to this than meets the eye.

---

### Post by jasay on 2006-02-03
Well, in his zeal to help I think Breaks forgot a "}" to end the block.  Like so: ```
/dev/cdrom0 {
dma = on
}
```but I don't know if that's what causing  your lockup.

---

### Post by Breaks on 2006-02-03
Oh crap yeah i just noticed id left out the last bracket, my baad... sorry for that. Corrected.

---

### Post by annsachd on 2006-02-03
Ah, so that's what zeal is, a missing bracket. I still have the lockup with the drive with the bracket included.

---

### Post by annsachd on 2006-02-03
I think I figured it out. I added these lines to /etc/modules:

piix

ide-core

above the line

ide-cd 

Now no more lockup when I put in a DVD and DMA is on when the computer boots up.

Thanks for trying to help even though you left out that bracket! :p

---

### Post by rharris on 2006-02-03
The following link will be of some help:

[https://wiki.ubuntu.com/DMA?highlight=%28dma%29](https://wiki.ubuntu.com/DMA?highlight=%28dma%29)

Rob

---

