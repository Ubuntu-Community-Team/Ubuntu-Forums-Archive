---
title: "Get it Off!"
date: 2008-10-29
forum: Apple Hardware Users
---

### Post by RJWEcology on 2008-10-29
I recently put Ubuntu 8.04 on my iBook G3 but now I can't seem to get rid of it!? It was a clean install so I don't have any other partitions or other OS' on there. 

I have my Tiger CD's but they won't boot. I have my Live CD and that won't load either? 

How the hell can I get rid of Ubuntu from my Laptop!?!?!? 

I have an old ipod (20gb) and an external HDD I could also use. Any ideas or suggestions? 

A prize to the person who can guide me throught this!

---

### Post by DanTheFlyingMan on 2008-10-29
Stop trolling. There is absolutely no legitimate reason to remove Ubuntu from your system.

---

### Post by RJWEcology on 2008-10-29
I beg your pardon!?!?! I am not trolling! I have Ubuntu on my PC and I am very happy with it. I just don't want it on my iBook anymore.

---

### Post by tiresia on 2008-10-29
Can't you start from MacOSX just holding down C at startup?
Try resetting PRAM/NVRAM: hold down cmd+opt+P+R (and then  start again with C from Tiger)

---

### Post by DanTheFlyingMan on 2008-10-29
> **RJWEcology said:**
> I beg your pardon!?!?! I am not trolling! I have Ubuntu on my PC and I am very happy with it. I just don't want it on my iBook anymore.

You are spreading the myth that OS X is a better OS than Ubuntu. Stop trying to pass off your trolling as troubleshooting.

---

### Post by RJWEcology on 2008-10-29
> **tiresia said:**
> Can't you start from MacOSX just holding down C at startup?
Try resetting PRAM/NVRAM: hold down cmd+opt+P+R (and then  start again with C from Tiger)

I'll give that a try. I'm just confused as to why the live CD won't load?

---

### Post by RJWEcology on 2008-10-29
> **DanTheFlyingMan said:**
> You are spreading the myth that OS X is a better OS than Ubuntu. Stop trying to pass off your trolling as troubleshooting.

You're clearly a troll yourself. Go away and stop bothering my on my thread.

---

### Post by overdrank on 2008-10-29
> **DanTheFlyingMan said:**
> You are spreading the myth that OS X is a better OS than Ubuntu. Stop trying to pass off your trolling as troubleshooting.

> **DanTheFlyingMan said:**
> Stop trolling. There is absolutely no legitimate reason to remove Ubuntu from your system.

Hi and to the op OS X maybe the best operating system for them. Asking how to remove Ubuntu is not trolling.
The only legitimate reason needed to remove Ubuntu is up to the Owner of the system. :)
Please contribute to the issue at hand and if not then you can choose not to respond.

---

### Post by RJWEcology on 2008-10-29
Thank you. I am actually a very proud Ubuntu user (my PC) and use it every day. I wanted to try putting it on my old iBook as I like Ubuntu and wanted to see if it works well on that system. The reason for wanting to remove it is actually due to my G/F. She likes OSX better and wants it back. 

Now, do I have to explain myself any more?

---

### Post by steveneddy on 2008-10-29
> **DanTheFlyingMan said:**
> There is absolutely no legitimate reason to remove Ubuntu from your system.

LOL - have you looked at the BIOS settings to get the CD to boot first?

---

### Post by mkvnmtr on 2008-10-29
When you start your computer you should have yaboot come up and give you the option to press c to boot from the disk. Can you confirm that yaboot comes up and that you pressed c and then it would not boot from the disk.

---

### Post by RJWEcology on 2008-10-29
> **mkvnmtr said:**
> When you start your computer you should have yaboot come up and give you the option to press c to boot from the disk. Can you confirm that yaboot comes up and that you pressed c and then it would not boot from the disk.

That is correct. It normally just hangs there and nothing happens. I managed to get the live CD working but as for my apple CD's, not so good. I'm looking into different burning options (all 4 and .dmg files) 

I have transmac installed and power iso but they are still not booting and I'm running out of CD's!

---

### Post by tiresia on 2008-10-29
How did you install Ubuntu? Could you just start from the CD pressing C?

---

### Post by oswaldkelso on 2008-10-29
If booting holding the c key fails. Boot holding the alt/opt key with your osx disk in the drive, then select the cd.

---

### Post by RJWEcology on 2008-10-30
> **oswaldkelso said:**
> If booting holding the c key fails. Boot holding the alt/opt key with your osx disk in the drive, then select the cd.

I've tried both methods but to no such luck. I think it may be the disk. I'll try burning another. Problem is, I think it's a .dmg but I have to make it bootable. I think I'll have to google it.

---

