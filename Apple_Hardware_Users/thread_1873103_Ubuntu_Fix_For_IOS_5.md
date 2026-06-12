---
title: "Ubuntu Fix For IOS 5"
date: 2011-10-31
forum: Apple Hardware Users
---

### Post by shadowfax1 on 2011-10-31
Can't mount my iPad or iPhone. On IOS5.....Is there a fix.

---

### Post by kerry_s on 2011-10-31
Are you running the latest ubuntu 11.10 version?
I'm using an iPod touch 4g with iOS 5 & it mounted just fine when I was charging.

---

### Post by shadowfax1 on 2011-11-01
Yes....and the latest Libimobiledevice1.1.1

---

### Post by webereinc on 2011-11-02
Same here - running Ubuntu 10.04 and have iPhone 3GS with IOS 5 - before IOS 5, it used to mount and I could at least move my pictures from phone to Ubuntu file system.  Now, it no longer mounts.

---

### Post by tp21 on 2011-12-07
i am trying to sync my ipad 2 ios5 with my ubuntu 11.10 box and can not do it, although ipad is mounted in nautalits.
any ideas?

---

### Post by GrouchyGaijin on 2011-12-13
So, I have an iPhone 4 running iOS 4.3.5 and a computer running 11.10.  I guess I should not upgrade to iOS 5 then, eh?

---

### Post by roguejedi on 2011-12-17
i made the mistake of ugrading to ios 5 for my ipad. i'm currently running ubuntu 10.04. Nautalis will recognize the ipad, no other app will. i use rhythmbox for my ipod with no issues.  hopefully soon there will be a fix. :(

---

### Post by bshosey on 2011-12-20
While iphone is pluged in run this commands

sudo apt-get install libimobiledevice-utils

idevicepair unpair && idevicepair pair

---

### Post by jnubian on 2011-12-27
i got error code -256

---

### Post by bshosey on 2011-12-27
Please make sure the device is pluged in when this command is ran. Aslo make sure the device is unlocked.

---

### Post by jnubian on 2011-12-27
I did.
it is jailbroken/unlocked on ios 5.0.1 
first command is fine-
got the error when running this line

idevicepair unpair && idevicepair pair

---

### Post by jnubian on 2012-01-09
still error code -256

any fix for this?

---

### Post by dvsguyca12 on 2012-03-02
I have the same problem after running  "idevicepair unpair && idevicepair pair" in terminal I get -256 error. Has there been any updates on a fix?

---

### Post by David Alfonso on 2012-03-09
Same problem here. Running Ubuntu 10.04 Desktop x86.

---

### Post by alkhemista on 2012-03-09
Experiencing this as well on 64-bit Maverick Meerkat. Downloaded and installed newest lib, ran idevicepair, received an error. E_e

---

### Post by skaramanger on 2012-03-15
> **bshosey said:**
> While iphone is pluged in run this commands

sudo apt-get install libimobiledevice-utils

idevicepair unpair && idevicepair pair

Greetings,

I am running kubuntu 11.10 kernel 3.0.0-16-generic.  I installed these libraries and ran the command. lsusb run shows its there,  but it won't mount.  What might I try next?

Thx In advance

---

### Post by squee on 2012-03-17
> **skaramanger said:**
> Greetings,

I am running kubuntu 11.10 kernel 3.0.0-16-generic.  I installed these libraries and ran the command. lsusb run shows its there,  but it won't mount.  What might I try next?

Thx In advance

have you installed iFuse? 
```
sudo apt-get install ifuse
```

Not sure if that's a fix, but I found instructions that included that, and I can mount my ipod 4G iOS 5.1. However when I try and transfer music via Banshee, it appears to convert and transfer, but then doesn't show up in the library. Very frustrating!

---

### Post by Pablo Pablovski on 2012-03-18
> **squee said:**
> have you installed iFuse? 
```
sudo apt-get install ifuse
```

Not sure if that's a fix, but I found instructions that included that, and I can mount my ipod 4G iOS 5.1. However when I try and transfer music via Banshee, it appears to convert and transfer, but then doesn't show up in the library. Very frustrating!

Try deleting a siongle track after adding music, and make sure you eject the iPod rather than just disconnecting it from the cable - that works on mine (3GS / 11.04). 

Seems to be something to do with the database on the iPhone not being re-written by iFuse / libimobiledevice until a delete.

---

### Post by GrouchyGaijin on 2012-03-18
Hi Guys,

I'm running 11.10 with 3.0.0.16-generic and the iphone has 5.1
I installed FUSE as mentioned above.
Now I can can see the music I have on my phone when I launch Banshee. However, I can't add any tracks.
I can drag a track to the phone and it shows up in Banshee as being on the phone.  It does not show up when I check the iphone Music app that replaced (or maybe just had a name change) from the ipod app that was there prior to iOS 5.1.
Additionally after I eject the phone and reconnect it, the song no longer shows as being on the phone in Banshee.

I've tried deleting a song and then adding another with no luck.

Any ideas?

---

### Post by skaramanger on 2012-03-18
I did install it after your note. However, still a no go.  I get the seg fault msg.

Thanx

---

### Post by Wallynm on 2012-03-21
> **bshosey said:**
> While iphone is pluged in run this commands

sudo apt-get install libimobiledevice-utils

idevicepair unpair && idevicepair pair


I had problems when trying to mount the iPhone, jailbroken 5.1 at ubuntu 11.10, it was returning -15 error... But now everything is fine, thanks by the solution above!!!

---

### Post by d4m1r on 2012-04-07
This is still not working for me:

```
damir@Damir-Ubuntu:~$ idevicepair unpair && idevicepair pair
usbmuxd_get_result: Received packet is too small!
usbmuxd_connect: Connect failed, Error code=-1
ERROR: lockdownd_client_new failed with error code -12
```

iPhone 4 and Ubuntu 11.10 :confused:
[FONT=Verdana][/FONT]

---

### Post by YaStrannik on 2012-04-08
Whoever is having the same problem, make sure you get all the available updates for your computer. I don't know what it was, but it fixed the problem for me.

---

### Post by hughr2005 on 2012-04-08
I wasn't aware one could mount an iOS 5 device on Ubuntu. I'll have to have a go.

---

### Post by d4m1r on 2012-04-08
> **hughr2005 said:**
> I wasn't aware one could mount an iOS 5 device on Ubuntu. I'll have to have a go.

Doesn't appear that you can....I have iOS 5.0.1 and an iPhone 4 and it doesn't get recognized at all. Update manager shows no update available for my PC either :confused:

---

