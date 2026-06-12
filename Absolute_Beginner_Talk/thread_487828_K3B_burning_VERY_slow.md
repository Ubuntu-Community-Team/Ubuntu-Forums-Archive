---
title: "K3B burning VERY slow"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by AriciU on 2007-06-29
CD's that is. I have no problem burning DVD's at 10-16x but CD's (audio cd for example) burn very slow... at about 1-4x. It's horrible.

Any ideas?

---

### Post by Seisen on 2007-06-29
Are you using a seperate burner or a combo drive?

---

### Post by _simon_ on 2007-06-29
I assume the CD's you are using are capable of being burnt at over 4x ?

I've burnt CDRWs quicker than 4x without changing any of k3b's settings.

---

### Post by NewJack on 2007-06-29
I've been using it alot lately and haven't noticed it being slow.  Maybe, try removing and reinstalling it from Synaptic.

---

### Post by AriciU on 2007-06-29
Think i'll try some other software. I burn them at 52x in windows without problems. It's a combo drive of course.

---

### Post by bigken on 2007-06-29
could it be that its converting mp3 back to wave while its burning ?

---

### Post by AriciU on 2007-06-29
Don't think so. It's converting when i'm adding them. Not when i start the burn.

---

### Post by tarek on 2007-06-29
Have you tried Gnome baker? It works for me better than k3b
```
sudo aptitude install gnomebaker
```

---

### Post by AriciU on 2007-06-29
I'll give it a shot when i need to burn something else. Thanks

edit: i see that it has no DVD ISO Image burn unfortunately.

---

### Post by motin on 2007-08-30
Please file your experiences in the bug report: [https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/31709](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/31709)

---

### Post by TeaSwigger on 2007-08-30
...ah I'm also getting pathetic writing performance from my optical drives, but thought it was something I did that I'd get around to sorting. Now I'm noticing the posts on it. So I thought I'd follow that link to the bug report too. Bug #31709, first reported on **2006-02-17**?! Confirmed by many users with different ubuntu blends? Can't describe how I feel about it..., kind of embarrassed? Annoyed too, I was hoping to delete Windows and reclaim the disc space. So much for that! Maybe the "problem" is with me then, but I don't see the point to filing a bug report about this. I'm a bit puzzled by the situation.

It's a known problem affecting hardware functionality, it's this widespread and has been since at least Breezy beta and it still isn't fixed? 

It's a medium priority?

It's assigned to k3b and kubuntu when many people do seem to have been having the same problems on any app on any ubuntu? Wouldn't the problem be cdrtools or somewhere further down? Shouldn't ubuntu team have made a new writing layer or whatever it's called and fixed it? Or am I misunderstanding the way it works (which I could be...)?

Y'know if I were completely new to linux and experienced my hardware suddenly having writing performance this bad, and if writing performance were more of a priority to me (as it undoubtedly is to plenty of computer users these days)... Mightn't this be turning away a lot of folks? Awful scanner support I can grasp, in consideration of proprietary drivers and that sort of thing. Tough noogies. But this? Seems this should have been fixed over a year ago.

---

### Post by TeaSwigger on 2007-08-31
After all that ranting, I have an observation to offer which may hopefully be more useful.

Keeping an eye on the buffer displays, which is about as thrilling as watching water boil, I wasted some perfectly good media and performed a set of test burns of the same DVD Video ISO on my NEC 3540A DVD drive (IDE 80 ribbon as are all disc devices on the old PIII 933mhz PC). All burns succeeded. Results as to performance as follows:

1) kubuntu / DVD Decrypter (via WINE)
kubuntu / k3b (with root priv etc configured)
kubuntu / Gnomebaker
ISO source on ext3 partition

Observed: Inability to reach top media speed (16x). Top speed observed was 11.5x. Buffer at 94 - 96% at best with extended periodic bouts of losing all buffer resulting in a drop to a slow burning speed (4 - 9x in such an event). Device buffer, that is; software buffers remained at 93% to full. A pulsing pattern during worst instability.

2) Windows 2kPro / DVD Decrypter
Windows 2kPro / Nero 6.6
ISO source on NTFS partition

Observed: Flawless performance reaching media's top speed (~16x). Device and software buffers full and stable throughout burn. Gotta love this good ol' box.

3) Windows 2kPro / DVD Decrypter
Windows 2kPro / Nero 6.6
ISO source on ext3 partition (via ext2nfs driver)

Observed: The interesting part. I observed the exact same performance during this windows burn as during the kubuntu burn. Instability at what seemed to be the same points in the burn to what seemed to be the same degrees.

Hm.

---

### Post by tim71 on 2007-09-12
I would say, that this _may_ be hardware-related thing. 

I had Pioneer DVR-107 burner for some years and now I got a Samsung SH-182D for double layer burning etc. This was before switching to Ubuntu and I had no performance problems with this drive using Nero 6 under Windows. 

Then this problem appeared when I started burning with k3b and this Samsung burner (could not get speeds above 4...6x, sometimes even much below that).

