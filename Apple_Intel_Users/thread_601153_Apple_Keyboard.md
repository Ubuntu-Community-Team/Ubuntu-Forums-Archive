---
title: "Apple Keyboard?"
date: 2007-11-02
forum: Apple Intel Users
---

### Post by Sunnz on 2007-11-02
Just wondering how well does the new thin Apple Wired Keyboard work with Ubuntu, does everything works, volume buttons, Exposé, etc?

Thanks.

---

### Post by Levo75 on 2007-11-03
> **Sunnz said:**
> Just wondering how well does the new thin Apple Wired Keyboard work with Ubuntu, does everything works, volume buttons, Exposé, etc?

Thanks.

Everything works like a charm.

But can some one tell me what the F13-F16 buttons are for?

---

### Post by cyberdork33 on 2007-11-03
> **Levo75 said:**
> Everything works like a charm.

But can some one tell me what the F13-F16 buttons are for?
They don't do anything!

Ok, well on my older non-aluminum apple keyboard F14 -F16 are in the same location as 'Print Screen', 'Scroll Lock', and 'Break' on a standard keyboard. IDK if the perform the same functions though.

---

### Post by Levo75 on 2007-11-04
> **cyberdork33 said:**
> They don't do anything!

Ok, well on my older non-aluminum apple keyboard F14 -F16 are in the same location as 'Print Screen', 'Scroll Lock', and 'Break' on a standard keyboard. IDK if the perform the same functions though.

Thanx mate.

---

### Post by rubberglove on 2007-11-04
> **Levo75 said:**
> Everything works like a charm.

But can some one tell me what the F13-F16 buttons are for?

Hi - 

Did you have to do anything special to get the 'Fn' key to work? 
I got the same keyboard last week - and love it - but the 'Fn' key (and so the volume keys and brightness keys) doesn't seem to do anything... 

Checking it in Xev, it has no effect at all, alone or in combination with other keys.

Maybe I need to adjust some X or gnome settings?

From what I understood, the 'special keys' would require a kernel patch?

---

### Post by WinterWeaver on 2007-11-04
I saw a special keyboard config tool in Add/Remove Programs. (Gutsy)

Only looked at it very very briefly, but there may be configuration for apple keys... worth checking it out :)

good luck

WW

---

### Post by andreapl25 on 2007-11-04
Hello!
I have a problem with my keyboard. In my macbookpro intel, in the ubuntu the key Alt-gr doesnt work. I have a problem because I need the characters to work in pd 'cause i can't paste...
I've just had a look in the keyboard preferences , but I think that I have it ok...
Can anybody help me??
thank uuuuu!!

---

### Post by God of the Meeps on 2007-11-07
Is it just the regular ALT key? If so, that is the corresponding Windows START key, and I don't think that is actually supposed to do anything on Ubuntu.

---

### Post by cyberdork33 on 2007-11-07
> **God of the Meeps said:**
> Is it just the regular ALT key? If so, that is the corresponding Windows START key, and I don't think that is actually supposed to do anything on Ubuntu.
Alt is Alt on my install.

The Windows Key (or Apple / Command Key) is referred to as 'super' in linux.

---

### Post by Levo75 on 2007-11-08
> **rubberglove said:**
> Hi - 

Did you have to do anything special to get the 'Fn' key to work? 
I got the same keyboard last week - and love it - but the 'Fn' key (and so the volume keys and brightness keys) doesn't seem to do anything... 

Checking it in Xev, it has no effect at all, alone or in combination with other keys.

Maybe I need to adjust some X or gnome settings?

From what I understood, the 'special keys' would require a kernel patch?

Well i don't have an FN key...

---

### Post by bennyp on 2007-11-09
This is slightly OT, but does anyone have a source on configuring GNOME (or for that matter, any DE) to use the mac os x style keyboard shortcuts? IE Super-W instead of alt-f4, etc.

---

### Post by rubberglove on 2007-11-10
> **Levo75 said:**
> Well i don't have an FN key...

no 'fn' key? On the wired aluminum keyboard it's just to the left of the 'home' key, below the f13 key, and above the forward delete key...

---

### Post by superm1 on 2007-12-09
fn key doesn't work for me either on the brand new aluminum wireless one.  Not sure what to do about it.  Nothing in xev or anything.

---

