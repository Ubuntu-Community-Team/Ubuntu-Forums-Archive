---
title: "Having trouble on a macbook"
date: 2013-01-01
forum: Apple Hardware Users
---

### Post by macbuntuuu on 2013-01-01
just installed Ubuntu on my macbook (not pro or air)
its been slow and the cursor lags whenever I use the trackpad
this is a black macbook from 2008 and i installed Ubuntu off a disk

---

### Post by Bucky Ball on 2013-01-01
Welcome to the forums.

Which release did you install?

---

### Post by macbuntuuu on 2013-01-01
Thanks!
I believe it was the latest 12.10 32 bit
can it be run alongside macosx?

---

### Post by Bucky Ball on 2013-01-01
As far as I know, but you might have better luck if I move this to* Apple Users* sub-forum, so:

*Thread moved to** Apple Users***

Don't know much about Macs, but how old is it? If you have a dual-core you should probably be running the 64bit version.  Disregard the AMD bit. The 64bit AMD ISO is for ALL processors, Intel and AMD. You might also like to try the long-term release, 12.04 LTS. Supported until 2017 and might change things. Interim releases are supported for 18 months from the date of the release (e.g. 12.10 = 2012, October.)

Hopefully a Mac/Ubuntu guru can help you out. Good luck.

---

### Post by macbuntuuu on 2013-01-01
thanks:)

---

### Post by Bucky Ball on 2013-01-01
You might like to read my last post again for a bit more info. I've edited ...

---

### Post by macbuntuuu on 2013-01-01
Yep
Its a little over four years old running an intel core 2 duo with an intel gma
Last time i tried installing ubuntu i installed it as my sole operating system on my computer
it didnt work very well so i just got rid of ubuntu and reinstalled macOS
the next time i try i would prefer to be able to run them both

---

### Post by Bucky Ball on 2013-01-02
Try the 12.04 LTS 64bit AMD ISO. Make the CD and boot from that and try it out. See how it rolls. If all good, try an install. Did 12.10 work ok from the CD?

How much RAM? You might also like to provide the output of:

```
sudo blkid
```

... just so we can see how things are partitioned. To open a terminal, Application>Accessories>Terminal (I think, I'm using 10.04 LTS on this machine which doesn't use the Unity desktop enviornment so things could be different.)

---

### Post by macbuntuuu on 2013-01-02
It has 2 gb of ram and its currently running lion. I have no idea how to partition the computer to support both operating systems
when i was running it the main problem i had was that the cursor lagged while i was using the trackpad

---

### Post by Bucky Ball on 2013-01-02
Ah, this might help, but this is where I'm out of my Mac depth. 

[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)

Think you need refit or boot camp or something ...

I could be wrong and there could be a few ways of doing this.

---

### Post by macbuntuuu on 2013-01-02
i appreciate the link. ill be sure to give it a try:D

---

### Post by Bucky Ball on 2013-01-02
Yes, after a little more looking refit seems the way to go. You might want to dig around for info on that. Here's another one which might give a few more clues. It's for a triple boot and 10.04 LTS but fine for 12.04 LTS too I would think:

[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)

You might also like to trawl through this search:

[http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=2&q=mac+dual+boot+ubuntu+lion&ql=](http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=2&q=mac+dual+boot+ubuntu+lion&ql=)

The answer to your original question can be confirmed; yes, Lion and Ubuntu run fine in a dual-boot. The thing to remember is Macs apparently use EFI instead of BIOS so that presents issues which you need to work around. I figure that's where refit comes in.

You might want to find more info on EFI as well so you are reasonably across it all before doing anything that might screw things up. ;)

---

