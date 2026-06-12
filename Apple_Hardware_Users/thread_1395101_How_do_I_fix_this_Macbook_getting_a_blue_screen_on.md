---
title: "How do I fix this Macbook getting a blue screen on bootup?"
date: 2010-01-31
forum: Apple Hardware Users
---

### Post by Maheriano on 2010-01-31
My girlfriend's Macbook is doing what everyone else's Macbook is doing, just a blue screen on bootup. I read online this can be fixed by repairing the drives with the setup disc that came with the computer but of course she doesn't have it. Any other way? Can I create the disc somehow?

---

### Post by NoaHall on 2010-01-31
My Macbook isn't doing that.

---

### Post by pwnst*r on 2010-01-31
> **Maheriano said:**
> My girlfriend's Macbook is doing what everyone else's Macbook is doing, just a blue screen on bootup. I read online this can be fixed by repairing the drives with the setup disc that came with the computer but of course she doesn't have it. Any other way? Can I create the disc somehow?

I just asked one of my girl friends and her Macbook's not doing that.

---

### Post by dolphinaura on 2010-01-31
> **Maheriano said:**
> My girlfriend's Macbook is doing what everyone else's Macbook is doing, just a blue screen on bootup. I read online this can be fixed by repairing the drives with the setup disc that came with the computer but of course she doesn't have it. Any other way? Can I create the disc somehow?

Im not sure if this will work, because I dont have a genuine macbook, but use the flags (at bootup)
```

-x

```
to reach safe mode

and 
```

-f

```
to force the loading of all drivers.

---

### Post by Maheriano on 2010-01-31
> **NoaHall said:**
> My Macbook isn't doing that.
> **pwnst*r said:**
> I just asked one of my girl friends and her Macbook's not doing that.Not literally everyone's but if you search Google it happens a lot.

> **dolphinaura said:**
> Im not sure if this will work, because I dont have a genuine macbook, but use the flags (at bootup)
```

-x

```
to reach safe mode

and 
```

-f

```
to force the loading of all drivers.
Thanks, how do I run these flags? It starts up and shows the Apple loading screen, then just goes to a blue screen after a few minutes. That's it.

---

### Post by NoaHall on 2010-01-31
I don't want to google the problem, as there is not enough information for me to find the exact problem.

---

### Post by overdrank on 2010-01-31
Moved to Apple Users

---

### Post by dolphinaura on 2010-01-31
> **Maheriano said:**
> Not literally everyone's but if you search Google it happens a lot.


Thanks, how do I run these flags? It starts up and shows the Apple loading screen, then just goes to a blue screen after a few minutes. That's it.

nvm, im using a different bootloader from the standard mac one, so you need... [http://support.apple.com/kb/HT1455](http://support.apple.com/kb/HT1455)

---

### Post by wheredidrealitygo on 2010-01-31
Hold down the actual X key during the boot sequence. This will interact with the EFI on the motherboard and tell it to boot in safe mode.

---

### Post by MacJack on 2010-01-31
Try boot with verbose mode, It's boot for me once back then when I had an issue.


-s

or

-v

---

### Post by djchandler on 2010-01-31
> **Maheriano said:**
> My girlfriend's Macbook is doing what everyone else's Macbook is doing, just a blue screen on bootup. I read online this can be fixed by repairing the drives with the setup disc that came with the computer but of course she doesn't have it. Any other way? Can I create the disc somehow?

[http://support.apple.com/kb/TS1545](http://support.apple.com/kb/TS1545)

Option C looks like your answer if you are running leopard. I suppose the same could apply if you just upgraded to snow leopard. It removes unsupported third party enhancements after upgrading the OS, or perhaps installing the unsupported enhancement.

---

### Post by Maheriano on 2010-01-31
Got it, thanks guys. I booted to the command terminal and ran fsck but it said the volume check failed. So I ran fsck -f to force a disk check and that fixed the volume. A reboot booted right up.

---

### Post by Maheriano on 2010-04-02
Having this same problem again with the same computer. I tried everything I tried before and nothing works.

---

### Post by Maheriano on 2010-05-09
So now this is happening again and the previous fixes are no longer working. I've decided to copy everything off the hard drive onto another machine and reinstall the operating system to speed things up but I'm not really sure how to do that. I don't have the install discs that came with the computer and I don't know anyone else with another Macbook. Is there a place I can download the operating system or something? Can I use someone else's CD? What's the operating system even called for this? Is there a simple button configuration I can hold down on bootup to format it and reinstall fresh?

---

### Post by wheredidrealitygo on 2010-05-10
Depends entirely on which version of the operating system it is.. it's called Mac OS X (X being the roman numeral 10, so Mac OS 10), and the 'version' depends on which number it is, 10.4 is Tiger, XP timeline, 10.5 is Leopard, Vista timeline, 10.6 is Snow Leopard, windows 7 timeline.

The actual disc is dual layered, so if you manage to 'acquire' an .iso of it, keep that in mind.. another persons disc will likely work, but one from that particular model would work best. Hold option or c during the boot to boot off the disc when you get it, there is a 'disk utility' (that's what it's called) on the disc to allow you to format/repartition the hard drive.

---

### Post by Maheriano on 2010-05-10
Thanks, that's awesome. I found out she was running Leopard, can she upgrade to the newest version for free like Linux? Or is it paid like Windows? So if she wanted to install Leopard again, can she download it off the Apple site or something?
I hate Apple, I really do.

---

### Post by wheredidrealitygo on 2010-05-10
<rant> 'Upgrading' tends to break more than it fixes. Always clean install with every OS, be it Win/Lin/Mac. Saves headaches in the long run, I can't count how many OS installations I have done/fixed, just don't upgrade, it breaks stuff.

</rant>

To the issue:

You can go out to any [[COLOR="RoyalBlue"]Apple store[/COLOR]]("http://store.apple.com/ca/product/MAC_OS_X_SNGL")/[[COLOR="RoyalBlue"]Future Shop[/COLOR]]("http://www.futureshop.ca/en-CA/product/mac-os-x-snow-leopard-upgrade/10129665.aspx?path=733865820e2d6c66c02530a579b4b3e7en02&lid=fp-10129665-macosxsnowleopardupgrade-en")/place that sells Apple peripherals and buy a brand new copy of Snow Leopard, the newest one, for $35, assuming this is of course an Intel box and not an older PowerPC processor model. The 'upgrade' disc as they call it can do clean installs perfectly fine, and normally, this is your cheapest legal route assuming you can't find one from a friend.

I'm not going to mention other/possibly illegal methods, use your imagination.

---