### Post by Sunnz on 2007-12-09
Hmmm does anyone know which driver is responsible for the Keyboard? Maybe it need an update.

---

### Post by Seq on 2007-12-10
A patch has been created in [bug 163725]("https://bugs.edge.launchpad.net/ubuntu/+source/linux-meta/+bug/162083") for the macbook 3,1. This was based off a patch from the mactel-devel mail list that added support for the ANSI aluminum keyboard. The recent version of the patch also adds support for ISO and JIS variants.

This has already been patched in my ppa, so you could always try updating your kernel from that. Or build your own kernel with the patch in that bug. Or better yet, try to find out how we can get the ubuntu kernel updated...

```
deb http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
deb-src http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
```

For more information, check out the [macbook santa rosa thread]("http://ubuntuforums.org/showthread.php?t=610375").

On rereading this message, I should point out that it adds support for the ANSI, ISO, and JIS variants of the wired and wireless aluminum keyboards, in addition to the new macbook keyboard.

---

### Post by cyberdork33 on 2007-12-10
> **Seq said:**
> This has already been patched in my ppa, so you could always try updating your kernel from that. Or build your own kernel with the patch in that bug. Or better yet, try to find out how we can get the ubuntu kernel updated...
Probably won't be updated soon... i guess it is possible, but they tend not to unless absolutely needed. Filing the bug is the only thing you really can do to get changes made. Just give lots of support to the bug report and hopefully the changes will get integrated into the future kernels.

---

### Post by superm1 on 2007-12-10
> **Seq said:**
> A patch has been created in [bug 163725]("https://bugs.edge.launchpad.net/ubuntu/+source/linux-meta/+bug/162083") for the macbook 3,1. This was based off a patch from the mactel-devel mail list that added support for the ANSI aluminum keyboard. The recent version of the patch also adds support for ISO and JIS variants.

This has already been patched in my ppa, so you could always try updating your kernel from that. Or build your own kernel with the patch in that bug. Or better yet, try to find out how we can get the ubuntu kernel updated...

```
deb http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
deb-src http://ppa.launchpad.net/chrisirwin/ubuntu gutsy main
```For more information, check out the [macbook santa rosa thread]("http://ubuntuforums.org/showthread.php?t=610375").

On rereading this message, I should point out that it adds support for the ANSI, ISO, and JIS variants of the wired and wireless aluminum keyboards, in addition to the new macbook keyboard.
Matter of fact it's been added upstream already:
[http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=commitdiff;h=18947e227b295bc65ffa38401e151f08231828a0](http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=commitdiff;h=18947e227b295bc65ffa38401e151f08231828a0)
[http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=commitdiff;h=82bc1bf6e6e76a1adb6095303d08ec55e1e0362f](http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=commitdiff;h=82bc1bf6e6e76a1adb6095303d08ec55e1e0362f)

If we don't get those for "free" with 2.6.24 in hardy, those are the commits to reference at least.

Unfortunately the patch doesn't work for my apple keyboard though (bluetooth wireless aluminum).  Enabling those quirks is dependent upon the usbhid driver instead of the generic input driver only.

---

### Post by Seq on 2007-12-10
> **superm1 said:**
> Matter of fact it's been added upstream already:
[http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=commitdiff;h=18947e227b295bc65ffa38401e151f08231828a0](http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=commitdiff;h=18947e227b295bc65ffa38401e151f08231828a0)
[http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=commitdiff;h=82bc1bf6e6e76a1adb6095303d08ec55e1e0362f](http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=commitdiff;h=82bc1bf6e6e76a1adb6095303d08ec55e1e0362f)

If we don't get those for "free" with 2.6.24 in hardy, those are the commits to reference at least.

Unfortunately the patch doesn't work for my apple keyboard though (bluetooth wireless aluminum).  Enabling those quirks is dependent upon the usbhid driver instead of the generic input driver only.

It looks like that patch adds the wired keyboards only, though it does clean up the code a bit to change powerbook* to apple*, which makes more sense.

