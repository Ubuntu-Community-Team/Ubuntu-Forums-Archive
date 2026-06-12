---
title: "MacBook Pro 5,1 backlight keys do not work"
date: 2010-03-27
forum: Apple Hardware Users
---

### Post by Cavin on 2010-03-27
Hi,

I am dual-booting Karmic/OS X. I have a MacBook Pro 5,1. When using the keyboard to change the backlight, the graphic in the top left does move to indicate a higher brightness (albeit, it moves extremely slowly). 

I, of course, have all the necessary drivers installed.

I have all the packages I needed from the Mactel repository. This has been a problem within Karmic since I've put it on my MBP. There have been several updates from the Mactel repository concerning the Nvidia backlight package (I don't remember exactly what that package is called though). I hope each time that it will fix what is going on, but obviously, it hasn't.

Is there any program that I could use to otherwise change the backlight? When I'm sitting outside it's really difficult to see what's on my screen as it also doesn't automatically respond to the change in environmental brightness by making the screen brighter.

Thanks,
Cavin

---

### Post by linuxopjemac on 2010-03-27
interesting thread

[http://ubuntuforums.org/showthread.php?t=977558&page=21](http://ubuntuforums.org/showthread.php?t=977558&page=21)

---

### Post by Cavin on 2010-03-27
> **linuxopjemac said:**
> interesting thread

[http://ubuntuforums.org/showthread.php?t=977558&page=21](http://ubuntuforums.org/showthread.php?t=977558&page=21)

Unfortunately, the script on this thread page does not work because:
```
 cat: /root/.backlight: No such file or directory
/etc/init.d/backlight-set: 18: /usr/local/bin/nvclock: not found
```edit: installed nvclock, but still no such file or directory for /root/.backlight
After doing:
```
sudo touch /root/.backlight
```I get:
```
/etc/init.d/backlight-set: 18: /usr/local/bin/nvclock: not found
```After I install nvclock from apt, I the same thing, and I find out it's in /usr/bin. So I do:
```
 sudo ln -s /usr/bin/nvclock /usr/local/bin/nvclock
```
And then running:
```
sudo sh /etc/init.d/backlight-set start
``` 
I get:
```
/usr/local/bin/nvclock: option requires an argument -- 'S'
```So what now?

---

### Post by linuxopjemac on 2010-03-27
there are two nvidia backlight drivers available in the repository, you could try the one you don't use now
so either:

```
sudo apt-get install mbp-nvidia-bl-dkms
```

or
```

sudo apt-get install nvidia-bl-dkms
```

I guess you have pommed installed to make your F1/F2 key change the brightness.

---

### Post by Cavin on 2010-03-27
> **linuxopjemac said:**
> there are two nvidia backlight drivers available in the repository, you could try the one you don't use now
so either:

```
sudo apt-get install mbp-nvidia-bl-dkms
```or
```

sudo apt-get install nvidia-bl-dkms
```I guess you have pommed installed to make your F1/F2 key change the brightness.
I actually had both packages installed! hahha I uninstalled nvidia-bl-dkms and it fixed it! Thank you!

---

### Post by alexmurray on 2010-03-28
Yeah I was going to say the nvidia-bl driver doesn't work for the 9600M GT in the MBP - instead you need the mbp-nvidia-bl driver - if you have both installed nvidia-bl overrides mbp-nvidia-bl and so backlight doesn't work - as you noticed simply uninstalling nvidia-bl fixes it then.

---

### Post by jtayl22 on 2010-04-20
> **alexmurray said:**
> Yeah I was going to say the nvidia-bl driver doesn't work for the 9600M GT in the MBP - instead you need the mbp-nvidia-bl driver - if you have both installed nvidia-bl overrides mbp-nvidia-bl and so backlight doesn't work - as you noticed simply uninstalling nvidia-bl fixes it then.

Thanks for this note. It took many google searches, reboots and installing and uninstalling other packages, etc. before I finally stumbled upon your (CORRECT!!) advice. Uninstalling nvidia-bl allowed me to adjust the brightness with the function keys.

$ sudo dmidecode -s system-product-name
MacBookPro5,2

$ lspci | grep G
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic


Can the advice be added to [https://help.ubuntu.com/community/MacBook5-2/Karmic](https://help.ubuntu.com/community/MacBook5-2/Karmic) which (INCORRECTLY) states that "You can't adjust screen brightness under ubuntu using the NVidia driver. nvidia-bl and mbp-nvidia-bl don't work"

---

### Post by linuxopjemac on 2010-04-21
you can do it yourself, if you are sure that it works.

---

### Post by SwedishWings on 2010-05-30
> **Cavin said:**
> I actually had both packages installed! hahha I uninstalled nvidia-bl-dkms and it fixed it! Thank you!

I had the same problem for ages - thanks for finding this!

Something must be wrong in the repositories when both can be installed...

/Mike

---

### Post by Moz Holmes on 2010-11-11
It also took a lot of frustration and searching before I happened upon this simple solution. 

Completely removing nvidia-bl-dkms solved this issue upon restart.

I am on a MacBook Pro 6,2 and Ubuntu 10.10 btw. 

Cheers!

---

### Post by penkoad on 2010-11-15
Cheers !

Thanks to linuxopjemac I removed mbp-nvidia-bl-dkms and installed nvidia-bl-dkms.
And after a reboot, my function keys for screen brightness that broke during maverick upgrade are back again.

Great !! =D>

For information:
MacBook5,1
02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M] (rev b1)
Description:	Ubuntu 10.10

---

