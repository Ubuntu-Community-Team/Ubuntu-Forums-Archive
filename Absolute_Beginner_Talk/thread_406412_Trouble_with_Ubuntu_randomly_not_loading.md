---
title: "Trouble with Ubuntu randomly not loading"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by tobyism on 2007-04-10
I found out about Ubuntu a few months ago, and installed it on my older desktop for my wife and we've both thoroughly enjoyed playing with it.  It's simple enough that she can use it after it's set up with zero trouble.

So I decided to format my laptop and put Ubuntu on it.  It's a Dell Inspiron 1100 (few years old), P4 (can't remember what speed), 512MB Ram.  Installed Edgy 6.10.  I've got a Netgear Rangemax Wireless Card (WPN511) that works fine out of the box.

For the past two days after installation, when I turn the laptop on it will go through the motions of booting up, and after the GRUB screen the screen just goes blank.  It's still on as it's not actually dark, but nothing on it.  I can wait however long, no change.  Turning off the laptop and restarting doesn't always work.  Yesterday after work it took 3 reboots to get it to actually get to Ubuntu, today it took 2 reboots. 

Any idea why this is happening?  I'm still pretty much a newb when it comes to Linux, I've been able to get by thus far as this is the first major problem I've run into.

Thanks in advance for any help you can offer.

tobyism

---

### Post by lamalex on 2007-04-10
which version are you using? one thing i would recommend would be to remove quiet from your boot flags.
```

sudo gedit /boot/grub/menu.lst

```
and scroll down to the top entry and remove the word quiet, when you boot it will give lots of output which might help you figure out what's wrong.

---

### Post by tobyism on 2007-04-10
I removed quiet and a lot of things scroll by quickly and it's yet to do the same thing yet.  Thanks for the help though, if I can duplicate the problem and find anything out from the boot screen I'll post it here.

Oh btw, I am using Edgy v6.10

---