Because occasionally i got some other problems as well, I started to think, that this thing just may be about something else and bought a Pioneer DVR-112 burner. For now I had only few disks done with it, but it's already obvious, that I am achieving burning speeds higher than ever with that Samsung burner under Linux...

---

### Post by badguyanil on 2007-09-12
Read somewhere in the threads the line..> K3B does all that Nero does plus additional...
Well i have tried out burning a few CD's and god all of them have given me buffer overrun errors and screwed the cd's.. have tried speeds from 48x down to 16x all give the same damn error. No such problems with nero!!! never!!! and i can burn cd's at 48x everytime.... somethings look good only in text i guess!

---

### Post by tenjin1 on 2007-09-14
I also have a NEC 3520A and using K3B on Feisty. When I burn a DVD,  in the "Burn Medium" popup window, in the "speed" drop-down menu, my only choices are "Auto", "ignore" and "2.4x". If I choose "Auto" it seems to burn at 2x which is _really_ slow. If I choose "Ignore" it burns at full capcity: 16x.  This is a combo drive, capable of burning DVD's and CD's. The CD burning speeds are all detected when I insert a CD, but not DVD.

I am using K3B version 3.5.6. When I was using Edgy, I could use the drop-down speed menu and choose 8x. I'm not sure which version that was but I do know it was an earlier version, but it did detect all capable speeds of my DVD Burner. I _always_ used K3B for all my burning needs. But now that I can't burn at my preferred writing speed (8x), I'm thinking of trying something else unfortunately.

So as far as what someone said earlier that its a hardware issue I'm not so sure, because this didn't used to happen on the same drive with an earlier version of K3B. Isn't there a config file somewhere for K3B that I can manually add the proper device burning speeds of my NEC DVD Burner so it will reflect all of them (especially 8x) in the "Speed" drop-down menu?

---

### Post by tim71 on 2007-09-16
3.5.6 is the KDE version... I tried different versions of k3b and noticed the same thing with 1.0.1 - this lack of the speed selections. 

Now with 1.0.3 this problem seems to be solved for me (should be available on feisty repositories).

---

### Post by TeaSwigger on 2007-09-17
Tried K3b v1.0.3. Ensured perms were right via k3bsetup. Result: Same appalling performance.

Uninstalled K3b. Reinstalled Gnomebaker. Result: Gnomebaker works perfectly at the highest available drive / media speed.

Reverse of same: k3b still won't burn above 4x for CD and 2.4x for DVD. 

Gah... Really liked k3b but I guess Gnomebaker it must be.

---

### Post by bobpur on 2007-09-17
When I use K3b, I get a popup that says DMA needs to be turned off or really slow burn times will result. Have you tried turning it off? This popup is usually one of the first to show when K3b is activated. 
I've read down thru this thread and no one has mentioned it.
Just my two cents worth.
                                                       Good Luck.

---

### Post by tenjin1 on 2007-09-17
> **tim71 said:**
> 3.5.6 is the KDE version... I tried different versions of k3b and noticed the same thing with 1.0.1 - this lack of the speed selections. 

Now with 1.0.3 this problem seems to be solved for me (should be available on feisty repositories).

Ok will try 1.0.3. and see if it detects all my burning speeds, thanks for the reply.

---

### Post by sidey1234 on 2007-09-17
This may be down to to direct memory access (dma) not being enabled on the disk.

sslabs:/mnt/lol/sideshow # hdparm /dev/hda


/dev/hda:
 multcount    = 16 (on)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)                 <----- check for this
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 80293248, start = 0


you may find that it is off.

if it is try hdparm -d 1 /dev/hda,
 if it throws back error messages, you may need to look at recompiling the kernel as you may have unsupported hardware.

a google search on recompiling kernel and dma would throw back enough results to keep you busy for a bit

where hda is your cd/dvd writer :)

---

### Post by tenjin1 on 2007-09-17
> **sidey1234 said:**
> This may be down to to direct memory access (dma) not being enabled on the disk.

sslabs:/mnt/lol/sideshow # hdparm /dev/hda


/dev/hda:
 multcount    = 16 (on)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)                 <----- check for this
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 80293248, start = 0


you may find that it is off.

if it is try hdparm -d 1 /dev/hda,
 if it throws back error messages, you may need to look at recompiling the kernel as you may have unsupported hardware.

a google search on recompiling kernel and dma would throw back enough results to keep you busy for a bit

where hda is your cd/dvd writer :)

Ah Ha...I had a feeling this was related to DMA.

I did..```
tenjin@Ubuntu:~$ hdparm /dev/scd0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
tenjin@Ubuntu:~$ hdparm -d 1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```

So you hit the nail on the head with that one..thanks for the reply at least I know what is going on now...thanks.

---

### Post by r3v3ng3 on 2007-09-19
For everyone who is still having problems similar to this please make sure you update your firmware.

I had this problem with the LG GSA-4160B using nero linux and gnomebaker. The problem was resolved when i updated the firmware from A300 to A306. Apparently, some manufacturers limit the burning speed of their drives when being used on free/GNU software. For LG, you have to do this on a windows machine because they do not provide Linux drivers.

Good luck!