### Post by tiresia on 2008-10-30
How are you burning the image? In windows or in Linux?

---

### Post by RJWEcology on 2008-10-30
I've been using Windows as I have Transmac. It seems to read the .dmg better and offers the chance to burn it into an iso. Is there a linux altrnative? When loading the CD in Linux (on my laptop) it does say the CD is not mountable.  

Should I try burning it in Linux (on my PC)? What software should I use?

---

### Post by tiresia on 2008-10-30
In Linux you can read a dmg file just mounting it as hfsplus 
```
sudo mount -t hfsplus /path/to/image /mnt
```
To burn the image, umount it and burn it as root using the software you like (brasero?)
```
sudo brasero
```
or with wodim
```
sudo wodim -dao /path/to/image 
```
You can choose also the speed
```
sudo wodim -dao speed=4 /path/to/image
```

---

### Post by tiresia on 2008-10-30
Be sure to use the right medium: does your optical drive support dvd+r and dvd-r?

---

### Post by RJWEcology on 2008-10-30
I'm just using standard CD-R (my ibook doesn't have a DVD drive). I've tried a few times and it hasn't worked. I feel like my iBook is now bricked. I'm trying one more time 
It's a shame Ubuntu doesn't run well on it as I like it so much.  

I've also wasted about 6 CD's trying to make a bootable .dmg disk. Dammit!

---

### Post by tiresia on 2008-10-30
Have you tried to mount the image as I said you before? And do you know how was the image made?
Last question: do you have another mac, just to try if the problem is the cd or the ibook?

---

### Post by RJWEcology on 2008-10-30
I have tried to mount the image but it didn't work. It just said .dmg wasn't supported. I've contacted a friend in Nottingham who has a Macbook. I've asked him to burn me the CD's using the OSX programme he has. I very much doubt he will do it though.

---

### Post by tiresia on 2008-10-30
You may try using -o loop
```
sudo mount -t hfs -o loop /path/to/image /mnt
```

I'm asking this because, even if the image is not bootable, you can try to make it bootable.
Have you tried with wodim - it worked for me always, but run such commands always with root privileges

---

### Post by DRM_free on 2008-10-30
The only way I've found to **reliably** burn .dmg disks is using the "Disk Utility" that comes with Mac OS X. Do you have a friend with a Mac OS X computer that can burn the CD for you? Oh, and if you don't want to waste another 6 CDs, just burn the first one and see if it boots :)

Another reason why Tiger may not be booting on your G3 machine is that it dosen't have the latest firmware:

[http://support.apple.com/kb/HT1395](http://support.apple.com/kb/HT1395)

But if Tiger boots without a firmware update, I wouldn't worry about the firmware.

---

### Post by Concorde105 on 2008-10-30
As he said earlier, THE iBOOK G3 DOES ***NOT*** HAVE A DVD DRIVE. That makes booting from the Tiger disk impossible because it is a DVD. That said, IF he upgraded the CD drive to DVD (Which requires a complete take apart), then he can boot from the Tiger disk. HOWEVER, if he does not have the iBook with FireWire, Tiger won't install. (don't ask me why: I've NEVER used the FireWire port on my PowerBook G4. NEVER!!)

---

### Post by RJWEcology on 2008-10-30
> **DRM_free said:**
> The only way I've found to **reliably** burn .dmg disks is using the "Disk Utility" that comes with Mac OS X. Do you have a friend with a Mac OS X computer that can burn the CD for you? Oh, and if you don't want to waste another 6 CDs, just burn the first one and see if it boots :)

Another reason why Tiger may not be booting on your G3 machine is that it dosen't have the latest firmware:

[http://support.apple.com/kb/HT1395](http://support.apple.com/kb/HT1395)

But if Tiger boots without a firmware update, I wouldn't worry about the firmware.

I've only ever tried the 1st disk but I've asked a friend and he's agreed to burn me the disks.

---

### Post by cyberdork33 on 2008-10-30
> **Concorde105 said:**
> As he said earlier, THE iBOOK G3 DOES ***NOT*** HAVE A DVD DRIVE. That makes booting from the Tiger disk impossible because it is a DVD. That said, IF he upgraded the CD drive to DVD (Which requires a complete take apart), then he can boot from the Tiger disk. HOWEVER, if he does not have the iBook with FireWire, Tiger won't install. (don't ask me why: I've NEVER used the FireWire port on my PowerBook G4. NEVER!!)
Apple allowed people to get cd's in place of the DVD for tiger. I have a set for my iBook g3.

---

### Post by Frak on 2008-10-30
Here's something I find a lot of error with. No offense to the OP in any way.

Did you wait until ***after*** the gong to press c / opt / alt?

---

### Post by RJWEcology on 2008-10-31
I waited till after the gong.

---

