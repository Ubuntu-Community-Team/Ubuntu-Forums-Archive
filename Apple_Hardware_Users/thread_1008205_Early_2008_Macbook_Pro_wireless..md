---
title: "Early 2008 Macbook Pro wireless."
date: 2008-12-11
forum: Apple Hardware Users
---

### Post by Moptop650 on 2008-12-11
Hey,
I ran the latest version of Ubuntu off a liveCD yesterday, on my Early 2008 Macbook pro (Core2duo, 15"), and, everything went great, except - the wireless did not work.

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

I read there that on the Core2Duo MBPs, it should work out-of-the-box. 

I guessed at the time it was because I was Live CD-ing instead of an actual HD install, but I would like to confirm this.

(Or I had to set something up that I didn't know about, I'm new to Ubuntu, and have never worked with wireless on Linux before.)

Any help would be appreciated.

---

### Post by beauman on 2008-12-11
You are right, after you have activated the proprietary driver from broadcom, it will ask you to make a reboot, which is senseless for a  live CD.

see also: [https://help.ubuntu.com/community/MacBookPro_Penryn]("https://help.ubuntu.com/community/MacBookPro_Penryn")

(the link you posted is for a different hw)

---

### Post by Moptop650 on 2008-12-11
Hey, thanks for the link.

> These steps are no longer necessary with the latest updates applied in Hardy, nor in Intrepid. Simply enable the wireless driver in Hardware Drivers.

It mentions that, so would I not have to do the ndiswrapper stuff?

---

### Post by beauman on 2008-12-11
Yes, again you are right. Just go to Systems -> Hardware Drivers and activate "Broadcom STA wireless driver", reboot. :)

---

### Post by Moptop650 on 2008-12-11
Ok, thanks again =]

One issue came up - I have rEFIt installed because I already have a Mac and Linux partition, but now when I choose the Ubuntu partition in rEFIt, it goes to a black screen with the white blinking underscore in the upper left - what could this mean? When I installed Ubuntu I installed the Grub bootloader to /dev/sda4 partition, (The ubuntu one).

---

### Post by beauman on 2008-12-11
maybe you have to sync the partition table with refit. if you don't have 
have an english keyboard, "y" and "z" may be swapped. 

[https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation]("https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation")

You did install grub correct.

Come back here if it still not works.

cheers, beauman

EDIT: 