The missing codes are (directly from the ubuntu launchpad bug, so they may need to be renamed). The quirks list would also need to be added.
```
/* macbook3,1 keyboards */
#define USB_DEVICE_ID_APPLE_GEYSER4_HF_ANSI    0x0229
#define USB_DEVICE_ID_APPLE_GEYSER4_HF_ISO     0x022a
#define USB_DEVICE_ID_APPLE_GEYSER4_HF_JIS     0x022b

/* Apple 2007 Wireless keyboards */
#define USB_DEVICE_ID_APPLE_WIRELESS_KEYBOARD_ANSI	0x022c
#define USB_DEVICE_ID_APPLE_WIRELESS_KEYBOARD_ISO	0x022d
#define USB_DEVICE_ID_APPLE_WIRELESS_KEYBOARD_JIS	0x022e
```

---

### Post by superm1 on 2007-12-10
> **Seq said:**
> It looks like that patch adds the wired keyboards only, though it does clean up the code a bit to change powerbook* to apple*, which makes more sense.

The missing codes are (directly from the ubuntu launchpad bug, so they may need to be renamed). The quirks list would also need to be added.
```
/* macbook3,1 keyboards */
#define USB_DEVICE_ID_APPLE_GEYSER4_HF_ANSI    0x0229
#define USB_DEVICE_ID_APPLE_GEYSER4_HF_ISO     0x022a
#define USB_DEVICE_ID_APPLE_GEYSER4_HF_JIS     0x022b

/* Apple 2007 Wireless keyboards */
#define USB_DEVICE_ID_APPLE_WIRELESS_KEYBOARD_ANSI    0x022c
#define USB_DEVICE_ID_APPLE_WIRELESS_KEYBOARD_ISO    0x022d
#define USB_DEVICE_ID_APPLE_WIRELESS_KEYBOARD_JIS    0x022e
```


Ah yes, I did overlook that part.  Let me give Chris's PPA a shot.

---

### Post by superm1 on 2007-12-11
Well, Chris's PPA only included support for amd64.  I rebuilt it for i386 locally and then tried to load those modules.

As I had suspected, still doesn't work with my keyboard :(

---

### Post by Seq on 2007-12-12
> **superm1 said:**
> Well, Chris's PPA only included support for amd64.  I rebuilt it for i386 locally and then tried to load those modules.

As I had suspected, still doesn't work with my keyboard :(

I noticed you commented on that bug. but it is unclear if you tried building with the most recent attached patch from there, or if you just tried the cwi2 package (rebuilt) and looked at the recent patch.

Anyway, I've updated the package to cwi3, and that includes the most recent version of the patch (wireless ids, international support), though as you said, it may not work anyway due to the hid-quirks being part of the _usb_hid driver.

cwi3 has finished building for AMD64, but only started for i386 30 minutes ago. i386 should build this time, however.

---

### Post by superm1 on 2007-12-12
> **Seq said:**
> I noticed you commented on that bug. but it is unclear if you tried building with the most recent attached patch from there, or if you just tried the cwi2 package (rebuilt) and looked at the recent patch.

Anyway, I've updated the package to cwi3, and that includes the most recent version of the patch (wireless ids, international support), though as you said, it may not work anyway due to the hid-quirks being part of the _usb_hid driver.

cwi3 has finished building for AMD64, but only started for i386 30 minutes ago. i386 should build this time, however.
Well in my local build I checked to make sure the hid-quirks were updated to include the wireless ids. So as mentioned, it sounds like those need to be moved elsewhere.  Where that elsewhere is yet, i'm not sure :)

---

### Post by Ogonzz on 2008-05-29
I can't seem to get the numpad working on my apple keyboard...any suggestions?

---

### Post by cyberdork33 on 2008-05-29
Please post in the new Apple Forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by US41 on 2008-06-13
I bought one. Brought it home, replaced the other USB keyboard with it, and my PC won't even boot up. It just says "starting..." and dies. Replace the keyboards, reboot, no problems. 

I'm using 8.04 Hardy Heron.

---

### Post by defendguin on 2008-07-15
I am seriously considering buying this keyboard.  my current keyboard is a POS do you guys think the bugs will get worked out shortly?  

US41 are you still not able to boot with this keyboard?

---

### Post by defendguin on 2008-07-15
US41 have you tried the kernel with the patch suggested in this launchpad bug?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887)

---

### Post by cyberdork33 on 2008-07-16
> **defendguin said:**
> US41 have you tried the kernel with the patch suggested in this launchpad bug?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887)
This is an old thread. You should post in the new Apple Forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

