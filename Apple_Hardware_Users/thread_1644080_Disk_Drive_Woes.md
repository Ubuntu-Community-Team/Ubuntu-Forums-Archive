---
title: "Disk Drive Woes"
date: 2010-12-12
forum: Apple Hardware Users
---

### Post by Lodbrok on 2010-12-12
Greetings!

I am using an iSight 1.9 GHz iMac (PPC, of course). I'd like to install Ubuntu 10.10 on an external HD of mine.
The problem is, my CD drive is broken, so I can't use a burned Live CD.

I tried formatting a thumb drive into HFS+ and copied the contents of the 10.10 .iso onto it. After some fiddling with cmd + opt + o + f (a.k.a. Open Firmware;)), the system would attempt to boot off the USB drive, however, I'd get that flashing question mark folder icon which means that no OS could be found.

So, the question is, what other methods could I try to boot into Linux, or, failing that, how could I install Linux without booting into it?

Thanks.

---

### Post by linuxopjemac on 2010-12-13
just dd the contents of an iso to the thumb drive

```
sudo dd if=/point/to/your/iso of=/dev/your_thumb_drive
```

Be careful that you are sure which device is what. This can seriously screw your data.

---

### Post by Lodbrok on 2010-12-13
I figured I had always made a small typo during Open Firmware - txbi instead of tbxi makes a difference. I'll try that again, thanks.

Also, for a rather low-end PPC like mine, is 10.10 really a good choice?

---

### Post by shawnhcorey on 2010-12-13
> **Lodbrok said:**
> So, the question is, what other methods could I try to boot into Linux, or, failing that, how could I install Linux without booting into it?

I don't know if these will work on your machine but you can give them a go.

[LIST]
[*] [HOWTO Create A Bootable USB Drive From An ISO Image For Apple PowerPCs In Linux]("http://sites.google.com/site/shawnhcorey/howto-create-a-bootable-usb-drive-from-an-iso-image-for-apple-powerpcs-in-linux")
[*] [HOWTO Boot Apple PowerPCs From A USB Drive In Open Firmware]("http://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware")
[/LIST]

---

### Post by Lodbrok on 2010-12-13
Thanks, that helped a bit.
My computer now actually (attempts?) to boot into Linux, but after leaving Open Firmware (for following the second link's instructions) I am greeted by the grey screen with a prohibition sign instead of the dark grey apple with the wheel under it. I'm trying with 10.04 now, after that, I am at loss.

---

### Post by linuxopjemac on 2010-12-14
Install MintPPC 9.

---

### Post by Lodbrok on 2010-12-14
> **linuxopjemac said:**
> Install MintPPC 9.

Your own Linux seems nice and I'd like to install it, but I still get that 'Prohibitory sign' error.

Resolution, anyone? Please?

---

### Post by linuxopjemac on 2010-12-14
What do you mean with 'Prohibitory sign' ?

---

### Post by Lodbrok on 2010-12-14
> **linuxopjemac said:**
> What do you mean with 'Prohibitory sign' ?

As soon as I type

```
boot usb1/disk@1:2,\yaboot
```

the screen changes a few  times, I see some text, then I see a light grey background with a slashed circle instead of the dark grey apple.

[IMG]http://farm1.static.flickr.com/31/45459446_038f5cdff9.jpg?v=0[/IMG]

Like this, but without the wheel underneath.

---

### Post by linuxopjemac on 2010-12-14
I always boot with:
```

boot usb1/disk@1:2,\\yaboot
```

note the double \\

---

### Post by shawnhcorey on 2010-12-14
> **linuxopjemac said:**
> I always boot with:
```

boot usb1/disk@1:2,\\yaboot
```

note the double \\

I'm not sure that will always work.  I've been told that the double backslash means:  1) to search the device for the file, or 2) it is a short-cut notation for \System Files\

I guess it depends on where your yaboot is located.

---

### Post by Lodbrok on 2010-12-14
Hey, I'm definitely interested in your MintPPC.
Managed to find what prevented me from booting, no longer getting the prohibition sign.

Now, the following: Whenever I type 'expert' or 'expert video=ofonly', it loads.
Some moments later, it mentions something about memory violations in
```
%SRR0: 00000000.01403948
```
and
```
%SRR1: 10000000.00083030
```
 I can't quite figure out what that means, or what to do.

NOTE: This above is for MintPPC 9. I'll try with Ubuntu and report what happened.

---

### Post by Lodbrok on 2010-12-14
Ubuntu works like a charm, writing from it as I speak.
Linuxopjemac, I hope you've got an idea what I could do ;)

---

### Post by linuxopjemac on 2010-12-14
This memory thing I can't help you with, I have never seen it.

---

### Post by Lodbrok on 2010-12-14
Hm, too bad.

That aside, my fans are now always roaring at full speed, and thus, the computer isn't very quiet. How can I change that?

---