I had a look at [https://help.ubuntu.com/community/MacBookPro_Penryn]("https://help.ubuntu.com/community/MacBookPro_Penryn"). It seems that the keyboard section is out of date. I updated the [keyboard section of the MB 4,1 for Intrepid]("https://wiki.ubuntu.com/MacBook/SantaRosa#Keyboard") yesterday. I was wondering, if this section can also be applied to the MB Pro. If you like to, you can test it for me, thanks!

---

### Post by Moptop650 on 2008-12-11
I ran it's partition manager thing, it did its stuff, and, now it sits on the penguin image when I select the Ubuntu partition. I left it there for about 3 minutes, I had heard the hard drive head park.

Edit: Windows XP partition does the same thing, OsX is still fine.

I also installed a ext2 reader so I can access the Ubuntu partition from OsX. Would any relevant information be on it?

---

### Post by beauman on 2008-12-11
So you had OS X and XP and rEFIt installed, before you installed 
Ubuntu? 

The driver for ext2 is quite buggy. If you like to access the
data boot with the install CD. Before you mount the ext3 partition
run fsck.ext3.

Does it look to you like a hd crash?

---

### Post by Moptop650 on 2008-12-11
To clarify, I installed in this order - OsX, Windows XP, Ubuntu, rEFIt.

I did this in OsX, not sure if it's what you meant, but...

```
MBP:~ Dave$ sudo fsck /dev/disk0s4
** /dev/rdisk0s4
BAD SUPER BLOCK: MAGIC NUMBER WRONG

LOOK FOR ALTERNATE SUPERBLOCKS? [yn] y

SEARCH FOR ALTERNATE SUPER-BLOCK FAILED. YOU MUST USE THE
-b OPTION TO FSCK TO SPECIFY THE LOCATION OF AN ALTERNATE
SUPER-BLOCK TO SUPPLY NEEDED INFORMATION; SEE fsck(8).
MBP:~ Dave$ 

```

Should I try re-installing ubuntu on ext3 instead?

---

### Post by beauman on 2008-12-11
no. I have my root system also on an ext2 system. The driver 
under OS X is no good, forget it. Use a boot CD and see what
fsck says and if you can mount it.

How long did you use Win XP?

Test, if you can see the XP partition from the boot CD.

---

### Post by Moptop650 on 2008-12-11
Well I was messing around and clicked Verify Disk in OsX on the ubuntu partition, and it kernel paniced, but now rEFIt can boot into ubuntu, (I'm in it now :D).

I've got class for a few hours, I'll post back when I try that.

Thanks so much for all the help so far! :)

---

### Post by beauman on 2008-12-11
> **Moptop650 said:**
> Well I was messing around and clicked Verify Disk in OsX on the ubuntu partition, and it kernel paniced, but now rEFIt can boot into ubuntu, (I'm in it now :D).

I've got class for a few hours, I'll post back when I try that.

Thanks so much for all the help so far! :)

Yes, you get a blue screen, when you try to force mounting 
an ext2/3 partition under OS X. Can you still have a look at the link
I posted about the keyboard? 

Cheers, beauman

---

### Post by beauman on 2008-12-12
Hi again!

What I exactly do want to know, is the behavior of the caps lock LED on the MBP 4,1. 

In the wiki for the MB 4,1, I wrote a section about right and middle click emulation and about a [bug]("https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/218263") with the caps lock led. Now I like to know, if the MBP behaves the same as the MB.

Yesterday somebody with a MBP reported, that my proposed work-around does not work ([http://ubuntuforums.org/showthread.php?t=1002463]("http://ubuntuforums.org/showthread.php?t=1002463")), but it seems that in his case a different program caused the same bug. (or maybe the bug comes from a deeper layer both programs are using)

So your fresh install of Intrepid is just perfect for me.

First I like you to confirm the bug and the correct behavior of the mouse emulation: The caps lock led should be broken and mouse emulation should be available with Fn+F12 for right click.

Next I want you to remove mouseemu:

```
sudo apt-get remove mouseemu
```

You have to reboot after this step, because your keyboard will be broken. After the reboot the caps lock led should work.

That's all I like to know at the moment. If you like to, you can follow the whole section mapping middle & right click to the two cmd keys. It would of course be nice to know, if the complete section can be applied to the MBP.

If you just like to restore the original config, you install mouseemu with 

```
sudo apt-get install mouseemu
```

Thanks for your help, beauman

---

### Post by hyperboloid on 2008-12-12
Beauman, please see [http://ubuntuforums.org/showthread.php?t=1002463#8]("http://ubuntuforums.org/showthread.php?t=1002463#8") for the answer to your question.

---

### Post by cyberdork33 on 2008-12-12
> **Moptop650 said:**
> I ran the latest version of Ubuntu off a liveCD yesterday, on my Early 2008 Macbook pro (Core2duo, 15"), and, everything went great, except - the wireless did not work.

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

I read there that on the Core2Duo MBPs, it should work out-of-the-box.
If you have an early 2008 MacBook Pro, that is not the correct documentation. Please see the "Before You Post" link in my signature to properly identify your Mac version and find the appropriate documentation.

---

### Post by Moptop650 on 2008-12-13
> **beauman said:**
> JFirst I like you to confirm the bug and the correct behavior of the mouse emulation: The caps lock led should be broken and mouse emulation should be available with Fn+F12 for right click.

Yes, it is like that (Although it's just F12 since I set up pommed to do it that way)


I'll remove it and post back in a second....

Edit: Yes, that fixed it :D.


By the way, is there any say to boost the volume level? I've turned it up anywhere I could find in the settings, but it isn't as loud as in Mac/Windows.

Also, I installed the kubuntu-desktop package because KDE looks amazing - but KDE runs SLOWWWW, Xorg uses ALL the cpu when I do anything... Any ideas?

---

### Post by beauman on 2008-12-14
> **Moptop650 said:**
> 

By the way, is there any say to boost the volume level? I've turned it up anywhere I could find in the settings, but it isn't as loud as in Mac/Windows.

Also, I installed the kubuntu-desktop package because KDE looks amazing - but KDE runs SLOWWWW, Xorg uses ALL the cpu when I do anything... Any ideas?

You are not the only one: [http://ubuntuforums.org/showthread.php?t=1002431](http://ubuntuforums.org/showthread.php?t=1002431)

Gnome works like a charm.

The MacBook has a problem with the midrange speaker. I don't know, if this is also true for the MacBook Pro.

And I also found this: [http://ubuntuforums.org/showthread.php?t=1009905](http://ubuntuforums.org/showthread.php?t=1009905)

---

### Post by Chrisj303 on 2008-12-14
It is normal to get a blank screen, with just a flashing cursor after installing Ubuntu -this will continue until you use rEFIt's partition tool.

After using that, you need to reboot once or twice, before it will boot correctly - the first couple times, it is likely to get stuck on the "grey penguin" screen.

---

