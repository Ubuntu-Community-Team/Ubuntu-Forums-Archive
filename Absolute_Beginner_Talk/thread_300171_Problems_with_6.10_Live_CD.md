---
title: "Problems with 6.10 Live CD"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by oldnoob on 2006-11-15
I tried posting this in the Installation forum and no one is biting over there, so I am trying here to see if I get lucky...

Been trying to boot the 6.10 Live CD to take a look at Ubuntu. After the initial options screen, I get the logo with the status bar going back and forth. This goes for about 1-2 minutes then stops. Only option is to turn power off/on to reset. This is an Intel PII, 192Mb, NVIDIA Riva128.

I posted about a week ago and Xubuntu was suggested due to my old/minimal H/W. I downloaded the Live CD of Xubuntu and it does the same thing. I've checked MD5SUMS, burned using 2 different ISO tools (ISOBurn and ISORecorder), tried different brands of CD-Rs, with no luck.

After finding a thread in one of the forums, I tried to boot the live CD using the Safe Graphics mode and choosing F6 to change options and added break=bottom. This allowed me to see the messages coming back. The last one was "Kernel Panic - not syncing: Fatal exception in interrupt."

Searching more through the forums, it seems to indicate either a problem with the NVidia card (Riva 128, or the CD-ROM, which is a Mitsumi 13x/32x.

Any ideas? Could it be the CD-ROM is too old/slow?

I downloaded the alternate CD but I haven't tried it yet. Can I still use the alternate to boot up Xubuntu to take a look without having it reformat and install on the hard drive? It's still running Windows and I don't want to trash that until I'm certain what distro I want to go with permanently.

FYI - I've gotten different versions of Knoppix to work just fine, but Ubuntu/Xubuntu looks more intriguing.

Thanks

---

### Post by taurus on 2006-11-15
How fast did you burn the ISO image?  Make sure you burn it at 4x speed...

---

### Post by wpshooter on 2006-11-15
Did you check the integrity of the CD by running the verfication test found on the initial Ubuntu boot screen menu ?

Have you ran memtest ?

---

### Post by araz on 2006-11-15
Try the alternate cd. It worked for me. But you'll have to install.

---

### Post by oldnoob on 2006-11-15
I burned one at 4x speed and one at 1x speed.  The checksums were OK.  I tried the Memtest and the CD verification and they also freeze up.  So I am really confused.  I have about 8 or 9 CDs laying around that I burned with Ubuntu and Xubuntu, using different speeds, different ISO burners.  I even tried burning a CD on a different PC to make sure it wasn't a CD burner issue.

I guess I could try Dapper to see if that works.

The alternate CD is an option except I want to leave Windows in place until I decide which distro I want to live with.  If I install the alternate CD, would it be able to partition the drive and leave the Windows side alone, or does the partition have to be in place already?

---

### Post by taurus on 2006-11-15
The alternate CD is exactly identical to the desktop CD/LiveCD except it uses text mode.  Also, you don't have run from it first before you can install it.  It will let you install Edgy directly when you first boot it and yes, you can keep your Windows using the alternate CD...

---

### Post by blindmist on 2006-11-15
might be because of too little ram...

---

### Post by oldnoob on 2006-11-15
I'll give the alternate (Xubuntu) a try.  Thanks.  I only have 192Md RAM so I  figured I would have to use the alternate if/when I planned to install it permanently.  I'll just go that route.  If it doesn't work, then maybe it's the CD-ROM not reading properly.

---

### Post by Tpaw on 2006-11-25
I went through the same thing with a p3-450 with 512meg.  ubuntu nor xubuntu would load.  in my case it was the cd-rom I change it and both loaded.  I ended up using the xubuntu.

I have a laptop p3-600 with 128 meg and I'm having the same problem with it.  I don't have a different cd-rom for it.  I'll give the alternate xubuntu a try.

tpaw

---

### Post by ReaderRat on 2006-11-25
Tpaw - 
You may want to try something smaller:
[**Damn Small Linux**](http://www.damnsmalllinux.org/download.html)
OR  [**Puppy Linux**](http://www.puppyos.com/download/downpage.htm)

---

### Post by taurus on 2006-11-25
Fluxbuntu can run with only 92MB of RAM so your laptop should be fine with it...

---

### Post by Tpaw on 2006-11-25
I had winxpro sp2 on the p3-600,128meg laptop and it worked fine.  I upgraded the mem to 160meg, xubuntu installed, but ubuntu 6.10 didn't. I use belkin f5d7010 ver 5000, new but not plug and play.  I'll try a few of your guys smaller suggestions.  

Thanks.

Tpaw

---

