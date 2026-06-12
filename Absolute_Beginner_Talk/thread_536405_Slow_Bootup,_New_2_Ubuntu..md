---
title: "Slow Bootup, New 2 Ubuntu."
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by J2A. on 2007-08-27
Hello every1,

I'm a new Ubuntu user and am really likin it!, dnt think ill be goin to windows nemore unless im forced to lol

Onli 1 prob, when the Ubuntu screen comes up and that orange bar moves along when the OS is loading, it gets to nearly halfway and looks like it stops and stays there for like 30secs-minute then suddenly carries on loading, this results in an overall slow boot up time, im not sure if its normal or due to a setting problem? 

Running Dual-Boot @ the moment with Win XP, and drives are FAT32 and Linux is installed on a 10GB partition,

Brief specs, 1.6GHZ Core 2 Duo, 1GB Ram, 128MB dedicated Geforce Graphics card, 120GB HD.

Thanks in advance *thumbs up*

---

### Post by bdoe on 2007-08-27
I've noticed when mine does that, the lights on my wireless card come on, so I'm guessing that this "pause" is due to Linux initializing network connections.  This might be a bit faster if you use static IPs versus DHCP, and if you disable or remove any unused network adapters.

---

### Post by Inxsible on 2007-08-27
I would say that would be normal. I see that too. Altho, it feels that its not doing anything, it is actually loading stuff up in the background. 

If you'd rather see a bunch of text scrolling up while loading, instead of the splash screen, then all you have to do is change a line in /boot/grub/menu.lst but it won't change your boot times. It will just show you what it is doing behind the scenes.

---

### Post by ddrichardson on 2007-08-27
There are programs in the repo that can display a graph of how long everything is taking to load that can be useful (but i cannot for the life of me remember its name). I have found that ndiswrapper is the worst culprit.

---

### Post by rohan182 on 2007-08-28
i have the same problem i have a 2.2ghz C2D, 2gb Ram, ubuntu 7.04

and i have the same 30second block when booting. 

might check out verbose booting when i get home.

---

### Post by Crafty Kisses on 2007-08-28
> **J2A. said:**
> Hello every1,

I'm a new Ubuntu user and am really likin it!, dnt think ill be goin to windows nemore unless im forced to lol

Onli 1 prob, when the Ubuntu screen comes up and that orange bar moves along when the OS is loading, it gets to nearly halfway and looks like it stops and stays there for like 30secs-minute then suddenly carries on loading, this results in an overall slow boot up time, im not sure if its normal or due to a setting problem? 

Running Dual-Boot @ the moment with Win XP, and drives are FAT32 and Linux is installed on a 10GB partition,

Brief specs, 1.6GHZ Core 2 Duo, 1GB Ram, 128MB dedicated Geforce Graphics card, 120GB HD.

Thanks in advance *thumbs up*
Try booting in verbose mode, see where it hangs.

---

### Post by J2A. on 2007-08-28
Thanks for ure posts every1 :)

I saw in the text version of the loading procedure that it pauses on 'loading network settings' or something, sounds like its normal, no big prob

---

### Post by st33med on 2007-08-28
Try this:
```
sudo gedit /etc/network/interfaces
```

Comment out everything but lines with 'lo'
A comment is this: 
```
# Any thing after this, a computer ignores
```

So, add a # before every line except lines with #

---

### Post by J2A. on 2007-08-28
> **st33med said:**
> Try this:
```
sudo gedit /etc/network/interfaces
```Comment out everything but lines with 'lo'
A comment is this: 
```
# Any thing after this, a computer ignores
```So, add a # before every line except lines with #

Just done that & restarted , was **much faster** & the internet connection is as normal, Thanks!! :)

---

### Post by rohan182 on 2007-08-29
thanks st33med

that sped bootup heaps. :):)

---

### Post by st33med on 2007-08-29
You're welcome!

I was going to elaborate into more detail if it did not recognize the connection, but, that's great!

---

