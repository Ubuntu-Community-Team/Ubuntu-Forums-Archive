---
title: "Ubuntu won't boot now, PPC"
date: 2009-04-24
forum: Apple Hardware Users
---

### Post by joshdudeha on 2009-04-24
I installed ubuntu 9.04 jaunty off the Alternate CD on my Power Mac G4.
It was running fine, and yaboot works.
But, now when I press 'L' to boot into Linux, and press enter on the next screen, it boots up but just stops on a black screen with a white "_" in the top left, which isn't even flashing.

It didn't come up with the splash screen in the first time but it won't boot at all now.
I can't think why :/

Could someone help me please? (:

---

### Post by tiresia on 2009-04-24
Did you try to edit your xorg.conf file?
Can you switch to another console after booting, pressing ctrl-alt-F1 or ctr-alt-F2?

---

### Post by joshdudeha on 2009-04-24
I didn't edit my xorg
But I remember trying to hibernate and it failing; so I turned it off via the power button.
I can not get into the terminal that way :/
Its just stuck on the screen

---

### Post by stream303 on 2009-04-24
Can you try passing either one or both of these kernel parameters at that second-stage yaboot boot prompt:

```
Linux nosplash
```

or

```
Linux nosplash video=ofonly
```

If either one or both of those work, you can make these setting permanent by putting them into the APPEND= line of /etc/yaboot.conf and then making the system aware of that change.

Since you are running ubuntu, edit that file with root permissions and save the changes:

```
gksudo gedit /etc/yaboot.conf
```

Then, make the system aware of those changes with:

```
sudo ybin -v
```

One of these two options should work - barring any further configurations that might need to be done to your /etc/X11/xorg.conf file.

At least this way, you can get over the first hurdle of not being able to get past the locked-up screen.

For example, here is what a snippet of my /etc/yaboot.conf looks like with the nosplash modification on my 9.04 box:

...SNIP...
```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        **append="quiet nosplash"**

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        **append="quiet nosplash"**
```

Don't forget the quotations marks, and be sure to do a *sudo ybin -v* to make the Mac aware of this change.

---

### Post by joshdudeha on 2009-04-24
Thanks :D I will try that when I get the chance, I'm in my mac at the moment.

Cheers :D

---

### Post by joshdudeha on 2009-04-24
Right. I tried Linux nosplash

And it says 
"Loading, please wait..
/scripts/local-premount/resume ...something..
kinit: trying to resume some path or over"

and it freezes again

---

### Post by stream303 on 2009-04-24
Hmm.. I wonder if what you were seeing was the typical scenario where the system is looking for the hibernation or sleep file - which is something most Macs can't do successfully.

When you said it was working fine, did you go into power management and enable the sleep feature?  (the default is never)

I vaguely remember coming across this before..

Are you dual-booting?  If so, can you reboot by holding down the alt/option key, and choosing the Linux icon as the boot device?

Kind of going all over the place here...

---

### Post by joshdudeha on 2009-04-24
That's what I did. I wanted to see if it could sleep, like in Mac OS X and when It failed I went to school.
I came back and came to this.
I have tried that as well, but it just comes up to where I keep getting frozen at, is there anyway i can 'rescue' it? I have the alternate CD
And I am dual booting btw

---

### Post by stream303 on 2009-04-24
Another thought:

By working-fine, do you mean that the installation process seemed to work, but on your first reboot is when this problem occurred?

If so, it might be due to your PowerMacs hardware if it has multiple hard drive controllers - where the install is fine, but one has to go back in and manually fix the UUID's in /etc/fstab and whatnot.

What machine do you have?
[http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html](http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html)

This might help nail it down, and which drive (if you have multiple ones) are you using for Ubuntu?

---

### Post by joshdudeha on 2009-04-24
Right. I installed it.
And have booted from it about 5 times, and it has been normal every time.

Only until I put it on hibernate did this happen.
I have a Power Mac G4 Mirror Drive Doors; Dual 867Mhz Processor
I have one 60GB Baracudda Drive with Mac on it
and an 80GB one with Ubuntu on it.
But it's been fine up till now.

---

### Post by joshdudeha on 2009-04-25
Would you know how to rescue this? ;D

---

### Post by joshdudeha on 2009-04-25
Ah sweeet ;D It boots now.
I didn't do anything to it, but it's working great again :D

Thanks for your help.

---