EDIT: This was actually partly resolved. I can now burn DVDs at 8x rather than 4x. Still want to get to 16x though.

---

### Post by TeaSwigger on 2007-09-19
> **sidey1234 said:**
> This may be down to to direct memory access (dma) not being enabled on the disk.

Ah but in the newer kernels, drivers have evidently been changed to where hdparm and its DMA settings are no longer relevant. This can be seen in the change from drives being listed as /dev/hd* to /dev/s* where hd* was managed by hdparm and s* drives are not. I don't know much about that stuff and haven't found any answers as to how one with a drive listed as /dev/sc* determines the DMA state, or even if such a setting is relevant. The question has been posed in a few threads by different people but no one answered that I've seen. k3b was burning fine for me until that kernel transition. Yet hd* or s*, as mentioned above, Gnomebaker is burning at full speed just fine while k3b is not.

> **r3v3ng3 said:**
> For everyone who is still having problems similar to this please make sure you update your firmware.

A good thing to check in troubleshooting but in my case the firmware was and is up to date.

---

### Post by r3v3ng3 on 2007-09-19
> **TeaSwigger said:**
> After all that ranting, I have an observation to offer which may hopefully be more useful.

Keeping an eye on the buffer displays, which is about as thrilling as watching water boil, I wasted some perfectly good media and performed a set of test burns of the same DVD Video ISO on my NEC 3540A DVD drive (IDE 80 ribbon as are all disc devices on the old PIII 933mhz PC). All burns succeeded. Results as to performance as follows:

1) kubuntu / DVD Decrypter (via WINE)
kubuntu / k3b (with root priv etc configured)
kubuntu / Gnomebaker
**ISO source on ext3 partition**

Observed: Inability to reach top media speed (16x). Top speed observed was 11.5x. Buffer at 94 - 96% at best with extended periodic bouts of losing all buffer resulting in a drop to a slow burning speed (4 - 9x in such an event). Device buffer, that is; software buffers remained at 93% to full. A pulsing pattern during worst instability.

2) Windows 2kPro / DVD Decrypter
Windows 2kPro / Nero 6.6
ISO source on NTFS partition

Observed: Flawless performance reaching media's top speed (~16x). Device and software buffers full and stable throughout burn. Gotta love this good ol' box.

3) Windows 2kPro / DVD Decrypter
Windows 2kPro / Nero 6.6
**[B]ISO source on ext3 partition (via ext2nfs driver**)[/B]

Observed: The interesting part. I observed the exact same performance during this windows burn as during the kubuntu burn. Instability at what seemed to be the same points in the burn to what seemed to be the same degrees.

Hm.

Hmmm indeed. You only achieved fast speeds when the iso was on NTFS.. coincidence? maybe.. .
I don't know enough about the difference between ext3 and NTFS filesystems to make a proper judgement. Could someone try burning a .iso from an NTFS partition whilst in Linux and report what happens?

---

### Post by tenjin1 on 2007-09-19
> **TeaSwigger said:**
> Ah but in the newer kernels, drivers have evidently been changed to where hdparm and its DMA settings are no longer relevant. This can be seen in the change from drives being listed as /dev/hd* to /dev/s* where hd* was managed by hdparm and s* drives are not. I don't know much about that stuff and haven't found any answers as to how one with a drive listed as /dev/sc* determines the DMA state, or even if such a setting is relevant. The question has been posed in a few threads by different people but no one answered that I've seen. k3b was burning fine for me until that kernel transition. Yet hd* or s*, as mentioned above, Gnomebaker is burning at full speed just fine while k3b is not.

True, mine was also listed as /dev/hd in the older kernel and now is /dev/sc in 2.6.20-16. Gnomebaker is also burning at correct speed for me as well, just not k3b.

---

### Post by sidey1234 on 2007-09-19
> **tenjin1 said:**
> Ah Ha...I had a feeling this was related to DMA.

I did..```
tenjin@Ubuntu:~$ hdparm /dev/scd0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
tenjin@Ubuntu:~$ hdparm -d 1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```

So you hit the nail on the head with that one..thanks for the reply at least I know what is going on now...thanks.

no worries :)

---

### Post by Miroku on 2007-11-04
damn, k3b was so kool. it worked wonderfully for such a long time with feisty and then it just got stuck at 2.4x with dvds. i was hoping this would be fixed somehow when i upgraded to gutsy, but no luck! argh.

well gnomebaker is good too but it just doesnt have the features that i got used to in k3b. at least the speed is normal though.

i even told people that k3b is better than nero6, lol.

---

### Post by Fred_E _krugar on 2007-11-04
> **tarek said:**
> Have you tried Gnome baker? It works for me better than k3b
```
sudo aptitude install gnomebaker
```


 I would have to agree GnomeBaker seems to run better on Gnome than K3B does.

---

### Post by corte123 on 2007-11-09
Hi everyone, this is how i got k3b to burn my dvd media at full 16x speed ,an i got my dvd+rw media to burn at a full 4.1x   all i did was set the burn speed to ignore !  solved my problems.   please post if it worked for you

---

