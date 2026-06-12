---
title: "Linux on mac....How To..."
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by daruma_mac on 2008-03-02
As much as I've been a hardcore mac user, I'm starting to become interested in server side software/hardware on the side. Leopard Server/Xserve/Unix/etc. And to go along with that, I'm also getting a little tug, in my brain, from Linux. So, I'd like to try out one of the more popular distros out there. Ubuntu is the one I'm considering. It seems pretty stable and easy for a GUI user like myself to dive into, without knowing command line witchcraft...yet.

So, I have two questions:

1) I was told that I could run Ubuntu off the iso/disk to try it out, before I partitioned my drive. Is that even possible?

2) Can I run Linux off Boot Camp? I'm running 10.5.2, so I'm up to date... but I know, from the Boot Camp manual and Boot Camp Assistant, there is not one mention of anything other than Windows. 

Any help would be great. I'm an open source fan, but as for open source OS', i'm completely in the dark.

Best.

Justin Cash

---

### Post by Madman6510 on 2008-03-02
1. Yes.
2. It might be possible, but I've never tried it and have never heard of anyone doing it. You might want to Google that one. However, the GRUB bootloader that comes with Ubuntu should recognise your OSX.

---

### Post by daruma_mac on 2008-03-02
Thanks for the help. 

Over at the Apple forums, which I didn't really expect a reply from (or at least, any real knowledge of Linux), I got one simple reply from a Boot Camp user with Windows installed....

"Check out:
http://www.mactel-linux.org/wiki/Dual_Booting"

Still going through the site, but it just might be worthwhile. We will see.

As for the bootable iso/disk... I'm used to booting right into a single OS, not a partitioned drive. So for now, I'm going to have to use the disk to try Ubuntu out. But I'm really excited. 

One thing though... Will the disk store any pref.'s on my mac(so I can store settings/etc.)? Or am I on a factory fresh version every time? Also, to save a file, while using the iso, where will it save? Can I choose the mac as a location?

Thanks again.

Justin Cash

---

### Post by Madman6510 on 2008-03-02
The disk resets itself to the default settings every time you boot it, so you'll have to save your files on a USB disk (or the Mac's HDD if you want to).

---

### Post by UpsideDownFace on 2008-03-02
I bought a MacBook 3 weeks ago and put in the Ubuntu 7.04 installation disk and ran Administration >: Partition Manager.
The MacBook was reconditioned, but otherwise unused.
With Partition manager I reduced the Macintosh partition from 120 GB to 30 GB, and then re-booted into Leopard to check that it still worked as a MacBook.
I then rebooted with the Ubuntu DVD and partitioned the now free 90 GB into 10 GB FAT32; 20GB ext3 for /; 45 GB ext3 for /home; 2GB for linux-swap

Then I installed linux and most of it worked straight away.

The things that didn't work were 
1. screen resolution was 1024x768, mac needs 1280x800
2.wireless not working, but ethernet connection to my ADSL modem OK
3.the touchpad is crap, so I wanted it disabled, and bought a mini-mouse

1 corrected by downloading "915resolution" from [http://www.geocities.com/stomlijen/](http://www.geocities.com/stomlijen/)
command line :-
   # 915resolution -l
gives a list including
  mode 5c 12800x768, 32 bits/pixel

I then modified /etc/X11/xorg.conf using "sudo gedit /etc/X11/xorg.conf"
 to have in Section "Screen"  (along with several other similar subsections)
   SubSection "Display"
       Depth 24
      Modes    "1280x800"
  EndSubSection

2 corrected by downloading from [http://snapshots.madwifi.org](http://snapshots.madwifi.org) madwifi-ng-current.tar.gz
 and doing
  tar -zxf madwifi-ng-current.tar.gz
  cd madwifi-ng-*
  make
  sudo make install
  sudo depmod -a
  sudo modprobe ath_pci
  sudo modprobe wlan_scan_sta

There is a problem if you use WEP password with MacBook. On the MacBook you have to add "$" (without the quotes) at the start of the password which is set on the router. An answer to this is to use WPA.
 
3 in /etc/X11/xorg.conf I changed 

  Section "InputDevice"
      Option   "SendCoreEvents"  "true"
to
      Option  "SendCoreEvents"  "false"

When I just switch on the MacBook it boots up straight into Leopard

But if I hold down the <alt> key it shows 2 disks - "Macintosh" and "Windows"
By clicking on "Windows" or <right arrow> key it boots into linux

"Windows" really means "non-Macintosh" which for me is linux.

So any casual user would think my MacBook is just a MacBook, but I know better

I got most help by Googling "linux on macbook" or "Ubuntu on Apple Macbook"  which gets you to
desert at desert dot ca
and his articles on Dapper,Feisty Gutsy on Apple Macbook

---

### Post by JoshuaRL on 2008-03-02
> **UpsideDownFace said:**
> I then modified /etc/X11/xorg.conf using "sudo gedit /etc/X11/xorg.conf"

Just as an FYI, the proper command to use here would be:
```

gksu gedit /etc/X11/xorg.conf

```
That will use "gksu" or graphical sudo.  Sometimes you can have messed up permissions problems with graphical apps run with sudo.  So a good rule of thumb is that if it's graphical, use gksu.  If it's CLI, use sudo.

---

### Post by UpsideDownFace on 2008-03-02
Sorry, I clicked accidentally on the post button

---

### Post by UpsideDownFace on 2008-03-02
Thanks JoshuaRL
The reason I didn't use gksu is this is the first time I have seen it.
Maybe it explains some oddities I have had

---

